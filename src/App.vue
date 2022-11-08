<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
    <router-link to="/reference">reference</router-link>
    <router-link to="/youtube">youtube</router-link>
    <router-link to="/movie">movie</router-link>
    <router-link to="/unsplash">unsplash</router-link>
  </nav>
  <router-view />
</template>

<style lang="scss">
@import 'index.scss';
</style>
