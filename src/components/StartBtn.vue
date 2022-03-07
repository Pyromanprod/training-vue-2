<template>

  <div class="col-12">
    <button class="btn btn-warning" @click="createNewSecret">Commencer</button>
  </div>
</template>
<script>
export default {
  emits: ['secretNb'],
  methods: {
    createNewSecret() {
      let min = Math.ceil(1);
      let max = Math.floor(100);
      this.$emit('secretNb', Math.floor(Math.random() * (max - min + 1)) + min);
    },
  }
}

</script>