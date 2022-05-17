<template>
    <div>
        <div>
            <!-- Formulário do pedido -->
            <form id="burger-form">
                <!-- Input - Nome do Cliente -->
                <div class="input-container">
                    <label for="nome">Nome do cliente:</label>
                    <input type="text" name="nome" id="nome" v-model="nome" placeholder="Digite o seu nome!">
                </div>
                <!-- Input - Tipo do pão -->
                <div class="input-container">
                    <label for="nome">Escolha o seu pão:</label>
                <select name="pao" id="pao" v-model="pao" value="selectbread">
                        <option value="selectbread" disabled hidden>Selecione o seu pão!</option>
                        <option value="Brioche"> Pão brioche</option>
                        <option value="3queijos">Pão 3 Queijos</option>
                    </select>
                </div>
                <!-- Input - Selecione sua Carne -->
                <div class="input-container">
                    <label for="nome">Escolha a sua Carne:</label>
                    <select name="Carne" id="Carne" v-model="Carne">
                        <option value="" selected>Selecione a sua Carne!</option>
                        <option value="BoiBandido">Boi Bandido</option>
                        <option value="GalinhaLoka">Galinha Loka</option>
                        <option value="PorcoCorrupto">Porco Corrupto</option>
                    </select>
                </div>
                <!-- Selecione os opcionais -->
                <div class="input-container" id="opcionais-container">
                    <label for="opcionais" id="opcionais-title">Selecione os opcionais:</label>
                    <!-- Orégano -->
                    <div class="checkbox-container">
                    <input type="checkbox" name="opcionais" v-model="opcionais" value="oregano">
                    <span>Orégano</span>
                    </div>
                    <!-- Vinagrete -->
                    <div class="checkbox-container">
                    <input type="checkbox" name="opcionais" v-model="opcionais" value="vinagrete">
                    <span>Vinagrete</span>
                    </div>
                    <!-- Barbecue -->
                    <div class="checkbox-container">
                    <input type="checkbox" name="opcionais" v-model="opcionais" value="barbecue">
                    <span>Barbecue</span>
                    </div>
                </div>
                <!-- Botão de enviar -->
                <div class="input-container">
                    <input type="button" class="submit-btn" value="Enviar meu pedido!">
                </div>
            </form>
        </div>
    </div>   
</template>

<script>
export default {
    name: "PedidoForm"
}
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
    color: #222;;
    padding: 5px 10px;
    border-left: 4px solid #fcba03;
  }
  input, select {
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
    color:#fcba03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
  }
  .submit-btn:hover {
    background-color: #fcba035d;
    color: #222;
  }
</style>