### html DOM parser
```
const parser = new DOMParser();
const htmlDoc = parser.parseFromString(htmlStr, 'text/html');
const contents = htmlDoc.querySelectorAll('p');
const img = htmlDoc.querySelector('img');
img.getAttribute('src')
```