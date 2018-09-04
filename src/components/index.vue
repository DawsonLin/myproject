<template>
    <div>
        <search-card :search-data="searchData" @change_status="change_status" @search-data="search_data"
        @clear="clear"></search-card>
        <add-dialog :add-editform="addEditform" :time-list="timeList" :order-function="orderFunction"
        @submit="submit"></add-dialog>
        <edit-dialog @update = update @cancel='cancel' :add-editform="addEditform" :is-look="addEditform.isLook"
                     :look-edit-dialog="lookEditDialog" :time-list="timeList" :order-function="orderFunction"
                     @close="close"></edit-dialog>
        <table-data :table-data="tableData" @look-up="look_up" @handle-edit="handle_edit" @get-title="get_title"
        @delete-row="delete_row"></table-data>
    </div>
</template>

<script>
    import searchCard from './search-card.vue'
    import addDialog from './add-dialog.vue'
    import editDialog from './edit-dialog.vue'
    import tableData from './table-data.vue'
    export default {
        name: "index",
        data(){
            return {
                lookEditDialog:false,
                searchData:{
                    radio3:'',
                    value1:0,
                    value2:'',
                    input:'',
                },
                addEditform:{
                    account:'',
                    shop:'',
                    abshop:'',
                    shopID:'',
                    value3:'',
                    value4:'',
                    value5:'',
                    isLook:'',
                },
                tableData:[],
                addDialog:false,
                lookDialog:false,
                editDialog:false,
                dialogTableVisible: false,
                dialogFormVisible: false,
                shops: '',
                state1: '',
                value: '',
                originData: [
                    {
                        shop: 'DawsonAliexpress',
                        abshop: 'DawsonAli',
                        account: 'Dowson',
                        data_sync: '',
                        value3:1,
                        value4:2,
                        value5:1,
                        system_state: true,
                        opera: '操作'
                    }, {
                        shop: 'Amason',
                        abshop: 'Ama',
                        account: 'Mary',
                        value3:1,
                        value4:2,
                        value5:1,
                        data_sync: '',
                        system_state: true,
                        opera: '操作'

                    }, {
                        shop: 'BigEbay',
                        abshop: 'baby',
                        account: 'Jay',
                        data_sync: '',
                        value3:1,
                        value4:2,
                        value5:1,
                        system_state: true,
                        opera: '操作'
                    }
                ],

                timeList: [
                    {value: 0, label: '未启用'},
                    {value: 1, label: '1小时'},
                    {value: 2, label: '2小时'},
                    {value: 3, label: '3小时'},
                    {value: 4, label: '5小时'},
                    {value: 5, label: '6小时'},
                    {value: 6, label: '8小时'},
                    {value: 7, label: '12小时'},
                    {value: 8, label: '24小时'},
                ],
                orderFunction: [
                    {value: 0, label: '未启用'},
                    {value: 1, label: '15分钟'},
                    {value: 2, label: '30分钟'},
                    {value: 3, label: '60分钟'},
                ],


            }
        },
        mounted(){
            this.tableData = this.originData;
        },
        methods:{
            delete_row(index,rows){
                rows.splice(index,1);
            },
            get_title(row,type){
                let list= type===this.addEditform.value3? this.timeList:this.orderFunction;
                let find= list.find(res=>res.value===row);
                if(find)return find.label
            },

            clear(){
                this.searchData.radio3='';
                this.searchData.value2='';
                this.searchData.input='';
                this.searchData.value1='';
            },
            search_data(){
                this.tableData=this.originData.filter(row=>
                this.searchData.radio3===''?row:row.system_state===this.searchData.radio3).filter(row=>
                this.searchData.input===''?row:row.abshop.includes(this.searchData.input))
            },
            submit(){
                let find = this.tableData.find(row=>row.account === this.addEditform.account);
                if(find) return this.$message({type:"warning",message:"平台账号重复，请修改"});
                console.log(this.addEditform,'this.addEditform');
                this.tableData.unshift(this.addEditform);
                this.addDialog = false;
            },
            update(){
                this.lookEditDialog = false;
            },
            cancel(){
                this.lookEditDialog = false;
            },
            look_up(row){
                console.log(row);
                this.lookEditDialog = true;
                this.addEditform = row;
                this.addEditform.isLook=true;

            },
            close(){
              this.lookEditDialog = false
            },

            handle_edit(row){
                this.lookEditDialog = true;
                this.addEditform.isLook = false;
                this.addEditform = row;

            },
            change_status(val){
                this.tableData=this.originData.filter(row=> val===''?row:row.system_state===val)
            },
        },
        components: {
            searchCard,
            addDialog,
            editDialog,
            tableData
        },
    }
</script>