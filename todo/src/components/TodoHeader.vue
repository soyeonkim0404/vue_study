<template>
    <div>
        <header>
            <h1 class="text-left mb-4">Todo List</h1>
        </header>
        <div class="top">
            <div class="input-group mb-4">
                <input type="text" class="form-control" v-model="newTodoItem" @keyup.enter="addTodo">
                <div class="input-group-append">
                    <button class="btn btn-info" type="button" id="button-addon2" @click="addTodo">ADD ITEM</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodoItem: ''
        }
    },
    methods: {
        addTodo() {
            if(this.newTodoItem !== ''){
                let value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.newTodoItem = '';
            }
        }
    }
}
</script>

<style>
h1{
font-weight: 100;
color:#fff;
padding:0 3rem;
}

.input-group{
width:80%;
margin:0 auto;
}

.input-group input{
background: #fafafa;
}

.input-group:placeholder{
color:#ddd;
}

.form-control{
height: calc(1.5em + .75rem + 15px);
border-radius:0;
}

.btn{
padding:.375rem .95rem;
border-radius: 0;
}
</style>