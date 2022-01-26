<template>
  <div class="sidebar">
    <div class="red-dot">
      <svg height="100" width="100">
        <circle cx="80" cy="40" r="20" fill="red" />
      </svg>
    </div>
    <ul class="side-nav"  >
      <li class="side-nav-item item-active">
        <div class="item-icon">
        </div>
        <div class="item-text">Polls</div>
      </li>
      <li class="side-nav-item">
        <div class="item-icon">
        </div>
        <div class="item-text">Users</div>
      </li>
      <li class="side-nav-item">
        <div class="item-icon">
        </div>
        <div class="item-text">Black lists</div>
      </li>
      <li class="side-nav-item">
        <div class="item-icon">
        </div>
        <div class="item-text">Call-center</div>
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
    min-width: 10rem;
  }
  .side-nav{
    flex-grow: 1;
    list-style-type: none;
    padding: 4px;
  }
  .side-nav-item{
    height: 7rem;
    border: 3px solid transparent;
    border-radius: 10px;
    margin: 5px;
    display: flex;
    flex-direction: column;
  }
  .item-icon{
      background-color: gray;
      border-radius: 4px;
      width: 3rem;
      height: 3rem;
      margin: 1.5rem auto 0;
  }
  .item-text{
    margin: 0 auto;
  }
  .side-nav-item:hover{
    border: 3px solid rgb(169, 216, 93);
    color: rgb(169, 216, 93);
    cursor: pointer;
  }

  .item-active{
    height: 7rem;
    background-color:  lightgray;
    border-radius: 10px;
    margin: 5px;
  }
  .help{
    height: 3rem;
    width: 3rem;
    border: 3px solid black;
    border-radius: 50%;
    text-align: center;
    padding: 3px;
    font-size: 2rem;
    margin: 2rem auto;
    color: green;
  }
  .help:hover{
    background-color: rgb(169, 216, 93);
    border: 3px solid rgb(169, 216, 93);
    color: white;
    cursor: pointer;
  }

</style>