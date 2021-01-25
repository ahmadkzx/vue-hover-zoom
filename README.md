# Vue Hover Zoom

  
Easy to use package for zoom image when hover on it with the mouse cursor

### Getting started  

1. Install the package:
```shell
npm install vue-hover-zoom
```

2. Import component:
```javascript
import  VueHoverZoom  from  'vue-hover-zoom'
```
3. Add component to components:
```javascript
components: {  
  VueHoverZoom  
}
```

4. Use component in template
```html
<vue-hover-zoom imageUrl="https://test.com/img.png"></vue-hover-zoom>
```

  

### ✅ Config

You can config VueHoverZoom Component with props.

⚙ imageUrl:  
❗ Required  

⚙ imageAlt:  
🔹 default: null   

⚙ zoomPercent:  
🔹 default: 200   

⚙ zoomCursor:  
🔹 default: true   

⚙ animation:  
🔹 default: fade  
🔸 options: fade, shrink, growup, slidedown, slideup  
You Can use multiple animations like: fade shrink  

⚙ showWhenImageLoaded:  
🔹 default: false  
If you enable this, image shows when fully loaded 


### 📌 Note  
You can select the element in css and set image width.  
default class: hover-zoom-image