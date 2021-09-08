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