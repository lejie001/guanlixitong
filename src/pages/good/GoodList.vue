<template>
<div class="qf-goodlist">
  <div>商品列表</div>

  <!-- 栅格系统 -->
  <!-- 一行 -->
  <div>
    <el-row style="margin:25px 0" type='flex' align='middle'>
      <el-col :span='2'>名称搜索：</el-col>
      <el-col :span='4'>
        <el-input v-model="filter.searchText" placeholder="请输入内容" size='mini'></el-input>
      </el-col>
      <el-col :span='3'><div style="margin:0 0 0 30px">品类筛选：</div></el-col>
      
      <el-col :span='4'>
        <CateSelect v-model="filter.cate" size='mini'></CateSelect>
      </el-col>

      <el-col :span="4" :offset='7'>
        <div style="textAlign:right">
          <el-button type="primary" size='mini' @click='skipToAdd'>新增</el-button>
        </div>
      </el-col>
    </el-row>

    <el-row style="margin:25px 0" type='flex' align='middle'>
      <el-col :span='2'><div>日期筛选：</div></el-col>

      <el-col :span='6'>
        <el-date-picker
          size='mini'
          v-model="value2"
          type="daterange"
          align="right"
          unlink-panels
          range-separator="至"
          start-placeholder="开始日期"
          end-placeholder="结束日期"
          :picker-options="pickerOptions">
        </el-date-picker>
      </el-col>
    </el-row>
  </div>

  <div class="qf-table">
    <el-table
      :data="tableData"
      style="width: 100%">

      <el-table-column
        prop="date"
        label="日期"
        width="180">
      </el-table-column>

      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>

      <el-table-column
        prop="address"
        label="地址">
      </el-table-column>

      <el-table-column
        prop="mobile"
        label="手机">
      </el-table-column>
    </el-table>

  </div>

  <div class="qf-page">
    <el-pagination
      @size-change="sizeChange"
      @current-change="pageChange"
      :current-page="1"
      :page-sizes="[1, 2, 5, 10]"
      :page-size="100"
      layout="total, sizes, prev, pager, next, jumper"
      :total="150">
    </el-pagination>
  </div>
</div>
</template>

<script>
import { CateSelect } from '@/components/'
export default {
  components:{
    CateSelect
  },
  data: function() {
    return {
      tableData: [{
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄',
        mobile: '1000000000'
      }, {
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1517 弄',
        mobile: '1000000000'
      }, {
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1519 弄',
        mobile: '1000000000'
      }, {
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1516 弄',
        mobile: '1000000000'
      }],
      filter: {
        searchText: '' ,
        cate: ''
      },
      pickerOptions: {
        shortcuts: [{
          text: '最近一周',
          onClick(picker) {
            const end = new Date();
            const start = new Date();
            start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
            picker.$emit('pick', [start, end]);
          }
        }, {
          text: '最近一个月',
          onClick(picker) {
            const end = new Date();
            const start = new Date();
            start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
            picker.$emit('pick', [start, end]);
          }
        }, {
          text: '最近三个月',
          onClick(picker) {
            const end = new Date();
            const start = new Date();
            start.setTime(start.getTime() - 3600 * 1000 * 24 * 90);
            picker.$emit('pick', [start, end]);
          }
        }]
      },
      value2: ''
    }
    
  },
  methods: {
    // 跳转到商品新增页面
    skipToAdd() {
      this.$router.history.push('/good/add')
    },
    sizeChange(val) {
      console.log('size', val)
    },
    pageChange(val) {
      console.log('page', val)
    }
  }
}
</script>

<style lang="scss" scoped>
.qf-goodlist{
  font-size: 14px;
}
.qf-page{
  text-align: right;
  padding: 20px;
}
</style>
