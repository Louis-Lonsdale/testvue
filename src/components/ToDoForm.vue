<template>
    <form @submit.prevent="onsubmit">
        <h2 class="label-wrapper">
        <label for="new-todo-input" class="label__lg"> What needs to be done? </label>
        </h2>
        <input
        type="text"
        id="new-todo-input"
        name="new-todo"
        autocomplete="off" 
        v-model.trim.lazy="label"
        />

        <button
        type="submit"
        class="btn btn__primary btn__lg"
        > Add Task </button>
    </form>
</template>

<script>
    export default {
        methods: {
            onsubmit() {
                if (this.label === "")
                { 
                    return;
                }
                this.$emit("todo-added", this.label);
                this.label = "";
            }
        },
        data() {
            return {
                label: "",
            }
        }
        
    };
</script>