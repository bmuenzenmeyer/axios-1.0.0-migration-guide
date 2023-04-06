# axios-1.0.0-migration-guide

crowd-sourced migration guide for [axios1.0.0](https://github.com/axios/axios/releases/tag/v1.0.0)

- [CONTRIBUTING GUIDE](./CONTRIBUTING.md)

## axios links

- [axios docs](https://axios-http.com/docs/intro)
- [axios Community Discussion](https://github.com/axios/axios/discussions/4996)
- [Upgrade Guide needs to be updated with 0.x.x -> 1.0.0](https://github.com/axios/axios/issues/5014)

---

# BREAKING CHANGES

Documenting the potential breaking changes between [0.27.2...1.0.0](https://github.com/axios/axios/compare/v0.27.2...v1.0.0)

## import from @bundled-es-modules

> from [@ghiscoding](https://github.com/ghiscoding) via https://github.com/axios/axios/discussions/4996#discussioncomment-5537237

If you were using axios@0.x with ESM/Vite, such as in Vue3, your import syntax may have changed:

```diff
- import { axios } from '@bundled-es-modules/axios';
+ import axios from 'axios';
```

## `AxiosRequestConfig` for http interceptors

> from [@ghiscoding](https://github.com/ghiscoding) via https://github.com/axios/axios/discussions/4996#discussioncomment-5537237

> the only other issue we had was with the AxiosRequestConfig interface that we use in our http interceptors and for that we simply had to switch to the InternalAxiosRequestConfig interface

```diff
- import { axios, AxiosRequestConfig, AxiosResponse } from '@bundled-es-modules/axios';
+ import axios, { AxiosError, AxiosResponse, InternalAxiosRequestConfig } from 'axios';

function startInterceptors() {
  axios.interceptors.request.use(onRequestFullfilled, onRequestResponseRejected);
  axios.interceptors.response.use(onResponseFullfilled, onRequestResponseRejected);
}

async function onRequestResponseRejected(reason: AxiosError<string>) {
-  const originalRequest = reason.config;
+  const originalRequest = reason.config as InternalAxiosRequestConfig;
   // ...
}
```


## Serialization of get `params`

https://github.com/axios/axios/issues/5630


## `axios.create` is not a function

https://github.com/axios/axios/issues/5613
