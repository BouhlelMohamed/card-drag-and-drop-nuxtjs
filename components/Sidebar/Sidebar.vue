<template>
  <v-col class="d-grid justify-start">
    <div class="mb-13">
      <v-color-picker
        class="ma-2"
        hide-canvas
        @update:color="$emit('update-color-card',$event.hexa)"
      />
    </div>
    <v-slider
      v-model="valueSliderWidth"
      label="width"
      thumb-label="always"
      max="700"
      min="150"
      @end="$emit('update-width', $event)"
    />
    <v-slider
      v-model="valueSliderHeight"
      label="height"
      thumb-label="always"
      max="420"
      min="100"
      @end="$emit('update-height', $event)"
    />
    <sidebar-button
      v-for="sidebarElement in sidebarElements"
      :key="sidebarElement.type"
      :type="sidebarElement.type"
      @add-item="$emit('add-item', $event)"
    />
  </v-col>
</template>

<script>
import SidebarButton from './SidebarButton.vue'
export default {
  components: { SidebarButton },
  data () {
    return {
      valueSliderWidth: 400,
      valueSliderHeight: 300,
      sidebarElements: [{ type: 'input' }, { type: 'icon' }]
    }
  }
}
</script>

<style lang="scss">
.d-grid {
  display: grid
}
</style>
