<template>
    <form @submit.prevent="onsubmit">
        <label for="new-todo-input"> What needs to be done? </label>

        <input
        type="text"
        id="new-todo-input"
        name="new-todo"
        autocomplete="off" 
        v-model.trim.lazy="label"
        />

        <button
        type="submit"> Add Task </button>
    </form>
</template>

<script>
    export default {
        methods: {
            onsubmit() {
                this.$emit("todo-added", this.label);
            }
        },
        data() {
            return {
                label: "",
            }
        }
        
    };
</script>