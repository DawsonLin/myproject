<template>
    <div>
        <div>{{send}}</div>
        <div>
            <h1>子组件的内容</h1>
            <button @click="spot">Click me</button>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return {
            }
        },
        props:{
            send:'',
        },
        methods:{
          spot(){
              this.$emit('spot','子组件给父组件传数据')
          }
        }
    }
</script>

<style scoped>

</style>