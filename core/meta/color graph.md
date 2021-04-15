


![[Pasted image 20210406102412.png]]

Well, its' a bit of a manual hack... and it only works to colour entire folder and its content if you happen to organize your graph colour by folder. You can take the RGB code of the node and copy it manually into a CSS snippet and use CSS Attribute Selectors ([https://www.w3schools.com/css/css\_attribute\_selectors.asp](https://www.w3schools.com/css/css_attribute_selectors.asp "https://www.w3schools.com/css/css_attribute_selectors.asp")), because each `.nav-folder-title` and `.nav-file-title` also has an attribute named `data-path` with the full path and filename of the file. Sample CSS:

```css
/\* Copy colours of Graph View to make folders match \*/

\[data-path^="Aviation"\] {
	color: #5CADD6; 
} 

\[data-path^="D&D"\] { 
	color: #AD5CD6; 
}
```