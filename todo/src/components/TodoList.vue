<template>
    <div>
        <ul class="list-group mb-4">
            <li 
                class="list-group-item text-left" 
                v-for="(todoItem, index) in propsdata" 
                v-bind:key="todoItem">
                {{ todoItem }}

                <button type="button" 
                    class="btn btn-light" 
                    @click="removeTodo(todoItem, index)"
                >
                    <i class="fa fa-trash-o"></i>
                    <span class="hidden">delete</span>
                </button>

                <button type="button"
                    class="btn btn-light" 
                >
                    <div 
                        class="icon-wrap" 
                        @click="isActive = !isActive"
                        :area-expanded="isActive ? 'isActive' : '!isActive'">
                        <i v-if="isActive" class="complate-icon fa fa-heart"></i>
                        <i else class="complate-icon fa fa-heart-o"></i>
                        <span class="hidden">Complete</span>
                    </div>
                </button> 
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    data() {
        return {
        isActive: false
        }
    },
    props: ['propsdata'],
    methods: {
        removeTodo(todoItem, index) {
            this.$emit('removeTodo', todoItem, index);
        }
    }
}
</script>

<style>
.list-group{
    overflow:hidden;
    border-radius: 0;
}

.list-group li {
    position: relative;
    list-style: none;
    padding: .75rem 2.6rem; 
    background: rgba(255,255,255,0.1);
    border:none;
}

.list-group li + li{
    margin-top: .35rem;
}

.list-group li button{
    float:right;
    background: rgba(53, 49, 49, 0.1);
    border:none;
}
.active {
  background: #f00;
  color: #fff;
  font-size: 30px;
}
</style>