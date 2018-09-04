<template>
    <div>
        <el-table
                :data="tableData"
                style="width: 100%">
            <el-table-column
                    prop="shop"
                    label="平台店铺"
                    width="180">
            </el-table-column>
            <el-table-column
                    prop="abshop"
                    label="店铺简称"
                    width="180">
            </el-table-column>
            <el-table-column
                    prop="account"
                    label="平台账号"
                    width="180">
            </el-table-column>
            <el-table-column
                    label="数据同步"
                    width="180">
                <template slot-scope="scope">
                    <img src='../assets/targetOn.png' width="20" height="20" v-if="!!scope.row.value3 && scope.row.system_state"
                         :title="`远程订单${get_title(scope.row.value3,'value3')}抓取一次`" />
                    <img src='../assets/targetOff.png' width="20" height="20" v-else title="远程订单功能未开启" />
                    <img src='../assets/syncOn.png' width="20" height="20" v-if="!!scope.row.value4 && scope.row.system_state"
                         :title="`同步发货${get_title(scope.row.value4,'value4')}同步一次`" />
                    <img src='../assets/syncOff.png' width="20" height="20" v-else title="同步发货功能未开启" />
                    <img src='../assets/downloadOn.png' width="20" height="20" v-if="!!scope.row.value5 && scope.row.system_state"
                         :title="`抓取远程刊登数据${get_title(scope.row.value5,'value5')}一次`" />
                    <img src='../assets/downloadOff.png' width="20" height="20" v-else title="抓取远程刊登数据未开启" />
                </template>
            </el-table-column>
            <el-table-column
                    label="系统状态"
                    width="180">
                <template slot-scope="scope">
                    <el-switch
                            v-model="scope.row.system_state"
                            active-text="已启用"
                            inactive-text="已停用"
                            active-color="#13ce66">
                    </el-switch>
                </template>
            </el-table-column>
            <el-table-column
                    label="操作"
                    width="180">

                <template slot-scope="scope">
                    <el-button type="text" size="mini"
                               @click.native="look_up(scope.row)">查看
                    </el-button>

                    <el-button type="text" size="mini"
                               @click.native="handleEdit(scope.row)">编辑
                    </el-button>

                    <el-button type="text" size="mini"
                               @click.native.prevent="delete_row(scope.$index, tableData)">移除
                    </el-button>
                </template>
            </el-table-column>
        </el-table>

    </div>
</template>

<script>
    export default {
        name: "table-data",
        methods:{
            get_title(row,type){
                this.$emit('get-title',row,type)
            },
            look_up(row){
                this.$emit('look-up',row);
            },
            handleEdit(row){
                this.$emit('handle-edit',row);
            },
            delete_row(index,rows){
                this.$emit('delete-row',index,rows)
            },
        },
        props:{
            tableData:{},
            addEditform:{},
        },

    }
</script>

<style scoped>

</style>