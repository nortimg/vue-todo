<template>
    <form @submit.prevent="onSubmit">
        <input type="text" v-model="title">
        <button type="submit">Create</button>
    </form>
</template>

<style scoped>
    form {
        display: flex;
        margin: 20px 0;
    }

    input {
        width: 100%;
    }
</style>

<script>
export default {
    data() {
        return {
            title: ''
        }
    }, 
    methods: {
        onSubmit() {
            if (this.title.trim()) {
                const newTodo = {
                    id: Date.now(), 
                    title: this.title, 
                    completed: false, 
                }

                this.$emit('add-todo', newTodo)
                this.title = ''
            }
        }
    }
}
</script>