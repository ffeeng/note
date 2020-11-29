### webpack中有用函数

```
//记住无参函数的值
const memorize = fn => {
 let memorized = false;
 /** @type {T} */
 let result = undefined;
 return () => {
  if (memorized) {
   return result;
  } else {
   result = fn();
   memorized = true;
   // Allow to clean up memory for fn
   // and all dependent resources
   fn = undefined;
   return result;
  }
 };
};

module.exports = memorize;
```