<template>
    <div class="condition-age">
        <div class="range" v-for="range,i in condition_obj.ranges" :key="i">
            <div class="range-name">
                <div class="label-or" v-if="i != 0">
                    OR
                </div>
                <p>Range {{i+1}}</p> 
                </div>

            <div class="range-input">
                from <input type="text" name="" id="" v-model="range['min']">
                to <input type="text" name="" id="" v-model="range['max']">
            </div>

        </div>
        <button @click="addRange()"> <span class="big">+</span> Add range</button>


    </div>
</template>

<script>
    export default {

        props: ['condition'],

        computed: {
            condition_obj() {
                return this.condition
            }
        },
        methods: {
             cleanup(){
                for (let prop in this.condition_obj){
                    if(prop != "condition_id")
                      if(prop != "type")
                      if (prop !="ranges"){
                        delete this.condition_obj[prop]
                    }
                }
            },

            addRange() {
                    this.condition_obj.ranges.push({
                    'min': '',
                    'max': ''
                })
                
            }
        },
        mounted() {
            this.cleanup()
            if (this.condition_obj.ranges == undefined)
            {   
                this.condition_obj.ranges = []
                this.addRange()
            }

        },
    }
</script>
<style scoped>
    .range {
        display: flex;
        margin: 1rem 2rem;
    }

    .range-name {
        width: 160px;
    }

    .range-input {
        align-items: left;
    }
    .label-or{
        display: inline-block;
        border-radius: 4px;
        background-color: rgb(226, 204, 195);
        margin: 0 10px 0 0;
        padding: 6px 3px;
        height: 2rem;
        width: 2rem;
    }
    .range-name >p{
        display: inline-block;
    }

    input {
        width: 100px;
        background-color: white;
        height: 2rem;
        border-radius: 4px;
        border: 2px lightgray solid;
    }

    button {
        margin: 2rem 2rem 1rem calc(140px + 2rem);
        margin-bottom: 1rem;
        height: 2rem;
        width: 10rem;
        background-color: white;
        color: yellowgreen;
        border: 2px solid yellowgreen;
        border-radius: 4px;
        font-weight: 600;
    }
    button>text{
        margin: auto;
    }

    button:hover {
        background-color: yellowgreen;
        ;
        color: white;
        cursor: pointer;
    }
</style>