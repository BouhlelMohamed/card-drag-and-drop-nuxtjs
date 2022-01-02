<template>
  <v-row justify="center" align="center">
    <v-col cols="3">
      <Sidebar
        class="ml-5"
        @update-width="localWidth = $event"
        @update-height="localHeight = $event"
        @update-color-card="localColorCard = $event"
        @add-item="addItem($event)"
      />
    </v-col>
    <v-col>
      <card :width="localWidth" :height="localHeight" :style="'background:' + localColorCard">
        <div>
          <vue-draggable-resizable
            v-for="(item,index) in items"
            :key="index"
            :w="item.w"
            :h="item.h"
            @dragging="onDrag"
            @resizing="onResize"
          >
            <textarea
              v-if="item.type === 'input'"
            >
              Text
            </textarea>
            <v-icon v-else-if="item.type === 'icon'">
              {{ item.iconName }}
            </v-icon>
          </vue-draggable-resizable>
        </div>
      </card>
    </v-col>
  </v-row>
</template>
<script>
import Card from '@/components/Card/Card.vue'
import Sidebar from '~/components/Sidebar/Sidebar'
import VueDraggableResizable from '~/plugins/VueDraggableResizable.js'

export default {
  components: { Sidebar, Card, 'vue-draggable-resizable': VueDraggableResizable },
  data () {
    return {
      localWidth: 400,
      localHeight: 300,
      width: 0,
      height: 0,
      x: 0,
      y: 0,
      items: [],
      localColorCard: ''
    }
  },
  methods: {
    addItem (item) {
      this.items.push(item)
    },
    onResize (x, y, width, height) {
      console.log('resize', x, y, width, height)
      this.x = x
      this.y = y
      this.width = width
      this.height = height
    },
    onDrag (x, y) {
      console.log(x, y)
      this.x = x
      this.y = y
    }
  }
}
</script>
