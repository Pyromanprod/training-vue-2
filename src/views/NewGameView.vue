<template>
  <div class="newgame">
    <h1 class="mb-5">Nouvelle partie</h1>
  </div>
  <div class="container">
    <div class="row" v-if="secretNb!==0">
      <div class="col-6">
        <div class="form-floating mb-3">
          <input type="number" class="form-control " id="nbTry" placeholder="2" v-model="nbTry" @keyup.enter="checkNb">
          <button class="btn btn-secondary mt-3" @click="checkNb">Essayer</button>
          <label for="nbTry">Entrez un nombre entre 1 et 100</label>
        </div>
      </div>
      <div class="col-6">
        <p>Nombre d'essaie {{ nbCoup }}</p>
        <p>{{ response }}</p>
        <Start v-if="win" @secretNb="(nb)=>this.secretNb = nb" @click="reset"/>
        <ul>
          <li :key='nb.nb' v-for="nb in listNbTry">pour le nombre : {{ nb.nb }} la réponse était : {{
              nb.response
            }}
          </li>
        </ul>
      </div>
    </div>
    <div class="row" v-else>
      <Start @secretNb="(nb)=>this.secretNb = nb"/>

    </div>
  </div>
</template>

<script>
//import du composant "bouton commencer"
import Start from '@/components/StartBtn.vue'

export default {
  name: 'HomeView',
  data() {
    return {
      response: "",
      nbCoup: 0,
      secretNb: 0,
      nbTry: '',
      win: false,
      listNbTry: []
    }

  },
  methods: {
    reset() {
      this.win = false;
      this.listNbTry = [];
      this.nbTry = "";
      this.nbCoup = 0;
      this.response ="";
    },

    checkNb() {
        this.nbCoup++;
      if (this.nbTry > this.secretNb) {
        this.response = "C'est moins"
        this.listNbTry.push({nb: this.nbTry, response: "Moins"});
        this.nbTry = "";
      } else if (this.nbTry < this.secretNb) {

        this.response = "C'est plus"
        this.listNbTry.push({nb: this.nbTry, response: "Plus"});
        this.nbTry = "";
      } else {
        this.response = "Bravo Vous avez trouvé " + this.secretNb +" en " + this.nbCoup + " Coups"
        this.win = true;
      }

    }
  },
  components: {

    Start

  }
}
</script>

<style scoped>
li {
  list-style: none;
}
</style>
