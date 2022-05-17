<template>
    <div id="nav">
        <router-link to="/" id="logo-url">
            <img :src="logo" :alt="alt" id="log">
        </router-link>
        <router-link to="/">Home</router-link>
        <router-link to="/Pedidos">Pedidos</router-link>
    </div>
</template>

<script>
export default {
    name: "Navbar",
    props: ["logo", "alt"]
}
</script>

<style scoped>
#nav {
  background-color: #222;
  border-bottom: 2px solid #000;
  padding: 15px 50px;
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

#nav #logo-url{
    margin: auto;
    margin-left: 0px;
}

#log {
  width: 40px;
  height: 40px;
}

#nav a {
  color: yellow;
  text-decoration: none;
  margin: 12px;
  transition: 1.0s;
}

#nav a:hover{
    color: white;
}
</style>