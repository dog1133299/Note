# REACT基本語法

* 元件式寫法

## 基本宣告

* 使用Class進行宣告
* 可驗證格式
* 可設定預設值
* Class 名稱開頭要大寫

```
//  注意元件開頭第一個字母都要大寫
class MyComponent extends React.Component {
	// render 是 Class based 元件唯一必須的方法（method）
	render() {
		return (
			<div>Hello, World!</div>
		);
	}
}

// PropTypes 驗證，若傳入的 props type 不符合將會顯示錯誤
MyComponent.propTypes = {
  todo: React.PropTypes.object,
  name: React.PropTypes.string,
}

// Prop 預設值，若對應 props 沒傳入值將會使用 default 值
MyComponent.defaultProps = {
 todo: {}, 
 name: '', 
}
```	

## 使用inline css寫法

在 React Component 中 CSS 使用 Inline Style 寫法，全都封裝在 JavaScript 當中：

```
const divStyle = {
  color: 'red',
  backgroundImage: 'url(' + imgUrl + ')',
};

ReactDOM.render(<div style={divStyle}>Hello World!</div>, document.getElementById('app'));
```


## 變數使用方法

使用花括弧{}表示變數

```
var text = 'Hello React';
<h1>{text}</h1>
<h1>{'text'}</h1>
```

## 回傳的是節點

另外要特別要注意的是由於 JSX 最終會轉成 JavaScript 且每一個 JSX 節點都對應到一個 JavaScript 函數，所以在 Component 的 render 方法中只能回傳一個根節點（Root Nodes）。

**例如：若有多個 <div> 要 render 請在外面包一個 Component 或 <div>、<span> 元素。**

## 屬性

在 HTML 中，我們可以透過標籤上的屬性來改變標籤外觀樣式，在 JSX 中也可以，但要注意 class 和 for 由於為 JavaScript 保留關鍵字用法，**因此在 JSX 中使用 className 和 htmlFor 替代。**

```
class HelloMessage extends React.Component {
  render() {
    return (
      <div className="message">
        <p>Hello React!</p>
      </div>
    );
  }
}
```

### Boolean 屬性
在 JSX 中預設只有屬性名稱但沒設值為 true，例如以下第一個 input 標籤 disabled 雖然沒設值，但結果和下面的 input 為相同：

```
<input type="button" disabled />;
<input type="button" disabled={true} />;
```
反之，若是沒有屬性，則預設預設為 false：
```
<input type="button" />;
<input type="button" disabled={false} />;
```

## ... 迭代用法

在 ES6 中使用 `...` 是迭代物件的意思，可以把所有物件對應的值迭代出來設定屬性，但要注意後面設定的屬性會蓋掉前面相同屬性：

```
var props = {
  style: "width:20px",
  className: "main",
  value: "yo",  
}

<HelloMessage  {...props} value="yo" />
```

```
// 等於以下
React.createElement("h1", React._spread({}, props, {value: "yo"}), "Hello React!");
```


## 事件處理
事件處理為前端開發的重頭戲，***在 JSX 中透過 inline 事件的綁定來監聽並處理事件（注意也是駝峰式寫法）***，更多事件處理方法請參考官網。

```
<HelloMessage onClick={this.onBtn} />
```

