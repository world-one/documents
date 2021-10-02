#### entry file hash
캐시 문제로 hash를 추가
- @rollup/plugin-html
  - build 디렉토리 안에 생성되서 방법 찾다가 rollup-plugin-generate-html-template로 변경
- rollup-plugin-generate-html-template
  - dist/index.html에 template 만들어두고 public에 복사하는 방식
  ```
  html({
    template: 'dist/index.html',
    target: 'public/index.html'
  }),
  ```
- rollup-plugin-css-only
  - hash가 추가 안되는 듯 싶어서 postCss로 변경
- rollup-plugin-postcss
  - 아래와 같이 하니 추가됨
  ```
  postcss({
    extract: true,
  }),
  ```
- js
```
output: {
  sourcemap: true,
  format: 'iife',
  name: 'app',
  // file: 'public/build/bundle[hash].js',
  dir: 'public/build',
  entryFileNames: 'bundle[hash].js',
},
```
- 결과
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset='utf-8'>
	<meta name='viewport' content='width=device-width,initial-scale=1'>
	<title>Svelte app</title>
	<link rel='icon' type='image/png' href='./favicon.png'>
	<link rel='stylesheet' href='./global.css'>
<link rel="stylesheet" type="text/css" href="bundle3b7fa4ea.css">
</head>
  <body>
  <script  src="build/bundle3b7fa4ea.js"></script>
</body>
</html>

```

- postcss의 public path 설정이 잘 안되서.. 일단 직접 수정해주었다.
  - style href path 설정이 안되는 듯 하여 그냥 head에 style로 들어가는 방식으로 변경
    ```
    {
      exec: true
    }
    ```