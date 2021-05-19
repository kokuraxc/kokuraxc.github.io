> How to replace all the matched substring?

I always took it for granted that the **JavaScript** `replace()` function for a `string` would replace all the matched substrings, like how it works in **Python**.

But no, it doesn't work the same way in **JavaScript**.

As I found out in this [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace), `replace(substr, newSubstr)` will only replace the first occurrence of `substr` with `newSubstr`. To achieve global replacement, you'll need **regexp**'s help.


```js
// This will only remove the first empty space
str.replace(" ", "")

// This will remove all the empty spaces
str.replace(/ /g, "")
```