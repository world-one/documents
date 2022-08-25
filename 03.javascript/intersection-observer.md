### intersection observer
- https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API
- web api로 제공하는 기능이다. 특정 엘리먼트가 화면에 노출되는 것을 감지해서 이벤트를 발생 시킨다.
- 무한 스크롤에 활용할 수 있다.

```
function scrollObserver(callback: () => void): IntersectionObserver {
  return new IntersectionObserver(
    async (entries, observer) => {
      if (entries[0].isIntersecting) {
        await callback();
        observer.disconnect();
      }
    },
    { root: null, rootMargin: '0px', threshold: 1 }
  );
}
```