<template>
  <nav>
    <router-link to="/">TODOLIST</router-link>
  </nav>
  <router-view/>
</template>

<style>
body{
  margin:0;
  padding:0;
  box-sizing: border-box;
}

#app {
   width: 100vw;
   height: 100vh;
   margin: 0;
   display: flex;
   flex-direction: column;
   justify-content: center;
   align-items: center;
   background-image: 
                   linear-gradient(62deg,rgba(7,86,160,0.973) 13%,rgba(255,122,151,0.5) 4%),
                   linear-gradient(44deg,rgba(0,43,99,0.079) 39%,rgba(242,140,143,0.5) 18%),
                   linear-gradient(118deg,rgba(84,202,242,0.031) 40%,rgba(247,155,187,0.5) 54%),
                   linear-gradient(58deg,rgba(90,90,237,0.161) 83%,rgba(249,156,142,0.5) 23%);
 background-blend-mode: normal,lighten,multiply,hard-light;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: black;
}
</style>
