# [chapter6] 작동 위임

## 6.1 위임 지향 디자인으로 가는 길

- 자바스크립트의 [[Prototype]]은 클래스와 근본부터 다른 디자인 패턴이라는 것을 인지해야한다.

### 6.1.2 위임 이론

- 데이터 멤버와 같은 직속 프로퍼티는 위임하는 쪽(받는 부분)에 두고 위임받는 쪽(주는 부분)에는 두지 않는다.
- 작동 위임 패턴은 오버라이드를 하지 않는다. 서로 다른 수준의 [[Prototype]] 연쇄에서 같은 명칭이 뒤섞이는 일은 될 수 있으면 피해야 한다.
- 암시적 호출부에 따른 this 바인딩 규칙에 따라 바인딩된다. → 위임한 유틸리티 메서드를 얼마든지 이용할 수 있다.

## 6.2 클래스 vs 객체

### 6.2.1 위젯 클래스

```jsx
function Widget(width, hegith) {
  this.width = witdh || 50;
  this.height = height || 50;
  this.$elem = null;
}

Widget.prototype.render = function ($where) {
  if (this.$elem) {
    this.$elem
      .css({
        width: this.width + "px",
        height: this.height + "px",
      })
      .appendTo($where);
  }
};

function Button(width, height, label) {
  Widget.call(this, width, height);
  this.label = label || "Default";
  this.$elem = $("<button>").text(this.label);
}

Button.prototype = Object.create(Widget.prototype);
Button.prototype.render = function ($where) {
  Widget.prototype.render.call(this, $where);
  this.$elem.click(this.onClick.bind(this));
};

Button.prototype.onClick = function (evt) {
  console.log(this.label + "버튼이 클릭됨");
};

$(document).ready(function () {
  var $body = $(document.body);
  var btn1 = new Button(125, 30, "Hello");
  var btn2 = new Button(150, 40, "World");

  btn1.render($body);
  btn2.render($body);
});
```

### 6.2.2 위젯 객체의 위임

```jsx
var Widget = {
	init: function(width, height) {
		this.width = width || 50
		this.height = height || 50
		this.$elem = null
	}
	insert: function($where) {
		if (this.$elem) {
			this.$elem.css({
				width: this.width + "px",
				height: this.height + "px"
			}).appendTo($where)
		}
	}
}

var Button = Object.create(Widget)

Button.setup = function(width, height, label) {
	this.init(width, height)
	this.label = label || "Default"

	this.$elem = $("<button>").text(this.label)
}

Button.build = function($where) {
	this.insert($where)
	this.$elem.click(this.onClick.bind(this))
}

Button.onClick = function(evt) {
	console.log(this.label + "버튼이 클릭됨")
}

$(document).ready(function(){
	var $body = $(document.body)
	var btn1 = Object.create(Button)
	btn1.setup(125, 30, "Hello")

	var btn2 = Object.create(Button)
	btn2.setup(150, 40, "World")

	btn1.build($body)
	btn2.build($body)
})
```
