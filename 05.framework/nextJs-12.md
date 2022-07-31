### Next js Version 12

https://github.com/vercel/next.js/releases/tag/v12.0.0

https://nextjs.org/blog/next-12

#### Rust compiler로 더 빠른 빌드와 새로 고침이 가능해졌다.
- swc(https://swc.rs/)를 기반으로 한 Rust 컴파일러
- 대규모 코드베이스에 대한 추가 속도 개선
- 성능에 대한 향상된 관찰 가능성
- 기본 웹팩 개선
- Rust를 사용한 컴파일은 Babel보다 17배 빠르다.
  - styled-jsx
- 코드 압축은 Terser 보다 7배 빠르다.

#### React 18을 위하여 준비
#### ES 모듈 지원
- next 12에선 ES 모듈에 대한 지원이 기본값

#### URL Imports
```
//next.config.js
module.exports = {
  experimental: {
    urlImports: ['https://cdn.skypack.dev']
  }
}


//use
import confetti from 'https://cdn.skypack.dev/canvas-confetti'
```

#### Bot-Aware ISR Fallback
- 페이지 로드(서버 렌더링)을 차단할 때 'blocking' 사용
```
fallback: true
fallback: 'blocking'
```

#### AVIF를 사용한 작은 이미지
- AVIF 지원으로 WebP에 비해 20% 더 작은 이미지
- WebP에 비해 최적화하는 데 시간이 더 오래 걸릴 수 있음
```
module.exports = {
  images: {
    formats: ['image/avif', 'image/webp']
  }
}
```
- 브라우저가 avif를 지원하면 제공, webp를 지원하면 webp를 제공, 둘다 아닐 경우 원본

#### Output File Tracing

#### 기타 개선 사항
- _app.js, _document.js를 수정하더라도 재시작할 필요가 없음
- ESLint integration 단일 파일 린트 지원 `next lint --file`
- getStaticProps에 대해 진행 중인 중복 요청 제거
- 정적 페이지 확인은 공유된 작업자 풀을 이용한다.
- 빠른 새로 고침은 EventSource 연결 대신 WebSocket 연결을 사용

#### 주요 변경 사항
- webpack 5를 기본값으로 설정한 후 공식적으로 webpack 4는 제거
- next.config.js의 target 은 더 이상 필요하지 않다.
- next/image의 wrapping은 div 대신 span을 사용한다.
- 최소 지원 Node.js 버전은 12.0.0에서 12.22.0로 변경(ES 모듈 지원한 첫번째 버전)


#### 업그레이드 가이드
https://nextjs.org/docs/upgrading