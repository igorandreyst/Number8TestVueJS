<template>
    <nav class="main-nav">
        <ul class="ul-nav">
            <li class="li-nav">
                <router-link :to="{ name: 'Home' }" class="a-nav">Home</router-link>
            </li>
            <li class="li-nav">
                <router-link :to="{ name: 'Demo' }" class="a-nav">Demo</router-link>
            </li>
        </ul>
    </nav> 
</template>

<script>
export default {
  name: 'NavBar'
}
</script>

<style scoped>
.ul-nav {
    list-style-type: none;
    padding: 0;
}
.a-nav {
    color: #42b983;
}
.li-nav {
    display: inline-block;
    margin: 10px;
}
</style>