# Funny-CSS
The tool about CSS serialize and CSS selector identifier escape (The robust polyfill of [CSS.escape](https://drafts.csswg.org/cssom/#the-css.escape%28%29-method)).  
    
## API  
  
### `css.serialize(index, [format=false])`   
  
Serialize the Style Sheet by index in the document.
   
Example:  
```css
/* The first style sheet in the document. */
div, p {
    margin: 20px;	
}
p {
    padding: 20px;
}
```  
Serialize the first Style Sheet:  
```js
css.serialize(0)
// => 
/*
    {
        0: { names: ['margin'], selectorText: 'div', margin: '20px', cssText: 'div { margin: 20px; }' },
        1: { names: ['margin', 'padding'], selectorText: 'p', margin: '20px', padding: '20px', cssText: 'p { margin: 20px; padding: 20px; }'  },
        length: 2
    }
 */
```
  
### `css.escape(selectorText)` 
  
The polyfill of [CSS.escape](https://drafts.csswg.org/cssom/#the-css.escape%28%29-method).  
  
Example:  
```js
css.escape('#()[]{}')
// => '\#\(\)\[\]\{\}'
```                  
Now look at this HTML element:
```html
<div id="#()[]{}"></div>
```     
Get this HTML element by selector:
```js
document.querySelector('#' + '#()[]{}')
// => Error: '##()[]{}' is not a valid selector
```