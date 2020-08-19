<template>
<div>
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
      style="width:80 !important">
      <el-table-column
        prop="date"
        label="名称"
        align="center">
      </el-table-column>
      <el-table-column
        prop="name"
        label="类型">
      </el-table-column>
      <el-table-column
        prop="address"
        label="网址">
      </el-table-column>  
        <el-table-column
        prop="address"
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
      data() {
        return {
          tableData: [{
            date: '2016-05-02',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄',
          }, {
            date: '2016-05-04',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1517 弄'
          }, {
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }, {
            date: '2016-05-03',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1516 弄'
          }]
        }
      }
}
</script>
<style scoped>
    .div data-v-b2ed89a4{
      display: block;
      margin-left: 100px !important;
      margin-right: 0px;
    }
</style>
