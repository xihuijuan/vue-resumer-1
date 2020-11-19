<template>
  <div>
    <h2>添加学习经历</h2>
    <!-- 已经和workHistoryEditor合并为ArrayEditor -->
        <el-form>
          <div class="container" v-for="(item,index) in items">
            <el-form-item label="毕业院校">
              <el-input v-model="item.school"></el-input>
            </el-form-item>
            <el-form-item label="毕业时间">
              <el-input v-model="item.duration"></el-input>
            </el-form-item>
            <el-form-item label="学历">
              <el-input v-model="item.degree"></el-input>
            </el-form-item>
            <i class="el-icon-circle-close" v-on:click="removeItemHistory(index)"></i>
          </div>
            <el-button type="primary" v-on:click="addItemHistory">学习经历</el-button>
        </el-form>
  </div>
</template>
<script>
export default {
  props:['items'],
  methods: {
    addItemHistory(){
      this.items.push({
        school:'',
        duration:'',
        degree:''
      })
    },
    removeItemHistory(index){
      this.items.splice(index,1)
    }
  }
}
</script>