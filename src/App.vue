<template>
  <div class="root">
    <side-bar />
    <div class="page-space">
      <headbar />
      <page />
    </div>
  </div>
</template>

<script>
  import SideBar from "./components/SideBar.vue";
  import Headbar from "./components/Headbar.vue";
  import Page from "./views/Page.vue";

  export default {
    name: "App",
    components: {
      SideBar,
      Headbar,
      Page
    },
  };
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  }

  .root {
    display: flex;
  }

  .page-space {
    flex-grow: 1;

  }
</style>