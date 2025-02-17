<script setup>
    import {ref, defineEmits} from 'vue'
    const text = ref('')
    const amount = ref('')

    const emit = defineEmits([
        'transactionSubmitted'
    ])

    const onSubmit = ()=>{
        const transactionsData = {
            text: text.value,
            amount: parseFloat(amount.value),
        }

        emit('transactionSubmitted', transactionsData)

        text.value = ''
        amount.value = ''
    }

</script>

<template>
    <h3>Add a new Transaction</h3>
    <form id="form" @submit.prevent="onSubmit">
    <div class="form-control">
        <label for="text">Enter Transaction</label>
        <input type="text" id="text" v-model="text" placeholder="Enter Transaction...">
    </div>
    <div class="form-control">
        <label for="amount">Enter Transaction Amount</label>
        <input type="text" id="amount" v-model="text" placeholder="Enter Negative Value for Expenses">
    </div>
    <button class="btn">Add Transaction</button>
    </form>
</template>