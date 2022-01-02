<template>
  <v-card
    class="mx-auto"
    :width="width"
    :height="height"
    outlined
  >
    <slot>hola</slot>
  </v-card>
</template>

<script>
export default {
  name: 'Card',
  props: {
    width: {
      type: Number,
      default: 300
    },
    height: {
      type: Number,
      default: 300
    }
  }

}
</script>

<style scoped>

</style>
