<template>
    <div class="search">
        <h4>全站搜索</h4>
        <el-row :gutter="18" >
  <el-col :span="16"><el-input v-model="input" placeholder="请输入内容"></el-input></el-col>
  <el-col :span="4"><el-button type="primary" icon="search" @click="searchFn(input)">搜索</el-button></el-col>
</el-row>
    </div>
  
 
 
</template>


<script>
    import {
        mapActions
    } from "vuex"
    import action_type from "../store/action_type.js"
    export default {
        data() {
            return {
                input: ''
            }
        },
        methods: {
            ...mapActions({
                searchFn: action_type.SEARCHDATA.actions
            })
        }
    }
</script>
<style>
    .search h4 {
        text-align: center;
        color: #000;
        padding: 8px 0;
        font-weight: normal;
    }
    
    .search {
        margin-bottom: 10px;
        background: #ddd;
        padding: 5px;
        border-radius: 5px;
    }
</style>