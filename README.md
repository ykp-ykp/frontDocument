		箭头函数和es5中的function的不同
1：箭头函数本身没有this，他在定义的时候this就已经确定了，指向其上层作用域
2：箭头函数没有arguments参数、Prototype属性，如果要实现的话，可以使用rest方式，如let fn = (...rest){}
3：箭头函数不能使用new关键字1：因为使用new关键字创建对象的时候，会将构造函数的Prototype属性赋值给实例对象
的__proto__属性，但是箭头函数没有Prototype属性；2：箭头函数没有自己的this，这与new执行时生成的新对象的this不符合
4：因为箭头函数不具备this，arguments等，所以其也不能使用call、apply、bind方法去改变this指向。
