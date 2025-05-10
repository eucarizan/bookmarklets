# bookmarklets

- [bookmarklets](#bookmarklets)
  - [URL cleaner](#url-cleaner)

## URL Cleaner
Removes tracking parameters and fragments from URLs

```js
javascript:(function(){const e=window.location.href.match(/(https:\/\/www\.seek\.com\.au\/job\/\d+)(?=[?#]|$)/)?.[0];if(!e||e===window.location.href)return alert("URL is already clean!\n"+window.location.href);const n=document.createElement("div");n.style="position: fixed; top: 20px; right: 20px; z-index: 9999; padding: 15px; background: white; border-radius: 8px; box-shadow: 0 2px 10px rgba(0,0,0,0.2); font-family: Arial;",n.innerHTML=%60<p>Replace current URL?</p><p><small>${window.location.href}</small></p><p>→ <strong>${e}</strong></p><div style="display: flex; gap: 10px; margin-top: 10px;"><button id="confirm" style="padding: 5px 10px; background: #4CAF50; color: white; border: none; border-radius: 4px;">✅ Yes</button><button id="cancel" style="padding: 5px 10px; background: #f44336; color: white; border: none; border-radius: 4px;">❌ No</button></div>%60,document.body.appendChild(n),n.querySelector("#confirm").addEventListener("click",()=>{window.location.href=e}),n.querySelector("#cancel").addEventListener("click",()=>{document.body.removeChild(n)})})();
```

<details>
<summary>beautified</summary>

```js
javascript:(function(){
  const currentUrl = window.location.href;
  const cleanUrl = currentUrl.match(/(https:\/\/www\.seek\.com\.au\/job\/\d+)(?=[?#]|$)/)?.[0];
  
  if (!cleanUrl || cleanUrl === currentUrl) {
    alert("URL is already clean!\n" + currentUrl);
    return;
  }

  const dialog = document.createElement('div');
  dialog.style = `
    position: fixed; top: 20px; right: 20px; z-index: 9999;
    padding: 15px; background: white; border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0,0,0,0.2); font-family: Arial;
  `;
  
  dialog.innerHTML = `
    <p>Replace current URL?</p>
    <p><small>${currentUrl}</small></p>
    <p>→ <strong>${cleanUrl}</strong></p>
    <div style="display: flex; gap: 10px; margin-top: 10px;">
      <button id="confirm" style="padding: 5px 10px; background: #4CAF50; color: white; border: none; border-radius: 4px;">✅ Yes</button>
      <button id="cancel" style="padding: 5px 10px; background: #f44336; color: white; border: none; border-radius: 4px;">❌ No</button>
    </div>
  `;

  document.body.appendChild(dialog);
  
  dialog.querySelector('#confirm').addEventListener('click', () => {
    window.location.href = cleanUrl;
  });
  
  dialog.querySelector('#cancel').addEventListener('click', () => {
    document.body.removeChild(dialog);
  });
})();
```
</details>
<hr/>

<!--
## 

```javascript
```

<hr/>
-->
<!--
<details>
<summary>beautified</summary>
```js
```
</details>
<hr/>
-->

