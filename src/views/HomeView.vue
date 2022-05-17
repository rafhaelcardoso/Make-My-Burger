<template>
  <div class="main-container">
    <Banner />
    <h1>Monte o seu Burger:</h1>
    <PedidoForm/>
  </div>
</template>

<script>
import Banner from "../components/Banner.vue"
import PedidoForm from "../components/PedidoForm.vue"

export default { 
  name: "Home",
  components: {
    Banner,
    PedidoForm
  }
}
</script>

<style scoped>

#h1 {
  margin-bottom: 50px;
}
</style>
