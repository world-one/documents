### CJS (CommonJS)
- http://www.commonjs.org/
- require를 통해 모듈을 변수에 담을 수 있다.
- exports로 다른 파일에서 사용할 수 있도록 추출
```
    var lib = require('package/lib');
    exports.foobar = foo;
```
- Node.js가 CommonJS를 채택
- 동기로 동작한다.

### AMD (Asynchronous Module Definition)
- CommonJs는 동기적인 동작이 가능한 서버사이드 자바스크립트 환경을 전제로 한다. 브라우저에서는 모듈을 모두 다운받을 때까지 아무것도 할 수 없다.
- AMD는 비동기 상황에서 자바스크립트 모듈을 사용하기 위해 CommonJS로부터 독립한 그룹
- define, return을 통해 모듈의 로드와 내보내기가 가능
```
    define(['libs/lib'], function (lib) {
        function foo () {
            lib.log('hello');
        }

        return {
            foo
        }
    });

    // 선언된 모듈의 사용
    require(['package/myModule'], function (myModule) {
      myModule.foobar();
    });
```

### UMD (Universal Module Definition)
- AMD와 CJS의 두 그룹이 서로 호환되지 않는 문제가 발생하여, 이를 해결하기 위해 나온 것이 UMD
- UMD는 디자인 패턴에 가깝다.
- exports와 module이 존재하면 CommonJS방식
- define이 함수이고 define.amd가 존재할 경우 AMD 방식
- 둘 다 아니라면 window 객체에 모듈을 내보낸다.

### ESM (ECMAScript Module)
- 자바스크립트 공식 모듈 시스템이지만 브라우저에서 지원하지 않아 번들러를 함께 사용해야 한다.
```
import lib from 'package/lib';

function foo () {
  lib.log('hello world!');
}

export {
  foobar: foo
};
```
`<script type="module" src="index.mjs">`