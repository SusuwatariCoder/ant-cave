<template>
<div class="content-box">
    <el-table
      :data="tableData"
      class="table"
      stripe
      border
      width='0%'
      :header-cell-style="{
          'text-align':'center',
          'border-top':'3px solid rgb(16, 217, 243)',
          'padding-bottom':'1px',
      }"
      :cell-style="{
          'text-align':'center',
          'padding-bottom':'1px',
      }"
      style="width:50 !important">
      <el-table-column
        prop="name"
        label="名称"
        align="center">
      </el-table-column>
      <el-table-column
        prop="tag"
        label="标签">
        <template slot-scope="scope">
            <div slot="reference" class="name-wrapper">
              <el-tag size="medium">{{ scope.row.tag }}</el-tag>
            </div>
        </template>
      </el-table-column>
      <el-table-column
        width="50"
        prop="cent"
        label="评分">
      </el-table-column>
      <el-table-column
        prop="url"
        label="网址">
      </el-table-column>  
        <el-table-column
        prop="url"
        label="查看">
        <template slot-scope="scope">
        <el-button @click="handleClick(scope.row)" type="text" size="small">访问</el-button>
      </template>
      </el-table-column>
    </el-table>
</div>
</template>

<script>
    export default {
      name: "ShowContent",
      methods: {
        handleClick(row) {
          console.log(row.url);
          window.open(row.url,'_blank') // 新窗口打开外链接
      }
      },
      data() {
        return {
          tableData: [{
            name: '鸠摩搜索',
            tag: '搜索引擎',
            cent: '-',
            url: 'https://www.jiumodiary.com/',
          }, {
            name: '多吉搜索',
            tag: '搜索引擎',
            cent: '-',
            url: 'https://www.dogedoge.com/',
          }, {
            name: '盘搜',
            tag: '搜索引擎',
            cent: '-',
            url: 'http://www.pansou.com/',
          }, {
            name: '茶杯狐',
            tag: '搜索引擎',
            cent: '-',
            url: 'https://www.cupfox.com/',
          }]
        }
      }
}
</script>
<style scoped>
.content-box {
  width: 70%;
  margin: 0 auto;
}
</style>
