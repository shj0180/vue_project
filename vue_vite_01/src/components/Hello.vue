
<script lang="ts">
    import { ref, reactive, toRefs, watch } from 'vue'

    export default {
        setup() {
            const count = ref(0)
            function add(){
                count.value += 2
            }

            const obj = reactive({
                name: 'zhangsan',
                age: 18,
                child: {
                    name: 'xiaozhang',
                    age: 3
                }
            })
            function change(){
                obj.age = 20
            }

            // 解构
            // 一种直接 ...toRefs(obj),  
            let {name, age, child} = toRefs(obj)

            // ES扩展运算符... 解构出来的对象属性没响应式；
            // 需要借助toRefs

            return {
                count,
                add,
                // ...toRefs(obj),  
                change,
                name, age, child

            }


        }
    }

</script>

<template>
    <div>
        hello, setup
        <br>
        {{ count }}
        <button @click="add" >add</button>
        <hr>
        <div>
            {{name}} - {{ age }}
            <button @click=" change">change</button>
            <hr>
            <div >{{ child.name }} - {{ child.age }}</div>
            

        </div>

    </div>
</template>



