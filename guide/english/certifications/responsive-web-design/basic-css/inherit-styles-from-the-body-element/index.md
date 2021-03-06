---
title: Inherit Styles from the Body Element
---
# Inherit Styles from the Body Element

---
## Problem Explanation
We need to create a ```h1``` element with the text ```Hello World```, then we need to give all elements on your page the color of ```green``` in our ```body``` element's style declaration, and finally, we need add  to our ```body``` element  font-family of ```monospace```.

 ## Solutions
 
<details><summary>Solution 1 (Click to Show/Hide)</summary>

**Create a ```h1``` element with the text ```Hello World```:**
 
 add ```h1``` after ```</style>``` element:
 
```css
    <h1>Hello World</h1>
```

**Give all elements on your page the color of ```green``` and font-family of ```monospace``` in our ```body``` element's style declaration:**

add between ```<style>``` and ```</style>```:

```css
    color: green;
    font-family: monospace;
```

**Full solution**

```css
<style>
  body {
    background-color: black;
    color: green;
    font-family: monospace;
  }
</style>

<h1>Hello World</h1>
```

</details>