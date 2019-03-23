<template>
    <section class="todo">
        <ul class="todo__list">
            <li class="todo__item clearfix" v-for="(todoItem, index) in propsdata" v-bind:key="todoItem">
                <span class="todo__check">
                    <i class="fas fa-check" aria-hidden="true"></i>
                </span>
                <p class="todo__content">
                    {{todoItem}}
                </p>
                <span class="todo__remove" v-on:click="removeTodo(todoItem, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </ul>
    </section>
</template>

<script>
export default {
    props: ["propsdata"],
    methods: {
        removeTodo(todoItem, index) {
            this.$emit("removeTodo", todoItem, index);
        }
    }
}
</script>

<style scoped>
.todo {
    margin-bottom: 1.5rem;
}

.todo__list {
    list-style-type: none;
}

.todo__item {
    background-color: #fff;
    margin: 0.5rem 0rem;
    padding: 0.9rem 0.5rem;
    border-radius: 5px;
}

.todo__check {
    float: left;
    padding-right: 0.3rem;
    width: 8%;
}

.todo__content {
    float: left;
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
    text-align: left;
    width: 80%;
}

.todo__remove {
    float: right;
    cursor: pointer;
    width: 8%;
}

.clearfix::after {
    content: "";
    display: block;
    clear: both;
}
</style>
