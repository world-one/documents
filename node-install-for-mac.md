### node 설치
nvm을 이용해서 node의 버전관리를 한번에 하면 편하다.
우선 nvm을 homebrew로 설치한다.

```
brew install nvm
```


~/.zshrc에 아래 내용을 추가해준다.
```
export NVM_DIR="$HOME/.nvm"
[ -s "/usr/local/opt/nvm/nvm.sh" ] && . "/usr/local/opt/nvm/nvm.sh"
[ -s "/usr/local/opt/nvm/etc/bash_completion" ] && . "/usr/local/opt/nvm/etc/bash_completion"
```

```
nvm install node
or
nvm install [ version ]
```

```
nvm ls
nvm use [ version ]
nvm alias default 13.10.1
```