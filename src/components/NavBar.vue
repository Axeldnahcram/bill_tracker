<template>
    <ul>
        <li
            v-for="category in categories"
            :key="category">
            {{category}}
        </li>
        <li @click="triggerShowAddCategory">+</li>
    </ul>
</template>

<script>
export default {
    props: ['categories'],
    methods: {
        triggerShowAddCategory() {
            this.$emit('triggerShowAddCategory')
        }
    }
}
</script>