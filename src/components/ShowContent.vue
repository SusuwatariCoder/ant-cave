 <template>
    <el-table
      :data="tableData"
      style="width: 100%">
      <el-table-column
        prop="date"
        label="名称">
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
  </template>

  <script>
    export default {
      data() {
        return {
          tableData: [{
            date: '2016-05-02',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄'
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