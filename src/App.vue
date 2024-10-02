<template>
  <div id="app">
    <nav>
      <router-link to="/">Homeview</router-link> |
      <router-link to="/progetti">Progetti</router-link>
    </nav>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
};
</script>