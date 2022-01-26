<template>
    <div class="condition" :id="uuid">
        <div class="label-and" v-if="position != 0">
            AND
        </div>
        <div class="condition-select">
            <h4 class="condition-num">
                Condition {{position+1}}
            </h4>
            <select v-model="condition_obj.type" class="condition-type-select">
                <option value="none" disabled> Select condition type</option>
                <option value="age"> Age of respondent</option>
                <option value="card-type"> Loyality card type</option>
                <option value="card-status"> Loyality card status</option>
            </select>
        </div>
        <component :is="condition_obj.type + '-condition-component'" :condition=condition></component>
        <div class="button-line">
            <button @click="del()" class="delbutton">delete condition</button>
        </div>
    </div>
</template>

<script>
    import AgeConditionComponent from './conditions/AgeConditionComponent.vue'
    import CardTypeConditionComponent from './conditions/CardTypeConditionComponent.vue'
    import CardStatusConditionComponent from './conditions/CardStatusConditionComponent.vue'
    
    let uuid = 0
    export default {
        props: [
            'position', 
            'condition', 
            'bgcolor'
            ],

        emits: [
            'deleted'
            ],

        beforeCreate() {
            this.uuid = uuid.toString();
            uuid += 1;
        },

        computed: {
            condition_obj() {
                return this.condition
            }
        },

        methods: {
            del() {
                this.$emit('deleted', this.condition_obj)
            }
        },

        mounted() {
            let instance = document.getElementById(this.uuid)
            let bodyStyles = instance.style;
            bodyStyles.setProperty('--primary-color', this.bgcolor[0]);
            bodyStyles.setProperty('--secondary-color', this.bgcolor[1]);
        },

        components: {
            AgeConditionComponent,
            CardTypeConditionComponent,
            CardStatusConditionComponent,
        }

    }
</script>
<style scoped>
    select {
        background-color: white;
        height: 2rem;
        border-radius: 4px;
        border: 2px lightgray solid;
    }

    .condition {
        border-top: 1px solid lightgrey;
        min-height: 150px;
        padding-bottom: 1px;
        display: flex;
        flex-direction: column;
        background-color: var(--primary-color);
    }

    .label-and {
        width: 3rem;
        height: 2rem;
        position: relative;
        padding: 6px;
        margin: -20px 0 0 3rem;
        background-color: inherit;
        border-radius: 4px;
        background-color: var(--secondary-color);
    }

    .condition-select {
        display: flex;
        justify-content: space-between;
        margin: 1rem 2rem;
        flex-grow: 1;
    }

    .condition-num {
        width: 140px;
        font-size: 0.8rem;
    }

    .condition-type-select {
        flex-grow: 1;
    }

    .button-line {
        display: flex;
    }

    .delbutton {
        margin: -3rem 2rem 2rem auto;
        height: 2rem;
        background-color: transparent;
        color: tomato;
        border: 2px solid tomato;
        border-radius: 4px;
        position: relative;
    }

    .delbutton:hover {
        background-color: tomato;
        color: white;
        cursor: pointer;
    }
</style>