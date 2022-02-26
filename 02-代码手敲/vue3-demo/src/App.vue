<template>
    <div class="container">
        <h1>{{msg}}</h1>
        <button @click="say">按钮</button>
    </div>
</template>

<script>
    export default{
        name:'App',
        //1.组合API的起点，将来的组合API的代码，基本上在这里
        //2.可以理解为：在beforeCreate钩子执行前执行，组件实例创建前就执行了
        //3.因为组件实例还没创建，所以setup中不能用this,使用了也是undefined
        //4.模板中需要使用的数据和函数，需要在setup中返回(要有return,且返回的值要为对象)
        //5.setup函数中还可以传参，我们在学父子通讯时可以用到
        setup(){
            console.log('setup在beforeCreate之前执行了,且this是undefined',this);   //undefined
            //数据
            const msg = 'hi vue3'
            //函数
            const say = ()=>{
                console.log('你好啊');
            }
            return {msg,say}
            //return的值为对象，你可以往对象里面丢很多的数据和函数
        },
        beforeCreate(){
            console.log('beforeCreate',this);
        }
    }
</script>
