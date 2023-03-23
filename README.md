# vue-tsc bug reproduction

Bug reproduction repo for issue: https://github.com/vuejs/language-tools/issues/2543

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
