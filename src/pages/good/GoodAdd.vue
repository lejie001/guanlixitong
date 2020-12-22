<template>
<div class="qf-good-add">
  <div>商品新增</div>


  <div class="qf-form">
    <el-form 
    :model="info" 
    :rules="rules" 
    ref="ruleForm" 
    label-width="100px"
    >
      <el-form-item label="商品名称" prop="name">
        <el-input v-model="info.name"></el-input>
      </el-form-item>

      <el-form-item label="商品描述" prop="desc">
        <el-input type="textarea" v-model="info.desc"></el-input>
      </el-form-item>

      <el-form-item label="选择品类" prop="cate">
        <CateSelect v-model='info.cate'></CateSelect>
      </el-form-item>

      <el-form-item label="商品价格" prop="price">
        <el-input-number v-model="info.price" :min="0" label="输入价格"></el-input-number>
      </el-form-item>

      <el-form-item label="上传图片" prop="image">
        <el-upload
          action="https://jsonplaceholder.typicode.com/posts/"
          list-type="picture-card"
          :multiple='false'
          :limit='1'
        >
          <i class="el-icon-plus"></i>
        </el-upload>
        <el-dialog :visible.sync="dialogVisible">
          <img width="100%" :src="info.image" alt="img">
        </el-dialog>
      </el-form-item>



      

      <el-form-item label="是否热销" prop="hot">
        <el-switch v-model="info.hot"></el-switch>
      </el-form-item>

      <el-form-item>
        <el-button type="primary" @click="submitForm()">添加商品</el-button>
      </el-form-item>
    </el-form>
  </div>
</div>
</template>

<script>
import {CateSelect} from '@/components/'
export default {
  components: {
    CateSelect
  },
  data: function() {
    return {
      info: {
        name: '',
        desc: '',
        hot:false,
        cate: 'a',
        price: 0,
        image: '',
      },
      rules: {
        name: [
          { required: true, message: '请输入商品名称', trigger: 'blur' },
          { min: 2, max: 8, message: '长度在 2 到 8 个字符', trigger: 'blur' }
        ],
        
        desc: [
          { required: true, message: '请填写商品描述', trigger: 'blur' },
          { min: 10, max: 30, message: '长度在 10 到 30 个字符', trigger: 'blur' }
        ],

        cate: [
          { required: true, message: '请选择品类', trigger: 'change' }
        ],

        price: [
          { required: true, message: '请输入商品价格', trigger: 'blur' }
        ]
      },
      dialogVisible: false
    }
  },
  methods: {
    submitForm() {
      console.log('商品信息', this.info)
    }
  },
}
</script>

<style lang="scss" scoped>
.qf-form{
  width: 60%;
}
</style>
