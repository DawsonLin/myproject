<template>
    <div>{{send}}
        <input v-model="send" type="text">
        <child :send="send" @spot="spot"></child>
    </div>
</template>

<script>
    import child from './child.vue'
    export default {
        data(){
            return {
                send:'',
            }
        },
        methods:{
            spot(row){
                console.log(row)
            }
        },
        components:{
            child
        },
    }
</script>

<style scoped>

</style>