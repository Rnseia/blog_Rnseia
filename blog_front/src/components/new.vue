<template>
   <el-row class="rowall">
  <el-col :span="24" style="border-radius: 4px;">
    
    <el-row class="classrowone">
 最新文章
</el-row>
<el-row v-for="(i,index) in datalist" class="classrow" :span="24">
    <el-col :span="2" class="classrow1">☛</el-col>
  <el-col :span="14" class="classrow2">{{i.article_name}}</el-col>
  
  <el-col :span="6" class="classrow3">{{i.TIME}}</div></el-col>
</el-row>
  </el-col>
</el-row>
 
</template>


<script>
    import {
        mapActions,
        mapState
    } from "vuex"
    export default {
        data() {
            return {

            }
        },
        computed: {
            ...mapState({
                datalist: (state) => state.newlist
            })
        }
    }
</script>
<style scoped>
    .rowall {
        background: #ddd;
        padding: 5px;
        border-radius: 5px;
    }
    
    .classrowone {
        text-align: center;
        color: #000;
        padding: 8px 0;
        font-weight: normal;
    }
    
    .classrow {
        margin: 5px 0;
    }
    
    .classrow1 {
        width: 26px;
        height: 20px;
        text-align: center;
        line-height: 15px;
        color: crimson;
        margin-right: 10px;
        font-size: 16px;
    }
    
    .classrow2 {
        margin-right: 10px;
        font-size: 13px;
    }
    
    .classrow3 {
        font-size: 13px;
    }
</style>