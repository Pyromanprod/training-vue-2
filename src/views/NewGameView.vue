<template>
  <div class="newgame">
    <h1>Nouvelle partie</h1>
  </div>
  <div class="container">
    <div class="row">
      <div class="col-6">
        <div class="form-floating mb-3">
          <input type="number" class="form-control" id="nbTry" placeholder="2">
          <label for="nbTry">Entrez un nombre entre 1 et 100</label>
        </div>
      </div>
      <div class="col-6">
        <div class="form-floating mb-3">
          <p>Ici ce sera un recap des nombres essayé</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'HomeView',
  components: {

  }
}
</script>
