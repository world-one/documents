### helmet
- 보안을 위한 노드 모듈입니다.
- 웹 취약점으로부터 서버를 보호해줍니다.

- 팀원이 며칠 동안 cdn으로 부터 이미지를 받아오지 못하는 이슈가 있다고 끙끙대는걸 봤다. cors 이슈로 인해 이미지가 제대로 보이지 않았다.
- 내가 그 이슈를 받게 되었고, 다른 프로젝트에서는 문제없이 잘 나온다는 말을 듣고 우선은 좀 무식하게 server 코드를 싹 옮겨서 확인해보았다.
- 여전히 나오지 않아 설정 파일들을 하나씩 옮겨보았다. 그러던 중 package를 확인해보니 helmet의 버전이 다른것을 발견했고, 관련해서 검색해보니 원인을 찾았다.
  - https://stackoverflow.com/questions/70752770/helmet-express-err-blocked-by-response-notsameorigin-200
- helmet이 5 버전으로 올라가면서 `crossOriginEmbedderPolicy`가 default로 설정되어 있어서 해제하니 문제 없이 이미지가 노출되었다.