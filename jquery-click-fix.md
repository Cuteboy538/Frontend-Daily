# 🐞 Fix: jQuery `.click()` Not Firing on Dropdown Items

## 🚩 Problem

You're creating a custom dropdown using jQuery.  
You want to detect when a user clicks on a list item — but nothing happens.

---

## 💡 Common HTML Setup

```html
<div class="dropdown">
  <input type="text" class="dropdown-input" />
  <div class="dropdown-menu">
    <div class="dropdown-option">Apple</div>
    <div class="dropdown-option">Banana</div>
    <div class="dropdown-option">Cherry</div>
  </div>
</div>

❌ Doesn't Work

$(document).on('click', '.dropdown-option', function () {
  alert('You selected: ' + $(this).text());
});

This might not work if the dropdown disappears before the click registers.


✅ Works: Use .mousedown() Instead

$(document).on('mousedown', '.dropdown-option', function () {
  alert('You selected: ' + $(this).text());
});


🔍 Why It Happens
.click() happens after the input loses focus.

Some dropdowns hide on blur, which cancels the click.

.mousedown() fires before blur, so it captures the event in time.
