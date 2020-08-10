<template>
  <div class="wordcloud">
   <wordcloud
      :data="defaultWords"
      nameKey="name"
      valueKey="value"
      color="Accent"
      :showTooltip="true"
      :wordClick="wordClickHandler">
      </wordcloud>
  </div>
</template>

<script>
import wordcloud from 'vue-wordcloud'
export default {
  name: 'WordCloud',
   components: {
    wordcloud
  },
   methods: {
    wordClickHandler(name, value, vm) {
      console.log('wordClickHandler', name, value, vm);
    }
  },
  data() {
    return {
      myColors: ['#1f77b4', '#629fc9', '#94bedb', '#c9e0ef'],
      defaultWords: [{
          "name": "电影",
          "value": 26
        },
        {
          "name": "音乐",
          "value": 19
        },
        {
          "name": "电商",
          "value": 18
        },
        {
          "name": "宠物",
          "value": 16
        },
        {
          "name": "编程",
          "value": 15
        },
        {
          "name": "区块链",
          "value": 9
        },
        {
          "name": "数据库",
          "value": 9
        },
        {
          "name": "汽车",
          "value": 9
        },
        {
          "name": "金融",
          "value": 6
        },
        {
          "name": "科技",
          "value": 9
        },
        {
          "name": "农业",
          "value": 9
        },
        {
          "name": "财经",
          "value": 6
        },
        {
          "name": "娱乐",
          "value": 9
        },
        {
          "name": "前端",
          "value": 9
        },
        {
          "name": "以太坊",
          "value": 6
        },
        {
          "name": "",
          "value": 64
        }
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 
</style>
