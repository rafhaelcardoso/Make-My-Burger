<template>
  <Message :msg="msg" v-show="msg" />
  <div>
    <div>
      <!-- Formulário do pedido -->
      <form id="burger-form" method="POST" @submit="createBurger">
        <!-- Input - Nome do Cliente -->
        <div class="input-container">
          <label for="nome">Nome do cliente:</label>
          <input
            type="text"
            name="nome"
            id="nome"
            v-model="nome"
            placeholder="Digite o seu nome!"
          />
        </div>
        <!-- Input - Tipo do pão -->
        <div class="input-container">
          <label for="nome">Escolha o seu pão:</label>
          <select name="pao" id="pao" v-model="pao">
            <option value="" selected>Selecione o seu pão!</option>
            <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
          </select>
        </div>
        <!-- Input - Selecione sua Carne -->
        <div class="input-container">
          <label for="nome">Escolha a sua Carne:</label>
          <select name="carne" id="carne" v-model="carne">
            <option value="" selected>Selecione a sua Carne!</option>
            <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
          </select>
        </div>
        <!-- Selecione os opcionais -->
        <div class="input-container" id="opcionais-container">
          <label for="opcionais" id="opcionais-title"
            >Selecione os opcionais:</label
          >
          <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
          <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
          <span>{{ opcional.tipo }}</span>
        </div>
        </div>
        <!-- Botão de enviar -->
        <div class="input-container">
          <input type="submit" class="submit-btn" value="Enviar meu pedido!" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import Message from './Message'

export default {
  name: "PedidoForm",
  components:{
    Message,
  },

  data() {
    return {
    paes: null,
    carnes: null,
    opcionaisdata: null,
    nome:  null,
    pao: null,
    carne: null,
    opcionais: [],
    status: "Solicitado",
    msg: null
    }
   },

  methods: {
    async getIngredients() {
      const req = await fetch("http://localhost:3000/ingredientes");
      const data = await req.json();

      this.paes = data.paes
      this.carnes = data.carnes
      this.opcionaisdata = data.opcionais
    },

    async createBurger(e) {
      e.preventDefault()
      const data = {
        nome: this.nome,
        carne: this.carne,
        pao: this.pao,
        opcionais: Array.from(this.opcionais),
        status: "Solicitado"
      }
      const dataJson = JSON.stringify(data)    
      const req = await fetch("http://localhost:3000/pedidos", {
        method: "POST",
        headers: { "Content-Type" : "application/json" },
        body: dataJson
      });
      const res = await req.json()
      this.msg = 'Pedido n° ${res.id} realizado com sucesso!'
      // clear message
      setTimeout(() => this.msg = "", 3000)
      // limpar campos
      this.nome = ""
      this.carne = ""
      this.pao = ""
      this.opcionais = []
    }
  },

  mounted() {
    this.getIngredients();
  },
};
</script>

<style scoped>
#burger-form {
  max-width: 400px;
  margin: 0 auto;
}
.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}
label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}
input,
select {
  padding: 5px 10px;
  width: 300px;
}
#opcionais-container {
  flex-direction: row;
  flex-wrap: wrap;
}
#opcionais-title {
  width: 100%;
}
.checkbox-container {
  display: flex;
  align-items: flex-start;
  width: 50%;
  margin-bottom: 20px;
}
.checkbox-container span,
.checkbox-container input {
  width: auto;
}
.checkbox-container span {
  font-weight: bold;
  padding-left: 5px;
}
.submit-btn {
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}
.submit-btn:hover {
  background-color: #fcba035d;
  color: #222;
}
</style>
