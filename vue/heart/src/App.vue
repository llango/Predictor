<template>
  <div id="app">
    <div id="nav">
      <!--router-link to="/about">关于</router-link-->
    </div>
    <router-view />
  </div>
</template>

<script>
export default {
  name: "App"
};
</script>

<style>
#app{
  margin-top:15px;
}
</style>
