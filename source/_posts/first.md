---
title: 技术总结V1.0
date: 2023-04-13 19:32:17
tags:
---
# 技术总结v1.0

## 1. 面向对象与面向过程的区别

​ **面向过程**：是将事件分成步骤，按部就班一步一步完成的。

​ **面向对象** ：将事件分成一个又一个对象，每个对象有自己的属性及方法。是各个对象之间的方法交互。

## 2. flex布局与grid布局的区别

​ grid布局讲容器分成行与块，远比flex布局强。

参考链接


## 3.Sass与Less的区别？用哪个好？

​ Sass 的主版本现在已经改用 Dart 实现了，Ruby 的版本一年前就不再维护了。Sass 和 Less 的使用并没有明显的「复杂」和「简单」的区别，常用部分大同小异。Less 运行在浏览器端只是方便初学者上手，生产环境是绝对不会这么做的，都是随着前端项目一起构建，构建完之后的都是静态资源，不涉及服务端什么事。两者都有线上的 REPL，所以简单的演示代码不用担心用不了 Sass。Sass 以 $ 打头比较不容易和 CSS 标准语法冲突，Less 的语法跟 CSS 标准太像了，有时候会难以区分（Stylus 更糟糕）。Sass 和 Less 的变量机制有很大的不同，Sass 是类似 JS 的块级作用域一样，可以在作用域内重新赋值而不影响外部，Less 是以全局的最后一次赋值为准，这也是为什么大部分 UI 组件库都选择 Less。Compass 这个东西……已经没什么人在用的了，只存在于教材上的东西，忘了它吧。SASS 和 SCSS 只是两种语法风格而已，**推荐使用 SCSS** ，但 SASS 也没有不再支持，放到现在来看，跟版本没关系。Sass 的模块机制现在大改了，建议跟进下。不论国内外市场如何，Less 和 Sass 最常用的部分并没有明显的区别，不用太在意该用哪个，Just pick one。我个人比较偏好 Sass，生态更好（踩过 Stylus 的坑，深刻的教训），至于公司用哪个，跟着用就行，不出大问题不用考虑换。

## 4.sass使用过程中的问题

### Easy Sass插件没有生成.css文件问题

- 检查是否安装好

```
sass -v //检查是否安装好sass
compass -v
```

- **路径保存问题**，settings.json中保存路径应该为`css/`这样才能在上一级文件夹（当前在sass文件夹内）的`css`文件夹生成对应`.css`文件。<b>ps</b>:需要自己新建`css`文件夹，不然会报错。
- settings.json配置

```
"easysass.compileAfterSave": true,
"easysass.formats": [ 
        //nested：嵌套缩进的 css 代码。
        //expanded：没有缩进的、扩展的css代码。
        //compact：简洁格式的 css 代码。
        //compressed：压缩后的 css 代码

        {
            "format": "expanded",
            "extension": ".css" //设置编译输出的文件名
    ],
      //这会回到根目录的css文件夹内创建同名.css文件
    "easysass.targetDir": "css/" //提供 css 输出路径的设置.
  
```

- 需要自己提前在**根目录创建好css文件夹**否则会报错。

## 5.写css的命名规范--BEM

- 命名规范

```

```

参考连接[css命名规范--知乎](<https://zhuanlan.zhihu.com/p/122214519>)

## 6.tree生成目录的使用

- 在在Tree for Winodws页面，下载二进制文件Binaries zip
- 解压压缩包，找到压缩包内的 bin 目录，将 bin 目录下的 tree.exe 复制到git文件夹Git\usr\bin 目录下，将 tree.exe 粘贴到该目录下，安装完成，即可使用。
- git bash

```
tree -L 1 >tree.txt
```

### tree命令行参数

-a 显示所有文件和目录。<br>
-A 使用ASNI绘图字符显示树状图而非以ASCII字符组合。<br>
-C 在文件和目录清单加上色彩，便于区分各种类型。<br>
-d 显示目录名称而非内容。<br>
-D 列出文件或目录的更改时间。<br>
-f 在每个文件或目录之前，显示完整的相对路径名称。<br>
-F 在执行文件，目录，Socket，符号连接，管道名称名称，各自加上"*","/","=","@","|“号。<br>
-g 列出文件或目录的所属群组名称，没有对应的名称时，则显示群组识别码。<br>
-i 不以阶梯状列出文件或目录名称。<br>
-I 不显示符合范本样式的文件或目录名称。<br>
-n 不在文件和目录清单加上色彩。<br>
-N 直接列出文件和目录名称，包括控制字符。<br>
-p 列出权限标示。<br>
-P 只显示符合范本样式的文件或目录名称。<br>
-q 用”?"号取代控制字符，列出文件和目录名称。<br>
-s 列出文件或目录大小。<br>
-t 用文件和目录的更改时间排序。<br>
-u 列出文件或目录的拥有者名称，没有对应的名称时，则显示用户识别码。<br>
-x 将范围局限在现行的文件系统中，若指定目录下的某些子目录，其存放于另一个文件系统上，则将该子目录予以排除在寻找范围外。

## 7.this的指向

- **方法中**，`this`指向方法所在的对象。
- 单独使用`this`指向`window`。
- 函数中`this`为函数的所有者。如果在浏览器中就是`window`。
<br>函数默认指向最高的`window`。
<br><b>构造函数是obj对象</b>，所以`this`会指向该构造函数（obj）。
- **事件中**的`this`指向接收事件的HTML元素。因为**HTML元素是对象**。???
  
## 8.for in 与for of的区别

- `for in`其中的参数保存的是**键名**，而`for of`其中的参数保存的是**键值**。

## 9.逻辑中断

- 某些场景用来替代if-else操作，默认值
- `&`中断，左边false中断

```
let a = false && 5 //false
let a = true && 5 // 5
```

- `||`中断，左边true中断

```
let a = true || 5 // true
let a = false || 5 // 5
```

## 10.原型与原型链与原型对象

<https://juejin.cn/post/6984678359275929637#comment>这篇文章写的十分透彻

### 10.1构造函数创建实例对象过程？

  1、创建新对象
  <br>2、将构造函数作用域赋值给新对象（this指向新对象）
  <br>3、执行构造函数中的代码，给实例对象添加实例属性和实例方法。

  ```
  // 构造函数
function Person(name, age) {
    this.name = name;
    this.age = age;
}

// 生成实例
const p = new Person('zhangsan', 18);
  ```

### 10.2原型对象

  `函数`在创建时会生成一个`prototype`属性，该属性`指向一个对象`，这个对象就是`原型对象`
![](/images/%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E4%B8%8E%E5%8E%9F%E5%9E%8B%E5%AF%B9%E8%B1%A1.awebp)

### 10.3原型链

- 通过`构造函数`创建出的`实例对象`有个`_proto_`属性，该属性指向`实例对象的构造函数的原型对象`
![](/images/%E5%AE%9E%E4%BE%8B%E4%B8%8E%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E7%9A%84%E5%8E%9F%E5%9E%8B%E5%AF%B9%E8%B1%A1.awebp)
其实就是`实例的_proto_`指向`原型对象`,同时`构造函数的prototype`也指向`原型对象`。
- **原型链**就是访问对象属性时，查找对象有没有查找的对象，没有就找`_proto_的原型对象（构造函数的prototype）`，还是没有就找`原型对象的_proto_查找`，因此形成原型链。
- 原型链的尽头是`null`

### 10.4在构造函数原型对象修改属性

- 要让所有实例共享构造函数属性，添加或删改内在的属性或方法，应该在`构造函数的prototype（原型对象）`去更改。
- 在实例对象修改`_proto_`会影响**所有共享构造函数**的实例对象。

### 10.5GPT的说法

在 JavaScript 中，每个对象都有一个原型对象（prototype），它定义了该对象的属性和方法。当访问一个对象的属性或方法时，如果该对象本身没有定义该属性或方法，则会沿着原型链向上查找，直到找到该属性或方法为止。

原型链是由一系列原型对象组成的链式结构，它描述了对象之间的继承关系。每个对象都有一个原型对象，如果对象 A 的原型对象是对象 B，那么对象 A 就可以继承对象 B 中定义的属性和方法。

原型对象可以通过函数的 `prototype` 属性进行访问和修改。例如，可以定义一个构造函数 `Person`，并在其原型对象上添加一个方法 `sayHello()`：

```
function Person(name) {
  this.name = name
}

Person.prototype.sayHello = function() {
  console.log(`Hello, my name is ${this.name}`)
}

let person = new Person('John')
person.sayHello() // 输出：Hello, my name is John
```

在这个例子中，`Person` 函数定义了一个 `name` 属性，并在其原型对象上添加了一个 `sayHello()` 方法。当创建一个 `Person` 对象时，可以通过 `new` 运算符调用 `Person` 函数，并返回一个新的对象。这个新对象的原型对象指向 `Person.prototype`，因此可以访问 `sayHello()` 方法。

需要注意的是，原型对象是在对象创建时动态生成的，因此可以在运行时动态地修改原型对象。同时，原型对象是基于引用的，即多个对象可以共享同一个原型对象。这种机制不仅可以提高代码的复用性，还能够实现面向对象编程中的继承和多态等特性。

### 10.6为什么有原型链？

JavaScript 之所以有原型链，是因为其是一种基于**原型继承**的面向对象编程语言。在 JavaScript 中，`每个对象都有一个指向其原型的内部链接`，这个链接被称为原型链。

当我们访问一个对象的属性或方法时，如果当前对象没有这个属性或方法，JavaScript 引擎就会去该对象的原型对象中查找是否有这个属性或方法。如果原型对象中也没有这个属性或方法，那么就会继续在原型对象的原型对象中查找，直到找到 Object.prototype 对象为止，如果还没有找到，则返回 undefined。

这样的设计可以让对象之间实现继承，从而使得代码更加简洁、灵活和可重用。通过在原型对象中定义方法和属性，我们可以让所有基于该原型的对象都共享这些方法和属性，从而避免在每个对象中都定义一遍，提高了代码的复用性和效率。

因此，原型链是 JavaScript 面向对象编程的一个重要特性，也是理解 JavaScript 中对象和继承机制的关键。

### 10.7浏览器的[[prototype]]是什么

在JavaScript中，每个对象都有一个原型对象（即_proto_属性），它决定了对象的属性和方法。同时，每个构造函数也有一个原型对象（即prototype属性），它是通过new操作符创建的实例的原型对象。

在浏览器中，对象的_proto_属性通常被称为对象的“隐式原型”（implicit prototype），它指向该对象的原型对象。而该对象的原型对象通常被称为对象的“显示原型”（explicit prototype），它是一个对象，它包含了该对象的属性和方法。

具体来说，浏览器中的对象的[[prototype]]属性（即_proto_属性）指向该对象的原型对象，它是一个内部属性，通常无法直接访问。而该对象的原型对象通常是通过构造函数的prototype属性设置的，从而让该对象可以访问到构造函数中定义的属性和方法。

例如，以下代码演示了在浏览器中创建对象时的[[prototype]]属性和prototype属性的关系：

```
// 定义一个构造函数
function Person(name) {
  this.name = name;
}

// 在构造函数的原型对象中定义一个方法
Person.prototype.sayHello = function() {
  console.log(`Hello, my name is ${this.name}`);
}

// 创建一个Person对象
const person = new Person('Tom');

// 输出person对象的[[prototype]]属性
console.log(person.__proto__); // 输出：Person {sayHello: ƒ, constructor: ƒ}

// 输出person对象的构造函数
console.log(person.constructor); // 输出：ƒ Person(name) {this.name = name;}

// 调用person对象的方法
person.sayHello(); // 输出：Hello, my name is Tom
```

在这个例子中，我们定义了一个构造函数Person，然后在它的原型对象中定义了一个方法sayHello。接着，我们使用new操作符创建了一个Person对象，并输出了它的[[prototype]]属性和constructor属性。可以看到，person对象的[[prototype]]属性指向了Person构造

## 11.自增的数据类型转换

```js
var a1 = "2";
var a2 ="w";
var b1 = false;
var bin = 1.1;
var o ={
 valueOf:function(){
  return -1;
 }
};
a1++;
a2++;
b1++;
bin--;
o--;
console.log(a1);  //3
console.log(a2);  //NaN
console.log(b1);  //0.10000000000000009
console.log(bin);  //1.1
console.log(o);   //-2

```

## 12.闭包的理解

闭包是指在函数内部定义的函数可以访问函数外部的变量，即使在函数外部这些变量已经不可访问。闭包通常由一个函数和在该函数内部定义的另一个函数组成，在内部函数中可以访问外部函数的变量和参数，即使在外部函数执行完毕后，这些变量和参数仍然可以被内部函数访问。

闭包的概念可能比较抽象，以下是一个例子来帮助理解：

```
function outer() {
  let count = 0
  function inner() {
    count++
    console.log(count)
  }
  return inner
}

let fn = outer()
fn() // 1
fn() // 2
fn() // 3
```

在这个例子中，函数 `outer` 内部定义了一个变量 `count` 和一个函数 `inner`，`inner` 函数可以访问 `outer` 函数中的变量 `count`。`outer` 函数最终返回 `inner` 函数，并将其赋值给变量 `fn`。

当执行 `fn()` 的时候，实际上是在执行 `inner()` 函数，因此每次执行 `fn()` 都会输出 `count` 变量的值，并将其自增。由于 `count` 变量是在 `outer` 函数中定义的，因此在 `inner` 函数中也可以访问和修改 `count` 变量的值，即使 `outer` 函数已经执行完毕。

这个例子就展示了一个闭包的具体实现：内部函数 `inner` 可以访问外部函数 `outer` 中的变量 `count`，即使 `outer` 函数执行完毕后这个变量仍然可以被访问和修改。闭包可以用于实现一些高级的 JavaScript 技术，例如柯里化、函数式编程、模块化等。

## 13.函数式编程

函数式编程是一种编程范式，它是一种程序设计的风格，强调函数的使用来构建软件应用程序。它是一种声明式编程，而不是命令式编程。在函数式编程中，程序由许多小的、可组合的函数组成，每个函数都有一个明确定义的输入和输出，不会修改函数外的状态。函数式编程的目标是编写简单、可读、可维护和可扩展的代码。

函数式编程的一些特征包括：

- 纯函数：函数的输出仅取决于输入，而不依赖于任何外部状态或副作用。
- 不可变性：数据不可被修改，一旦创建就不能再改变，因此任何对数据的修改都会创建一个新的数据对象。
- 高阶函数：函数可以作为参数传递给其他函数，也可以返回其他函数。
- 延迟执行：表达式的求值被延迟到需要使用它的时候。
- 函数组合：将函数组合起来构建更复杂的函数。

函数式编程有许多优点，例如代码简洁、可读性高、易于测试、可维护性强、并发性好等。它在处理大规模数据、并发编程和分布式系统方面具有巨大的优势。在 JavaScript 中，函数式编程的特征可以通过使用高阶函数和内置的 `Array` 方法如 `map()`、`filter()`、`reduce()` 等来实现。

## 14.开源项目怎么学习

学习开源项目需要一定的技能和经验，以下是一些建议：

1. 了解项目：在探索一个新的开源项目之前，应该先了解项目的背景、目的和技术栈等信息。这可以通过项目的文档、代码库、社区和邮件列表等渠道来获取。
2. 安装和运行代码：安装和运行代码是了解项目的一个重要部分。这可以通过阅读项目的文档和代码库来完成。如果遇到问题，可以查看项目的社区和邮件列表，也可以尝试在开发者社区中提问。
3. 阅读代码：阅读代码是了解项目的另一个重要部分。可以通过阅读项目的代码库来了解代码的结构、功能和实现细节。此外，还可以使用调试工具来了解代码的执行过程。
4. 参与社区：参与社区是学习开源项目的另一个重要部分。可以通过参加社区讨论、提供反馈和贡献代码等方式来参与项目。这可以帮助学习项目，并建立联系和信任。
5. 贡献代码：贡献代码是学习开源项目的最终目标之一。可以通过提供修复错误、新增功能、重构代码等方式来贡献代码。这可以帮助学习项目的实现和贡献开源社区。

总之，学习开源项目需要花费一定的时间和精力。一旦掌握了这些技巧和经验，就可以更轻松地了解和贡献开源项目。

### 源代码的阅读

阅读源代码可以帮助深入了解项目的实现细节和结构，以下是一些阅读源代码的建议：

1. 了解项目结构：在阅读代码之前，应该先了解项目的目录结构和文件组织方式。这可以帮助理解代码中各个模块和组件之间的关系和依赖关系。
2. 阅读文档：阅读项目的文档可以帮助了解项目的功能、设计和代码结构。这可以帮助理解代码的目的和实现细节，减少阅读代码的时间和难度。
3. 阅读代码注释：阅读代码注释可以帮助理解代码的实现细节和目的。注释应该提供有关代码结构、函数用途、变量定义等方面的信息。
4. 使用调试工具：使用调试工具可以帮助了解代码的执行过程和调用关系。可以使用调试器、日志和断点来追踪代码的执行路径和状态变化。
5. 运行示例代码：运行示例代码可以帮助理解代码的实现和功能。可以尝试运行和调试示例代码，并尝试修改代码和观察结果。
6. 尝试重构代码：尝试重构代码可以帮助理解代码的结构和逻辑。可以尝试删除冗余代码、合并函数或变量、提取公共代码块等操作，以改善代码的可读性和维护性。

总之，在阅读源代码时，应该有一个系统性的方法来了解项目的结构和实现细节。可以阅读文档和代码注释，使用调试工具和运行示例代码，并尝试重构代码以提高代码的可读性和维护性。

## 15. 魔术字符串

魔术字符串是指在代码中多次出现的、与代码实现相关的、没有被封装成常量或变量的字符串。这些字符串通常被直接硬编码在代码中，而没有使用变量或常量的形式来表示。

魔术字符串有以下几个问题：

1. 可读性差：魔术字符串通常没有描述性的名称，使用它们的代码难以理解和阅读。
2. 维护性差：魔术字符串存在于代码的多个地方，如果需要修改它们，就需要在多个地方进行修改，增加了代码的维护成本。
3. 可重用性差：魔术字符串通常不能被重用，如果需要在代码的不同地方使用相同的字符串，就需要重复硬编码这些字符串，增加了代码的冗余。

为了解决这些问题，可以将魔术字符串封装成常量或变量。这样可以提高代码的可读性、维护性和可重用性。

例如，下面的代码中使用了魔术字符串：

```
function getUserRole(user) {
  if (user.role === 'admin') {
    return 'admin';
  } else if (user.role === 'manager') {
    return 'manager';
  } else {
    return 'guest';
  }
}
```

可以将魔术字符串封装成常量形式，例如：

```
const ROLE_ADMIN = 'admin';
const ROLE_MANAGER = 'manager';
const ROLE_GUEST = 'guest';

function getUserRole(user) {
  if (user.role === ROLE_ADMIN) {
    return ROLE_ADMIN;
  } else if (user.role === ROLE_MANAGER) {
    return ROLE_MANAGER;
  } else {
    return ROLE_GUEST;
  }
}
```

这样可以提高代码的可读性、维护性和可重用性，减少代码中的冗余和错误。

## 16. 对象的计算属性

### 16.1 计算属性

在 JavaScript 中，对象的属性名可以是字符串或 Symbol 类型。在这个例子中，`val.name` 是一个字符串类型，而我们需要将它作为属性名添加到对象中。因为对象属性名需要满足标识符的命名规则，所以我们需要将 `val.name` 包含在方括号中，将它作为属性名添加到对象中。这种方式被称为计算属性名，它可以让我们在对象字面量中使用表达式作为属性名。

例如，如果我们想要使用一个变量作为属性名，就可以使用计算属性名：

```
const propName = 'name';
const person = {
  [propName]: 'Alice'
};
console.log(person); // { name: 'Alice' }
```

在这个例子中，`[propName]` 就是一个计算属性名，它会将 `propName` 的值作为属性名添加到对象中。

在我们的代码中，`{[val.name]: val.age}` 就是一个计算属性名，它会将 `val.name` 的值作为属性名添加到对象中，同时将 `val.age` 的值作为属性值添加到对象中。

### 16.2对象的键值类型

在 JavaScript 中，对象的键值可以是字符串类型或符号类型。

通常，我们使用字符串作为对象的键值，例如：

```
const obj = {
  name: 'John',
  age: 30,
  'last name': 'Doe'
};
```

在上面的代码中，对象 `obj` 中的键值分别是 `name`、`age` 和 `last name`，它们都是字符串类型。

然而，在ES6引入符号类型（Symbol）之后，我们也可以使用符号作为对象的键值，例如：

```
const mySymbol = Symbol('mySymbol');
const obj = {
  [mySymbol]: 'Hello World'
};
```

在上面的代码中，我们创建了一个符号 `mySymbol`，然后将其作为对象 `obj` 的键值，键名用方括号括起来。符号类型的键值在一些特定场景中很有用，例如在定义私有属性或者避免键名冲突时。需要注意的是，符号类型的键值是唯一的，它们不会与其他键名冲突。

### 16.3变量名作为键名

可以，JavaScript 中对象的键名可以使用变量来动态生成。

例如，可以使用变量作为对象的键名，如下所示：

```
const key = 'name';
const obj = {
  [key]: 'John'
};

console.log(obj.name); // 输出 "John"
```

在上面的代码中，我们使用变量 `key` 来定义对象 `obj` 中的键名，这个键名是动态生成的。使用方括号语法，将变量 `key` 包裹在其中，就可以将其解析为一个字符串，作为对象的键名。

需要注意的是，由于 JavaScript 对象的键名只能是字符串类型或符号类型，因此变量 `key` 中存储的值必须是字符串类型或符号类型，否则会导致语法错误。

## 17. Object.defineProperty

Object.defineProperty是一个内建对象函数，它用于给对象定义属性。它允许你定义一个对象的新属性或修改对象的已有属性，并且可以控制一些属性的行为，例如可写、可枚举和可配置等。

Object.defineProperty的语法如下：

```
Object.defineProperty(obj, prop, descriptor)
```

其中：

- obj：要定义属性的对象。
- prop：需要定义或修改的属性的名称。
- descriptor：一个对象，用来描述这个属性的特性。

descriptor参数可以包含以下属性：

- value：属性的值，默认为undefined。
- writable：布尔值，表示属性是否可写。默认false。
- enumerable：布尔值，表示属性是否可枚举。默认false。
- configurable：布尔值，表示可配置性。默认false。
- get：取值函数，当访问该属性时，会调用此函数。默认为undefined。
- set：赋值函数，当属性值改变时，会调用此函数。默认为undefined。

举例如下：

```
let obj = {};

// 添加普通属性
obj.a = 123;

// 定义属性方式一
Object.defineProperty(obj, 'b', {
  value: 456,
  writable: true,
  enumerable: true,
  configurable: true
});

// 定义属性方式二
let c = 789;
Object.defineProperty(obj, 'c', {
  get() {
    return c;
  },
  set(newValue) {
    console.log(`New value of c is: ${newValue}`)
    c = newValue;
  },
  enumerable: true,
  configurable: true
});
```

以上代码将obj对象添加了三个属性，其中b和c使用了Object.defineProperty进行定义，b是一个普通的数据属性，而c具有getter和setter方法，在读取和修改c属性时会触发这两个方法，并输出日志。

需要注意的是，使用Object.defineProperty定义的属性有些限制：

1. __proto__属性不能被定义，必须使用Object.getPrototypeOf()方法访问。
2. 可以使用Object.getOwnPropertyDescriptors()方法获取到一个属性的完整描述符，并复制到新对象中。
3. 可以在同一对象上定义多个同名属性。会覆盖之前定义的。
4. 原型上的属性在遍历时不会出现。只能定义可枚举或不可枚举的属性。
5. 不能将数据属性定义为不可配置后再将其转换为访问器属性或反之。
6. 不能将一个访问器属性定义为可写或可配置的，或者同时修改一个访问器描述符的值和getter或setter的描述符的值。

综上，要使用Object.defineProperty需谨慎，需要清楚地了解其限制和使用场景。在实际开发中，我们通常使用ES6引入的class语法糖和语法规范中的getter和setter来更方便地操作对象的属性。

举个例子：

```
class Person {
  // 使用语法糖定义私有变量_name
  #_name;

  constructor(name) {
    this.#_name = name;
  }

  // 定义公共的getter和setter访问私有变量_name
  get name() {
    return this.#_name;
  }

  set name(newName) {
    this.#_name = newName;
  }
}

const person = new Person('Tom');
console.log(person.name); // "Tom"

person.name = 'Jerry'
console.log(person.name); // "Jerry"
```

以上代码演示了如何使用class语法糖来简单地定义一个Person类，并使用getter和setter访问私有变量。UIColor、UIFont等常见第三方库也大量采用了这种语法糖的应用，代码更加清新易读。

通过语法糖和规范进行属性定义的好处是，不用过多考虑对象属性的具体实现和私有特性，从而提高代码的可读性和可维护性。

## 19.Vue什么是响应式数据绑定

在Vue中，响应式的数据绑定是一种机制，它允许数据与视图之间建立实时的关联，当数据发生变化时，视图会自动更新以反映数据的最新状态。这种机制允许开发者以一种更加声明式和简单的方式进行数据处理和组件化开发。

Vue中的响应式数据绑定是通过Vue实例中的数据对象，以及Vue组件中的props和data对象来实现的。结合Vue的模板系统和组件化开发机制，开发者可以以一种容易理解、易于维护的方式进行应用程序开发。

Vue是如何实现响应式数据绑定的呢？Vue在使用数据对象时，会将数据对象转换为getter/setter形式，当数据发生变化时，setter函数会被触发，并通知Vue框架数据发生了变化。Vue会自动检测数据对象的变化，并将数据的变化反映在相关的视图上。这种机制允许我们在Vue中声明式地描述我们的应用状态，而不需要手动更新DOM，从而实现更少的模版代码和更少的样板代码。

例如，在Vue模板中，可以通过v-model指令绑定到表单元素上，实现双向数据绑定：

```
<template>
  <div>
    <input v-model="message" placeholder="Enter your message">
    <p>{{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello Vue!'
    }
  }
}
</script>
```

在这个例子中，v-model指令允许我们将input元素与message变量绑定起来。当input元素的值发生变化时，Vue会自动将变化的内容赋值给message变量，当message变量发生变化时，Vue会自动更新视图以反映数据的最新状态。这就是Vue响应式的数据绑定机制。

## 20. Vue生命周期流程

在 Vue.js 中，每个组件实例都会经历一系列的生命周期过程。这些生命周期过程由一系列的钩子函数组成，这些钩子函数可以在不同的生命周期步骤中执行代码逻辑，以响应特定的事件或执行必要的操作。

以下是 Vue.js 组件生命周期的流程：

1. 创建阶段

- `beforeCreate`：在实例初始化之后，数据观测（data observer）和事件配置之前被调用，此时 `vue` 实例的挂载阶段还没有开始。
- `created`：实例已经完全创建，属性和方法都已经完成配置。需要注意的是此阶段不能更新属性和 DOM，此时 `$el` 还不存在。

1. 挂载阶段

- `beforeMount`：在挂载开始之前被调用。此时 `vue` 实例的 `$el` 和 `data` 都已经初始化，但并未创建真正的 `DOM` 节点。
- `mounted`：在实例挂载到 `DOM` 后被调用。此时 `vue` 实例已经构建完成，可以操作 `DOM`，初始化发生在该钩子内部。

1. 更新阶段

- `beforeUpdate`：在响应式数据发生改变时，虚拟 `DOM` 重新渲染和打补丁之前被调用。此时可以进行必要的更新准备工作。
- `updated`：当虚拟 `DOM` 重新渲染和打补丁之后调用。假如要对 `DOM` 进行更改会触发该钩子，注意不要在此修改数据，会导致无限循环。

1. 销毁阶段

- `beforeDestroy`：实例销毁之前调用。此时实例仍然完全可用，可以进行必要的清理工作，如清除定时器、解绑事件等等。
- `destroyed`：实例销毁之后调用。调用该钩子之后，vue 实例以及所有的事件监听器会被移除，所有与实例相关的指令、过滤器等也会被销毁。

1. 激活与停用阶段

- `activated`: 被 keep-alive 缓存的组件激活时调用
- `deactivated`: 被 keep-alive 缓存的组件停用时调用

上述的生命周期钩子用于对应不同的组件状态，并且也为开发者提供了丰富的扩展能力，使用这些钩子函数，开发者可以在不同的状态阶段下进行相应的操作或处理业务逻辑。

<img src="./images/生命周期.png">

---

在整个 Vue.js 组件生命周期的过程中，可以看到一些重要的时机：

- 在 `beforeCreate` 钩子函数中，实例已经完成了 `data` 对象的初始化，但还没有完成 `$el` 和事件的初始化。
- 在 `created` 钩子函数中，除了可以访问 `$data` 和 `$el` 对象之外，其他的一切都需要等到挂载阶段才能访问到。
- 在 `beforeMount` 钩子函数中，Vue.js 将开始创建组件的真实 `DOM`。此时，组件的 `$el` 属性已经存在，但是还没有挂载到实际的页面上。
- 在 `mounted` 钩子函数中，Vue.js 完成了组件的挂载过程，并将组件的 `DOM` 添加到页面中。
- 在 `beforeUpdate` 钩子函数中，响应式数据发生了变化，但是尚未对组件进行重新渲染。
- 在 `updated` 钩子函数中，组件完成了重新渲染，并更新了 `DOM`。
- 在 `beforeDestroy` 钩子函数中，组件即将被销毁，但仍然可以访问 `$data` 和 `$el` 等属性。
- 在 `destroyed` 钩子函数中，组件已经被销毁，所有的事件监听器和指令等都已经被移除。

-------

下面是一个简单的 Vue.js 组件项目，展示了 Vue.js 生命周期的完整流程及各个时机绑定的钩子：

```
<template>
  <div ref="root">
    <p>{{ message }}</p>
    <button @click="updateMessage">Update Message</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: 'Hello, Vue.js!',
    };
  },
  beforeCreate() {
    console.log('beforeCreate');
  },
  created() {
    console.log('created');
  },
  beforeMount() {
    console.log('beforeMount');
  },
  mounted() {
    console.log('mounted');
  },
  beforeUpdate() {
    console.log('beforeUpdate');
  },
  updated() {
    console.log('updated');
  },
  beforeDestroy() {
    console.log('beforeDestroy');
  },
  destroyed() {
    console.log('destroyed');
  },
  methods: {
    updateMessage() {
      this.message = 'Updated message!';
    },
  },
};
</script>
```

在这个示例中，我们定义了一个简单的组件，其中包含一个 `message` 数据属性和一个按钮，点击按钮之后可以更新 `message` 的值。在组件中，我们绑定了 Vue.js 生命周期中的所有钩子函数，并通过控制台输出相应的消息来表示当前执行的生命周期钩子。

在组件的生命周期中，当组件被创建时，Vue.js 会依次触发 `beforeCreate` 和 `created` 钩子函数，在 `created` 钩子函数中可以访问组件 `data` 数据和 `el` 元素，但此时组件尚未挂载到页面中。接下来，当 Vue.js 开始挂载组件时，会依次触发 `beforeMount` 和 `mounted` 钩子函数，在 `mounted` 钩子函数中组件已经被挂载到页面中，此时可以对 `this.$el` 进行相关操作。

在组件挂载后，如果组件中的 `data` 有变化，那么 Vue.js 会依次触发 `beforeUpdate` 和 `updated` 钩子函数，分别表示数据更新前后的状态。在所有的钩子函数执行完成后，Vue.js 会在组件销毁时依次触发 `beforeDestroy` 和 `destroyed` 钩子函数，分别表示销毁前和销毁后的状态，这个时候应该清除所有的事件监听器和定时器，否则可能会造成内存泄漏的问题。

通过这个示例，可以更好地理解 Vue.js 的生命周期过程，并注意在不同的生命周期阶段下执行不同的操作，从而使组件功能更加完善和稳定。

## 21.箭头函数的带大括号与不带大括号的区别

`(x) => x + 1` 与 `(x) => {x + 1}` 的区别是：

- `(x) => x + 1` 是一个箭头函数，它接受一个参数 `x`，返回 `x+1` 的结果。
- `(x) => {x + 1}` 也是一个箭头函数，但是它使用了花括号 `{}`，其中包含了一个语句 `x + 1`。由于花括号中包含语句而非表达式，因此需要使用 `return` 语句将结果返回。

具体来说，`(x) => {x + 1}` 不会直接返回 `x + 1` 的结果，而是返回 `undefined`，因为花括号中并没有 `return` 语句将结果返回。因此需要将其改写为 `(x) => {return x + 1;}` 或 `function(x){return x + 1;}` 才能实现与 `(x) => x + 1` 相同的功能。

综上，`(x) => x + 1` 是一个返回表达式的箭头函数，而 `(x) => {x + 1}` 则是一个返回 `undefined` 的箭头函数，需要使用 `return` 语句明确返回结果。

## 22.依赖关系

依赖关系指的是一个模块（类、函数、对象等）依赖于其他模块，即它使用了其他模块中的功能或数据。这种依赖关系可以表现为代码中的函数调用、对象引用、类继承等形式。

在软件开发中，模块化是一种常见的编程思想，它将一个大型的应用程序拆分成多个小的模块，每个模块都有自己的特定功能和职责。这种模块化的设计可以提高代码的可读性、可维护性和可扩展性。

然而，模块之间的依赖关系也可能会导致一些问题。例如，如果一个模块依赖于其他模块中的某个函数或对象，而这个函数或对象被删除或修改了，那么依赖于它的模块也需要进行相应的修改。如果依赖关系过于复杂，这种修改可能会涉及到多个模块，从而增加了代码的维护难度。

因此，在软件开发中，需要注意模块之间的依赖关系，避免出现过于复杂的依赖关系。一些常见的减少依赖关系的方法包括：

- 使用接口或抽象类定义模块之间的通信接口，从而降低了模块之间的耦合度。

- 使用依赖注入（Dependency Injection）等技术，将依赖关系的控制权交给容器，从而减少了模块之间的直接依赖关系。

- 使用事件驱动编程（Event-Driven Programming）等技术，通过事件的发布和订阅来解耦模块之间的依赖关系。

- 以下是一个简单的例子，展示了模块之间的依赖关系：

  ```
  // 定义一个模块A
  const moduleA = {
    data: 'data from module A',
    getData() {
      console.log(this.data);
    }
  };
  
  // 定义一个模块B，依赖于模块A
  const moduleB = {
    data: 'data from module B',
    getData() {
      console.log(this.data);
      moduleA.getData(); // 调用模块A的方法
    }
  };
  
  // 在模块B中调用模块A的方法
  moduleB.getData(); // 输出：data from module B 和 data from module A
  ```

  在这个例子中，模块B依赖于模块A，即在模块B中使用了模块A中的方法。通过调用模块B的getData方法，可以看到它先输出了自己的数据，然后再调用了模块A的getData方法，输出了模块A的数据。这种依赖关系可以通过控制模块之间的通信接口、使用依赖注入等方式进行优化和管理。

## 23.回调函数

  回调函数是一种特殊的函数，它作为参数传递给另一个函数，并在该函数执行完毕后被调用。回调函数通常用于异步编程中，例如在处理网络请求、读取文件、执行数据库操作等情况下，可以使用回调函数等待操作完成后再执行回调函数。

  回调函数的使用方法与普通函数类似，只需要将函数名作为参数传递给另一个函数即可。例如，以下代码演示了在JavaScript中使用回调函数的基本方法：

  ```
  // 定义一个异步函数，接受一个回调函数参数
  function asyncFunction(callback) {
    // 模拟异步操作
    setTimeout(function() {
      console.log('Async operation completed.');
      callback(); // 执行回调函数
    }, 1000);
  }
  
  // 定义一个回调函数
  function callbackFunction() {
    console.log('Callback function executed.');
  }
  
  // 调用异步函数并传入回调函数
  asyncFunction(callbackFunction);
  ```

  在这个例子中，我们定义了一个异步函数`asyncFunction`，它接受一个回调函数`callback`作为参数。在异步函数中，我们使用`setTimeout`方法模拟了一个异步操作，并在操作完成后执行了回调函数。同时，我们也定义了一个回调函数`callbackFunction`，它会在异步操作完成后被调用。最后，我们通过调用异步函数并传入回调函数的方式，实现了在异步操作完成后执行回调函数的效果。

  回调函数能回调的原因是因为在JavaScript中，函数也是一种数据类型，可以被作为参数传递给其他函数。当我们将一个函数作为参数传递给另一个函数时，实际上是将这个函数的引用传递给了另一个函数。在另一个函数中，我们可以通过这个函数的引用来调用它并执行它。因此，在使用回调函数时，我们可以将一个函数作为参数传递给另一个函数

，在异步操作完成后再执行这个函数。这种方式可以避免在异步操作中阻塞代码执行，提高了代码的效率和可读性。

总之，回调函数是一种常见的编程技术，在异步编程中广泛应用。使用回调函数可以避免代码阻塞，提高代码的效率和可读性。同时，回调函数也是一种函数类型，可以被作为参数传递给其他函数，并在其他函数中执行。

### 22.1更简单的例子

以下是一个简单的例子，演示了在JavaScript中使用回调函数的基本方法：

```
// 接受一个数字参数和一个回调函数参数
function square(num, callback) {
  const result = num * num;
  callback(result);
}

// 定义一个回调函数
function printResult(result) {
  console.log("The result is: " + result);
}

// 调用square函数并传入回调函数
square(5, printResult); // 输出：The result is: 25
```

在这个例子中，我们定义了一个`square`函数，它接受一个数字参数和一个回调函数参数。在函数中，我们计算了数字的平方，并将结果传递给回调函数。同时，我们也定义了一个回调函数`printResult`，它会在`square`函数执行完毕后被调用。最后，我们通过调用`square`函数并传入回调函数的方式，实现了在计算完成后输出结果的效果。

----------

以下是一个使用回调函数的简单例子：

function add(a, b, callback) {
  var result = a + b;
  callback(result);
}

function display(result) {
  console.log("The result is " + result);
}

add(2, 3, display);
在这个例子中，我们定义了一个add函数，它接受两个参数a和b，并在它们上执行加法操作。add函数还接受第三个参数callback，它是一个回调函数。

在add函数内部，我们首先计算出结果，然后将其作为参数传递给回调函数callback。在这个例子中，我们将display函数作为回调函数传递给add函数。

display函数将结果作为参数打印到控制台上。

最后，我们调用add函数并传递两个数字和回调函数作为参数。当add函数完成计算时，它将调用回调函数display，并将结果作为参数传递给它。display函数将结果打印到控制台上。

### 22.2函数可以被传递

回调函数能够回调的原因在于JavaScript中的函数是一等公民，也就是说，函数可以像其他数据类型一样被传递、返回、存储等。在JavaScript中，函数不仅可以被定义和调用，还可以作为参数传递给另一个函数或作为另一个函数的返回值。

在异步编程中，我们通常需要在某个操作完成后执行某些代码，但是由于JavaScript是单线程执行的，如果在操作完成前执行这些代码，会导致程序阻塞。为了解决这个问题，我们可以将这些代码封装成一个函数，然后将这个函数作为回调函数传递给异步操作。当异步操作完成后，系统会自动调用这个回调函数，以执行我们需要执行的代码。

回调函数的形式参数通常为函数类型，当异步操作完成后，将会调用这个函数，并将异步操作的结果作为参数传递给这个函数。这样，我们就可以在异步操作完成后使用异步操作的结果进行后续操作。因此，回调函数的能够回调的原因在于函数是一等公民，可以作为参数传递，以及JavaScript的事件循环机制。

## 23.set 与对象的区别

在JavaScript中，`set`和对象（`object`）是两种不同的数据类型，它们具有不同的特点和用途。

`Set`是ES6中新增的一种集合类型，它类似于数组，但是具有以下特点：

- `Set`中的元素是唯一的，不会重复；
- `Set`中的元素是无序的，不能通过下标来访问；
- `Set`中的元素可以是任何数据类型，包括基本类型和对象。

在`Set`中，添加重复元素会被自动忽略，因此`Set`通常被用于去重或者判断元素是否存在等场景。

对象是JavaScript中的一种复合数据类型，它由一组属性（`key-value`对）组成，每个属性都有一个唯一的键和对应的值，可以是基本类型或者其他对象。对象可以通过键来访问和修改属性的值，因此对象通常被用于存储和管理复杂的数据结构。

总之，`Set`和对象是两种不同的数据类型，它们具有不同的特点和用途。`Set`通常被用于去重或者判断元素是否存在等场景，而对象通常被用于存储和管理复杂的数据结构。

## 24.类与构造函数的区别

### 24.1不同的对象创建方式

类（Class）和构造函数（Constructor）是两种不同的对象创建方式，它们具有不同的特点和用途。

构造函数是一种用于创建对象的函数，它使用`new`关键字来创建对象，并且可以接受参数来初始化对象的属性。构造函数通常通过`this`关键字来引用当前对象的属性和方法，同时也可以通过原型链来实现方法的继承。例如：

```
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.sayHello = function() {
  console.log(`Hello, my name is ${this.name}, and I'm ${this.age} years old.`);
};

const person = new Person("Alice", 20);
person.sayHello(); // 输出：Hello, my name is Alice, and I'm 20 years old.
```

在这个例子中，我们定义了一个构造函数`Person`，用于创建`Person`对象。构造函数接受两个参数`name`和`age`，用于初始化对象的属性。然后，我们通过给`Person.prototype`添加方法的方式来定义`sayHello`方法，并将它继承给`Person`对象。最后，我们创建了一个`Person`对象，并调用`sayHello`方法来输出相应的信息。

类是ES6中新增的一种对象创建方式，它使用`class`关键字来定义类，并且使用`new`关键字来创建对象。类中包含了构造函数和实例方法，用于初始化对象的属性和定义对象的行为。类也可以通过继承来实现方法的复用和扩展。例如：

```
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  
  sayHello() {
    console.log(`Hello, my name is ${this.name}, and I'm ${this.age} years old.`);
  }
}

const person = new Person("Alice", 20);
person.sayHello(); // 输出：Hello, my name is Alice, and I'm 20 years old.
```

在这个例子中，我们使用`class`关键在这个例子中，我们使用`class`关键字定义了一个名为`Person`的类。类中包含了一个构造函数`constructor`和一个实例方法`sayHello`。构造函数用于初始化对象的属性，实例方法用于定义对象的行为。在类的内部，可以通过`this`关键字引用当前对象。

我们创建了一个`Person`类的实例，并将`"Alice"`和`20`作为参数传递给构造函数。然后，我们通过调用实例方法`sayHello`来输出相应的信息。

需要注意的是，虽然类的定义和构造函数的定义在语法上有所不同，但它们都可以用来创建对象并定义对象的行为。类的定义更加清晰和简洁，具有更好的可读性和可维护性，同时还提供了继承和其他高级特性的支持。而构造函数则更加灵活，可以通过原型链自由地扩展和定制对象的方法和属性。

总之，类和构造函数是两种不同的对象创建方式，它们具有不同的特点和用途。在实际开发中，可以根据具体的需求和场景选择合适的方式来创建对象和定义对象的行为。

### 24.2 不同的继承方式

此外，类和构造函数的继承方式也有所不同。在构造函数中，可以通过修改原型链来实现继承。例如，可以通过将子类的原型对象指向父类的一个实例来实现继承。例如：

```
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.sayHello = function() {
  console.log(`Hello, my name is ${this.name}, and I'm ${this.age} years old.`);
};

function Student(name, age, grade) {
  Person.call(this, name, age);
  this.grade = grade;
}

Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;

const student = new Student("Bob", 18, 90);
student.sayHello(); // 输出：Hello, my name is Bob, and I'm 18 years old.
```

在这个例子中，我们定义了一个`Person`构造函数和一个`Student`构造函数。然后，我们通过在`Student`构造函数中调用`Person`构造函数并继承其属性，来实现对`Person`构造函数的继承。接着，我们通过将`Student`的原型对象指向一个`Person`实例来继承`Person`的方法。最后，我们创建了一个`Student`对象，并调用`sayHello`方法来输出相应的信息。

在类中，继承使用`extends`关键字来实现。例如：

```
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  
  sayHello() {
    console.log(`Hello, my name is ${this.name}, and I'm ${this.age} years old.`);
  }
}

class Student extends Person {
  constructor(name, age, grade) {
    super(name, age);
    this.grade = grade;
  }
}

const student = new Student("Bob", 18, 90);
student.sayHello(); // 输出：Hello, my name is Bob, and I'm 18 years old.
```

在这个例子中，我们定义了一个`Person`类和一个`Student`类，并使用`extends`关键字将`Student`类继承自`Person`类，从而实现对`Person`类的继承。在`Student`类的构造函数中，我们通过调用`super`关键字来调用父类的构造函数并继承其属性。然后，我们定义了一个`grade`属性，用于表示学生的分数。最后，我们创建了一个`Student`对象，并调用`sayHello`方法来输出相应的信息。

需要注意的是，类的继承方式更加简洁和直观，同时也提供了更好的语言特性支持，例如`super`关键字和`constructor`方法。而构造函数的继承方式则更加灵活，可以通过原型链自由地扩展和定制对象的方法和属性。

总之，类和构造函数是两种不同的对象创建方式，它们具有不同的特点和用途。类提供了更加清晰和简洁的语法来定义对象和实现继承，而构造函数则更加灵活和自由。在实际开发中，可以根据具体的需求和场景选择合适的方式来创建对象和定义对象的行为。

### 24.3高级特性

此外，类还提供了一些其他的高级特性，例如静态方法、getter和setter等。

静态方法是指类的方法，不需要实例化对象就可以调用。在类中，可以使用`static`关键字来定义静态方法。例如：

```
class MathUtil {
  static add(x, y) {
    return x + y;
  }
}

console.log(MathUtil.add(1, 2)); // 输出：3
```

在这个例子中，我们定义了一个`MathUtil`类，并使用`static`关键字定义了一个静态方法`add`。静态方法可以直接通过类来调用，而不需要先实例化对象。

Getter和Setter是指用于读取和设置对象属性的方法。在类中，可以使用`get`和`set`关键字来定义Getter和Setter方法。例如：

```
class Person {
  constructor(name, age) {
    this._name = name;
    this._age = age;
  }
  
  get name() {
    return this._name;
  }
  
  set name(value) {
    this._name = value;
  }
  
  get age() {
    return this._age;
  }
  
  set age(value) {
    if (value > 0 && value < 100) {
      this._age = value;
    } else {
      throw new Error("Invalid age value.");
    }
  }
}

const person = new Person("Alice", 20);
console.log(person.name); // 输出：Alice
person.name = "Bob";
console.log(person.name); // 输出：Bob
console.log(person.age); // 输出：20
person.age = 200; // 抛出异常：Invalid age value.
```

在这个例子中，我们定义了一个`Person`类，并使用`get`和`set`关键字定义了`name`和`age`属性的Getter和Setter方法。Getter方法用于读取属性的值，Setter方法用于设置属性的值。在Setter方法中，我们可以对属性的值进行验证和处理。

需要注意的是，Getter和Setter方法可以使用不同的属性名来定义，例如在上面的例子中，我们使用了`_name`和`_age`属性来存储实际的属性值，并使用`name`和`age`来定义Getter和Setter方法。这样可以保证Getter和Setter方法的调用方式与普通属性的调用方式相同，同时也可以避免Getter和Setter方法的递归调用。

总之，类提供了一系列高级特性，例如静态方法、Getter和Setter等，可以更加方便地实现对象的行为和属性的管理。在实际开发中，需要根据具体的需求和场景选择合适的特性来使用。

### 24.4语法特性

除了上述特性之外，类还有一些其他的语法和用法需要注意。

首先是类的表达式语法。类可以像函数一样，使用表达式来定义。例如：

```
const MyClass = class {
  constructor(name) {
    this.name = name;
  }
  
  sayHello() {
    console.log(`Hello, ${this.name}!`);
  }
};

const obj = new MyClass("Alice");
obj.sayHello(); // 输出：Hello, Alice!
```

在这个例子中，我们使用类表达式的方式定义了一个名为`MyClass`的类，并创建了一个`MyClass`的实例。类表达式与类声明的语法类似，只是将类名省略了而已。

其次是类的默认构造函数。如果类没有定义构造函数，那么会默认生成一个空的构造函数。例如：

```
class MyClass {
  sayHello() {
    console.log("Hello!");
  }
}

const obj = new MyClass();
obj.sayHello(); // 输出：Hello!
```

在这个例子中，我们定义了一个名为`MyClass`的类，并在其中定义了一个`sayHello`方法。由于没有定义构造函数，因此会默认生成一个空的构造函数。我们创建了一个`MyClass`的实例，并调用`sayHello`方法来输出相应的信息。

最后是类的继承链。在类的继承中，如果一个子类继承自多个父类，那么它的继承链会按照从左到右的顺序进行。例如：

```
class A {
  sayHello() {
    console.log("Hello from A!");
  }
}

class B {
  sayHello() {
    console.log("Hello from B!");
  }
}

class C extends A,B {
  
}

const obj = new C();
obj.sayHello(); // 输出：Hello from A!
```

在这个例子中，我们定义了三个类`A`、`B`和`C`。类`C`继承自类`A`和类`B`，并且没有定义自己的`sayHello`方法。由于继承链的顺序是从左到右，因此`C`类的`sayHello`方法会继承自`A`类而不是`B`类。我们创建了一个`C`类的实例，并调用`sayHello`方法来输出相应的信息。

需要注意的是，如果类的继承链中存在同名的方法，那么会按照从左到右的顺序取第一个方法。这个特性在多重继承和方法的定制中非常有用。

总之，类是ES6中新增的一种语言特性，提供了更加清晰和简洁的语法来定义对象和实现继承。类的特性和用法也非常丰富，可以根据具体的需求和场景选择合适的特性来使用。在实际开发中，需要熟练掌握类的语法和用法，以便更加高效地进行编程。

## 25.链式写法

链式写法是一种将多个操作按照一定的顺序连在一起的编程风格。在链式写法中，每个操作都返回自身的对象，从而可以继续进行下一个操作。这种风格的代码通常非常简洁和直观，可以提高代码的可读性和可维护性。

链式写法通常使用方法链的方式实现。在方法链中，每个方法都返回自身的对象，从而可以继续调用下一个方法。例如：

```
// 传统的写法
const arr = [1, 2, 3];
const filtered = arr.filter(function(item) {
  return item > 1;
});
const mapped = filtered.map(function(item) {
  return item * 2;
});

// 链式写法
const arr = [1, 2, 3];
const mapped = arr.filter(function(item) {
  return item > 1;
}).map(function(item) {
  return item * 2;
});
```

在这个例子中，我们分别使用传统的写法和链式写法来实现了一个数组的过滤和映射操作。在传统的写法中，我们需要使用多个中间变量来存储中间结果。而在链式写法中，我们可以直接将多个操作连接在一起，从而避免了中间变量的使用，使得代码更加简洁和直观。

-------

链式写法通常是从左往右进行读取和理解的。在链式写法中，每个方法都是基于前一个方法的结果进行操作的，因此需要按照从左往右的顺序进行读取和理解。例如，在下面的代码中：

```
const result = arr.filter(function(item) {
  return item > 1;
}).map(function(item) {
  return item * 2;
});
```

我们可以先看到`arr`对象的`filter`方法，然后再看到`map`方法。这样就能够理解这段代码的含义，即先将数组`arr`中大于1的元素过滤出来，然后将剩余的元素都乘以2。

需要注意的是，有些方法也可以从右往左进行读取和理解。例如，在下面的代码中：

```
const result = arr.reduceRight(function(prev, curr) {
  return prev + curr;
});
```

我们可以先看到`arr`对象的`reduceRight`方法，然后再看到回调函数。这样就能够理解这段代码的含义，即从右往左地对数组`arr`中的元素进行累计求和。

总之，链式写法需要按照从左往右的顺序进行读取和理解，以便理解代码的含义和作用。在实际开发中，需要注意代码的可读性和可维护性，以便其他开发者能够更加容易地理解和维护代码

## 26.形参命名为什么经常用foo

形参命名为`foo`、`bar`、`baz`等是一种编程中常用的命名方式，通常被称为哑变量或占位符。这种命名方式的目的是为了强调变量的重要性或类型，同时也可以避免歧义和冲突。**类似张三和李四，foo第一个无名变量，bar第二个无名变量，以此类推**

具体来说，这种命名方式通常用于以下几个方面：

1. 强调变量的重要性：在一些情况下，变量的名称并不重要，重要的是变量的作用和含义。例如，在某些算法和数据结构中，变量的名称可能并不重要，重要的是它们的作用和含义。使用哑变量或占位符可以强调变量的作用和含义，而不会分散注意力。
2. 强调变量的类型：在一些情况下，变量的类型比名称更加重要。例如，在某些函数中，参数的类型可能比名称更加重要。使用哑变量或占位符可以强调变量的类型，而不会分散注意力。
3. 避免歧义和冲突：在一些情况下，变量的命名可能会引起歧义和冲突。例如，在一些示例代码和教学材料中，变量的名称可能已经被占用或者已经有了特定的含义。使用哑变量或占位符可以避免歧义和冲突，使得示例代码和教学材料更加通用和易懂。

需要注意的是，虽然哑变量或占位符可以提高代码的可读性和可维护性，但是也需要注意使用的场景和范围。在实际开发中，应该根据具体的需求和场景选择合适的命名方式，以便其他开发者能够更加容易地理解和维护代码。

此外，还有一些其他的命名方式和规范，例如驼峰命名法、下划线命名法等。这些命名方式和规范都有自己的特点和适用场景，需要根据具体的需求和场景选择合适的命名方式和规范。

驼峰命名法是一种常用的命名方式，它将多个单词连接起来，每个单词的首字母大写，除第一个单词外其他单词的首字母都小写。例如，`firstName`、`lastName`、`emailAddress`等。驼峰命名法通常用于变量、函数和对象的命名。

下划线命名法是另一种常用的命名方式，它将多个单词连接起来，每个单词之间用下划线分隔。例如，`first_name`、`last_name`、`email_address`等。下划线命名法通常用于数据库表名、URL路径、CSS类名等。

需要注意的是，在使用命名方式和规范时，应该尽量保持一致性和规范性，以便提高代码的可读性和可维护性。同时，也需要注意命名的长度和含义，以避免过长或者过短的命名导致代码的可读性下降。

------

在编程中，选择合适的变量名是非常重要的，可以提高代码的可读性和可维护性。在不同的场景下，选择不同的变量名可以更好地表达变量的含义和作用。

下面是一些常见的场景和对应的变量名：

1. 数组和列表：对于数组和列表中的元素，可以使用单数的名词来表示。例如，`item`、`element`、`value`等。
2. 布尔值：对于布尔值，可以使用形容词或动词的过去分词来表示。例如，`isDone`、`isEnabled`、`hasError`等。
3. 函数和方法：对于函数和方法，可以使用动词或动词短语来表示。例如，`getLength`、`calculateSum`、`renderList`等。
4. 对象和类：对于对象和类，可以使用名词来表示。例如，`person`、`customer`、`product`等。
5. 常量：对于常量，可以使用全大写的字母和下划线来表示。例如，`MAX_VALUE`、`DEFAULT_TIMEOUT`等。
6. 迭代器和计数器：对于迭代器和计数器，可以使用单词或单词缩写来表示。例如，`i`、`j`、`k`、`index`、`count`等。

需要注意的是，在选择变量名时，应该遵循命名规范和良好的编程习惯，以便提高代码的可读性和可维护性。同时，在实际开发中，应该根据具体的需求和场景选择合适的变量名，以便其他开发者能够更加容易地理解和维护代码。

-----

`foo`、`bar`、`baz`是一组常用的哑变量或占位符，通常用于编程中临时测试、示例代码、伪代码等场景。这些变量名通常被视为没有具体含义的变量名，只是作为占位符来使用。

在实际开发中，这三个变量名通常用于测试代码和示例代码中，以便提供一些简单的例子来说明代码的用法和效果。例如，在下面的代码中：

```
function add(foo, bar) {
  return foo + bar;
}

const result = add(2, 3);
console.log(result); // 输出 5
```

我们使用了`foo`和`bar`作为函数`add`的参数，这两个变量名并没有具体的含义，只是作为占位符来使用。这样可以更加简单地说明函数`add`的用法和效果，而不会分散注意力。

需要注意的是，尽管这些变量名通常被视为没有具体含义的变量名，但是在实际开发中，我们应该尽量使用有意义的变量名来提高代码的可读性和可维护性。只有在一些简单的测试代码和示例代码中，才可以使用这些占位符变量名.

## 27.双标签改单标签

要将双标签形式中的尾标签删除，同时将尾标签中的 `/` 删除，这样就变成了单标签形式。

例如，将双标签形式的 `<input type="text"></input>` 改成单标签形式，就需要将它修改成 `<input type="text">`。

另外，需要注意的是，并非所有的双标签都可以简单地改成单标签。如果一个双标签有子元素或者属性值为空，那么它就无法转换成单标签。例如 `<div><span></span></div>`、`<input type="text" value="">` 等都无法改成单标签形式。只有像上面示范的那个例子一样，没有子元素并且没有属性值为空的双标签才能写成单标签形式。

好的，下面再给一些例子来详细介绍如何将双标签改成单标签。

1. `<img>` 标签

`<img>` 标签是 HTML 中最常见的单标签之一，它表示文档中的图像。在双标签形式中，它通常被写成 `<img></img>` 或者 `<img />` 的形式。

将其改成单标签的形式，只需要删除尾标签即可，这样就得到了 `<img>` 标签的单标签形式。

1. `<input>` 标签

`<input>` 标签用来表示文档中的表单控件，例如文本框、单选框、复选框等。在双标签形式中，它通常被写成 `<input></input>` 或者 `<input />` 的形式。

对于 `<input>` 标签来说，如果它没有子元素和属性值，那么它就可以改成单标签的形式。例如 `<input type="text" name="username" />` 就是合法的单标签形式。

但如果它有子元素或者属性值为空，那么它就不能改成单标签的形式。例如 `<input type="text">输入框</input>` 和 `<input type="text" value="" />` 都不能改成单标签的形式。

1. `<br>` 标签

`<br>` 标签用来表示文档中的换行符。在双标签形式中，它通常被写成 `<br></br>` 或者 `<br />` 的形式。

和 `<img>` 标签一样，将 `<br>` 标签改成单标签的形式，只需要删除尾标签即可，这样就得到了 `<br>` 标签的单标签形式。

1. `<link>` 标签

`<link>` 标签用来加载外部资源，例如样式表、脚本文件等。在双标签形式中，它通常被写成 `<link></link>` 或者 `<link />` 的形式。

和 `<input>` 标签一样，对于 `<link>` 标签来说，如果它没有子元素和属性值，那么它就可以改成单标签的形式。例如 `<link rel="stylesheet" href="style.css" />` 就是合法的单标签形式。

但如果它有子元素或者属性值为空，那么它就不能改成单标签的形式。例如 `<link>` 标签中的属性 rel 和 href 就不能为空。

1. `<meta>` 标签

`<meta>` 标签用来表示文档的元数据，例如编码方式、关键字、描述等。在双标签形式中，它通常被写成 `<meta></meta>` 或者 `<meta />` 的形式。

对于 `<meta>` 标签来说，如果它没有子元素和属性值，那么它就可以改成单标签的形式。例如 `<meta charset="utf-8" />` 就是合法的单标签形式。

但如果它有子元素或者属性值为空，那么它就不能改成单标签的形式。例如 `<meta>` 中的 charset 属性就不能为空。

1. `<hr>` 标签

`<hr>` 标签用来表示文档中的水平线。在双标签形式中，它通常被写成 `<hr></hr>` 或者 `<hr />` 的形式。

和 `<img>` 标签一样，将 `<hr>` 标签改成单标签的形式，只需要删除尾标签即可，这样就得到了 `<hr>` 标签的单标签形式。

1. `<source>` 标签

`<source>` 标签用来定义多媒体资源（如视频、音频）的可选来源。在双标签形式中，它通常被写成 `<source></source>` 或者 `<source />` 的形式。

和 `<input>` 标签一样，对于 `<source>` 标签来说，如果它没有子元素和属性值，那么它就可以改成单标签的形式。例如 `<source src="video.mp4" type="video/mp4" />` 就是合法的单标签形式。

但如果它有子元素或者属性值为空，那么它就不能改成单标签的形式。例如 `<source>` 标签中的 src 和 type 属性就不能为空。

总之，将双标签改成单标签的关键就是删除尾标签。但需要注意的是，并非所有的双标签都可以简单地改成单标签，只有没有子元素并且没有属性值为空的双标签才能改成单标签。所以在修改标签形式的时候，一定要注意检查标签中的子元素和属性值。

## 28.多层嵌套数组，对象

```
const {
  a: {
    b: {c}
  }
} = obj;
console.log(c); // 1
```

1. 解构多层数组和对象

```
const data = [
  {
    id: 1,
    name: 'Alice',
    cats: [
      {id: 1, name: 'Mimi'},
      {id: 2, name: 'Kiki'}
    ]
  },
  {
    id: 2,
    name: 'Bob',
    cats: [{id: 3, name: 'Lala'}]
  }
];

const [{cats: [cat1, cat2]}, {cats: [cat3]}] = data;
console.log(cat1, cat2, cat3); // { id: 1, name: 'Mimi' } { id: 2, name: 'Kiki' } { id: 3, name: 'Lala' }
```

以上示例中，使用 `...` 操作符将多层的数据结构展开并解构到变量中，简化了代码并使得操作更加清晰易懂。在实际开发中，可以根据具体情况选择使用解构赋值的方式来取出多层嵌套结构中的值。

### 28.2更多示例

多层嵌套数组和多层嵌套对象都是在编程中常见的数据结构，本质上它们都是存储一组相关数据的容器。

1. 多层嵌套数组

多层嵌套数组指的是将多个数组嵌套在一起的数据结构，形成了多层的嵌套结构。例如，下面的代码展示了一个三层嵌套数组的例子：

```
const arr = [
  [1, 2, 3],
  [4, 5, 6, [7, 8]],
  [9]
];
```

在这个例子中，常量 arr 是一个三层嵌套的数组，其中第二层的第四个元素又是一个二层嵌套的数组。通过多层嵌套，我们可以方便地表示复杂的数据结构和数据关系。

要访问嵌套数组中的元素，可以通过多次使用数组索引来获取。例如，获取第三个元素的第一个元素的值，可以使用下面的代码：

```
const x = arr[2][0];
```

1. 多层嵌套对象

多层嵌套对象指的是将多个对象嵌套在一起的数据结构，形成了多层的嵌套结构。例如，下面的代码展示了一个三层嵌套对象的例子：

```
const obj = {
  name: 'Alice',
  age: 20,
  address: {
    country: 'USA',
    city: 'New York',
    street: {
      name: 'Broadway',
      number: 1234
    }
  }
};
```

在这个例子中，常量 obj 是一个三层嵌套的对象，其中第二层和第三层都是嵌套的对象。通过多层嵌套，我们可以方便地表示复杂的数据结构和数据关系。

要访问嵌套对象中的属性，可以使用点号（.）操作符或方括号（[]）操作符来获取。例如，获取地址的街道名称，可以使用下面的代码：

```
const streetName = obj.address.street.name;
```

需要注意的是，在使用点号操作符时，属性名必须是一个合法的标识符。如果属性名中包含特殊字符或关键字，就必须使用方括号操作符，并将属性名用引号括起来。例如：

```
const propertyName = 'street.name';
const value = obj['address'][propertyName];
```

1. 嵌套数组和嵌套对象的异同点

虽然嵌套数组和嵌套对象都是用于存储多个相关数据的容器，但它们之间还是有一些区别和异同点的。

相同点：

- 均可进行多级嵌套，可以表示较为复杂的数据结构。
- 均可访问其内部嵌套的元素或属性。

不同点：

- 嵌套数组是一种基于索引值来访问和操作的数据结构，而嵌套对象是一种基于属性名来访问和操作的数据结构。
- 嵌套数组的元素是有序的，而嵌套对象的属性是无序的。
- 在实际开发中，嵌套数组常用于存储一组相同类型的数据，而嵌套对象则常用于存储一个实体对象的各个属性。
- 嵌套数组可以使用循环来遍历、查找、过滤和修改数据，而嵌套对象则可以使用对象方法和操作符来操作属性，如 Object.keys()、Object.values()、Object.assign() 等。

1. 多层嵌套数组与多层嵌套对象的注意事项

在使用多层嵌套数组或多层嵌套对象时，需要注意以下事项：

- 不要过度嵌套，一般不要超过三层。
- 尽量保持数据结构清晰，以便于阅读和维护代码。
- 多层嵌套数组和多层嵌套对象的访问操作比较繁琐和易错，需要仔细处理。建议使用变量和常量来保存中间结果，以便于复用。
- 在修改多层嵌套数组或多层嵌套对象时，请避免对原数据进行直接修改，可以使用深拷贝（deep clone）来获得一份新的数据，然后对新的数据进行修改。否则可能会引起意外的副作用。
- 使用多层嵌套数组或多层嵌套对象时，还需要考虑数据之间的关系和依赖，以便于数据之间的传递和交互。例如，可以使用回调函数、事件监听器、Promise、Async/Await 等机制进行数据传递和交互。
- 示例代码

下面通过一些示例代码来演示使用多层嵌套数组和多层嵌套对象的相关操作。

5.1. 多层嵌套数组的示例代码：

```
const arr = [
  [1, 2, 3],
  [4, 5, 6, [7, 8]],
  [9]
];

// 访问嵌套数组的元素
const x = arr[1][3][1]; // 8

// 遍历嵌套数组的所有元素
for(let i = 0; i < arr.length; i++) {
  for(let j = 0; j < arr[i].length; j++) {
    console.log(arr[i][j]);
  }
}

// 过滤嵌套数组的元素
const filteredArr = arr.filter(item => item.includes(2));
console.log(filteredArr); // [[1, 2, 3]]

// 修改嵌套数组的元素
arr[1][1] = 0;
console.log(arr); // [[1, 2, 3], [4, 0, 6, [7, 8]], [9]]
```

5.2. 多层嵌套对象的示例代码：

```
const obj = {
  name: 'Alice',
  age: 20,
  address: {
    country: 'USA',
    city: 'New York',
    street: {
      name: 'Broadway',
      number: 1234
    }
  }
};

// 访问嵌套对象的属性
const streetName = obj.address.street.name; // Broadway

// 遍历嵌套对象的所有属性
for(let prop in obj) {
  if(typeof obj[prop] === 'object') {
    for(let subProp in obj[prop]) {
      console.log(subProp + ': ' + obj[prop][subProp]);
    }
  } else {
    console.log(prop + ': ' + obj[prop]);
  }
}

// 修改嵌套对象的属性
obj.address.street.number = 5678;
console.log(obj);
/* {
  name: 'Alice',
  age: 20,
  address: {
    country: 'USA',
    city: 'New York',
    street: {
      name: 'Broadway',
      number: 5678
    }
  }
} */
```

### 28.3多层数组合并到一个数组

可以使用 `...` 操作符并结合 `Array.reduce()` 方法来合并多个数组套数组到一个数组中。`Array.reduce()` 方法会遍历每个数组并将其合并到一个新的数组中，代码实现如下：

```
const arr = [[1, 2], [3, 4], [5, 6]];
const flattened = arr.reduce((acc, val) => acc.concat(val), []);

console.log(flattened); // [1, 2, 3, 4, 5, 6]
```

在上面的示例中，`arr` 是一个由三个数组组成的数组。使用 `Array.reduce()` 方法将它们合并到一个新的数组 `flattened` 中。在每次迭代中，回调函数接收两个参数，即累加器（`acc`）和当前值（`val`）。起始值为一个空数组（`[]`）。在每次迭代中，将当前值（一个数组）连接到累加器中。最后返回一个扁平化后的数组。

如果你使用了 ES6，还可以用简化的箭头函数语法和展开运算符来简化代码：

```
const arr = [[1, 2], [3, 4], [5, 6]];
const flattened = arr.reduce((acc, val) => [...acc, ...val], []);

console.log(flattened); // [1, 2, 3, 4, 5, 6]
```

以上两种方法均可实现将多个数组套数组合并到一个数组中。

**如果需要将多层嵌套的数组全部展开到一个新数组中**，除了使用多层的 `Array.reduce()` 递归调用外，还可以使用 ES6 中的展开运算符和递归函数来实现。具体实现如下：

```
function flatten(arr) {
  return arr.reduce((acc, val) => Array.isArray(val) ? [...acc, ...flatten(val)] : [...acc, val], []);
}

const arr = [[1, [2], [3, [[4]]]], 5];

console.log(flatten(arr)); // [1, 2, 3, 4, 5]
```

在上面的代码中，`flatten` 函数递归调用自身并使用展开运算符将每个层次的数组展开到一个新数组中。在每个迭代中，如果当前值为数组，则递归调用 `flatten` 函数，否则直接将它添加到新数组中。最终会得到扁平化后的数组 `[1, 2, 3, 4, 5]`。

需要注意的是，如果嵌套的数组很多，递归调用函数可能会导致栈溢出的问题。可以使用尾调用优化或其他的解决方案来解决这个问题。

### 28.4对象的嵌套合并

在 JavaScript 中，对象可以包含其他对象或数组，并且可以嵌套多层。如果需要将多层嵌套的对象或数组全部展开到一个新对象或数组中，可以使用递归函数和 ES6 中的展开运算符来实现。

展开对象中的嵌套对象示例如下：

```
const obj = {
  a: 1,
  b: {
    c: 2,
    d: {
      e: 3
    }
  },
  f: [4, 5, [6, 7]]
};

function flattenObj(obj) {
  return Object.entries(obj).reduce((acc, [key, val]) => {
    return acc.concat(
      typeof val === "object" && !Array.isArray(val)
        ? flattenObj(val)
        : { [key]: val }
    );
  }, []);
}

const flattenedObj = Object.assign({}, ...flattenObj(obj));

console.log(flattenedObj);
// { a: 1, c: 2, e: 3, '0': 4, '1': 5, '2': [ 6, 7 ] }
```

在上面的代码中，`flattenObj` 函数递归调用自身并使用 `Object.entries()` 方法将对象转换为可迭代的键/值数组。在每个迭代中，如果当前值为对象，则递归调用 `flattenObj` 函数。否则，将当前键/值对转换为一个新对象并返回。最后使用展开运算符和 `Object.assign()` 方法将所有新对象合并成一个扁平化的新对象。

展开数组中的嵌套数组示例如下：

```
const arr = [1, [2, [3, [4]]], 5];

function flattenArr(arr) {
  return arr.reduce((acc, val) =>
    Array.isArray(val) ? acc.concat(flattenArr(val)) : acc.concat(val), []);
}

const flattenedArr = flattenArr(arr);

console.log(flattenedArr); // [ 1, 2, 3, 4, 5 ]
```

在上面的代码中，`flattenArr` 函数递归调用自身并使用 `Array.reduce()` 方法遍历每个嵌套数组。在每个迭代中，如果当前值为数组，则递归调用 `flattenArr` 函数。否则，将当前值添加到新数组中。最后返回扁平化后的新数组。

需要注意的是，在处理对象或数组时，循环引用可能会导致无限递归的问题。需要特别小心处理或者采取其他的解决方案。

## 29.重排重绘

重排和重绘是网页性能优化中重要的概念。**重排（reflow）**指的是当DOM结构发生改变，影响到元素的布局、尺寸、位置等属性时，浏览器需要重新计算元素的几何属性和布局，这个过程就是重排。而**重绘（repaint）**则是指当元素的样式发生改变，但不影响到布局时，浏览器只需要重新绘制元素的视觉效果，这个过程就是重绘。重排和重绘都会消耗大量的计算资源，因此会影响网页的性能。以下是一些常见的导致重排和重绘的操作：

1.改变元素的位置、尺寸和布局：包括改变元素的宽高、margin、padding、border、position、display等属性。

2.改变元素的内容：包括改变文本内容、图片大小、添加或删除DOM节点等操作。

3.改变浏览器窗口大小：当窗口大小改变时，会影响到整个页面的布局，因此会触发重排。

为了减少重排和重绘的次数，可以采取以下措施：

1.使用CSS3的transform属性来改变元素的位置和尺寸，而不是通过改变元素的position、width、height等属性。

2.将需要多次操作的元素，先脱离文档流，进行操作后再重新插入文档流。

3.对需要改变的元素，先使用display:none将其隐藏，修改完后再显示。

4.使用requestAnimationFrame来优化动画效果，避免频繁的重排和重绘。

5.避免频繁地修改DOM：可以先将需要修改的数据存储在JavaScript中，最后一次性更新到DOM中。

6.使用CSS Sprites来减少图片的请求次数，将多张小图片合成一张大图，通过background-position来显示不同的图片。

7.避免使用table布局：table布局很容易导致重排，可以使用div+CSS布局代替。

8.使用缓存技术：对于静态资源，可以使用浏览器缓存或CDN缓存来减少请求次数。

9.使用CSS动画代替JavaScript动画：CSS动画可以避免频繁的JavaScript操作，减少重排和重绘的次数。

总之，减少重排和重绘是优化网页性能的重要手段之一，需要在开发过程中注意避免频繁进行DOM操作和样式修改，以及采用一些优化技术来减少不必要的重排和重绘。

## 30.循环中，判断条件，重复某值用if赋值比较好还是取余？

这两种方法都可以实现让`index`在循环中到达7后重新从0开始。但是在实际开发中，推荐使用`index % 7`的方法，因为它比`if(index===7) index=0`的方法更简洁、更易读、更易扩展。

使用取模运算符`%`可以将`index`的值限制在0~6的范围内，当`index`的值达到7时，`index % 7`的结果为0，从而实现了从头开始的效果。而使用`if(index===7) index=0`的方法则需要显式地判断`index`的值是否为7，代码量较大，不够简洁。

此外，如果循环的次数需要变更为其他值，如10或者14，使用取模运算符也可以轻松实现，只需要将7改为相应的值即可。而使用`if`语句则需要手动修改判断条件和重新赋值的代码，不够易扩展。

因此，使用取模运算符`%`可以使代码更简洁、易读和易扩展，是更好的选择。

## 31.return num++与return ++num的区别

### 31.1前后置++的区别

不一样，而且`return`不会影响后续的+1。

`return num++` 先返回num的值，然后再将num加1，相当于先返回原来的num值，再执行`num=num+1`。

而 `return ++num` 先将num加1，再返回新的num的值，相当于先执行`num=num+1`，然后再返回新的num值。

例如：

```
let num = 1;
console.log(return num++); // 输出1
console.log(num); // 输出2

num = 1;
console.log(return ++num); // 输出2
console.log(num); // 输出2
```

因此，`return num++` 和 `return ++num` 的返回值是不同的，需要根据具体情况选择使用哪个。

### 31.2 return 为什么不会影响

`return` 依旧影响，但是后置++，返回的是没有+1的值；前置+1可以看成在`return`语言前已经+1了，所以返回了+1的值。

是的，`return ++num` 先将 `num` 加 1，然后再返回新的 `num` 的值。相当于先执行 `num = num + 1`，然后再执行 `return num`。

因此，可以理解为 `num = num + 1` 在 `return` 语句前面执行了。在执行 `return ++num` 语句时，`num` 的值已经被加 1 了，然后将加 1 后的 `num` 值作为返回值返回。

例如：

```
function test() {
  let num = 1;
  return ++num;
}
console.log(test()); // 输出2
```

在这个例子中，`test` 函数返回 `2`，因为 `return ++num` 语句先将 `num` 加 1，然后再返回新的 `num` 值，即 `2`。

因此，可以理解为 `num = num + 1` 在 `return` 语句前面执行了。

## 33.函数中return的理解

### 33.1如果没有返回值就返回undefined

```
function doSomething() {
  // 这里不需要返回值
}
function doSomethingElse() {
  return; // 返回 undefined
}
console.log(doSomething()); // 输出 undefined
console.log(doSomethingElse()); // 输出 undefined
```

在这个例子中，`doSomething` 函数和 `doSomethingElse` 函数都没有明确使用 `return` 语句返回值，因此它们的返回值都是 `undefined`。在 JavaScript 中，如果函数没有明确使用 `return` 语句返回值，那么函数默认返回 `undefined`。

## 34.' ' 与 “ ” 都是字符串，这两个有什么区别

在 JavaScript 中，`''` 与 `""` 都表示空字符串，它们没有本质区别。即使在字符串拼接、字符串截取、字符串比较等操作中，也没有区别。

例如：

```
let str1 = '';
let str2 = "";
console.log(str1 === str2); // 输出 true
console.log(str1 + str2); // 输出空字符串 ''
console.log(str1.substring(0, 1)); // 输出空字符串 ''
console.log(str1.length === str2.length); // 输出 true
```

在这个例子中，`str1` 和 `str2` 都表示空字符串，它们之间没有区别。我们可以使用 `===` 运算符比较它们的值，也可以进行字符串拼接、字符串截取、字符串比较等操作。

需要注意的是，在编写 JavaScript 代码时，应该保持一致性，即要么使用单引号 `''`，要么使用双引号 `""`，不要混用。这样可以使代码风格更加统一，易于阅读和维护。

### 34.1为什么有两个呢？

使用两种不同的引号来表示字符串，可以让程序员在字符串中使用另一种引号，而不必进行转义。例如：

```
let str1 = "It's a beautiful day.";
let str2 = 'She said, "Hello."';

```

在这个例子中，`str1` 使用了双引号，因此可以在字符串中使用单引号；`str2` 使用了单引号，因此可以在字符串中使用双引号。如果使用相同的引号来表示字符串，那么在字符串中使用相同的引号就需要进行转义，这会使代码变得难以阅读和维护。

在实际编码中，我们可以根据具体情况选择使用单引号 `''` 或双引号 `""` 来表示字符串，以便让代码更加易于编写和阅读。

## 35.函数数据类型

### 35.1 函数数据

在 JavaScript 中，`function` 是一种数据类型，它可以表示一个函数。JavaScript 中的函数是一等公民，也就是说函数可以像其他类型的值一样被赋值、传递、返回和存储。

例如，我们可以将一个函数赋值给一个变量，然后通过变量来调用这个函数：

```
function add(a, b) {
  return a + b;
}

let sum = add;
console.log(sum(1, 2)); // 输出 3
```

在这个例子中，我们将 `add` 函数赋值给了 `sum` 变量，然后通过 `sum` 变量来调用这个函数。

我们也可以将一个函数作为参数传递给另一个函数，然后在函数内部调用这个函数：

```
function add(a, b) {
  return a + b;
}

function multiply(a, b) {
  return a * b;
}

function calculate(operation, a, b) {
  return operation(a, b);
}

console.log(calculate(add, 1, 2)); // 输出 3
console.log(calculate(multiply, 3, 4)); // 输出 12
```

在这个例子中，我们定义了三个函数：`add`、`multiply` 和 `calculate`。`calculate` 函数接受一个函数作为参数 `operation`，然后在函数内部调用这个函数，并传递 `a` 和 `b` 作为参数。我们可以通过调用 `calculate` 函数并传递不同的函数来实现不同的计算。

需要注意的是，在 JavaScript 中，函数本身也是一个对象，它可以拥有属性和方法。我们可以给函数添加属性，也可以给函数添加方法。例如：

```
function add(a, b) {
  return a + b;
}

add.name = 'addition';
add.description = 'This function adds two numbers.';

console.log(add.name); // 输出 'addition'
console.log(add.description); // 输出 'This function adds two numbers.'
```

在这个例子中，我们给 `add` 函数添加了两个属性：`name` 和 `description`。然后我们可以通过函数名来访问函数的属性，例如 `add.name` 和 `add.description`。需要注意的是，给函数添加属性或方法并不会影响函数的执行逻辑，它们只是函数对象的属性和方法，与函数的行为无关。

另外，JavaScript 中的函数可以根据定义方式分为函数声明和函数表达式两种类型。函数声明是指使用 `function` 关键字来定义函数的方式，它们会被解析器提前到作用域的顶部，因此可以在函数声明之前调用。例如：

```
function add(a, b) {
  return a + b;
}

console.log(add(1, 2)); // 输出 3
```

函数表达式是指将函数赋值给变量或属性的方式定义函数，它们不会被解析器提前到作用域的顶部，因此只能在定义后调用。例如：

```
let add = function(a, b) {
  return a + b;
};

console.log(add(1, 2)); // 输出 3
```

需要注意的是，在实际编程中，我们应该根据具体情况选择使用函数声明或函数表达式来定义函数，以便让代码更加清晰、易于阅读和维护。同时，我们也可以使用箭头函数来定义函数，它们是一种更加简洁、易于编写的函数定义方式，可以使代码更加简洁、易于理解。

### 35.2 为什么没有单独把函数数据类型提出来

JavaScript 中的数据类型包括原始类型和引用类型。原始类型包括数字（`number`）、字符串（`string`）、布尔值（`boolean`）、`null`、`undefined` 和 `Symbol`。引用类型包括对象（`object`）、数组（`array`）、函数（`function`）和日期（`date`）等。

虽然 JavaScript 中的函数是一种数据类型，但是它与其他数据类型有些不同。函数可以执行代码并返回值，因此它们不仅仅是数据类型，还可以用于实现程序的功能。因此，在 JavaScript 中，函数是一等公民，它们可以像其他类型的值一样被赋值、传递、返回和存储。

**由于函数是一等公民，因此在介绍 JavaScript 的数据类型时通常不会将函数列为独立的数据类型。**通常将函数视为一种可以执行代码并返回值的数据类型，它们可以与其他数据类型一起使用，为程序实现各种功能。

需要注意的是，虽然函数不是原始类型，但是在 JavaScript 中，函数的值也可以作为变量、对象属性或数组元素存储和传递。因此，我们可以将函数视为一种可以存储和传递的数据类型，它们与其他数据类型一起构成了 JavaScript 中的数据类型系统。

## 36.Object.prototype.toString.call()是是什么，怎么用

`Object.prototype.toString.call()` 是一个用于获取变量的类型信息的方法。它可以返回一个表示变量类型的字符串，例如 `[object Object]` 表示一个对象类型，`[object Array]` 表示一个数组类型，`[object String]` 表示一个字符串类型，等等。

它的常见用途是用于判断一个变量的类型，尤其是在处理不同类型的数据时。例如，我们可以使用 `Object.prototype.toString.call()` 来判断一个变量是否为数组类型：

```
let arr = [1, 2, 3];
console.log(Object.prototype.toString.call(arr)); // 输出 '[object Array]'
```

在这个例子中，我们使用 `Object.prototype.toString.call()` 方法来获取 `arr` 变量的类型信息，它返回了一个字符串 `'[object Array]'`，表示 `arr` 是一个数组类型。

需要注意的是，直接使用 `typeof` 运算符来判断一个变量的类型并不总是可靠的，因为它只能判断出原始类型和函数类型，无法判断其他类型（例如对象类型和数组类型）。因此，在实际编程中，我们通常会结合 `Object.prototype.toString.call()` 方法来判断一个变量的类型，以便使代码更加健壮、可靠。

下面是一个使用 `Object.prototype.toString.call()` 方法来判断变量类型的示例：

```
function getType(variable) {
  return Object.prototype.toString.call(variable);
}

console.log(getType(123)); // 输出 '[object Number]'
console.log(getType('abc')); // 输出 '[object String]'
console.log(getType(true)); // 输出 '[object Boolean]'
console.log(getType(null)); // 输出 '[object Null]'
console.log(getType(undefined)); // 输出 '[object Undefined]'
console.log(getType({})); // 输出 '[object Object]'
console.log(getType([])); // 输出 '[object Array]'
console.log(getType(function() {})); // 输出 '[object Function]'
```

在这个示例中，我们定义了一个名为 `getType` 的函数，它接受一个参数 `variable`，并返回 `Object.prototype.toString.call(variable)` 的结果，即变量的类型信息。通过调用 `getType` 函数，我们可以获取不同类型变量的类型信息，并进行相应的处理。例如，我们可以编写一个函数来打印不同类型的变量：

```
function printType(variable) {
  let type = getType(variable);

  switch (type) {
    case '[object Number]':
      console.log('This is a number.');
      break;
    case '[object String]':
      console.log('This is a string.');
      break;
    case '[object Boolean]':
      console.log('This is a boolean.');
      break;
    case '[object Null]':
      console.log('This is a null.');
      break;
    case '[object Undefined]':
      console.log('This is an undefined.');
      break;
    case '[object Object]':
      console.log('This is an object.');
      break;
    case '[object Array]':
      console.log('This is an array.');
      break;
    case '[object Function]':
      console.log('This is a function.');
      break;
    default:
      console.log('This is an unknown type.');
  }
}

printType(123); // 输出 'This is a number.'
printType('abc'); // 输出 'This is a string.'
printType(true); // 输出 'This is a boolean.'
printType(null); // 输出 'This is a null.'
printType(undefined); // 输出 'This is an undefined.'
printType({}); // 输出 'This is an object.'
printType([]); // 输出 'This is an array.'
printType(function() {}); // 输出 'This is a function.'
printType(new Date()); // 输出 'This is an unknown type.'
```

在这个示例中，我们定义了一个名为 `printType` 的函数，它接受一个参数 `variable`，并根据变量的类型信息打印相应的信息。通过调用 `getType` 函数获取变量的类型信息，然后使用 `switch` 语句根据类型信息进行不同的处理。

需要注意的是，在使用 `Object.prototype.toString.call()` 方法时，我们需要使用 `call()` 方法来明确指定调用对象，即 `Object.prototype`。这是因为 `toString()` 方法可以被所有 JavaScript 对象继承，但是不同对象的 `toString()` 方法可能会返回不同的值，因此我们需要使用 `call()` 方法来确保获取的是 `Object.prototype` 对象的 `toString()` 方法返回的值。

下面是一个错误的示例，它没有使用 `call()` 方法，导致获取的类型信息不正确：

```
let arr = [1, 2, 3];
console.log(Object.prototype.toString(arr)); // 输出 '[object Object]'
```

在这个示例中，我们没有使用 `call()` 方法，而是直接调用 `Object.prototype.toString(arr)` 方法来获取 `arr` 的类型信息。由于 `toString()` 方法可以被所有对象继承，因此这里调用的是 `arr` 对象的 `toString()` 方法，它返回了 `'[object Object]'`，而不是 `'[object Array]'`。

因此，在使用 `Object.prototype.toString.call()` 方法时，我们需要明确指定调用对象，并传递要获取类型信息的变量作为参数：

```
let arr = [1, 2, 3];
console.log(Object.prototype.toString.call(arr)); // 输出 '[object Array]'
```

在这个示例中，我们使用 `call()` 方法来明确指定调用对象为 `Object.prototype`，并传递 `arr` 变量作为参数，确保获取到的是 `arr` 变量的类型信息。

## 37.浏览器控制台

const obj = {name:'zs',age:{year:18}} undefined 为什么浏览器上控制台会返回一个undefined ？

 在控制台中输入代码时，控制台会返回最后一个表达式的结果。在你的代码中，执行了一条赋值语句 `const obj = {name:'zs',age:{year:18}}`，这条语句并不会返回任何值，所以控制台返回了 `undefined`。

如果你想在控制台中查看这个对象，可以在代码后面添加 `console.log(obj)` 或者直接输入 `obj`，这样控制台就会输出这个对象了。例如：

```
const obj = {name:'zs',age:{year:18}};
console.log(obj); // 输出 {name: "zs", age: {year: 18}}
```

或者直接在控制台中输入 `obj`，按回车键，控制台也会输出这个对象。

因此，控制台返回 `undefined` 并不代表代码出现了错误，只是最后一个表达式并没有返回任何值。

## 38.boostrap间距的设置

Bootstrap提供了一些CSS类来改变元素的间距、行高、文字大小和边距等样式，这些类可以通过在HTML标签中添加class属性来使用。下面是一些常用的类和其作用：

1. 间距（Spacing）：用于控制元素之间的间距。

   - `.m-*`：设置元素的外边距（Margin），*可以为以下值：0-5，auto。
   - `.p-*`：设置元素的内边距（Padding），*可以为以下值：0-5。
   - `.mx-*`：设置元素的左右外边距（Margin）。
   - `.my-*`：设置元素的上下外边距（Margin）。
   - `.px-*`：设置元素的左右内边距（Padding）。
   - `.py-*`：设置元素的上下内边距（Padding）。

2. 行高（Line Height）：用于控制文本行与行之间的距离。

   - `.lh-*`：设置元素的行高（Line Height），*可以为以下值：1-5。

3. 文字大小（Text Size）：用于控制文本的大小。

   - `.text-*`：设置元素的文本大小，*可以为以下值：sm（小号）、lg（大号）、*（默认大小）。

4. 边距（Margin）：用于控制元素与其他元素之间的距离。

   - `.mt-*`：设置元素的上外边距（Margin Top），*可以为以下值：0-5。

   - `.mb-*`：设置元素的下外边距（Margin Bottom），*可以为以下值：0-5。

   - `.ml-*`：设置元素的左外边距（Margin Left），*可以为以下值：0-5。

   - `.mr-*`：设置元素的右外边距（Margin Right），*可以为以下值：0-5。

   - `.m-*`：设置元素的外边距（Margin），*可以为以下值：0-5，auto。 - `.mt-*`、`.mb-*`、`.ml-*`、`.mr-*`：也可以使用 `.m-*` 替代，例如 `.m-3` 相当于 `.mt-3 mb-3 ml-3 mr-3`。

     下面是一个示例代码，展示如何使用这些类来改变元素的样式：

     ```
     <div class="container">
       <div class="row">
         <div class="col-md-6">
           <h1 class="text-primary text-center mt-5">标题</h1>
           <p class="lead text-muted mx-3 my-4">这是一段引导性文字。</p>
           <ul class="list-group list-group-flush px-4">
             <li class="list-group-item">列表项1</li>
             <li class="list-group-item">列表项2</li>
             <li class="list-group-item">列表项3</li>
           </ul>
         </div>
       </div>
     </div>
     ```

     在这个代码中，我们使用了 `.mt-5`、`.mx-3`、`.my-4`、`.px-4`、`.list-group-flush` 等类来改变元素的样式。`.mt-5` 用于设置标题的上外边距为5个间距单元，`.mx-3` 和 `.my-4` 用于设置引导性文字的左右外边距和上下外边距，`.px-4` 用于设置列表的左右内边距，`.list-group-flush` 用于去除列表的边框和圆角。这些类的使用可以让我们更加方便地控制元素的样式，从而使网页设计更加美观。

## 39.函数的传递

JavaScript 函数是一等公民，可以作为变量、参数或返回值在其他函数中传递，因此函数的传递成为了 JavaScript 中的常见操作。

在 JavaScript 中，函数传递主要有以下几种方式：

1. 作为函数参数传递
2. 作为函数返回值传递
3. 作为对象属性传递

接下来，让我们分别来详解这些方式。

### 作为函数参数传递

在 JavaScript 中，可以将一个函数作为另一个函数的参数，从而实现进一步的功能。这种方式可以让代码更加抽象、模块化和可复用。

比如下面的代码：

```
function add(a, b) {
  return a + b;
}

function square(c) {
  return c * c;
}

function compose(fn1, fn2) {
  return function(x) {
    return fn2(fn1(x));
  }
}

var addAndSquare = compose(add, square);

console.log(addAndSquare(2, 3)); // 25
```

在上面的代码中，我们定义了三个函数，其中 `add` 和 `square` 分别是两个单独的函数，而 `compose` 函数用于将两个函数连接起来，并返回一个新的函数 `addAndSquare`。在调用 `addAndSquare` 函数时，它会先执行 `add` 函数，然后将结果再传递给 `square` 函数。最终得到的结果是 25。

可以看到，将函数作为参数传递，可以方便地实现代码模块化和抽象，提高代码的可读性和可维护性。

### 作为函数返回值传递

除了作为参数传递外，在 JavaScript 中，函数还可以作为返回值进行传递。这种方式通常可以用于实现柯里化（currying）和函数式编程的一些高级特性。

比如下面的代码：

```
function add(a) {
  return function(b) {
    return a + b;
  }
}

var add5 = add(5);

console.log(add5(3)); // 8
console.log(add5(6)); // 11
```

在上面的代码中，我们定义了一个 `add` 函数，它的作用是将一个数加上另一个数。注意到 `add` 函数返回了一个匿名函数，这个匿名函数在调用时可以继续接收参数，并返回结果。

通过调用 `add(5)` 这个函数，我们得到了一个新的函数 `add5`，它的作用是将一个数加上 5。这样，无论我们传入什么参数，`add5` 都会将其加上 5，并返回结果。

可以看到，这种函数返回函数的方式，使我们能够更加灵活地组合和复用函数，提高了代码的可扩展性和可复用性。

### 作为对象属性传递

另外，函数也可以作为对象属性进行传递，这种方式在事件绑定和回调函数中比较常见，可以方便地将某个对象的方法传递到其他函数中去。

比如下面的代码：

```
var obj = {
  name: 'Jack',
  sayHello: function() {
    console.log(`Hello, my name is ${this.name}`);
  }
};

setTimeout(obj.sayHello.bind(obj), 1000); // 1秒后输出 "Hello, my name is Jack"
```

在上面的代码中，我们定义了一个对象 `obj`，它包含了一个姓名属性和一个 `sayHello` 方法。在调用 `setTimeout` 函数时，我们将 `obj.sayHello` 方法作为参数传入，并在需要时通过 `bind` 方法绑定执行上下文（也就是 `this` 关键字）。

在 1 秒后，`sayHello` 方法将被调用，并输出 "Hello, my name is Jack"。

可以看到，将函数作为对象属性传递，可以方便地在不同的上下文中传递并执行函数，提高代码的复用性和灵活性。

总结

以上是 JavaScript 中函数传递的几种方式，它们为前端开发提供了更多的编程思路和技能，可以帮助我们编写更加优雅和高效的代码。

