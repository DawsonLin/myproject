<template>
    <div>
        <!--查看-->
        <!--<el-dialog title="查看账户：" :visible.sync="lookDialog">-->
            <!--<el-form :model="addEditform" label-width="100px">-->
                <!--<el-form-item class="width-default" label="平台账号:" >-->
                    <!--<el-input v-model="addEditform.account" auto-complete="off"></el-input>-->
                <!--</el-form-item>-->
                <!--<el-form-item class="width-default" label="平台店铺:">-->
                    <!--<el-input v-model="addEditform.shop" auto-complete="off"></el-input>-->
                <!--</el-form-item>-->
                <!--<el-form-item class="width-default" label="店铺简称:">-->
                    <!--<el-input v-model="addEditform.abshop" auto-complete="off"></el-input>-->
                <!--</el-form-item>-->
                <!--<el-form-item class="width-default" label="商户ID:">-->
                    <!--<el-input v-model="addEditform.shopID" auto-complete="off"></el-input>-->
                <!--</el-form-item><br><br>-->
            <!--</el-form>-->
            <!--<div slot="footer" class="dialog-footer">-->
                <!--<el-button @click="lookDialog = false">取 消</el-button>-->
                <!--<el-button type="primary" @click="update">确 定</el-button>-->
            <!--</div>-->
        <!--</el-dialog>-->
        <!--查看和编辑框-->
        <el-dialog :title="isLook?'查看账户':'编辑账户'" :visible.sync="lookEditDialog" @close="close">
            <el-form :model="addEditform" class="width-editform" label-width="100px" :disabled="isLook">
                <el-form-item label="* 平台账号：">
                    <el-input v-model="addEditform.account" auto-complete="off" disabled></el-input>
                </el-form-item>
                <el-form-item label="* 平台店铺：">
                    <el-input v-model="addEditform.shop" auto-complete="off"></el-input>
                </el-form-item>
                <el-form-item label="* 店铺简称：">
                    <el-input v-model="addEditform.abshop" auto-complete="off"></el-input>
                </el-form-item>
                <el-form-item label="商户ID:">
                    <el-input v-model="addEditform.shopID" auto-complete="off"></el-input>
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
                <el-button @click="cancel">取 消</el-button>
                <el-button type="primary" @click="update">确 定</el-button>
            </div>
        </el-dialog>
    </div>
</template>
<style type="text/css">
    .width-editform{
        width:60%;
    }
</style>

<script>
    export default {
        name: "edit-dialog",
        data(){
            return {
                lookEditDialog: false,
            }
        },
        methods: {

            update(){
                this.$emit('update');
            },
            cancel(){
                this.$emit('cancel');
            },
            update(){
                this.$emit('update');
            },
            close(){
                this.$emit('close')
            }


        },
        watch:{
            // lookEditDialog(val){
            //     this.$emit('input',val);
            // },
            // value(val){
            //     this.lookEditDialog = val;
            // },
        },
        props: {
            addEditform:{},
            lookEditDialog: {
                type: Boolean
            },
            isLook:{
                type:Boolean
            },
            timeList:{type: Array},
            orderFunction:{type: Array},
        },
    }
</script>
