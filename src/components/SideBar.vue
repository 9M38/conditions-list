<template>
  <div class="sidebar">
    <div class="red-dot">
      <svg height="100" width="100">
        <circle cx="60" cy="40" r="20" fill="red" />
      </svg>
    </div>
    <ul class="side-nav"  >
      <li class="side-nav-item">
        Polls
      </li>
      <li class="side-nav-item">
        Users
      </li>
      <li class="side-nav-item">
        Black lists
      </li>
      <li class="side-nav-item">
        Call-center
      </li>
    </ul>
    <div class="help">
      ?
    </div>
  </div>

</template>

<script>
  export default {
    name: "SideBar",
  };
</script>


<style scoped>
  .sidebar {
    display: flex;
    flex-direction: column;
    height: 1000px;
    border: 1px solid lightgray;
    min-width: 130px;
  }
  .side-nav{
    flex-grow: 1;
    list-style-type: none;
    padding: 4px;
  }
  .side-nav-item{
    height: 80px;
    border: 1px solid lightgray;
    border-radius: 10px;
    margin: 5px;
  }

</style>