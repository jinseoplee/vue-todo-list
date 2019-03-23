<template>
    <section class="todo">
        <transition-group class="todo__list" name="list" tag="div">
            <div class="todo__item clearfix" v-for="(todoItem, index) in propsdata" v-bind:key="todoItem">
                <span class="todo__check">
                    <i class="fas fa-check" aria-hidden="true"></i>
                </span>
                <p class="todo__content">
                    {{todoItem}}
                </p>
                <span class="todo__remove" v-on:click="removeTodo(todoItem, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </div>
        <!-- <ul class="todo__list"> -->
            <!-- <li class="todo__item clearfix" v-for="(todoItem, index) in propsdata" v-bind:key="todoItem">
                <span class="todo__check">
                    <i class="fas fa-check" aria-hidden="true"></i>
                </span>
                <p class="todo__content">
                    {{todoItem}}
                </p>
                <span class="todo__remove" v-on:click="removeTodo(todoItem, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li> -->
        <!-- </ul> -->
        </transition-group>
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

.list-enter-active, .list-leave-active {
    transition: all 1s;
}

.list-enter, .list-leave-to {
    opacity: 0;
    transform: translateY(30px);
}

.todo__list {
    max-width: 1400px;
    margin: 0 auto;
}

.todo__item {
    min-width: 380px;
    box-sizing: border-box;
    background-color: #fff;
    margin: 0.5rem 0rem;
    padding: 0.9rem 1rem;
    border-radius: 5px;
}

.todo__check {
    float: left;
    padding-right: 5px;
}

.todo__content {
    float: left;
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;
    text-align: left;
    width: 89%;
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

@media screen and (min-width: 790px) {
    .todo__item {
        float: left;
        width: 49%;
        margin-right: 1.3%;
    }

    .todo__list::after {
        content: "";
        display: block;
        clear: both;
    }

    .todo__item:nth-child(2n) {
        margin-right: 0;
    }
}

@media screen and (min-width: 1191px) {
    .todo__item {
        width: 32%;
    }

    .todo__item:nth-child(2n) {
        margin-right: 1.3%;
    }

    .todo__item:nth-child(3n) {
        margin-right: 0;
    }
}
</style>
