# Next.js
## What is it
Next.js 是 React 的 framework\
![next.js](https://nextjs.org/static/images/learn/foundations/next-app.png)\
## How browser interpret your code
當 user 造訪網頁時，server 返回一個 html 檔給 browser\
![html and DOM](https://nextjs.org/static/images/learn/foundations/html-to-dom.png)\
Browser 閱讀 html 且創建 Document Object Model(DOM)\
DOM 是一個 html 元素的物件表現模式，是一種樹狀結構，具有親代與子代的關係\
我們撰寫 JavaScript 去聆聽 user event 和 manipulate DOM (select, add, update, delete)\
DOM 有哪些方法呢？\
- `document.getElementById('app')`
- `document.createElement('h1')`
- `document.createTextNode('Hi, how you doing?')`
html represents 初始頁面內容，DOM represents 更新後的頁面內容\
## imperitive vs declaritive programming
imperitive 是給予指令步驟，令其遵照指示執行，因此就像耳提面命一般，執行速度較慢\
declaritive 是給予目標，然後對方就自動自發的達成目標，執行速度飛快\
而 **React** 就是declaritive UI(user interface) library\
