<template>
  <v-col>
    <v-sheet
      v-if="type === 'input'"
      style="background: #df90ff4f;color:grey"
      class="mx-auto transition-swing d-flex justify-center align-content-center flex-wrap"
      elevation="12"
      max-width="400"
      width="180"
      height="60"
      @click="addReactiveElement(type)"
    >
      {{ type }}
    </v-sheet>
    <v-col v-else>
      <v-sheet
        elevation="10"
        rounded="xl"
      >
        <v-sheet
          class="pa-3 primary text-right"
          dark
          rounded="t-xl"
        >
          <v-btn icon>
            <v-icon>mdi-content-save-outline</v-icon>
          </v-btn>
        </v-sheet>

        <div class="pa-4">
          <v-row
            active-class="primary--text"
          >
            <v-icon
              v-for="icon in icons"
              :key="icon"
              class="pa-1"
              @click="addReactiveElement(type,icon)"
            >
              {{ icon }}
            </v-icon>
          </v-row>
        </div>
      </v-sheet>
    </v-col>
  </v-col>
</template>

<script>
export default {
  name: 'SidebarButton',
  props: {
    type: {
      type: String,
      required: false,
      default: ''
    }
  },
  data () {
    return {
      input: { type: 'input', className: '', style: '', w: 'auto', h: 'auto' },
      itemsLocal: [],
      icons: ['mdi-cloud', 'mdi-cloud-outline', 'mdi-cup-water', 'mdi-currency-eur']
    }
  },
  methods: {
    addReactiveElement (type, icon = '') {
      if (type === 'icon') {
        const iconName = 'mdi ' + icon
        icon = { type: 'icon', options: '', iconName, className: '', style: '', w: 'auto', h: 'auto' }
        // icon = `<i class="mdi ${icon}"></i>`
        this.$emit('add-item', icon)
      }

      if (type === 'input') {
        this.$emit('add-item', this.input)
      }
    }
  }
}
</script>

<style>

</style>
