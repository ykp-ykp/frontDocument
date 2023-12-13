JS篇
js的8个数据类型
o number：数字类型，取值范围为-2^53-1到2^53-1
o string：表示文本数据
o boolean：只有两个值：false、true
o null：只有一个值：null
o undefined：一个没有被赋值的变量会有一个默认值undefined
o bignit（es11）：是一个基础的数值类型，可以表示任意精度的整数，不能表示浮点数。
定义方法：const num = 123n；（需要后缀n，用于区别number）const num = BigInt(123)；
数学运算符（加减乘除）：number类型的运算符都可以使用，但是两者不能通过运算符操作
比较：number类型和bigint类型可以使用==比较，不能使用===比较（因为数据类型不一样）
BigInt(0)进行布尔运算时为false
o symbol（es6）：是唯一且不可变的值，通常用作属性的键值。
o object：Math、Date、Array、Function、RegExp
	前7中属于基本数据类型，存储在栈中，所有的基本数据类型本身是无法被修改的，所谓的修改只是重新创建了一个。
Date对象使用：
o new Date()和Date.now()都是返回时间戳。另外有getYear（当前年-1900的数字）、getFullYear（4位数年份）、getMonth（0-11）、getDate（月份中的某一天）、getDay（星期0-6）、getHours（0-23）、getMinutes（0-59）、getSeconds（0-59）；以上方法均对应的有set方法，比如setFullYear、setMonth等。new Date().format(‘YYYY-MM-DD HH:mm:ss’)格式化日期。
script标签中的defer和async属性的区别
defer和async属性都仅适用于外部脚本，如果script标签没有src属性，尽管写了defer或async属性也会被忽略。
o script ：会阻碍 HTML 解析，只有下载好并执⾏完脚本才会继续解析 HTML。
o async script ：解析 HTML 过程中进⾏脚本的异步下载，下载成功⽴⻢执⾏，有可能会阻断 HTML 的解析。
o defer script：完全不会阻碍 HTML 的解析，HTML 文档解析完成之后再按照顺序执⾏脚本。
引用数据类型使用==和===与基本数据类型使用==和===的区别是什么？
o 对于基本类型，==比较值，===比较值和类型。
o 引用类型使用==和===时，效果是一样的，因为不涉及类型转换，只会比较对象的内存地址。
for in 和 for of的比较
o for...in用于遍历对象的可枚举属性（key值），包括原型链上的属性（可使用hasOwnProperty来排除原型链上的属性）。
o for...of用于遍历可迭代对象，如数组、Map、Set、字符串等。
person.key和person[key]的区别
person.key是静态访问属性（意思是“key”就是person的一个属性）。person[key]是动态访问属性（key是变量）。
let person = {name : "闫昆鹏"}
for(let key in person){console.log(person.key，person[key])    //undefined、闫昆鹏}
typeof和instanceOf用法
typeof返回一个表示数据类型的字符串，可以判断基本数据类型（除了null返回object之外，其他6种返回都正确）。instanceof运算符返回一个布尔值，可以判断对象的具体类型。
find、findeIndex函数
o find 函数的返回值只能是满足条件的一个元素本身或undefined（不论return语句返回什么），回调函数的 return 值不会污染 find()和findIndex()方法的返回值。
o findeIndex函数它与 find 方法类似，返回的值只能是满足条件的元素在数组中的索引或-1，而不能是其他任何值。
const i= list.findIndex(item => {
      return item.id === 2 });
foreach、filter、map、some方法比较
o forEach方法的目的是为了遍历数组，并在每个元素上执行回调函数，他不关心是否有return语句，即使有也会被忽略，并不会影响forEach的遍历过程。
o filter方法是一个用于过滤数组的方法,它会遍历数组中的每个元素,并返回一个符合过滤条件的新数组，其需要返回一个boolean值，true表示当前元素符合过滤条件,会被包含在新数组中，反之则被过滤掉。
o map常用于对数组元素进行一系列的操作和变换。方法会对每一个元素执行一个回调函数，而这个回调函数期望返回一个值，以便将其添加到新的数组中，如果回调函数中没有显示的return语句，那么会默认返回undefined，反之返回的就是return后面的值。因此map方法最终返回的数组长度与原数组长度一定相等。
o some用来检测数组中的元素是否满足指定条件，每个元素执行一个回调函数，如果有一个返回true，则some方法就不继续往下执行且返回true，如果所有元素的回调都返回false，则some方法返回false。Arr.some(callback(item,index,arr){},)
o 总结：上面三种方法的回调函数都可以接受三个参数：（item，index，arr）分别表示数组中的元素，对应的索引，原始数组，并且后面两个可以省略。
concat、assign、reduce方法
o concat方法：属于Array的方法，用于连接数组，可以接受多个参数（参数可以是数组也可以是基本类型），返回一个新的数组，并不会改变原数组，let res = arr.concat(arr1，2，arr2，’xiaoming’)。 （实现数组扁平化）
o assign方法：属于Object的方法，用于将对象中的所有可枚举属性全部复制到另一个对象中，并且可以覆盖原有属性的值，该函数是直接修改（目标）target对象，并返回。其可以接收一个目标对象和多个源对象，并且目标对象和源对象可以是不同类型，只要其中具有可枚举属性即可。Object.assign(target,source1,source2,….)，。适用于数组、对象，不适用于Set、Map、字符串等。（虽然字符串属于具有可枚举属性，但是其是只读的，字符串具有一旦创建就不可更改的特性）
o reduce方法：属于Array的方法，接收一个或两个参数，第一个是callback函数；第二个是可选参数，用作初始值传递给callback中的累加器，arr.reduce((accumulator, cur, index, arr) => {}, init)；accumulator表示累加值，上次callback的返回值会传递给accumulator。（如果传递了第二个参数，那么cur从数组的第一个元素开始，反之则从数组的第二个元素开始）
number和string之间的转换和运算
o 字符串转数字：parseInt、Number、parseFloat；parseInt遇到非数字字符会立刻停止（除了开头符号为’-‘），而Number可以转换各种类型数字，并且是对整体进行转换，如果转换失败则返回NaN。例如：
let a2 = '1231qwe';
    console.log(parseInt(a2)) //1231
    console.log(Number(a2))	//NaN
o 数字转字符串：1：通过字符串拼接：num + ‘’；2：使用String函数：String(num)；3：使用toString方法：num.toString()；4：使用模板字符串：`${num}`；
运算
o 相加：当字符串和数字进行相加操作时，js会将数字转换为字符串，在于另外一个字符串进行拼接。
o 相减：当字符串和数字进行相减操作时，无论是字符串在前还是在后，js都会尝试将字符串转换为数字，再进行相减操作。如果字符串不能转换为数字，那么将直接返回NaN。（相乘、相除操作类似）
作用域和作用域链
作用域
o 作用域类别：在es6之前，js的作用域只有全局作用域和函数作用域。ES6提供了块级作用域，可以通过let和const来声明。
o 作用范围：在代码的任何地方都能访问的对象是全局作用域，一般是定义在最外层的函数、变量和未定义直接赋值的变量；块级作用域里面的变量只能在该代码块中访问，并且不存在变量提升。
作用域链
o 解释：当js运行时需要使用到某个变量，那么js引擎会首先尝试在当前作用域下寻找该变量，如果找不到，就去上层作用域寻找，直到到达全局作用域，如果还是没有找到则报错。
Let、Const、Var声明变量
o let 和 const 的作用域都是块级作用域，不存在变量提升；const声明变量的时候必须初始化；二者在同一个块内都不可以重复声明同一个变量。Const声明的对象和数组等内部的值是可以改变的，只是其引用的地址不能变。
o 作用域范围：var声明的变量是函数作用域或全局作用域，let声明的变量是块级作用域。
o 变量提升：指的是变量的声明会被提升到当前作用域的顶部,但是赋值不会提升。如下：
console.log(num); // undefined
var num = 10;
上面的代码相当于下面：
var num;
console.log(num); // undefined
num = 10;
o let和var的区别：能否重复声明、作用域范围、是否存在变量提升。
o 在js中，如果声明一个变量时没有使用let、const、var等去声明，那么这个变量将被视为全局变量，属于window。
o for循环内使用var和let：
注：上面代码中，变量i是let声明的，当前的i只在本轮循环有效，所以每一次循环的i其实都是一个新的变量，所以最后输出的是6。你可能会问，如果每一轮循环的变量i都是重新声明的，那它怎么知道上一轮循环的值，从而计算出本轮循环的值？这是因为 JavaScript 引擎内部会记住上一轮循环的值，初始化本轮的变量i时，就在上一轮循环的基础上进行计算。
另外，for循环还有一个特别之处，就是设置循环变量的那部分是一个父作用域，而循环体内部是一个单独的子作用域。以下左侧代码中的{}内可以使用let重新声明变量i，就说明这个i与循环变量i不在同一个作用域，而是有各自单独的作用域。（因为同一作用域下，不能使用let声明同一个个变量）
o 暂时性死区：只要块级作用域内存在let命令，它所声明的变量就会“绑定”（binding）这个区域，不再受外部的影响。上面右侧代码中，存在全局变量tmp，但是块级作用域内let又声明了一个局部变量tmp，导致后者绑定这个块级作用域，所以在let声明变量前，对tmp赋值会报错
数组和对象的解构赋值
o 数组解构赋值：let a = [1,2,3]; let [a1,a2,a3] = a;
o 对象的解构赋值：let people = {name : “ykp”, age : 23}; let {name,age} = people;
注意点：1：如果要解构的属性名在对象中不存在,则该属性值为undefined。（let {name1，age} = people）
2：可以为属性命名一个新名称。（let {name：firstName} = people;console.log(firstName)//ykp）
3：可以设置默认值,在属性不存在或值为undefined时生效。（let {name = “csy”} = people）
组||和&&的返回值
o ||：如果第一个数为真，返回第一个；如果第一个为假，返回第二个。
o &&：如果第一个数为真，返回第二个；如果第一个为假，返回第一个。
JS事件循环机制（事件循环是js的异步实现方式，js单线程是异步产生的原因）
o Js是单线程的，同一时间只能做一个事情，其通过事件循环机制来实现单线程异步执行的。
o 如何理解JS的异步：执行js代码的线程其实只有一个，就是浏览器提供的渲染主线程（也叫js引擎线程）（所以js是单线程的），而渲染主线程承担着诸多的工作，如解析HTML、CSS、执行JS代码等；如果采用同步方式，那么渲染主线程将必须等待定时器、http请求等任务结束之后才能继续执行，会导致页面的阻塞，并且大大浪费主线程的时间。为了能够执行异步任务，浏览器提供了定时器线程、http请求线程、事件监听线程等，这些代码都不是用来跑js代码的。当渲染主线程遇到这些任务时，就交由对应的线程去执行，自身则立即结束任务的执行，转而继续执行下面的代码。当其他线程完成任务时，将回调函数添加到任务队列的队尾，等待主线程调用。
o 浏览器不仅有多个线程，还有多个进程，如渲染进程、GPU进程和插件进程等，渲染进程就包含了渲染主线程、http请求线程、定时线程等。这些线程为js异步执行提供了基础。
o 执行栈：Js在解析一段代码时，会将同步代码按顺序放入执行栈中去执行并弹出。当遇到异步任务时就交给其他线程处理，待当前执行栈中所有同步代码执行完之后，会从任务队列中依次取出已完成的异步任务的回调加入执行栈中继续执行，遇到异步任务时又交给其他线程，如此循环往复。
o 微任务和宏任务：任务队列不只有一个，有微任务队列和宏任务队列。
o 事件循环的过程中，执行栈在同步代码执行完成之后，会无限循环检查任务队列，其中首先检查微任务队列是否有任务需要执行，如果没有，再去宏任务队列检查是否有任务执行，如此往复循环，中间再遇到异步任务时又交给其他线程去执行。微任务一般在当前循环就会优先执行，而宏任务会等到下一次循环，并且微任务队列只有一个，宏任务队列可以有多个。
o 微任务：promise.then()、promise.catch()、process.nextTick()、async、await等。为任务的优先级高于宏任务。
o 宏任务：setTimeout()、setInterval()、Ajax、DOM事件、点击事件、键盘事件等。目前浏览器都出了新的标准，不在只有一个宏任务队列了，而是根据任务类型划分队列，相同类型任务必须在同一队列中，且不同队列的优先级不同。
JS中监听器的使用：
监听器绑定事件
function test() {
  console.log('test invoked')
  return () => {  console.log('callback invoked')  }
}
document.addEventListener('click', test())
o 这里的 test函数只会在注册监听时被执行一次，它返回了一个箭头函数。这个箭头函数才是真正的回调函数，会在每次点击事件触发时执行。如果想每次触发点击事件时都执行test函数，应该写成document.addEventListener('click', test)，或者这样写：document.addEventListener('click', ()=>{  test()  })
o 注：function()代表的是被执行后函数返回的值。function代表的是函数自身，一般被作为参数传递给另一个函数。
标签中进行事件绑定
<input v-on:input="debounce()" type="text" />
debounce() { 
let t = null;   console.log("debounce"); 
return function () { console.log("debounce返回函数"); };
}
当触发input事件时，只会输出“debounce”，是否证明了，绑定的是函数debounce，而并非他返回的函数。这一点与监听器绑定不同。如果想达到监听器一样的效果，需要另外声明一个变量debounceFn = debounce() 来接受返回函数，然后input事件绑定debounceFn 即可。
防抖和节流：
防抖和节流都是对高频触发事件的一种优化，但是两者也有很明显的区别。
防抖：当用户快速多次触发同一个事件时，只执行最后一次操作，常用于输入框动态搜索、滚动条的scroll事件
节流：是指在固定一段时间内的所有操作只能成功一次。
正则表达式
o 正则表达式的创建方法：
字面量形式：const regex = /hello/g;
构造函数方式：const regex = new RegExp(“hello”,g);
上面的g是一种修饰符，表示全局匹配。除此之外还有：m、i(不区分大小写)等
o 字符串的方法：
①　str.match(regExp)：用于在字符串中检索与正则表达式匹配的内容。如果参数regExp没有全局标志g，则match()函数只查找第一个匹配，并返回包含查找结果的数组，该数组对象包含如下成员:匹配的子字符串、索引、完整字符串，如果没有匹配，则返回 null。如果设置全局标志g，则match()函数会查找所有的匹配，返回的数组是匹配的所有结果，不包含额外的属性。（返回数组类型）
②　str.search(regExp)：查找第一个与正则表达式相匹配的子串的索引，如果没有则返回-1。（返回number类型）
③　str.replace(regExp,newStr)：使用子串替换掉字符串中的指定内容，它返回一个新的字符串，原字符串不变（使用修饰符g可以替换所有，不适用只替换第一个子串）。（返回string类型）
④　str.split(regExp)：使用正则表达式作为分隔符，将字符串进行分隔，返回一个分隔后的数组。（返回数组类型）
o RegExp方法：
①　regExp.test(str)：检测字符串是否匹配正则表达式。（返回boolean类型）
②　regExp.exec(str)：匹配字符串，并返回匹配得到的结果，这个方法基本上不怎么实用，功能与str.match比较相似。
使用二进制实现菜单权限管理
①　假设权限分配如下：read-0001，write-0010，del-0100，update-1000。
②　二进制运算：与运算：只有当两个同时为1时才为1，其他为0。或运算：两个有一个为1就为1，两个都为0时才为0。异或运算：相同为0，不同为1。非运算：把整个二进制位全部反转，0变成1，1变成0。
③　菜单权限操作：设小明（xm）的权限现在只有read，即二进制位为0001。
判断小明是否有读权限：console.log(xm & read)，0表示无，其余表示有
现在给小明添加写权限：xm = xm | write，之后xm二进制位为：0011。
现在给小明删除读权限：xm = xm ^ read，之后xm二进制位为：0010。
Promise知识点
o 支持链式调用，可以解决地狱回调，指定回调的方式更为灵活
o ☆☆Promise函数：它有三种状态：pending、fulfilled、rejected。一般用于封装异步操作，通常异步操作执行成功之后调用resolve函数，执行失败调用reject函数，通过这两个方法来改变Promise对象的状态，之后才会执行后面的then或catch函数并立即返回一个Promise对象（而不是执行then里面的回调函数）。当Promise对象转变为失败时，如果没有catch或then中的第二个函数来捕获，那么程序将报错。Promise函数对象拥有方法：resolve()、reject()、all()、any()等；Promise实例对象拥有方法：then、catch、finally。
o executor函数：它是Promise函数的一个形参，是一个执行器函数，并且这个执行器函数是同步调用的（被当作同步代码执行）。new Promise((resolve,reject)=>{})，里面的箭头函数就是执行器函数。只有在执行器函数内部才能够改变Promise对象的状态。
o 终止Promise链条的执行有且只有一种方法：在then函数中返回一个pending类型的Promise对象，后面的then或catch或finally方法都将不会执行。
o Promise的状态：即Promise对象的一个属性：PromiseState，其有三个值，分别为：pending、fulfilled/resolve、rejected。他的状态改变只有两种，pending->fulfilled（成功）或者pending->rejected（失败），并且只能变换一次。改变对象状态只有三种方式：在executor 函数中调用resolve、reject方法、通过throw抛出错误。并且只有Promise对象的状态发生改变的时候，才会调用回调函数then、catch等。
o Promise对象的值：实例对象中另一个属性：PromiseResult，保存的是异步任务成功或失败的结果，只能由resolve或reject函数去修改这个属性的值。
o ☆☆then函数：then函数内部可以接受两个函数形式的参数，第一个函数用于Promise对象成功的回调（resolve函数），第二个函数用于Promise对象失败的回调（reject函数），通常只写一个，且表示成功的回调。并且then()方法返回的也是一个Promise对象（与下面的Promise函数方法resolve返回情况一样），如果其返回的Promise对象状态为pending，那么将中断Promise链条的执行。如果then方法内部的函数没有return语句，那么默认返回undefined，返回的Promise状态为成功，值为undefined。
o catch函数：只能表示Promise对象失败的回调。
o finally函数：无论Promise对象的状态为失败还是成功最终都会执行。
o resolve函数：为Promise函数对象所拥有的函数（实例对象没有改方法），let p = Promise.resolve(参数)，其返回值分为两种情况：1：如果传入的参数是非Promise类型的对象，则返回的结果为成功状态的Promise对象（没有return语句默认返回undefined）。2：如果传入的是Promise类型对象，那么返回的Promise对象的状态取决于传入的Promise对象的状态，与传入的对象状态相同。
o reject函数：为Promise函数对象所拥有的函数（实例对象没有改方法），let p = Promise.reject(参数)，无论传入任何值都只返回一个失败的Promise对象，失败的Promise对象的值为传入的值。（即使传入的是一个成功的Promise对象，返回的也是一个失败的Promise对象）
o all函数：接受一个Promise的数组作为参数，当这个数组里的所有Promise都变为resolved状态时，它才会去调用.then方法。只要有一个Promise失败，那么Promise.all立马就返回失败状态。（适用于并发请求）
o ☆☆Promise函数与微任务队列：Promise中的执行器函数属于同步执行，会被当作同步代码立即执行用于初始化Promise对象，当在执行器函数中调用resolve或者reject函数以后（或者说Promise对象的状态发生变化时），会将后面跟的then或catch中的回调函数（比如then(resolve)中的回调函数resolve）加入到微任务队列中，但是Promise对象会立即返回，只是暂时状态为pending，之后才根据回调函数resolve的返回值来确定then函数返回的Promise对象的状态。
Async-await
o Async：用于修饰一个函数，表示该函数为一个异步函数，异步函数的返回值永远是一个Promise对象。async函数内部的代码可以有同步的也可以有异步的，异步的是指使用await调用的async函数。
o Await的阻塞作用：await通常是在async函数内部使用，当执行到await时，其会暂停下面语句的执行，等待Promise处理完成之后（被调用的async函数返回的对象promise状态变为resolved），才会继续执行下面的代码。如果被调用的async函数返回的Promise对象状态是pending，那么后面的代码就会一直等待，不执行。其实await下面的代码就相当于then函数中的回调函数，会被加入到微任务队列中，如下：
    async function func1() {
      console.log("func1");
      var a = await func2();
      console.log("func1 return");
}
    function func2() {
      console.log("func2");
}
func1()
遇到await func2()时会先返回一个Promise对象，并执行func2里面的代码，并阻塞await后面的代码执行。await func2()可以看做是func2.then(res => console.log("func1 return"));。

异步编程
o 概念：异步编程允许程序在执行一个长任务时，不用原地等待，可以继续执行下面的代码。直到长时间任务完成之后再以回调函数的形式来执行。
原型与原型链
先想一下基本的构造函数的内容:
function Person(name, age, job) {
 this.name = name;
 this.age = age;
 this.job = job;
 this.sayName = function() { alert(this.name) } 
}
var person1 = new Person('Zaxlct', 28, 'Software Engineer');
var person2 = new Person('Mick', 23, 'Doctor');
o 首先明确几个概念：①Person.prototype叫原型对象；②原型对象是构造函数Person的一个实例对象；③：实例对象都有一个constructor属性指向该实例的构造函数；
o 在这个例子中，person1, person2 都是 Person 的实例，这两个实例都有一个 constructor（构造函数）属性，该属性（是一个指针）指向 他们的构造函数 Person， 即：person1.constructor === Person;并且console.log(person1.constructor)输出为如下：
ƒ Person(name, age, job) {
      this.name = name;
      this.age = age;
      this.job = job;
      this.sayName = function () {
        alert(this.name);
      };
    }
o 这里要记住两个概念： 构造函数，实例： person1 和 person2 都是构造函数 Person 的实例；以及最重要的一点：实例 的 构造函数属性（constructor）指向 构造函数本身。
o 在JS中，构造函数本身首先是一个函数，可以说任意的一个函数 都可以当作构造函数，但是一般在定义自定义构造函数时，要将函数名首字母改用大写的形式，以跟普通函数区分，形式就是上面的 Person 构造函数的形式；另外，JS 的内置函数 Object, Function, Array, String, Number, Boolean, Date 等都是构造函数，跟 Person 差不多，只不过他们只是 JS 内部 出于创建 特定类型的 对象 而自定义的，他们又叫构造器，都是函数对象。
o 在JS中，每个函数（对象(因为函数也是对象)）都会有一个prototype属性（是一个指针）,它指向一个对象——通过该函数创建的实例对象的原型，所以叫原型对象。
o Person.prototype 就是原型对象，我们通过Person.prototype.xxx 这些操作对原型对象进行的 扩展，目的就是 Person 构造函数的所有实例都可以 继承 这些属性。
o 默认情况下，所有的 原型对象 都会包含一个 constructor （构造函数）属性（一个指针），这个属性指向 prototype 属性所在的 构造函数：即：Person.prototype.constructor === Person.
o Person.prototype.constructor === Person
o person1.__proto__ === Person.prototype
o person1.constructor === Person


 
 

CSS篇
Css选择器及其优先级
 
上面的属性选择器格式错了，应该为：[attr]{}、[attr=value]{}等格式，前面不需要有标签。优先级：内联样式 >  id选择器 > 类选择器 > 标签（元素）选择器> 子选择器
Css行内元素和块级元素
o 行内元素不会占据整行，在一条直线上，水平方向排列；块级元素会占据一行，垂直方向排列。
o 行内元素设置width、height无效(可以设置line-height)，上下margin、padding均无效。
o 替换元素：替换元素就是浏览器根据元素的标签和属性，来决定元素的具体显示内容。例如浏览器会根据<img>标签的src属性的值来读取图片信息并显示出来，而如果查看(x)html代码，则看不到图片的实际内容。注：可替换元素类型的行内元素也是可以设置宽和高的，如image、input等。
o 不可替换元素：html 的大多数元素是不可替换元素，即其内容直接表现给用户端（例如浏览器）。例如：<p>段落的内容</p>，段落<p>是一个不可替换元素，文字“段落的内容”全被显示。注：不可替换元素类型的行内元素不可以设置宽和高的，如a、span等。
o 非替换行内元素设置宽高无效，而可替换行内元素设置宽高有效，
o 块级元素：<div>、<p>、<h1>到<h6>、<form>、<table>、<ul><ol><li>:以及<header>、<footer>、<section>等语义化标签。
o 行内元素：<a>、<span>、<img>、<input>、<button>
动画效果-keyframes
o 实现动画效果主要依靠两个关键的特性：@keyframes 和 animation 属性。
o keyframes属性：用于创建动画帧，百分比%值表示动画进行的时间百分比，from和to关键字定义元素的起始状态和结束状态，一个动画中%和from、to可以混用。如下：
@keyframes frame1{ 0% { opacity: 0; } 50% { opacity: 1; transform: scale(1.2); } 100% { opacity: 0; } }
@keyframes frame2{from{transform:rotate(0deg)} 50%{transform:rotate(100deg)} to{transform:rotate(360deg)}}
o animation属性：将keyframes定义的动画应用到元素上，他是一个缩写属性，包含了很多其他的，可以定义动画的名称、时长、时间函数（linear、ease-in加速、ease-out等）等。
o 其他animation属性：animation-delay（动画时长）、~-timing-function（动画时间函数：匀速、加速等）、~-play-state（用于开始和暂停动画）、~-iteration-count（动画播放次数：正整数或infinite）
o 关于阻塞问题：js代码会阻塞部分动画效果，但是不会阻塞transform效果。所以在平时使用动画时，多用transform可以让页面性能和效果达到最佳。
元素水平垂直居中
o 利用绝对定位，先将元素的左上角通过top:50%和left:50%定位到页面的中心，然后再通过translate来调整元素的中心点到页面的中心（子元素的样式）。该方法需要考虑浏览器兼容问题。
o 利用绝对定位，设置四个方向的值都为0，并将margin设置为auto，由于宽高固定，因此对应方向实现平分，可以实现水平和垂直方向上的居中（子元素的样式）。该方法适用于盒子有宽高的情况。
o 使用flex布局，通过设置父元素的align-items:center和justify-content:center使其子元素在垂直和水平方向上为居中对齐。该方法要考虑兼容的问题，该方法在移动端用的较多。
Flex布局
o justify-content：定义主轴上子元素的对齐方式，start、end、center、space-between（起始和结束无空白间隙，中间的空白间距相等）、space-around（两侧留有相等的空白间隔，中间空白间距相等）、space-evenly（包括容器的起始和结束位置，以及每两个子项目之间的间距完全相等）。
o align-items：定义交叉轴上单行/单列元素（行/列内成员）的对齐方式。start、end、center、baseline（是子元素的所有基线对其）、stretch。
o 元素的基线：元素的基线（baseline）是指包含文字或内联元素的盒模型中的一条虚拟的水平线；对于行内元素，基线通常是与文字底端对齐的水平线。对于块级元素，基线通常是元素的底部边缘。
o align-content：当子元素有多行时（假设flex按行排列），可以定义多行中所有元素的对齐方式，无法作用域单行（其属性类似justify-content，（把每行看作是一个子元素））。
o flex-wrap：控制子元素是否换行显示。
Css中可继承属性与不可继承属性有哪些？
o 不可继承属性：display、文本属性（vertical-align、text-decoration、white-space）、盒子模型属性（width、height、margin、padding、border）、背景属性（background、background-color等）、定位属性（float、position、top、right、max-height、）等等。
o 可继承属性：字体系列：font-size、font-family、font-weight；文本text-align、line-height、color
Display的属性值及其作用
o none：元素不显示，并且会从文档流中移除；block：块级元素，默认宽度为父元素宽度，可以设置高度，换行显示；inline：行内元素，默认宽度为内容宽度，不可设置宽度和高度，同行显示；inline-block：默认宽度为内容宽度，可以设置宽高，同行显示；inherit：规定应该从父元素继承display属性的值。
Float浮动流的特点
o 浮动的元素会脱离文档流（标准流），可以让多个盒子排列成一行，直到其触及父元素的框或另一个浮动元素的边框，其在页面中不再占有原来的位置，并且文本会环绕浮动元素；浮动的元素只影响其后面的标准流，不会影响前面的标准流。并且浮动元素换行时只参考其前面那个浮动元素的位置。
o 浮动元素的属性和inline-block极其相似，可以设置宽高，可以设置内外边距，不再独占一行。
o 父元素高度塌陷： 如果父元素只包含浮动元素，而没有清除浮动，会导致父元素高度塌陷，从而影响后面元素的布局。（由于元素脱离原来的文档流，且父盒子没有添加高度属性，那么父盒子无法感知到子盒子的存在，因此父盒子不会被撑开）
o 清除浮动：
· 浮动元素的父元素设置overflow属性为auto、hidden。
· 浮动元素的父元素的伪元素after设置content: "";display: block;clear: both;
· 浮动元素的父元素下面设置一个同级且属性为clear:both的div元素。
元素隐藏的方式
o display：none：将元素完全从渲染树中移除，元素不会占用任何空间，无法响应事件。
o opacity：0，只会使元素透明，元素仍在文档中占据空间，并可以响应事件。
o visibility: hidden:  使元素隐藏，元素仍在文档中占据空间，无法响应事件。
o 通过绝对定位：position: absolute；left：-9999px; （将元素移除可见区域）
元素定位的方式（position）
o static：元素的默认定位方式，其top、left、right等属性无效。
o relative：相对定位，不脱离文档流，元素自己相对于原来位置的定位，通过设置top、left等调整位置。
o absolute: hidden:  绝对定位，会脱离文档流，元素相对于离自己最近的且非static的父元素进行定位，通过设置top、left等调整位置，如果父元素都没有定位，则相对<html>标签定位。如果不设置便宜属性，那么元素会在默认位置。
o fix：固定定位，元素脱离文档流，元素相对于屏幕窗口（viewport）进行定位，不会随着屏幕的滚动而改变位置。
o 当元素设置了定位属性之后，如果不设置偏移量，那么元素会在其默认位置上，不进行偏移。
o 注：元素设置定位之后（static不算），他的z-index属性默认会高于普通元素
伪元素和伪类有什么区别？
o 伪元素：用于在元素前后插入额外的元素或样式，在实际html文档中并不存在。例如::before、::after、::placeholder。通过双冒号指定。
o 伪类：当已有元素处于某种状态时（悬浮、点击等），为其添加特殊的效果，它是在已有元素上添加类别的。例如:hover、:focus、:first-child，通过单冒号指定。
VW、VH和PX有什么区别？
o VW、VH：VW是相对于视图窗口的宽度单位，1vw等于窗口宽度的1%，VH是相对于视图窗口的高度单位，1vh等于窗口高度的1%，二者是用于响应式布局。px则是固定单位，1px等于1个像素，适合用于固定宽高的定位。
rem和em有什么区别？
o Rem：rem是相对于根元素<html>的font-size计算值。
o Em：em是相对于父元素的font-size计算值。如果自身定义了font-size，则相对于自身font-size计算值。
选择器:first-child和first-of-type和nth-child(n)的区别
o 针对下面的first-child和first-of-type和nth-child这三种，首先其前面的A需要是某个元素下的子元素（如果没有，父元素则默认为body）。如果他们外面没有父元素，那么将不起作用
o A:first-of-type：匹配的是某父元素下相同类型子元素中的第一个A，比如 p:first-of-type，就是指所有类型为p的子元素中的第一个。
p:first-of-type  匹配到的是p元素,因为p是div的所有类型为p的子元素中的第一个；
span:first-of-type  匹配到的是第三个子元素span。这里div有两个为span的子元素，匹配到的是它们中的第一个。
o A:first-child：表示在一组兄弟元素中的第一个是A元素，而不是选择A元素的第一个孩子：如下
p:first-child  匹配到的是p元素,因为p元素是div的第一个子元素；
h1:first-child  匹配不到任何元素，因为在这里h1是div的第二个子元素，而不是第一个；
span:first-child  匹配不到任何元素，因为在这里两个span元素都不是div的第一个子元素；
o A:nth-child(n)：根据父元素内的所有兄弟元素的位置来选择子元素。
h1:nth-child(2)  匹配到的是h1元素，因为在div标签下面的第二个子元素是h1
o 注意：如果想要选择某个元素下面的第几个元素，且不限制类型的话，可以这样使用div :nth-child(n){}，注意div和：之间是有一个空格的
 

 
VUE篇
谈谈你对Vue的理解？
官方：Vue是一套用于构建用户界面的渐进式框架，Vue的核心库只关注视图层。

MVVM框架
o MVVM全称为：Model–View–ViewModel。它的核心是ViewModel，其是由前端开发人员组织和维护的。它就像是一个中转站，负责转换 Model 中的数据对象来让数据变得更容易管理和使用，该层向上与视图层（View）进行双向数据绑定，向下与 Model 层通过接口请求进行数据交互，有着承上启下的作用。
o Model：是指数据模型，泛指后端进行的各种业务逻辑处理和数据操控，主要围绕数据库系统展开。
o View：是指视图层，也就是用户界面。View 层展现的不是 Model 层的数据，而是 ViewModel 的数据。
o ViewModel：是指视图模型层，其是由前端开发人员组织和维护的。它就像是一个中转站，负责转换 Model 中的数据对象来让数据变得更容易管理和使用，该层向上与视图层进行双向数据绑定，向下与 Model 层通过接口请求进行数据交互，有着承上启下的作用。

o MVVM和MVC的区别在于：mvvm是数据驱动的，而MVC是dom驱动的。mvvm的优点在于不用操作大量的dom，不需要关注model和view之间的关系，而MVC需要在model发生改变时，手动的去更新view。大量操作dom使页面渲染性能降低，影响用户体验。

VUE的双向数据绑定原理
o 什么是响应式？：就是在改变数据的时候，视图也会跟着更新。
o 数据的双向绑定指的是View和ViewModel之间。
o Vue是采用数据劫持和发布-订阅者模式，通过Object.defineProperty()来劫持数据对象（data中的数据）的属性，追踪属性的变化，并触发setter/getter来通知订阅者数据变化，订阅者收到通知后会调用对应的更新函数来更新视图。在视图的事件监听器中可以修改数据，从而反过来影响数据对象。这样实现了数据和视图之间的双向绑定关系。
VUE中的data为什么写成函数形式
o 因为data是组件的状态数据，当组件被复用的时候，如果data是对象形式的话，因为对象属于引用类型，改变一个组件内的值其他组件也会跟着改变，就无法满足毒箭的独立性和可复用性。而函数形式的data可以将数据隔离起来，各组件之间互不干扰。
VUE模板语法
o Vue模板语法使用{{}}绑定数据，而且里面只能写一个单一的表达式，不可以写条件判断语句。
o v-bind可用于动态绑定元素的属性值，通常用法例子为：v-bind:class=”prop”，如果这样使用：v-bind=”Object”,表示将对象中的属性值绑定到元素的属性上。如Object = {id:”id1”,class:”class1”}。
条件渲染
o v-if：当条件为false时，不会编译和渲染元素，当条件变化时，元素会重新创建或销毁。适用场景：条件不易改变，切换不频繁。
o v-show：包含v-show的元素无论条件真假都会编译，后面只是切换CSS中的display属性来实现是否展示，消耗较低。适用场景：条件容易改变，切换频繁。
v-for的使用
o v-for：既可以遍历数组也可以遍历对象；对象：v-for="(val, key, index) of userInfo"，数组：v-for="(item, index) of result"；遍历数组的时候有两个参数，遍历对象的时候有三个参数，并且顺序不可以修改。
o v-for后面的key通常需要绑定数组对象中的唯一索引值，一般不推荐绑定index，因为当向数组头部中添加或删除元素时，旧数组元素的index会发生变化，会导致所有元素的DOM重新渲染。Key的值只能是字符串或数字类型。
o key的作用：主要是为了高效的更新虚拟DOM，key 作为虚拟节点的唯一标识，在对比新旧节时减少不必要的重复渲染。
1如果不使用key，Vue会尽可能的尝试就地修改/复用相同类型(相同index)元素的算法（如下图）。会导致DOM的无效渲染，过渡效果混乱等问题。

在原来的dom上插入f，如果diff算法没有key值的话，那么在检测到f的时候就会用f来替换c，c替换d，d替换e，再插入e。
所以我们需要使用key来给每个节点做一个唯一标识，Diff算法就可以正确的识别此节点，找到正确的位置区插入新的节点。如下图：

2而使用key时，它会基于key的变化重新排列元素顺序，通过判断新旧节点的key是否相等，从而复用与新节点对应的老节点，节约性能。

前端权限的控制：
控制思路主要分为四大类：
o 菜单的控制：用户在登录请求中会得到权限数据，前端根据权限数据展示对应的菜单。
o 界面的控制：如果用户没有登陆，而是在地址栏中敲入某个页面的地址，则跳转到登陆界面。
o 按钮的控制：在某个菜单界面中，还要根据权限数据，展示出可进行操作的按钮，比如删除、修改、增加。
o 请求和响应的控制：用户通过非法操作，如通过浏览器调试工具发送请求，或者修改按钮状态再发送请求，也应该被前端所拦截。
VUEX的使用
o Vuex基本概念：Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式 + 库。它采用集中式存储管理所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化。
o 如何回答你对Vuex的理解：我们知道，两个子组件之间是无法直接通信的，一般通过父组件作为桥梁来实现通信。但是当共享数据较多、组件嵌套很复杂时这么做就不太可行了，所以Vuex就相当于一个公共数据管理区，来实现组件之间数据的一个共享。
o Vuex核心概念：State、Getter（从store中的state中派生出一些新的状态）、Mutation（更改状态的唯一方法且 mutation 必须是同步函数）、Action（异步逻辑都应该封装到 action 里面）、Module。
o Vuex数据消失：一旦页面刷新，Vuex中的数据就会被初始化（state中的初始数据），所以会导致数据为空的问题。因此，需要将一些刷新之后仍然需要保留的数据存储在sessionStorage中，并让其和Vuex中的数据保持同步（实现方式是：在mutation中更新数据的方法中保存数据到sessionStorage）。然后将state中的数据直接写成从sessionStorage中获取。这样每次页面刷新之后，state中的数据初始化时就会从sessionStorage中获取。
VUE权限管理
o 菜单的控制（vuex，sessionStorage）、界面权限（路由导航守卫，动态路由）、按钮权限（自定义指令）、请求和响应权限（axios的拦截器）。
o 菜单权限的控制：用户登录成功后返回用户的菜单权限数据，并将数据存储到Vuex和sessionStorage中，Vuex中的数据初始化时从sessionStorage中获取。以防止用户点击刷新之后，Vuex中的数据被清空，进而导致菜单界面为空。在其他组件中将Vuex中的数据通过mapState映射为计算属性，并渲染到视图中。
o 界面权限：是指用户不能访问其没有权限的界面。首先使用路由导航守卫：router.beforeEach来判断用户跳转页面之前是否已经登录，如果未登录则重定向到登陆界面。其次通过动态路由的方式，初始化路由里面的路由项为公共模块，当用户登陆成功后，调用函数initDynamicRoutes（自己定义），来根据Vuex中存储的用户权限数据动态的向路由router中添加路由项，这样就可以使当前用户所对应的路由信息中不包含他权限之外的路由项，所以也就不能访问其他页面了。同时为了防止用户刷新页之后路由重置为初始状态，所以需要在APP.vue模块中的mounted函数中调用函数initDynamicRoutes（因为每次刷新都会执行APP.vue中的mounted函数）。
o 按钮权限：虽然⽤户可以看到某些界⾯了, 但是这个界⾯的⼀些按钮，该⽤户可能是没有权限的。因此, 我们需要对组件中的⼀些按钮进⾏控制。⽤户不具备权限的按钮就隐藏或者禁⽤, ⽽在这块中, 可以把该逻辑放到⾃定义指令中。在自定义指令中判断按钮传递进来的信息与用户权限信息是否相匹配，进而隐藏或禁用按钮。
o 请求响应权限：除了登录请求都得要带上token, 这样服务器才可以鉴别你的身份，如果发出了⾮权限内的请求, 应该直接在前端访问内阻止，虽然这个请求发到服务器也会被拒绝。
VUE生命周期
o beforeCreate：表示实例对象被完全创建出来之前的状态，无法获取data中的数据、methods中的方法，也无法获取Dom元素。
o created：表示实例对象已经被完全创建出来，最早只能在这里面获取data中的数据或者调用methods中的方法，但是数据还未被挂载到DOM中。
o beforeMount：会在组件挂载到DOM之前被调用，此时Vue模板已经存在内存中编译完成了，但是尚未把模板渲染到页面中，实际的DOM元素还没有被创建出来，只是一个虚拟的节点。
o mounted：将内存中编译好的模板真实的替换到浏览器的页面中去。此时Vue示例中的data数据已经完全挂载到了DOM中，最早只能在这里访问Dom元素。（注：mounted并不保证所有的组件都被渲染到页面中）
o beforeUpdate：该函数内，数据已经更新了，但是视图上还没有更新。
o updated：该函数内，数据不仅更新了，视图也更新了。
o beforeDestory：执行到该函数时，实例身上的data、methods以及指令等都处于可用状态，还没有执行真正的销毁过程。
o destoryed：执行到该函数时，组件已经被销毁：实例身上的data、methods以及指令等都已经不可用。
o 请求写在created中或者mounted有什么区别？
在实际开发中，请求写在created或者mounted没有太大区别，因为这两个生命周期函数都是同步的，但是请求属于异步的，他也不会阻塞页面渲染的线程，而我们又无法控制请求时间，可能还是主要看个人习惯吧。但是如果是需要操作dom相关的请求，那么必须要放在mounted中，因为mounted中页面才挂在完成，而created中无法获取dom节点。
keep-alive：是vue的内置组件，它可以将组件缓存起来，避免在组件切换时，每次都重新渲染。被包含的组件会多出两个生命周期：activated和deactivated，如果想要在每次进入页面的时候获取最新的数据，需要在activated中获取数据（承担起created钩子函数的作用），因为被缓存的组件被再次展示/隐藏时，不会触发原有的8个生命周期函数。

 
VUE组件通信方式
o Vuex：作为公共数据管理去存储数据，可以通过state获取数据、mutation中的方法修改数据等。
o sessionStorage：存储公共数据，通过浏览器提供的setItem、getItem来共享数据。
o 路由传值：query：不需要路由声明参数、param：需要路由的url中已经声明了参数、（通过this.$route.params和this.$route.query获取）、state：通过state传参，只能在下一个页面使用history.state获取。
o Props：子组件定义接受父组件的值。
o provide和inject：在负组件中提供数据，然后任何后代组件中都可以通过inject来接受这些数据。
o Vue.config.globalProperty：使用该方法定义全局属性，所有组件都可以使用。
o Ref引用：通过ref可以修改子组件的值以达到传递的作用。
VUE3新增了那些特性
o 引入了Tree-shaking（摇树优化）：相比于vue2，很多函数都挂在全局Vue对象中，在vue3中，所有API都通过ES6模块化的方式引入，这样在打包的时候会将一些没有用到的API剔除，减少打包后的体积。
o 生命周期函数：新增了setup函数，该函数在beforeCreated之前执行。并用beforeUnmount、unmounted函数替换了函数beforedestory、destroyed。
o 响应式数据的定义：ref：基本数据类型，比如字符串和数值等；reactive：只接收object和array等复杂数据类型。
Hooks和Mixin(密克斯in)的特点：
o Hooks：是 Vue3 提供的一种函数式写法，可以将组件的状态和生命周期方法提取出来，封装成公共的组件，并在多个组件之间共享和重用。类似于Vue2中的mixin，相对 mixins 而言， hooks更清楚复用代码的来源, 更清晰易懂。
o Mixin：Mixin 是在 Vue 2 中引入的一种对象混入机制，可以像普通的实例对象一样包含各种选项，将这些选项合并到组件中，在多个组件之间复用，互不影响，可以定义各种生命周期函数。
o 区别：①语法和用法：Hooks是在Vue 3的 Composition API 中引入的一种函数式编程的方式，而 Mixins 是在 Vue 2 中的一种对象混入机制。②：组合特点不同：Hooks 可以根据逻辑功能来组合代码，然后封装成自定义 Hook 函数，进行复用。而 Mixins 在组件中会与组件本身的属性和方法进行合并，可能会导致一些不可预料的行为（如命名冲突，来源混乱）。

 
计算机网络篇
HTTP和HTTPS
o http：是基于TCP/IP协议，使用可靠连接，保证数据传输。采用请求/响应模型，用于在两点之间传输文字、图片、音频、视频等，属于无状态协议。
o https：是安全版本的http，通过SSL机制，实现了加密传输，保证数据的完整性，防止他人窃取篡改。
o SSL证书：SSL证书包含了一对密钥中的公钥和CA的数字签名等验证证书的一些信息。
o 对称加密和非对称加密：对称密钥是指使用同一个密钥进行加密和解密，也叫会话密钥；非对称加密一般指成对的公钥和私钥，其中一个加密之后，只能用另一个解密。（非对称加密比较复杂，所需时间较长）
o 如何实现HTTPS网站：可以在阿里云上申请并下载SSL证书，在服务器上绑定证书文件和密码，开启HTTPS端口监听即可。
o SSL证书如何实现加密：当浏览器连接到https的服务器时，服务器会将自己的SSL证书副本、公钥发送给浏览器，浏览器会检查证书是否合法，选择信任该证书后，使用服务器的公钥加密生成一个会话密钥并回传给服务器，服务器使用私钥解密出会话密钥，后续使用会话密钥进行传输数据。
o HTTP和HTTPS的区别：
· HTTP 是超文本传输协议，信息是明文传输，HTTPS 则是安全版的，通过 SSL 进行加密传输。
· http的端口是80，https的端口是443
· https可以保证数据的完整性，防止数据传输过程中被中间人篡改。
GET和POST的请求的区别：Post 和 Get 是 HTTP 请求的两种方法，其区别如下：
o 应用场景：GET 请求是一个幂等的请求，一般 Get 请求用于对服务器资源不会产生影响的场景，比如说请求一个网页的资源。而 Post 不是一个幂等的请求，一般用于对服务器资源会产生影响的情景，比如注册用户这一操作。
o 是否缓存：因为两者应用场景不同，浏览器一般会对 Get 请求缓存，但很少对 Post 请求缓存。
o 发送的报文格式：Get 请求的报文中实体部分为空，Post 请求的报文中实体部分一般为向服务器发送的数据。
o 安全性：Get 请求可以将请求的参数放入 url 中向服务器发送，这样的做法相对于 Post 请求来说是不太安全的，因为请求的 url 会被保留在历史记录中。
o 参数类型：post 的参数传递支持更多的数据类型。
HTTP请求和响应报文格式
o 请求报文格式：
请求行：请求方法  URL  HTTP协议版本
请求头：（也叫首部行）请求报文的属性，冒号分割的键值对，每组属性各占一行。
空行
请求体：如果请求体存在，请求头中会有一个 Content-Length 属性来表示请求体的长度。是可选部分，比如GET请求就没有请求正文，POST请求体中存放的是表单提交的键值对（通常是json格式）。
o 响应报文格式：
响应行：（也叫状态行）HTTP 协议版本  响应状态码  状态码解释短句
响应头：（也叫首部行）响应报文的属性，冒号分隔的键值对，每组属性各占一行。
空行
响应体：服务器给客户端返回的内容，如果服务器返回一个 html 页面，那么 html 页面内容就出现在响应体中。
 

HTTP1.0和HTTP1.1的区别
o http1.1：在HTTP/1.1中，所有的连接默认都是持久连接。浏览器向服务器进行一次HTTP请求后，并不会直接关闭这个连接，而是会默认保持一段时间，下一次浏览器继续访问的时候就会再次利用到这个连接。
o http1.0：在HTTP/1.0 中, 官方不支持keepalive 操作。如果浏览器支持 keep-alive，它会在请求头中添加：Connection: Keep-Alive来实现持久连接。
当在浏览器中输入 Google.com 并且按下回车之后发生了什么？
o 解析URL：首先会对 URL 进行解析，分析所需要使用的传输协议和请求的资源的路径。如果输入的 URL 中的协议或者主机名不合法，将会把地址栏中输入的内容传递给搜索引擎。
o 缓存判断：浏览器会判断所请求的资源是否在缓存里，如果请求的资源在缓存里并且没有失效，那么就直接使用，否则向服务器发起新的请求。
o DNS解析：下一步首先需要获取的是输入的 URL 中的域名的 IP 地址，首先会判断本地是否有该域名的 IP 地址的缓存，如果有则使用，如果没有则向DNS 服务器发起请求来获取ip地址。
o 获取MAC地址：当浏览器得到 IP 地址后，数据传输还需要获取目的主机 MAC 地址。
o TCP三次握手：通过tcp三次握手建立tcp连接。
o HTTPS握手：如果使用的是 HTTPS 协议，在通信前还存在 TLS 的一个四次握手的过程
o 返回数据：当页面请求发送到服务器端后，服务器端会返回一个 html 文件作为响应，浏览器接收到响应后，开始对 html 文件进行解析，开始页面的渲染过程
o 页面渲染：浏览器首先会根据 html 文件构建 DOM 树，根据解析到的 css 文件构建 CSSOM 树，如果遇到 script 标签，则判端是否含有 defer 或者 async 属性，要不然 script 的加载和执行会造成页面的渲染的阻塞。
o TCP四次挥手：最后一步是 TCP 断开连接的四次挥手过程。若客户端认为数据发送完成，则它需要向服务端发送连接释放请求。服务端收到连接释放请求后，会告诉应用层要释放 TCP 链接。
HTTP协议状态码：
2XX 表示客户端成功：
o 200 OK，表示从客户端发来的请求在服务器端被正确处理
o 204 No content，表示请求成功，但响应报文不含实体的主体部分
o 205 Reset Content，表示请求成功，但响应报文不含实体的主体部分，但是与 204 响应不同在于要求请求方重置内容
o 206 Partial Content，进行范围请求
3XX 表示请求的资源需要重定向
o 301 moved permanently，永久性重定向，表示资源已被分配了新的 URL
o 302 found，临时性重定向，表示资源临时被分配了新的 URL
o 303 see other，表示资源存在着另一个 URL，应使用 GET 方法获取资源
o 304 not modified，协商缓存，表示你请求的资源和上次请求的一样，并没有改变，直接从本地缓存中取吧。
o 307 temporary redirect，临时重定向，和302含义类似，但是期望客户端保持请求方法不变向新的地址发出请求
4XX 表示客户端出现错误，服务器无法完成请求
o 400 bad request，请求报文存在语法错误
o 401 unauthorized，表示发送的请求需要有通过 HTTP 认证的认证信息
o 403 forbidden，表示对请求资源的访问被服务器拒绝
o 404 not found，表示在服务器上没有找到请求的资源
5XX 表示服务器处理请求时发生错误
o 500 internal sever error，表示服务器端在执行请求时发生了错误
o 501 Not Implemented，表示服务器不支持当前请求所需要的某个功能
o 503 service unavailable，表明服务器暂时处于超负载或正在停机维护，无法处理请求
TCP和UDP协议
o Tcp：面向连接的协议（字节为单位），保证数据的正确性，按序到达，是一个可靠传输协议。
o Udp：面向无连接的协议（报文为单位），有可能丢包，不可靠协议。适用于视频会议、直播等。
为什么说TCP是可靠协议？
o 在数据传输时候，提供了校验和、序列号/确认应答、超时重传、滑动窗口、拥塞控制等方法。
网络模型：
o OSI七层模型：应用层、表示层、会话层、传输层、网络层、数据链路层、物理层。
o TCP/IP五层协议：应用层、传输层、网络层、数据链路层、物理层。
 
 
浏览器篇
HTTP和HTTPS，(点我跳转到网络篇里的http内容)
浏览器缓存sessionStorage、localStorage、IndexedDB、Cookie
o localStorage：①数据永久存储在浏览器中，除非用户删除手动删除；②：用于长期保存数据，比如用户的偏好。
o sessionStorage：①数据也是存储在浏览器中，属于会话级别，当关闭浏览器时，数据被删除；②：用于保存临时数据。
o 二者的相同点：都只能存储字符串类型数据；都存储在客户端，不会发送给服务器；大小都是5MB。
o Cookie：来回在客户端和服务器之间传递，主要用于保存网站的用户身份（通过保存sessionID）、跟踪用户行为等。大小不能超过4K。
o IndexedDB：是浏览器提供的面向对象的NoSQL数据库，它具有大容量和离线存储能力，适用于 web 应用程序对结构化数据的批量读写操作。
session、cookie、sessionID的区别？
o session：是一种采用在服务器端保持状态的方案，是存储在服务器端的特殊对象，服务器会为每一个浏览器（客户端）创建一个唯一的session，可以通过setAttribute将用户数据来保存起来。这个session是服务器共享的，而每个浏览器（客户端）是独享的。
o sessionID：一个服务器会同时为多个浏览器提供服务，所以说会产生多个session，而session针对每一个浏览器自身都是独一无二的，那么当某个浏览器访问服务器时，服务器怎么来获取这个浏览器对应的session呢？一般是通过sessionID来实现的，每一个sessionID标识了一个session对象（浏览器第一次访问服务器时，服务器就会创建一个session和sessionID，并将其作为该浏览器的标识），而服务器每次响应的时候都会将sessionID传递给浏览器，通常是将sessionID存储在响应头的set-cookie字段中中进行传递的，并且浏览器会自动将其保存到Cookie中。下次浏览器访问服务器的时候，将sessionID放入Cookie中发送到服务器，进而服务器就可以根据这个sessionID来获取该浏览器的session对象了。
o Cookie：是一种采用在客户端端保持状态的方案，以键值对来保存数据，用于存储服务器返回给浏览器的少量信息。在下一次访问该网站时，客户端会将保存的cookie数据发送给服务器，服务器利用cookie数据进行一些操作。比如说可以实现自动登录，保存游览历史，身份验证等功能。
DNS缓存
o 简介：DNS就是域名系统，用于域名和IP地址之间相互映射。
o 过程：①浏览器第一次请求获取到ip地址之后会将其缓存起来，下次向相同域名发起请求时，就会先查找本地缓存，如果没有命中就②：检查本地C盘host文件内是否有映射关系，如果依旧没有命中就③：请求本地域名服务器（递归方式），如果命中则停止解析，否则就④：由本地域名服务器代替主机通过迭代的方式分别向根域名服务器、顶级域名服务器、权限域名服务器发送请求查询，最终返回本机（每一次迭代，都会告诉下一步该去哪里查询）。
Nginx服务器反
什么是跨域，以及怎么解决
o 什么是跨域：是由浏览器的同源策略造成的。如果请求的URL地址与当前地址栏中的URL地址域名、协议和端口有不同时，都会成为跨域，这时就会限制ajax请求、限制读取Cookie、LocalStorage中的数据和获取DOM、JS对象等。
o 解决跨域的方案
CORS机制：通过设置Access-Control-Allow-Origin （响应头）指定域名。
Nginx服务器反向代理解决跨域问题。
WebSocket：使用wensocket创建持久连接，实现不同域间的通信。
长连接请求？
o 概念：在一次连接中可以发送多个请求和接收多个响应，连接在一定时间内保持打开状态，可以达到类似服务端推送(Server Push)的效果，可以使客户端快速获取到新数据。
o 啊萨达萨达萨达撒旦
强缓存和协商缓存
o 协商缓存：向服务器发送请求，服务器会根据这个请求的request header的一些参数来判断是否命中协商缓存，如果命中，则返回304状态码并带上新的response header通知浏览器从缓存中读取资源；
o 强缓存：浏览器不会向服务器发送任何请求，根据相应的参数（Expire或Cache-Control里面的max-age）来判断是否直接从本地缓存中读取文件并返回200 OK。
o 强缓存参数（2种）：
Expire(过期时间，HTTP1.0)：expire为服务器返回的响应字段，值为该资源在未来某个时间点（年月日时分秒）会过期，浏览器收到响应后会将该值保存下来。当下次发送请求的时候会将自己的时间与第一次请求保存下来的expire时间作比较，判断缓存是否过期。
Cache-Control（HTTP1.1）：当值设为max-age=300时，则代表在这个请求正确返回之后的5分钟（浏览器也会保存max-age的值）内再次加载资源，就会命中强缓存。浏览器下次发送请求的时候，会用现在的时间减去缓存这个文件的时间戳来与max-age作比较，来判断缓存是否过期。
Expirt和Cache-Control的区别：Cache-Control优先级高于Expire，Expires是一个具体的服务器时间（年月日时分秒），这就导致一个问题，如果客户端时间和服务器时间相差较大，强缓存就不一定能生效了。而Cache-Control是一个时间段，不受具体时间点的影响，控制就比较容易。
o 协商缓存参数（2种）：
Last-Modified/If-Modified-Since（HTTP1.0）：Last-Modified是该资源文件最后一次更改时间，服务器会在响应头里将其返回，同时浏览器会将这个值保存起来；在下一次发送请求时，将这个值放到请求头里的If-Modified-Since字段里面。服务器在接收到请求后，会和该资源在服务器的最后被修改时间做对比，判断是否命中协商缓存，进而返回200或304。
Etag/If-None-Match（HTTP1.1）：Etag是服务器响应请求时，返回当前资源文件的一个唯一标识（由服务器生成），浏览器会将其保存，在下一次发送请求时，将这个值放到请求头里的If-None-Match字段里面。服务器在接收到请求后，则会根据If-None-Match的字段值与该资源在服务器的Etag值做对比，判断是否命中协商缓存，进而返回200或304。
Last-Modified和ETag的区别：Last-Modified是该资源文件最后一次更改时间，而Etag是对资源的一种唯一标识，在精确度上，Last-Modified的精确度是秒，对于1秒内修改多次的资源会失效，但是Etag每次都会随着资源的改变而改变，确保了精度。

浏览器是如何渲染页面的？
o 开篇回答：当浏览器的网络线程收到HTML文档之后，会产生一个渲染任务，并将其传递给渲染主线程的任务队列。在事件循环机制的作用下，渲染主线程取出任务队列中的渲染任务，开启渲染流程。
o 渲染过程：整个渲染流程包括多个阶段，分别为：HTML解析、样式计算、布局、分层、绘制、分块、光栅化、画，每个阶段都有明确的输入输出，上一个阶段的输出会成为下一个阶段的输入，这样，整个渲染流程就形成了一套严密组织的流水线。简单来说包含了三个过程：构建DOM、布局、绘制页面。
· 构建DOM：浏览器会启动渲染主线程去解析html文档，同时会启动一个预解析线程，去下载css和js文件。在此过程中，css不会阻塞html的解析，js会阻塞html的解析，解析完成之后会得到一颗DOM树，和CSSOM树；然后遍历DOM树，并根据CSSOM树来计算最终样式，得到一颗带有样式的DOM树，也就是渲染树。
· 布局（也称回流）：当构建完渲染树之后，下一步进行的是布局。浏览器会获取渲染树的结构、节点的位置和大小，根据盒子模型进行排列和嵌套（分层）。经过一系列的计算之后就得出了每个节点应该被放到页面的哪个位置。
· 绘制：布局完成后在页面上是看不到内容的，需要对整个布局中的所有层进行绘制。
· 总结：构建DOM树→生成CSSOM树→结合生成Render Tree→进行布局（计算每个节点的几何信息）→绘制
 
TypeScript
Interface和type的区别
o type：叫类型别名，定义方式为type type1 = { }。
o interface：叫接口，定义方式为interface people{}
o 区别：①：interface可以重复声明，type不可以；②：interface可以通过extends继承，type可以通过交叉类型（&）来达到继承的效果；③：type能够表示字面量，可以通过联合类型来限制变量的取值（type type1 = 1|2|3|’xiaoming’）。Interface只能定义对象类型interface In{}；
联合类型和交叉类型
o Type和interface都可以用联合类型和交叉类型：
o 联合类型：联合类型是由两个或多个其他类型组合而成，表示一个值可以是几种类型之一，定义变量时在满足一个类型所有属性的基础上，也可以包含其他类型中的属性，使用联合类型时只能访问所有可能类型的共有属性和方法。
o 交叉类型：交叉类型是将多个类型合并为一个新的类型，并且这个类型包含所有子类型的所有属性。
泛型
o 概念：是指在定义函数、接口或类的时候，不先预先指定具体的类型，而使用的时候再指定类型的一种特性。
o 函数使用：
			let print = <T>(value: T): T => value;       //function print<T>(value: T):T{}
console.log(print<string>("ss"));
o 接口使用：
			interface List<T> {
  				listName: string;
  				level: number;
  				listData: T[];	//T类型的数组
}
interface Dog {color: string; weight: number;}
let dogList: List<Dog> = { listName:’’,level:4,listData:[{Dog对象},{Dog对象}] }

Pick 和 Omit
o Pick：从类型定义的属性中，选取指定一组属性，返回一个新的类型定义。
			interface Person { name: string， age: number，id: number，sex: 0 | 1 }
			// 问女生年纪不太礼貌，所以我们不需要 age 这个属性
			type Woman = Pick<Person, "name" | "id">;
			// 此时 Woman 等效于 Female
			interface Female {name: string，id: number }
o Pick：以一个类型为基础剔除某些属性，然后返回一个新类型。
			interface User { id: number， name: string，age: number，sex: 0 | 1，tel: number}
			type EditUser = Omit<User, "id"> // 就是在 User 的基础上，去掉 id 属性
 
 

Echarts
Echarts中常见的图表
o 柱状图：bar；
o 折线图：line，通过设置smooth：true，可以使折线变得光滑，成为一种曲线图。
o 饼图：pie。
Echarts中常用配置项
o title：标题组件，包含主标题和副标题；可以设置字体大小、颜色等样式。
o legend：图例组件，可以通过点击控制哪些系列不显示。
o grid：网格，一般情况下网格的上下最多两个x轴，左右2个y轴，可以设置网格离容器四周的距离、宽高等，在网格内绘制图表。
o xAxis：直角坐标系 grid 中的 x 轴，可在上下两侧，用于设置x坐标轴相关样式、刻度、刻度标签等内容。
o yAxis：
o series：是一个数组对象，用于定义图表中的数据系列，可以理解为图表中的一个数据集，不同的图表类型会有不同的 series 配置。例如line、bar、pie（饼图）、scatter（散点图）、map（地图）.
o toolbox：图表中的工具栏。内置有导出图片，数据视图，动态切换图表类型，数据区域缩放。
o tooltip：用于配置图表的提示框，当鼠标悬停在图表的数据点上时显示的信息框，提供该对数据点的详细信息。（trigger、formatter配置触发类型、提示内容格式化器）。
o dataZoom：dataZoom 组件是用于配置数据区域缩放的组件。可以让用户选择图表上的特定数据区域，并进行放大、缩小、平移操作。提供了两种类型的组件：slider（滑动条缩放） 和 inside（坐标系中数据区域缩放）。
o timeline：用于配置时间轴，可以实现在不同时间点上切换不同数据，以显示不同状态的图表，还可以控制播放、暂停等。
o 折线图：浏览器不会向服务器发送任何请求，根据相应的参数（Expire或Cache-Control里面的max-age）来判断是否直接从本地缓存中读取文件并返回200 OK。
 
项目技术难点
电能量可视化工具权限问题
问题：(左侧菜单栏问题)不同权限的人员登陆之后，左侧菜单栏显示与这个用户权限对应额菜单列表。
解决：(if判断)起初我是前端通过v-if判断登陆人员的类别进行显示和隐藏某个菜单选项，也算达到了菜单权限的控制。
问题：(页面跳转问题）但是还有问题，就是用户可以通过在地址栏上手动输入某个菜单对应的路径也能进入（因为路由项存在就能跳转过去），这样界面权限也有问题了。
解决：(数据库权限列表+路由拦截)然后我就在数据库中存储了每个用户所对应的权限列表数据（路径的url）。用户登陆成功之后，返回这些权限列表数据并存储到SessionStorage中，然后用路由拦截(router.beforeEach)的方式判断该用户是否具有即将要跳转的页面的权限。
问题：(条件判断语句多、扩展性差)但是这样做的话，当权限分类较多时，我又要增加很多判断语句，扩展性也比较差。
解决：(动态路由)然后发现了动态路由这种方式好像很适合解决我的问题，然后自己去探索学习了一下，对用户权限的数据库表又新增了每个权限url所对应的中文菜单名称。登陆之后存储在Vuex中，左侧菜单栏就根据这个权限列表进行渲染。然后路由初始化时只有公共模块，登录成功后根据返回的权限列表数据动态地添加路由项，这样每个用户登陆之后的router就没有多余的路由项了，也不需要手动去循环判断了。
大屏可视化技术难点
问题1：请问请问
请问请问

Echarts图表数据量太大是怎么优化
o 1：如果非必要，尽量取消动画效果，如关闭tooltip中的响应和触发鼠标事件
o 2：使用懒加载，只加载视图内的图表。
o 3：对数据进行降采样，减少数据点的同时还能保留数据的趋势和特征。echarts自带的属性sampling实现了数据的降采样，这个属性可以选择合适的采样算法，如lttb算法可以选择保留的数据点数，可以大大节约渲染时间。

电能量可视化工具数据无法满足业务需求
o 解析原有数据中的用户具体地址获得其所属区域以及经纬度，并生成区域表和用户地址与区域的关联表，以实现区域化图表查询的要求

