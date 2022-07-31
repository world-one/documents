#### eslint on save
설정에서 eslint on save가 없을 경우 아래 설정에서 코드를 직접 추가해준다.
command pallete -> preference open setting json 에 아래 코드 입력
```
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true    ## ES Lint 저장 시 자동 fix 설정
  },
  "editor.formatOnSave": true,      ## document formatting 자동 fix 설정
```

