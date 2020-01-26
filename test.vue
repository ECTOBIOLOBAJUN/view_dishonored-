<template>
    <div id="app-6">
        <testname
        v-bind:test6 ='changer'
        />
              </div>
</template>

<script>
    import  testname from '@/components/test2'
    export default {
        name: "test",
        data() {
            return {
                changer :[
                    {title:'eu',price:99},
                    {title:'dollar',price:123}
                ]
            }

        },
        components:{
            testname
        }
    }
</script>

<style scoped>

</style>