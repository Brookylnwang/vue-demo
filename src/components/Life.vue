<template>
    <div id="life">
        生命周期函数演示   ---{{ msg }}--{{ homemsg }}
        <h2>{{ title }}</h2>
        <button @click="setMsg()">点击改变数据</button>
        <button @click="run()">运行父组件</button>
    </div>
</template>
<script>
export default {
    data() {
        return{ 
            msg: '我是子组件'
        }
    },
    methods: {
        setMsg() {
            this.msg='我是改变后的数据'
        }
    },
    props: ['title', 'homemsg', 'run']
    /*beforeCreate() {
        console.log('实例创建之前')
    },
    created() {
        console.log('实例创建之后')
    },
    beforeMount() {
        console.log('模板编译之前')
    },
    mounted() {
        console.log('模板编译完成')
    },
    beforeUpdate() {
        console.log('数据更新之前')
    },
    updated() {
        console.log('数据更新完毕')
    },
    beforeDestroy() {
        console.log('数据销毁之前')
    },
    destroyed() {
        console.log('数据销毁之后')
    }*/
}
</script>