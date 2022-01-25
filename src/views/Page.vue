<template>
    <div class="page">
        <ul class="page-nav">
            <li class="page-nav-item">
                Parameters
            </li>
            <li class="page-nav-item">
                Questions
            </li>
            <li class="page-nav-item">
                Logic
            </li>
            <li class="page-nav-item">
                Conditions
            </li>
            <li class="page-nav-item">
                Respondents
            </li>

        </ul>
        <div class="main">
            <p class="secondary-info"> Add poll </p>
            <div class="conditions-list">
                <transition-group name="list">


                    <condition-component class="condition" v-for="condition, i in conditions" :key="i" :position=i
                        :condition=condition :bgcolor=colors[i%colors_len] @deleted=deleteCondition />
                </transition-group>
            </div>
            <div class="huge-add-button" @click="addCondition()">
                <h1>+</h1>
                <p>
                    Click here to add new condition.
                </p>
                <p>
                    All the conditions are binded together with logical "AND".
                </p>
            </div>
            <div class="page-footer">
                <button class="button-test"> Test question</button>
                <button @click="submitCondition" class="button-next"> Next -></button>
            </div>
        </div>
    </div>
</template>

<script>
    import ConditionComponent from "../components/ConditionComponent.vue";
    import axios from 'axios'


    export default {
        components: {
            ConditionComponent
        },
        data() {
            return {
                conditions: [],
                condition_id: 0,
                colors: [
                    ['hsl(68, 51%, 95%)', 'hsl(68, 51%, 80%)'],
                    ['hsl(100, 51%, 95%)', 'hsl(100, 51%, 80%)'],
                    ['hsl(181, 51%, 95%)', 'hsl(181, 51%, 80%)'],
                ]
            }
        },
        computed: {
            colors_len() {
                return this.colors.length
            }
        },
        methods: {
            addCondition() {
                this.condition_id++
                this.conditions.push({
                    condition_id: this.condition_id,
                    type: 'none'
                })
            },


            deleteCondition(condition_obj) {
                let index = this.conditions.findIndex(element => {
                    if (element.condition_id === condition_obj.condition_id) {
                        return true;
                    }
                })
                this.conditions.splice(index, 1)

            },
            async submitCondition() {
                let cond = JSON.parse(JSON.stringify(this.conditions))
                for (let i = 0; i < cond.length; i++) {
                    delete cond[i]["condition_id"]
                    if (cond[i]["type"] == "none") {
                        delete cond[i]
                    }
                }

                console.log(JSON.stringify(cond))
                await axios.post('api-endpoint', cond)
                    .catch(error => console.log(error))
                // actually that's it within given requirements )
            }
        }
    }
</script>
<style scoped>

    .page {
        margin: 2.5rem auto;
        max-width: 1200px;

    }
    .page-nav {
        list-style-type: none;
        display: flex;
        justify-content: space-evenly;
        padding: 0;
    }
    .page-nav-item {
        font-size: 1rem;
        margin: 0 10px;
        width: 100px;
        height: 30px;
        border-bottom: 3px solid transparent;
        text-align: center;
        flex-grow: 1;
        color: green;
    }
    .page-nav-item:hover {
        font-weight: 600;
        cursor: pointer;
        border-bottom: 3px solid rgb(189, 238, 144);
        margin-bottom: 0;
        color: black;
    }
    .main {
        border-top: rgb(189, 238, 144) 2px solid;
        box-shadow: 0px 10px 10px rgb(148, 148, 148);
        padding-bottom: 1px;
        /* likely bug*/
    }
    .secondary-info {
        color: rgb(170, 170, 170);
        font-size: 0.8rem;
        font-weight: 600;
        margin: 1rem 0;
        padding-left: 2rem;
    }
    .huge-add-button {
        border: 2px solid lightgrey;
        border-radius: 4px;
        text-align: center;
        padding: 1rem;
        color: green;
        margin: 2rem;
        transition: all cubic-bezier(0.075, 0.82, 0.165, 1) 0.2s;
    }
    .huge-add-button:hover {
        cursor: pointer;
        background-color: rgb(189, 238, 144);
    }

    .page-footer {
        display: flex;
        justify-content: space-between;
        padding: 2rem;
        background-color: rgb(221, 232, 243);
    }
    .page-footer>button {
        height: 2rem;
        width: 10rem;
        border-radius: 4px;
        font-weight: 600;
    }
    .button-next {
        background-color: green;
        color: white;
        border: 2px solid green;
        transition: all cubic-bezier(0.075, 0.82, 0.165, 1) 0.2s;
    }

    .button-next:hover {
        cursor: pointer;
        background-color: yellowgreen;
        

    }

    .button-test {
        background-color: rgb(255, 255, 255);
        color: green;
        border: 1px solid rgb(221, 221, 221);
        transition: all cubic-bezier(0.075, 0.82, 0.165, 1) 0.2s;
    }

    .button-test:hover {
        cursor: pointer;
        background-color: green;
        color: white;
        border: 1px solid rgb(221, 221, 221)
    }
</style>