- 没有重载，但可以实现重载效果

  可以通过arguments.length 来拿到实际传过来的参数个数实现。

  ```javascript
  function doAdd(num1, num2){
    if(arguments.length===1){
      //处理一个参数的逻辑
    }else if(arguments.length ===2){
      //处理一个参数的逻辑
    }
  } 
  
  //也可以 根据通过判断num1,num2是否为undefined判断
  function doAdd(num1, num2){
    if(num1!==undeined&&num2===undefined){
      //处理一个参数的逻辑
    }else if(num1!==undeined&&num2!==undefined){
      //处理一个参数的逻辑
    }
  } 
  ```

- arguments在严格模式和非严格模式下的区别

  ```javascript
  //严格模式下 arguments[1]和num2互不影响
  function doAdd(num1,num2){
      "use strict";
      arguments[1] = 10; //num2=2
      num2 = 20          //arguments[1]=10
      console.log(num2);
  }
  //非严格模式下 arguments[1]和num2同步变化
  function doAdd(num1,num2){
      arguments[1] = 10; //num2=10
      num2 = 20          //arguments[1]=20
      console.log(num2);
  }
  doAdd(1,2);
  ```
  
  
  
  



