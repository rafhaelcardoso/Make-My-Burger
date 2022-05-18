<template>
  <div>
    <div class="main-container">
      <h1>Gerenciar pedidos:</h1>
      <pedidos-dashboard />
    </div>
  </div>
</template>

<script>
import PedidosDashboard from '../components/PedidosDashboard'
export default {
  name: 'Pedidos',
  components: {
    PedidosDashboard
  }
}
</script>