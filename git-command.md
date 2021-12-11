### git 명령어
#### push한 commit을 되돌리고 싶을 때(reset)
git log를 통해 원하는 commit id를 찾는다.
```
git reset --hard commitId
```
위와 같이 하면 입력한 commit 이후로 삭제된다.
```
git push -f origin main
```
force는 굉장히 위험하지만 개인 저장소라서 사용해보았다.


#### merge가 끝난 branch 삭제
```
alias git-clear='git fetch -p && git branch --merged 
| grep -v "\*" | grep -v master 
| grep -v develop | xargs -n 1 git branch -d'
```

#### commit 날짜 변경
```
git log

// 가장 최신 commit 변경
git commit --ament --no-edit --date "May 2 11:23:12 2021 +0900"
```

### git reset, revert
```
git revert <commit hash>
git reset <commit hash>
```
8월 11일 커밋 안한 곳으로 날짜 변경 후 커밋을 되돌리거나 삭제했는데 기록이 남아있음..


### mac git install
```
$ brew install git
$ brew info git
$ git --version
$ echo "export PATH=/usr/local/bin:$PATH" >> ~/.bash_profile
$ git --version
```

### git rebase를 관련 메시지
`git status`를 하니 rebase를 진행중이라는 메시지가 떠서 잠깐 삽질..   
rebase에 대한 이해가 좀 부족했음,
`git rebase --abort`로 되돌린 후 관련 메시지는 사라짐
