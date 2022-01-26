<template>
    <div class="condition-card-type">
        <div class="card-type" v-for="cardtype,i in condition_obj.cardtypes" :key="i">
            <div class="card-name">
                <div class="label-or" v-if="i != 0">
                    OR
                </div>
                <p>Type {{i+1}}</p>
            </div>
            <select name="" id="" v-model="condition_obj.cardtypes[i]">
                <option value="gold"> Gold</option>
                <option value="silver">Silver</option>
                <option value="casual">Casual</option>
            </select>
        </div>
        <button @click="addCardType()"><span class="big">+</span> Add card type</button>
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
            cleanup() {
                for (let prop in this.condition_obj) {
                    if (prop != "condition_id")
                        if (prop != "type")
                            if (prop != "cardtypes") {
                                delete this.condition_obj[prop]
                            }
                }
            },

            addCardType() {
                this.condition_obj.cardtypes.push('gold')
            }
        },

        mounted() {
            this.cleanup();
            if (this.condition_obj.cardtypes == undefined) {
                this.condition_obj.cardtypes = []
                this.addCardType()
            }
        }
    }
</script>

<style scoped>
    .card-type {
        display: flex;
        margin: 1rem 2rem;
    }

    .card-name {
        width: 160px;
    }

    .label-or {
        display: inline-block;
        border-radius: 4px;
        background-color: rgb(226, 204, 195);
        margin: 0 10px 0 0;
        padding: 6px 3px;
        height: 2rem;
        width: 2rem;
    }

    .card-name>p {
        display: inline-block;
    }

    select {
        width: 400px;
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

    button:hover {
        background-color: yellowgreen;
        ;
        color: white;
        cursor: pointer;
    }
</style>