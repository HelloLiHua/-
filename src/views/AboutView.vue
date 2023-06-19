<template>
  <div class="about">
    <el-row>
      <el-col :span="8">
        <el-input v-model="inmessage" placeholder="请输入内容"></el-input>
      </el-col>
      <el-col :span="8">
        <el-button type="danger" @click="encrypt">加密</el-button>
        <el-button type="success" @click="decrypt">解密</el-button>
      </el-col>
      <el-col :span="8">
        <span>{{outmessage}}</span>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  data(){
    return{
      inmessage:undefined,
      outmessage:undefined
    }
  },
  methods:{
    encrypt(){
      let result = this.inmessage.split('')
      result.forEach((item,index,arr)=>{
        arr[index]=item.charCodeAt()
        arr[index] = arr[index] + 3
        arr[index] = String.fromCharCode(arr[index].toString())
      })
      result=result.join('')
      this.outmessage=result
    },
    decrypt(){
       let result = this.inmessage.split('')
        result.forEach((item, index, arr) => {
            arr[index] = item.charCodeAt()
            arr[index] = arr[index] - 3
            arr[index] = String.fromCharCode(arr[index].toString())
        });
        result = result.join('')
        this.outmessage = result
    }
  }
}
</script>
<style scoped>
.el-row{
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
