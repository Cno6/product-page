<template>
  <add-form></add-form>
  <products-list></products-list>
</template>

<script>
import AddForm from '@/components/AddForm.vue'
import ProductsList from '@/components/ProductsList.vue'

export default {
  name: 'App',
  components: {
    AddForm,
    ProductsList
  }
}
</script>

<style lang="scss">
@import './scss/main.scss';
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@600&family=Source+Sans+Pro:wght@400;600&display=swap');

#app {
  box-sizing: content-box;
  max-width: 1376px;
  padding: 30px;
  margin: auto;
  background-color: $color-background;
  display: flex;
  gap: $gap;
}
</style>
