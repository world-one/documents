## stylelint
- css, scss lint

```
yarn add -D stylelint post-scss 
yarn add -D stylelint-config-standard stylelint-config-standard-scss
```

```
//.stylelintrc.json
{
  "extends": ["stylelint-config-standard", "stylelint-config-standard-scss"],
  "rules": {
    "selector-class-pattern": null
  }
}
```

- global로 설치한 경우가 아니라면 로컬에서 실행
```
"lint:style": "./node_modules/stylelint/bin/stylelint.js \"src/**/*.scss\" \"src/**/*.css\" --fix"
 ```