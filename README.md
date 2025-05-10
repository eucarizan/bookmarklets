# bookmarklets

- [bookmarklets](#bookmarklets)
  - [URL cleaner](#url-cleaner)
  - [Scroll to top](#scroll-to-top)
  - [Auto-Click Solution Buttons](#auto-click-solution-buttons)
  - [Enable and Auto-Click Send button](#enable-and-autoclick-send-button)

## URL Cleaner
Removes tracking parameters and fragments from URLs. _*hardcoded url_

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

## Scroll to top
Scrolls to top of the page

```js
javascript:(window.scrollTo({top:0,behavior:'smooth'}))()
```
<hr/>

## Auto-Click Solution Buttons
Automatically clicks the "Solutions" tab and "Post solution" button in sequence.

```js
javascript:(async()=>{const e=(e=>new Promise(t=>{const n=setInterval(()=>{const t=document.querySelector(e);t&&(clearInterval(n),t&&t.click()},100)}));try{await e(".active-route.router-link-exact-active.btn.btn-link"),await e("#post-solution-button"),console.log("Bookmarklet executed successfully")}catch(e){console.error("Bookmarklet error:",e),alert("Bookmarklet failed: "+e.message)}})();
```

<details>
<summary>beautified</summary>

```js
javascript:(async () => {
  /**
   * Wait for an element to appear in the DOM
   * @param {string} selector - CSS selector of the element to wait for
   * @returns {Promise<Element>} - Resolves when element is found
   */
  const waitForElement = (selector) => new Promise((resolve) => {
    const interval = setInterval(() => {
      const element = document.querySelector(selector);
      if (element) {
        clearInterval(interval);
        resolve(element);
      }
    }, 100);
  });

  try {
    // Click the active route button
    const activeRouteBtn = await waitForElement('.active-route.router-link-exact-active.btn.btn-link');
    activeRouteBtn.click();
    
    // Click the post solution button
    const postSolutionBtn = await waitForElement('#post-solution-button');
    postSolutionBtn.click();
    
    console.log('Bookmarklet executed successfully');
  } catch (error) {
    console.error('Bookmarklet error:', error);
    alert('Bookmarklet failed: ' + error.message);
  }
})();
```
</details>

<hr/>

## Enable and Auto-Click Send button

```js
javascript:(async()=>{const e=document.getElementById("sendBtn");e&&e.removeAttribute("disabled");const t=t=>new Promise(e=>{const n=setInterval(()=>{const e=document.querySelector(t);e&&(clearInterval(n),e.click())},100)};try{await t("#sendBtn"),console.log("Send button clicked")}catch(e){console.error("Error:",e),alert("Enable & Click failed:\n"+e.message)}})();
```

<details>
<summary>beautified</summary>

```js
javascript:(async () => {
  /**
   * ENABLE & AUTO-CLICK SEND BUTTON BOOKMARKLET
   * Purpose: 
   *   1. Finds a disabled button with ID "sendBtn" and enables it
   *   2. Automatically clicks the button once enabled
   * Useful for: 
   *   - Bypassing temporary UI restrictions
   *   - Automating repetitive form submissions
   */
  
  // First: Enable the button if it exists and is disabled
  const sendButton = document.getElementById("sendBtn");
  if (sendButton) {
    sendButton.removeAttribute("disabled");
    console.log("Send button enabled");
  }

  // Wait for element to appear in DOM (with retry logic)
  const waitForElement = (selector) => new Promise((resolve) => {
    const interval = setInterval(() => {
      const element = document.querySelector(selector);
      if (element) {
        clearInterval(interval);
        resolve(element);
      }
    }, 100); // Check every 100ms
  });

  try {
    // Click the send button once available
    const enabledSendButton = await waitForElement("#sendBtn");
    enabledSendButton.click();
    console.log("Send button clicked successfully");
  } catch (error) {
    console.error("Failed to click send button:", error);
    alert("Enable & Click failed:\n" + error.message);
  }
})();
```
</details>

<hr/>

<!--

## 

```js
```

<details>
<summary>beautified</summary>

```js
```
</details>

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

