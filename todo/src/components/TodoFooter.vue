<template>
    <div class="footer text-center">
        <button type="button" class="btn btn-secondary btn-sm" v-on:click="clearTodo">all delete</button>
    </div>
</template>

<script>
export default {
    methods: {
        clearTodo() {
            this.$emit('removeAll');
        }
    }
}
</script>

<style>
</style>