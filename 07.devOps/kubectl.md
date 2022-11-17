### Kubectl 

#### 설치
https://formulae.brew.sh/formula/kubernetes-cli
```
brew install kubernetes-cli
```

#### 자동완성
https://kubernetes.io/ko/docs/reference/kubectl/cheatsheet/
```
source <(kubectl completion zsh)  # 현재 셸에 zsh의 자동 완성 설정
echo '[[ $commands[kubectl] ]] && source <(kubectl completion zsh)' >> ~/.zshrc # 자동 완성을 zsh 셸에 영구적으로 추가한다.
```

