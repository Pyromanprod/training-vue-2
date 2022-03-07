<template>
  <div class="newgame">
    <h1 class="mb-5">Nouvelle partie</h1>
  </div>
  <div class="container">
    <div class="row">
      <div class="col-6">
        <div class="form-floating mb-3">
          <input type="number" class="form-control" id="nbTry" placeholder="2" v-model="nbTry"  @keyup.enter="checkNb">
          <button class="btn btn-secondary mt-3" @click="checkNb">Essayer</button>
          <label for="nbTry">Entrez un nombre entre 1 et 100</label>
        </div>
      </div>
      <div class="col-6">
          <p>Ici ce sera un recap des nombres essayé</p>
        <p>Nombre d'essaie {{ nbCoup }}</p>
        <p>{{ response }}</p>
        <ul>
          <li :key='nb.nb' v-for="nb in listNbTry">pour le nombre : {{ nb.nb }} la réponse était : {{ nb.response }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>


export default {
  name: 'HomeView',
  data(){
    return {
      response:"",
      nbCoup:0,
      secretNb:50,
      nbTry:'',
      listNbTry:[]
    }

  },
  methods:{

  checkNb(){
    if (this.nbTry > this.secretNb){
      this.response = "C'est moins"
      this.listNbTry.push({nb: this.nbTry, response: "Moins"});
      this.nbTry = "";
      this.nbCoup++;
    }else if(this.nbTry < this.secretNb){
      this.response = "C'est plus"
      this.listNbTry.push({nb: this.nbTry, response: "Plus"});
      this.nbTry = "";
      this.nbCoup++;
    }else{
      this.response = "Bravo Vous avez trouvé en " + this.nbCoup + " Coups"
    }

  },
    createNewSecret(){

    },
  },
  components: {

  }
}
</script>

<style scoped>
li{
  list-style: none;
}
</style>
