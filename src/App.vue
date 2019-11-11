<template>
  <div>
    <h1>{{titulo}}</h1>
    <ul>
      <li v-for="foto of fotos" :key="foto.id"> {{foto.titulo}}
        <img :src="foto.url" :alt="foto.titulo" class="fotos" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titulo: "galeria de imagens",
      fotos: []
    };
  },
  created(){
    let promise = this.$http.get('http://localhost:3000/v1/fotos');
    promise.then(res => res.json())
    .then(fotos => this.fotos = fotos, err => console.log(err))
  }
};
</script>

<style>
.fotos{
    width: 300px;
}
</style>
