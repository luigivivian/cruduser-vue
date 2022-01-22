<template>
  <div class="hello">
    <h1>Lista de usuario</h1>

      <div>
          <ul>
            <li v-for="u in this.users" :key="u.firstName">{{u.firstName}}</li>
          </ul>
      </div>

      <button @click="getUsers()">Teste</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },

  // template data ( vue js)
  data(){
    return{
      //variavel que renderiza usuarios na tela
      users: []

    }
  },
  methods: {
    //meotod que dispara requisição para api
    getUsers(){
      console.log('Requsição para API efetuada');
      //requisição get para api
      this.axios.get('http://localhost:3000/user')
      .then((result) => { // resolvendo a requisição
        //seta usuarios
        this.users = result.data;
      });
    }    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
