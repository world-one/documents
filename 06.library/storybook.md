### Storybook
#### 설치 후 git dependabot
- trim, trim-newline, glob-parent 등 high severity 알림
```
//package.json
  "resolutions": {
    "trim": "^0.0.3",
    "nth-check": "^2.0.1",
    "glob-parent": "^6.0.1",
    "trim-newlines": "^3.0.1"
  },
```
- `yarn audit` 로 확인