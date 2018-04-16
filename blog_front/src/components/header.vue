<template>
    <nav>
        <h2 class="myTitle">小池同学个人博客<b style="color:crimson;">❤</b></h2>
        <el-menu theme="dark" :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
     
    <!--<el-menu-item index="1"></el-menu-item>-->

    <el-submenu v-for="(i,index) in datalist" :index="i.onedata.id" >
       
        <template slot="title">{{i.onedata.cnname}}</template>
<el-menu-item v-for="(j,index2) in i.twodata" :index="j.id">{{j.cnname}}</el-menu-item>

</el-submenu>
<!--<el-menu-item index="3"><a href="https://www.ele.me" target="_blank">订单管理</a></el-menu-item>-->
</el-menu>
</nav>

</template>

<script>
    import {
        mapState,
        mapActions
    } from "vuex"
    import action_type from "../store/action_type"
    export default {
        name: 'header',
        data() {
            return {
                activeIndex: '1',
            };
        },
        computed: {
            ...mapState({
                datalist: (state) => state.headData
            })
        },
        methods: {
            ...mapActions({
                changeList: action_type.HEADCHANGEDATA.actions,
                // 二级分类点击后改变面包屑数组
                headbreadList: action_type.HEADBREADDATA.actions
            }),
            handleSelect(key, keyPath) {
                // console.log(key)
                this.changeList(key)
                this.datalist.forEach(function(i) {
                    i.twodata.forEach(function(j) {
                        if (j.id == key) {
                            console.log(j)
                            var arr = [{
                                    cnname: i.onedata.cnname,
                                    oneId: i.onedata.id,
                                    twoId: null
                                }, {
                                    cnname: j.cnname,
                                    oneId: j.parent_id,
                                    twoId: j.id
                                }]
                                // console.log(arr)
                            this.headbreadList(arr)
                        }
                    }.bind(this))
                }, this);

            }
        },
        mounted() {
            console.log(this.datalist)
        }

    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
    .myTitle {
        font-size: 26px;
        font-weight: normal;
        margin: 20px;
    }
    
    .el-menu--dark {
        background: url("/static/navbg.jpg") no-repeat;
    }
    
    .el-menu--horizontal.el-menu--dark .el-submenu .el-submenu__title {
        color: #000;
    }
    
    .el-menu--horizontal.el-menu--dark .el-submenu__title:hover {
        background: url("/static/navbg.jpg") no-repeat;
        border-bottom: 5px solid #666!important;
    }
    
    .el-menu--horizontal>.el-menu-item:hover,
    .el-menu--horizontal>.el-submenu.is-active .el-submenu__title,
    .el-menu--horizontal>.el-submenu:hover .el-submenu__title {
        border-bottom: 5px solid #666!important;
    }
    
    .el-menu--horizontal.el-menu--dark .el-submenu .el-menu-item.is-active,
    .el-menu-item.is-active {
        color: crimson!important;
    }
    
    .index {
        width: 1000px;
        margin: 0 auto;
    }
    
    .el-row {
        margin-bottom: 20px;
        &:last-child {
            margin-bottom: 0;
        }
    }
    
    .el-col {
        border-radius: 4px;
    }
    
    .bg-purple-dark {
        background: #99a9bf;
    }
    
    .bg-purple {
        background: #d3dce6;
    }
    
    .bg-purple-light {
        background: #e5e9f2;
    }
    
    .grid-content {
        border-radius: 4px;
        min-height: 36px;
    }
    
    .row-bg {
        padding: 10px 0;
        background-color: #f9fafc;
    }
</style>