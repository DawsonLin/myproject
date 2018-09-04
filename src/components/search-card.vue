<template>
    <div id="app">
        <el-card class="text">
            <el-row style="float:left">
                <small>状态：</small>
                <el-radio-group size="mini" v-model="searchData.radio3" @change="change_status">
                    <el-radio-button label="">全部</el-radio-button>
                    <el-radio-button :label='true'>已启用</el-radio-button>
                    <el-radio-button :label="false">已停用</el-radio-button>
                </el-radio-group>

                <small>授权状态：</small>
                <el-select size="mini" style="width:100px"
                           v-model="searchData.value2"
                           placeholder="全部">
                    <el-option
                            v-for="item in options"
                            :key="item.value"
                            :label="item.label"
                            :value="item.value">
                    </el-option>
                </el-select>
                <br><br>

                <el-select style="width:100px"
                           size="mini"
                           v-model="searchData.value1">
                    <el-option
                            v-for="item in selectList"
                            :key="item.value"
                            :label="item.label"
                            :value="item.value">
                    </el-option>
                </el-select>

                <el-input size="mini" v-model.trim="searchData.input" style="width:150px" placeholder="请输入简称" clearable></el-input>

                <el-button size="mini" type="primary" @click.native="search_data">搜索</el-button>

                <el-button size="mini" type="info" plain disabled>还原/修改</el-button>

                <el-button size="mini" type="warning" @click.native="clear">清空条件</el-button>

            </el-row>
        </el-card>
    </div>
</template>
<style type="text/css">
    .text{
        text-align:left;
        margin-bottom:10px;
        margin-top:0px;
        padding-bottom:20px;
    }

</style>
<script>
    export default {
        name: "search-card",
        data(){
            return {
                options:[{
                    value: 0,
                    label: '未授权'
                }, {
                    value: 1,
                    label: '已授权'
                }, {
                    value: 2,
                    label: '全部'
                }],
                selectList:[
                    {value: 0, label: '店铺简称'},
                    {value: 1, label: '账号'},
                    {value: 2, label: '账号简称'},
                ],
            }
        },
        methods:{
            change_status(val){
                this.$emit('change_status',val)
            },
            search_data(){
                this.$emit('search-data')
            },
            clear(){
                this.$emit('clear')
            },
        },
        props:{
            searchData:{},

        },

    }
</script>