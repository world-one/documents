## axios
### retry
- 기본적으로 기능을 제공하지 않는다. interceptors를 이용해서 구현 가능하다.
- 아래와 같이 추가된 axios를 한번 감싸서 사용하면 된다.

```
_axios.interceptors.response.use(undefined, retryInterceptors);

function retryInterceptors(e: {
  config: AxiosRequestConfig & RetryOptionTypes;
  response: AxiosResponse;
}) {
  const { config, response } = e;
  if (response?.status === 404 || !config || !config.retryCount) {
    return Promise.reject(e);
  }

  if (!config._retryCount) config._retryCount = 0;

  if (config._retryCount >= config.retryCount) {
    return Promise.reject(e);
  }

  config._retryCount += 1;

  const delay = new Promise((resolve) => {
    setTimeout(() => {
      resolve(null);
    }, config.retryDelay || 1);
  });

  return delay.then(() => {
    return _axios(config);
  });
}
```