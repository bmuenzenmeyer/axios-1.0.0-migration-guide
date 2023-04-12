# axios-1.0.0-migration-guide

crowd-sourced migration guide for [axios1.0.0](https://github.com/axios/axios/releases/tag/v1.0.0)

- [CONTRIBUTING GUIDE](./CONTRIBUTING.md)

## axios links

- [axios docs](https://axios-http.com/docs/intro)
- [official migration guide](https://github.com/axios/axios/blob/v1.x/MIGRATION_GUIDE.md)
- [axios Community Discussion](https://github.com/axios/axios/discussions/4996)
- [Upgrade Guide needs to be updated with 0.x.x -> 1.0.0](https://github.com/axios/axios/issues/5014)
- [Is axios@1 stable?](https://github.com/axios/axios/discussions/5645)

---

# BREAKING CHANGES

Documenting the potential breaking changes between [0.27.2...1.0.0](https://github.com/axios/axios/compare/v0.27.2...v1.0.0)

> 1. not all have solutions, but are here for completeness
> 2. this guide mentions `1.0.0`, but most likely you will want to go to the latest `1.x` version

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

## `request.headers` shape changes

> from [@josias-r](https://github.com/josias-r) via https://github.com/axios/axios/discussions/4996#discussioncomment-5581701

Look out for the shape of `request.headers` to have changed.

```diff
-    if (request.headers?.common?.Authorization) {
-      request.headers.common.Authorization =
+    if (request.headers?.Authorization) {
+      request.headers.Authorization =
        axiosInstance.defaults.headers.common.Authorization;
    }
```

## Serialization of get `params`

https://github.com/axios/axios/issues/5630

## `axios.create` is not a function

https://github.com/axios/axios/issues/5613

## headers are not availabile in `beforeRedirect`

https://github.com/axios/axios/issues/5365

## axios attempts to resolve IPv6 addresses as hostnames

https://github.com/axios/axios/issues/5333

## `settle` helper not exported, or anything from `lib/helpers`

> internals that may not be exposed anymore

https://github.com/axios/axios/issues/5254
https://github.com/axios/axios/issues/5072

## `error.config` on `AxiosError` `ERR_INVALID_CHAR`

https://github.com/axios/axios/issues/5254
