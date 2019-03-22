<template>
    <section class="todo">
        <ul class="todo__list">
            <li class="todo__item clearfix" v-for="(todoItem, index) in todoItems" v-bind:key="todoItem">
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
    data() {
        return {
            todoItems: []
        }
    },
    methods: {
        removeTodo(todoItem, index) {
            localStorage.removeItem(todoItem);
            this.todoItems.splice(index, 1);
        }
    },
    created() {
        if (localStorage.length > 0) {
            for (let i = 0; i < localStorage.length; i++) {
                let localKey = localStorage.key(i);
                if (localKey === "loglevel:webpack-dev-server") continue;
                this.todoItems.push(localStorage.key(i));
            }
        }
    }
}
</script>

<style scoped>
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
}

.todo__content {
    float:left;
}

.todo__remove {
    float: right;
    cursor: pointer;
}

.clearfix::after {
    content: "";
    display: block;
    clear: both;
}
</style>
