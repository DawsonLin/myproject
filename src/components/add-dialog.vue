<template>
    <div>
        <el-button style="float:left" size="mini" type="primary" @click.native="add_data">添加</el-button>
        <el-dialog title="添加店铺：" :visible.sync="addDialog">
            <el-form :model="addEditform" label-width="200px" class="width-editform">
                <el-form-item label="* 平台账号：" >
                    <el-input class="width-default"  v-model="addEditform.account" auto-complete="off"></el-input>
                </el-form-item>
                <el-form-item label="* 平台店铺：" >
                    <el-input class="width-default" v-model="addEditform.shop" auto-complete="off"></el-input>
                </el-form-item>
                <el-form-item label="* 店铺简称：" >
                    <el-input class="width-default" v-model="addEditform.abshop" auto-complete="off"></el-input>
                </el-form-item>
                <el-form-item label="商户ID：">
                    <el-input class="width-default" v-model="addEditform.shopID" auto-complete="off"></el-input>
                </el-form-item>
                <el-form-item label="抓取Listing数据：">
                    <el-select size="medium"
                               v-model="addEditform.value3"
                               placeholder="请选择">
                        <el-option
                                v-for="item in timeList"
                                :key="item.value"
                                :label="item.label"
                                :value="item.value">
                        </el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="抓取Joom订单功能：">
                    <el-select size="medium"
                               v-model="addEditform.value4"
                               placeholder="请选择">
                        <el-option
                                v-for="item in orderFunction"
                                :key="item.value"
                                :label="item.label"
                                :value="item.value">
                        </el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="同步发货状态到Joom功能：">
                    <el-select size="medium"
                               v-model="addEditform.value5"
                               placeholder="请选择">
                        <el-option
                                v-for="item in orderFunction"
                                :key="item.value"
                                :label="item.label"
                                :value="item.value">
                        </el-option>
                    </el-select>
                </el-form-item>
            </el-form>
            <div slot="footer" class="dialog-footer">
                <el-button @click="addDialog = false">取 消</el-button>
                <el-button type="primary" @click="submit">确 定</el-button>
            </div>
        </el-dialog>
    </div>
</template>

<style type="text/css">
    .width-editform{
        width:50%;
    }
</style>

<script>
    export default {
        name: "add-dialog",
        data(){
            return {
                addDialog:false,
                timeList:[],
                orderFunction:[],
            }
        },
        methods: {
            add_data(){
                this.addDialog = true;
            },
            submit(){
                this.$emit('submit')
            },
        },
        props: {
            addEditform:{},
            timeList:{type: Array,},
            orderFunction:{type: Array},

        },
    }
</script>

<style scoped>

</style>