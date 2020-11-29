```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Title</title>
</head>
<body>
<canvas id="canvas" width="500" height="200"></canvas>
<button id="rec" disabled>record</button>

<script>
    var cStream,
        aStream,
        vid,
        recorder,
        analyser,
        dataArray,
        bufferLength,
        chunks = [];

    function clickHandler() {

        this.textContent = 'stop recording';
        cStream = canvas.captureStream(30);
        cStream.addTrack(aStream.getAudioTracks()[0]);

        var mixedStream = 'MediaStream' in window ? new MediaStream([cStream.getVideoTracks()[0], aStream.getAudioTracks()[0]]) : cStream;
        recorder = new MediaRecorder(mixedStream);
        recorder.start();

        recorder.ondataavailable = saveChunks;

        recorder.onstop = exportStream;

        this.onclick = stopRecording;

    };

    function exportStream(e) {

        if (chunks.length) {

            var blob = new Blob(chunks);
            var vidURL = URL.createObjectURL(blob);
            var vid = document.createElement('video');
            vid.controls = true;
            vid.src = vidURL;
            vid.onend = function() {
                URL.revokeObjectURL(vidURL);
            };
            document.body.insertBefore(vid, canvas);

        } else {

            document.body.insertBefore(document.createTextNode('no data saved'), canvas);

        }
    }

    function saveChunks(e) {

        e.data.size && chunks.push(e.data);

    }

    function stopRecording() {

        vid.pause();
        this.disabled = true;
        recorder.stop();

    }

    function initAudioStream(evt) {
       
        var audioCtx = new AudioContext();
        // create a stream from our AudioContext
        var dest = audioCtx.createMediaStreamDestination();
        aStream = dest.stream;
        // connect our video element's output to the stream
        var sourceNode = audioCtx.createMediaElementSource(this);
        sourceNode.connect(dest);
        // start the video
        this.play();

        // just for the fancy canvas drawings
        analyser = audioCtx.createAnalyser();
        sourceNode.connect(analyser);

        analyser.fftSize = 2048;
        bufferLength = analyser.frequencyBinCount;
        dataArray = new Uint8Array(bufferLength);
        analyser.getByteTimeDomainData(dataArray);

        // output to our headphones
        sourceNode.connect(audioCtx.destination);

        startCanvasAnim();

        rec.onclick = clickHandler;
        rec.disabled = false;
    };

    var loadVideo = function() {

        vid = document.createElement('video');
        vid.crossOrigin = 'anonymous';
        vid.oncanplay = initAudioStream;
        vid.src = 'https://vdept.bdstatic.com/58716268334863327079447651457571/705a43446e363557/9f08b29f52e9374d84421451d487d706e7167f8bc9c81948f27f76e3c59df9d6626304ffe8968dcb8336c0d0ca0bb263.mp4?auth_key=1596881668-0-0-3d15dbb0b8ce4c64e518903bbc31f1e2';
        document.body.append(vid);

    };

    function startCanvasAnim() {
        // from MDN https://developer.mozilla.org/en/docs/Web/API/AnalyserNode#Examples
        var canvasCtx = canvas.getContext('2d');

        canvasCtx.fillStyle = 'rgb(200, 200, 200)';
        canvasCtx.lineWidth = 2;
        canvasCtx.strokeStyle = 'rgb(0, 0, 0)';

        var draw = function() {

            var drawVisual = requestAnimationFrame(draw);

            analyser.getByteTimeDomainData(dataArray);

            canvasCtx.fillRect(0, 0, canvas.width, canvas.height);
            canvasCtx.beginPath();
            canvasCtx.drawImage(vid, vid.width, vid.height, canvas.width, canvas.height, canvas.width / 2, 0, canvas.width / 2, canvas.height);
            canvasCtx.drawImage(vid, vid.width, vid.height, canvas.width, canvas.height, 0, 0, canvas.width / 2, canvas.height);
            /* var sliceWidth = canvas.width * 1.0 / bufferLength;
            var x = 0;

            for (var i = 0; i < bufferLength; i++) {

              var v = dataArray[i] / 128.0;
              var y = v * canvas.height / 2;

              if (i === 0) {
                canvasCtx.moveTo(x, y);
              } else {
                canvasCtx.lineTo(x, y);
              }

              x += sliceWidth;
            }

            canvasCtx.lineTo(canvas.width, canvas.height / 2); */
            canvasCtx.stroke();

        };

        draw();

    }

    loadVideo();
</script>

</body>
</html>
```

