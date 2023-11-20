<template>
  <Message :msg="msg" v-show="msg" />
  <div>
    <form id="acai-form" method="POST" @submit="createPurple">
      <div class="input-container">
        <label for="nome">Nome do cliente:</label>
        <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
      </div>

      <div class="input-container">
        <label for="ac">Sabor do Açaí:</label>
        <select name="ac" id="ac" v-model="ac">
          <option value="">Escolha o Tipo</option>
          <option v-for="ac in acai" :key="ac.id" :value="ac.tipo">{{ ac.tipo }}</option>
        </select>
      </div>

      <div class="input-container">
        <label for="tam">Tamanho do Açaí:</label>
        <select name="tam" id="tam" v-model="tam">
          <option value="">Escolha o tamanho</option>
          <option v-for="tam in tamanho" :key="tam.id" :value="tam.tipo">{{ tam.tipo }}</option>
        </select>
      </div>

      <div id="opcionais-container" class="input-container">
        <label id="opcionais-title" for="opcionais">Selecione os acréscimos:</label>
        <div class="checkbox-container" v-for="opcional in opcionaisData" :key="opcional.id">
          <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
          <span>{{ opcional.tipo }}</span>
        </div>
      </div>  

      <div class="input-container">
        <input class="submit-btn" type="submit" value="Fazer Pedido!">
      </div>

    </form>
  </div>
</template>


<script>

  import Message from "./Message.vue"

  export default {
    name: "PurpleForm",
    data() {
      return {
        acai: null,
        tamanho: null,
        opcionaisData: null,
        nome: null,
        opcionais: [],
        status: "Solicitado",
        msg: null
      }
    },
    methods: {
      async getIngredients() {

        const req = await fetch("https://food-delivey-api.vercel.app/ingredientes");
        const data = await req.json();

        this.tamanho = data.tamanho;
        this.acai = data.acai;
        this.opcionaisData = data.opcionais;
      },

      async createPurple(event) {

        event.preventDefault();

        const data = {
          nome: this.nome,
          tamanho: this.tam,
          ac: this.ac,
          opcionais: Array.from(this.opcionais),
          status: "Solicitado"
        }

        const dataJson = JSON.stringify(data);

        const req = await fetch("https://food-delivey-api.vercel.app/roxinhos, {
          method: "POST",
          headers: {"Content-Type": "application/json"},
          body: dataJson
        })

        const res = await req.json();

        this.msg = `Pedido Nº ${res.id} realizado com sucesso!`

        setTimeout(() => this.msg = "", 3000);

        this.nome = "",
        this.tam = "",
        this.ac = "",
        this.opcionais = ""
        
      }
    },

    mounted() {
      this.getIngredients();
    },

    components: {
      Message
    }
  }

</script>


<style scoped>

#acai-form {
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
  .checkbox-container input {
    width: auto;
  }

  .checkbox-container span {
    margin-left: 6px;
    font-weight: bold;
  }

  .submit-btn {
    background-color: #371B34;
    color:#fcba03;
    font-weight: bold;
    border: 2px solid #371B34;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
  }

  .submit-btn:hover {
    background-color: transparent;
    color: #371B34;
  }


</style>
