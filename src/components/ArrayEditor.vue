<template>
  <div>
    <h2>{{title}}</h2>
        <el-form>
          <div class="container" v-for="(item,index) in items">
            <el-form-item v-for="key in keys" :label="labels[key] || key" :key="key">
              <el-input v-model="item[key]"></el-input>
            </el-form-item>
            <i class="el-icon-error" v-on:click="removeItemHistory(index)"></i>
          </div>
            <el-button type="primary" v-on:click="addItemHistory">增加经历</el-button>
        </el-form>
  </div>
</template>
<script>
export default {
  props:['items','labels','title'],
  computed:{
    keys(){
      return Object.keys(this.items[0])
    }
  },
  methods: {
    addItemHistory(){
      const empty ={}
      this.keys.map((key)=>{
        empty[key]=''
      })
      this.items.push(empty)
    },
    removeItemHistory(index){
      this.items.splice(index,1)
    }
  }
}
</script>