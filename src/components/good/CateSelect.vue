<template>
    <div class="qf-cate-select">
        <el-select v-model="cate" 
            placeholder="请选择品类" 
            :clearable=true
            @change="$emit('input',cate)"
            :size='size'
        >
          <el-option
            v-for="item in cateArr"
            :key="item.id"
            :label="item.cate_zh"
            :value="item.cate">
          </el-option>
        </el-select>
    </div>
</template>

<script>
export default {
    props: {
        value: {
            type: String,
            required: false,
            default: ''
        },
        size: {
            type: String,
            required: false,
            default: 'medium'
        }
    },
    data: function() {
        return {
            cate: '',
            cateArr: [
                { id: 1, cate: 'a', cate_zh: '汽车用品' },
                { id: 2, cate: 'b', cate_zh: '母婴用品' },
                { id: 3, cate: 'c', cate_zh: '汽车用品' },
                { id: 4, cate: 'd', cate_zh: '汽车用品' },
                { id: 5, cate: 'e', cate_zh: '汽车用品' }
            ],
        }
    }
}
</script>

<style lang="css" scoped>

</style>