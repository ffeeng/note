## 设置样式

1. :class="myClass"

2. :style="myStyle"

3. element.style.width=''100px"

4. element.style.cssText=''100px !important"

5. element.style.cssText=''100px !important"

6. element.setAttribute('style', 'height: 100px !important');

7. element.style.setProperty('height', '300px', 'important');

8. elmenet.className = ''myClass";

9. element.classList.add("myClass");

10. ```js
    document.styleSheets[0].addRule('.box', 'height: 100px');
    document.styleSheets[0].insertRule('.box {height: 100px}', 0);
    ```
11. ```js
    var styleEl = document.createElement('style'),
    styleSheet = styleEl.sheet;
    styleSheet.addRule('.box', 'height: 100px');
    styleSheet.insertRule('.box {height: 100px}', 0);
    document.head.appendChild(styleEl);  
    ```

