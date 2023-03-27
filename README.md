# vue-tsc bug reproduction

Bug reproduction repo for issue: https://github.com/vuejs/language-tools/issues/2543

> `vue-tsc --noEmit --watch` can not catch errors that can be catched by `vue-tsc --noEmit`.

Dependencies:

```
  "dependencies": {
    "vue": "^3.2.47",
    "vue-router": "^4.1.6"
  },
  "devDependencies": {
    "@vitejs/plugin-vue": "^4.1.0",
    "typescript": "^5.0.2",
    "vite": "^4.2.1",
    "vue-tsc": "^1.3.8"
  }
```

Reproduction steps:

Run `npm i`.

Run `npx vue-tsc --noEmit`, see error:

```
src/components/Hyperlink.vue:4:31 - error TS2322: Type 'unknown' is not assignable to type 'RouteLocationRaw'.

4   <RouterLink v-bind="$attrs" :to="$attrs.href"><slot /></RouterLink>
                                ~~~

  node_modules/vue-router/dist/vue-router.d.ts:1153:5
    1153     to: RouteLocationRaw;
             ~~
    The expected type comes from property 'to' which is declared here on type 'ComponentProps<_RouterLinkI>'


Found 1 error in src/components/Hyperlink.vue:4
```

Run `npx vue-tsc --noEmit --watch`, see no error.

While I expect to see the same error.
