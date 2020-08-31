<template>
<div>
    <div class="wordcloud">
   <wordcloud
      :data="defaultWords"
      color="Accent"
      top="30px" 
      right="30px" 
      bottom="30px" 
      left="30px"
      :showTooltip="false"
      :wordClick="wordClickHandler"
      >
      </wordcloud>
  </div>
  <div>
    <ShowContent />
  </div>
</div>

</template>

<script>
import Box from '3box';
import wordcloud from 'vue-wordcloud'
import ShowContent from './ShowContent'
export default {
   name: 'WordCloud',
   components: {
    wordcloud,
    ShowContent
  },
   methods: {
    wordClickHandler(name, value, vm) {
      this.ReadFrom3BoxByTag("搜索引擎")
      console.log('wordClickHandler', name, value, vm);

    },
    async ReadFrom3BoxByTag(tag){
            //  获得  信息 
            console.log(tag)
            const spaceData = await Box.getSpace(this.address, tag)
            console.log(spaceData)
            // const box = await Box.openBox(this.address, window.ethereum)
            // box.syncDone
            // console.log(box)
    },
    
  },
  data() {
    return {
      myColors: ['#1f77b4', '#629fc9', '#94bedb', '#c9e0ef'],
      defaultWords: [{
          "name": "区块链",
          "value": 26
        },
        {
          "name": "电影",
          "value": 19
        },
        {
          "name": "图片",
          "value": 18
        },
        {
          "name": "搜索引擎",
          "value": 15
        },
        {
          "name": "游戏",
          "value": 9
        },
        {
          "name": "编程语言",
          "value": 6
        },
        {
          "name": "科技",
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
