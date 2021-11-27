## firebase에 정적 사이트 올려보기
- https://firebase.google.com/docs/hosting/quickstart?hl=ko
- https://firebase.google.com/pricing
  - 무료
    - 스토리지 10GB
    - Data transfer 360MB/day 

---
### Firebase Console에서 프로젝트 추가
  - https://console.firebase.google.com/


### Firsebase Hosting 설정
- 빌드 -> 호스팅
1. Firsebase CLI 설치
```
yarn global add firebase-tools
or
npm install -g firebase-tools
```
2. `firebase login`을 한 뒤 브라우저에서 구글 로그인을 한다. 성공 메시지 뜬다.
3. `firebase init` 을 입력하면 여러 기능을 선택할 수 있다. 
    - 아래 두가지를 선택했다.
      - Hosting: Configure files for Firebase Hosting and (optionally) set up GitHub 
Action deploys
      - Hosting: Set up GitHub Action deploys
    - Console에서 추가한 프로젝트를 입력
    - 배포는 github를 연동해서 하도록 설정했는데 잘 될지는 모르겠다.
    - github deploy를 위해 새로운 저장소를 추가했다.
4. firebase deploy
  - Console에서 확인해보니 배포가 완료되었고, 연결된 사이트도 제대로 보인다.

  
