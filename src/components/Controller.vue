<template>
    <div id="controller">
        <input type="text" v-model="newItemName" @keyup.enter='addItem' placeholder="Add a new item">
        <button @click="addItem">Add</button>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                newItemName: '',
            }
        },
        methods: {
            addItem () {
                this.$emit('addItem', this.newItemName);
                this.newItemName = '';
            }
        }
    }
</script>

<style>

</style>