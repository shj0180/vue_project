
<script lang="ts">
    import { ref, reactive, toRefs, watch, watchEffect } from 'vue'

    export default {
        setup() {
            
            // 
            const age = ref(0)
            function add(){
                age.value ++
            }
            watch(age, (newval, oldval) => {
                console.log('newval', newval)
                console.log('oldval', oldval)

            })

            const sunwukong = reactive({
                pname: '孙悟空',
                sage: 500,
                skill: '变'
            })
            let {pname, sage, skill} = toRefs(sunwukong)
            watchEffect(()=>{
                console.log(sunwukong.sage)
            })

            // watch(sunwukong.sage, (newval, oldval) => {
            //     console.log('newval', newval)
            //     console.log('oldval', oldval)

            // })

            return {
                count: age, add,
                pname, sage, skill,
            }


        }
    }

</script>

<template>
    <div>
       <div>{{count}}</div>
       <button @click="add">add</button>

       <div> {{pname}} is {{sage}} and his skill is {{skill}}</div>
        <button @click="sage++">add</button>

    </div>
</template>



