<template>

    <div class="wrapper-person">
      <div v-if="item">
        <img :src="item.img" :alt="item.descr">
        <h1 style="color: #fff;" class="title">{{  item.title  }}</h1>
        <p>{{  item.descr  }}</p>

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

        <div>
          <router-link to="/" class="btn btnPrimary">Back to home</router-link>
        </div>
      </div>
    </div>

</template>

<script>
import items from '@/seeders/items.js'

export default {
  data() {
    return {
      item: null
    }
  },
    async created () {
      const alias = this.$route.params.itemAlias
      const item = items.find(el => el.alias === alias)

      this.item = item
      console.log(item)

      
      const item = data.items.find(el => el.alias === this.$route.params.itemAlias)

      if (!item) {
        return await this.$router.push({ name: 'NotFound' })
      }

      this.item = JSON.parse(JSON.stringify(item))
      this.isLoading = false
  }
}
</script>

<style lang="scss" scoped>
.wrapper-person {
  text-align: center;
  .card-stats {
    margin: 30px 0;
    border-radius: 14px;
  }
}
</style>
