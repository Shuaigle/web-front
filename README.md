# Next.js
## What is it
Next.js 是 React 的 framework\
![next.js](https://nextjs.org/static/images/learn/foundations/next-app.png)

## How browser interprets your code
當 user 造訪網頁時，server 返回一個 html 檔給 browser\
![html and DOM](https://nextjs.org/static/images/learn/foundations/html-to-dom.png)\
Browser 閱讀 html 且創建 Document Object Model(DOM)\
DOM 是一個 html 元素的物件表現模式，是一種樹狀結構，具有親代與子代的關係\
我們撰寫 JavaScript 去聆聽 user event 和 manipulate DOM (select, add, update, delete)\
DOM 有哪些方法呢？
- `document.getElementById('app')`
- `document.createElement('h1')`
- `document.createTextNode('Hi, how you doing?')`
html represents 初始頁面內容，DOM represents 更新後的頁面內容

## imperitive vs declaritive programming
imperitive 是給予指令步驟，令其遵照指示執行，因此就像耳提面命一般，執行速度較慢\
declaritive 是給予目標，然後對方就自動自發的達成目地，執行速度飛快\
而 **React** 就是declaritive UI(user interface) library\

## DOM vs html
html 呈現原始頁面內容\
而dom則呈現**更新後**的頁面內容\
然而以js去更新dom是繁瑣的，因此

## REACT
- react 是 React 的核心 lib
- react-dom 提供 dom 相關的操作，讓 react 也能操作 dom
- `ReactDom.render()`

## JSX
- 是一種類html語意
- JS的延伸語意
- 算是html + js
- 瀏覽器看不懂，需有js compiler把jsx -> js
- Babel是一種compiler
- 在index.html內加入，`<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>`
- 要告訴babel資料型態 type="text/jsx"
    ```
    <script type="text/jsx">
      const app = document.getElementById('app');
      ReactDOM.render(<h1>Develop. Preview. Ship. 🚀</h1>, app);
    </script>
    ```

## Components
- components 就是 functions
- components 就是 **return UI elements** 的 functions
```
function Header() {
    return (<h1> Oops </h1>)
}
```
- 寫好之後render出來
```
ReactDOM.render(<Header />, app)
```
- react components 要 capitalize 以與 html and js 區分開來
- render裏面要用html tag

### Nesting components
```
function HomePage(){
    return (
        <div>
            <Header />
        </div>
    )
}
```
- 把 Header 丟在裡面

### Components tree
![tree](https://nextjs.org/static/images/learn/foundations/component-tree.png)

## Props
- 重複使用components時，不知道components的內容，或想呈現不一樣的內容時，props出現惹
- 設計props去改變components的行為
- props可藉由parent components傳遞給child components(components tree)
- 在 HomePage裏面新增props title
```
function HomePage() {
  return (
    <div>
      <Header title="React" />
    </div>
  );
}
```
- Header為child components接收props
```
function Header(props) {
    console.log(props) // {title: "React"}
}
```
- props 屬於 objects，因此可destructure
- {} 提醒jsx這是js variable
```
function Header({ title }) {
    console.log(title); // "React"
    return <h1>{title}</h1>;
}
```
- 也可以這樣寫
```
function Header(props) {
  return <h1>{props.title}</h1>;
}
```
- 預設title
```
function createTitle(title) {
  if (title) {
    return title;
  } else {
    return 'Default title';
  }
}

function Header({ title }) {
  return <h1>{createTitle(title)}</h1>;
}
```
- 在{}裡面都是js樂園
- 稍微簡化寫法，三元
```
function Header({ title }) {
  return <h1>{title ? title : 'Default Title'}</h1>;
}
```

### 呈現array
- 用array.map() 
```
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

  return (
    <div>
      <Header title="Develop. Preview. Ship. 🚀" />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>
    </div>
  );
}
```

## 互動性的state
- 用button 按讚訂閱分享
```
<button>Like</button>
```
- 聆聽事件event
- 讓這button幹點事情，加個onClick
```
<button onClick={}>Like</button>
```
- in react, event得命名方式是駝峰的(camelCased)
- 除了onClick - button外，還有onChange - input，onSubmit - forms

### 處理event
- 自己寫的handle function 來處理event事件帶來的變化
- **function 寫在return 之前**
```
function HomePage() {
  //    ...
  function handleClick() {
    console.log('increment like count');
  }

  return (
    <div>
      {/* ... */}
      <button onClick={handleClick}>Like</button>
    </div>
  );
}
```
- 這樣當onClick觸發時，handle則被啟動

### State and Hooks
- react裡有一集合functions叫做Hooks
- Hooks讓我們能增加額外的邏輯
- like state on components
- state是啥？
- state代表任一UI資訊隨時間(被觸發)而改變狀態
![state](https://nextjs.org/static/images/learn/foundations/state.png)
- 可用`useState`保存或增加按讚數
- `useState`回傳array
- 可用array destructuring來獲取數值
```
function HomePage() {
  const [] = React.useState();

  // ...
}
```
- array內第一個值為狀態state `value`，最好將之命名為有描述性意義之名
- 第二數值為function`update`，用以更新`value`，通常以`setValue`命名
- useState(0)設初始值為0
```
function HomePage() {
  const [likes, setLikes] = React.useState(0);

  // ...
}
```
- 可以把`setLikes`寫入handleClick裏面去處理更新狀態
```
function HomePage() {
  // ...
  const [likes, setLikes] = useState()

  function handleClick() {
    setLikes(likes + 1)
  }}

  return (
    <div>
      {/* ... */}
      <button onClick={handleClick}>Likes ({likes})</button>
    </div>
  )
}
```
- state跟props不同之處在於
    - props是第一個至高無上的component的參數pass進來的
    - state在component創建之時，同時被初始化創建與儲存在component內部
    - state也可像props一樣被傳遞給child components
    - 然而state update的邏輯只與創建者component有關
    - props是read-only的
    - state可改變

