---
title: Javascript代码片段（持续更新）
date: 2017-04-27 12:26:06
tags:
---


## 继承

```js
/**
 * 继承
 */
function extend(Child, Parent) {　　　　
    var F = function() {};　　　　
    F.prototype = Parent.prototype;　　　　
    Child.prototype = new F();　　　　
    Child.prototype.constructor = Child;　　　　
    Child.uber = Parent.prototype;　　
}

var Perent = function() {};
Perent.prototype = {
    say: function() {
        console.log('Perent say function');
    }
}

var Children = function() {}
extend(Children, Perent);
Children.prototype.eat = function(){
        console.log('eat');
}
Children.prototype.say = function(){
        console.log('children say function');
}
```

## 单例模式
```js
/**
 * 单例模式
 */

var single = (function() {
    //初始化操作
    var a = 100;
    function init() {
        //累计变量
        var cnt = 0;
        //获取随机数
        this.getRandomNum = function() {
            console.log(a);
            return Math.random();
        }
        //累计数
        this.count = function() {
            return cnt++;
        }
    }

    //实例保持者
    var instance;

    return {
        //获取实例
        getInstance: function() {
            return instance || (instance = new init());
        },
        //销毁实例
        destroyInstance: function() {
            if (instance) {
                instance = null;
            }
        }
    }
})();
```

## 代理模式

```js
/**
 * 代理模式
 */

var myImage = (function() {
    var imgNode = document.createElement("img");
    document.body.appendChild(imgNode);

    return {
        setSrc: function(src) {
            imgNode.src = src;
        }
    }
})();

var proxyImage = (function() {
    var img = new Image;
    img.onload = function() {
        // 图片加载完成，正式加载图片
        myImage.setSrc(this.src);
    };
    return {
        setSrc: function(src) {
            // 图片未被载入时，加载一张提示图片
            myImage.setSrc("1.gif");
            img.src = src;
        }
    }
})();
// 调用代理对象加载图片
proxyImage.setSrc("https://wallpapers.wallhaven.cc/wallpapers/full/wallhaven-508690.jpg");
```

## 装饰者模式

```js
/**
 * 装饰者模式
 */

var House = function() {};
House.prototype.room = function() {
    console.log('room');
}

var Decorator = function(room) {
    this.decorator_room = room;
}
Decorator.prototype.room = function() {
    this.decorator_room.room();
    console.log('decorator room');
}


var house = new House;
var decoHouse = new Decorator(house);
decoHouse.room();
```
