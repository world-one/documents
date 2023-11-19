### [Next js Version 14](https://nextjs.org/blog/next-14)
2023.10.26

#### Turbopack
- 13버전부터 시작된 로컬 개발 성능 개선
- 현재 90%의 테스트 통과했으며 곧 stable로 이동
- 효과
  - local server startup 53.3% 빨라짐
  - fast refresh, 94.7%의 빠른 코드 업데이트
#### Server Action(Stable)
- API 경로를 생성할 필요 없이 React 코드에서 직접 호출하여 서버에서 실행되는 함수 정의
```
export default function Page() {
  async function create(formData: FormData) {
    'use server';
    const id = await createItem(formData);
  }
 
  return (
    <form action={create}>
      <input type="text" name="name" />
      <button type="submit">Submit</button>
    </form>
  );
}
```


#### Partial Prerendering(Preview)
- 개발중, 곧 출시
#### Metadata Improvements
- 블록, 논블록 메타데이터를 분리
- viewport, colorScheme, themeColor는 제거되며 [viewport, generateViewport](https://nextjs.org/docs/app/api-reference/functions/generate-viewport)로 대체된다
