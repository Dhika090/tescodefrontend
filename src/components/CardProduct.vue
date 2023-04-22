<template>
    <div class="card shadow card-product">
      <img :src="product.show.image.original" width="90%" class="card-img-top" alt="">
      <div class="card-body">
        <h5 class="card-title">
          <b>Name : {{ product.show.name }}</b></h5>
          <p class="card-text">
            language :{{ product.show.language }}
          </p>
          <p class="card-text">Genre :{{ product.show.genres }}</p>
           <a :href="product.show.officialSite" class="btn btn-success">Link</a>
      </div>
    </div>
</template>
<script>
export default {
  name: 'CardProduct',
  props: ['product']
};
</script>

<style>
</style>
