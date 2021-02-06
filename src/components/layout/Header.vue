<template>
    <header class="Header">
        <h1>TodoList </h1>
        <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
    </header>
</template>


<script>
export default {
    name:"Header",    
}
</script>

<style scoped>
 .header {

     background:lightpink;
     color: black;
     text-align: center;
     padding: 2px;
     background-color: brown;
     
    }

 .header a {
     color: beige;
     padding-right: 2px;
     background-color: brown;
     }
</style>