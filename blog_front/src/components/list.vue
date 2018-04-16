<template>
 
     <el-row class="rowall">
  <el-col :span="24" style="border-radius: 4px;">
    
    <el-row class="classrowone">
  <el-col :span="6" style="font-family:'华文新魏'">Title</el-col>
  <el-col :span="6" style="font-family:'华文新魏'">Style</el-col>
  <el-col :span="6" style="font-family:'华文新魏'">Author</el-col>
  <el-col :span="6" style="font-family:'华文新魏'">Time</div></el-col>
</el-row>

<el-row v-for="i in datalist" class="classrow">
    <router-link :to="{name:'detail',params:{id:i.id,onedata:{cnname:i.cnname_one,oneId:i.oneId,twoId:null},twodata:{cnname:i.cnname_two,oneId:i.oneId,twoId:i.twoId}}}">
         <el-col :span="6">{{i.article_name}}</el-col>
  <el-col :span="6">{{i.cnname_one}}</el-col>
  <el-col :span="6">{{i.editer}}</el-col>
  <el-col :span="6">{{i.TIME.substr(0,10)}}</div></el-col>
    </router-link>
 
</el-row>
  </el-col>
</el-row>
  

</template>

<script>
    import {
        mapState,
        mapActions
    } from "vuex"
    export default {
        name: 'header',
        data() {
            return {
                activeIndex: '1',
            }
        },
        computed: {
            ...mapState({
                datalist: (state) => state.articleList
            })
        },
        methods: {
            handleSelect(key, keyPath) {
                console.log(key, keyPath);
            }
        }

    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .classrow {
        height: 40px;
        background: #eee;
        line-height: 40px;
        margin: 10px 20px;
        border-radius: 5px;
        padding: 0 10px;
        font-size: 14px;
    }
    
    .classrowone {
        height: 40px;
        background: #ddd;
        line-height: 40px;
        margin: 10px 20px;
        border-radius: 5px;
        padding: 0 10px;
        font-family: '华文新魏'!important;
        font-weight: bold;
    }
    
    .classrowone div {
        font-family: '华文新魏'!important;
    }
    
    .rowall {
        min-height: 100%;
    }
</style>