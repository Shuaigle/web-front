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