<template>
    <div>
        <h1>Enter a new bill</h1>
        <p></p>
        <div>
            <input placeholder="Set amount" v-model="amount">
            <button @click="handleClick">Add</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'AddBill',
    data: function() {
        return {
            amount:0
        }
    },
    methods: {
        handleClick: function() {
            //we will do it later
        }
    }
}
</script>
