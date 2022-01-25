<template>
    <header>
        <div class="topline">
            <input type="text" name="search" id="search" placeholder="Search...">
            <div class="user">
                <div class="user-pic">
                    <svg height="40" width="40">
        <circle cx="18" cy="18" r="18" fill="gray" />
      </svg>
                </div>
                <div class="user-info">
                <h5 class="user-info-name">
                    Alexandr C.
                </h5>
                <p class="user-info-rank">
                    Administrator
                </p>
                </div>
            </div>
        </div>
        <div class="bottomline">
            <ul class="nav">
                <li class="nav-link">
                    Home ->
                </li>
                <li class="nav-link">
                    Polls ->
                </li>
                <li class="nav-link muted">
                    Add poll
                </li>
            </ul>
        </div> 
    </header>
</template>

<style scoped>
header{
    display: flex;
    flex-direction: column;
}
.topline{
    display:flex;
    overflow:auto;
    margin: 2rem
}
#search{
    width: 400px;
    height: 2rem;
    margin: 0 auto 0 0;
}
.user{
    width: 200px;
    display: flex;
}
.user-info-rank{
    font-size: 0.8rem;
}
.nav{
    display:flex;
    list-style-type: none;
    margin: 0 2rem;
    padding: 0;
}
.nav-link{
    font-size: 14px;
}
.nav-link:hover{
    font-weight: 600;
    cursor: pointer;
}
.muted{
    font-weight: 600;
    color: gray;
}
</style>