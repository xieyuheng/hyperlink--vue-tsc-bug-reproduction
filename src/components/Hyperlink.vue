<script setup lang="ts"></script>

<template>
  <RouterLink v-bind="$attrs" :to="$attrs.href"><slot /></RouterLink>
</template>
