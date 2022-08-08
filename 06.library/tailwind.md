### tailwind
- https://tailwindcss.com/
- 예전에 사용해본 bootstrap을 생각하고 고려하지 않았는데, 오늘 살펴보니 좋은 기능이 있어서 놀랐다.
- arbitrary values, 임의값을 넣어서 바로 적용시킬 수 있다. 생각보다 엄청나게 편하다.
```
<div class="bg-[#bada55] text-[22px] before:content-['Festivus']">
  <!-- ... -->
</div>
```

### next 설정
```
yarn -D tailwindcss postcss autoprefixer
```
```
npx tailwindcss init -p
```
tailwind.config.js와 postcss.config.js가 자동 생성된다. 거기서 내 프로젝트에 맞춰서 수정한다.

```
/** @type {import('tailwindcss').Config} */ 
module.exports = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```
```
//global.css

@tailwind base;
@tailwind components;
@tailwind utilities;
```