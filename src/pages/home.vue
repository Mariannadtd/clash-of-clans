<template>

    <carousel :settings="settings" :breakpoints="breakpoints">

    <slide class="card__wrapper" v-for="item in items" :key="item.id">
      <Card
        :name="`${item.lvl} lvl`"
        :title="item.title"
        :imgUrl="item.img"
        :link="`/${item.alias}`"
      >
        <template v-slot:body>
          {{  item.descr  }}
        </template>

        <CardFooter />
        <!-- <template v-slot:footer>
          <div class="card-stats">
            <div
              v-for="(stat, index) in item.info"
              :key="index"
              class="one-third"
            >
              <div class="stat-value">{{ stat.value  }}</div>
              <div class="stat">{{ stat.title  }}</div>
            </div>
          </div>
        </template> -->
      </Card>
    </slide>

    <template #addons>
      <navigation />
    </template>
  </carousel>

</template>

<script>
import items from '@/seeders/items.js'
import Card from '@/components/Card/Card'
import CardFooter from '@/components/Card/CardFooter'

import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Navigation } from 'vue3-carousel'

export default {
  components: {
    Card,
    CardFooter,
    Carousel,
    Slide,
    Navigation
  },
  data() {
    return {
      items: items,
      settings: {
        itemsToShow: 2,
        wrapAround: true,
        snapAlign: 'center',
        transition: 300,
        autoplay: 3000
      },
      breakpoints: {
        300: {
          itemsToShow: 1
        },
        800: {
          itemsToShow: 2
        }
      }
    }
  }
}
</script>
