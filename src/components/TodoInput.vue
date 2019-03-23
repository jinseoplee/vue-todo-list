<template>
    <div class="makeTodo">
        <input type="text" class="makeTodo__content" v-model="newTodoItem" placeholder="what do you have to do?">
        <span class="makeTodo__add" v-on:click="addTodo">
            <i class="makeTodo__addBtn fas fa-plus" aria-hidden="true"></i>
        </span>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodoItem: ""
        }
    },
    methods: {
        addTodo() {
            localStorage.setItem(this.newTodoItem, this.newTodoItem);
            if (this.newTodoItem !== "") {
                const value = this.newTodoItem && this.newTodoItem.trim();
                localStorage.setItem(this.newTodoItem, this.newTodoItem);
                this.clearInput();
            }
        },
        clearInput() {
            this.newTodoItem = "";
        }
    }
}
</script>
<style scope>
.makeTodo {
    margin-bottom: 2rem;
    align-items: center;
}

.makeTodo__content {
    width: 85%;
    height: 30px;
    border: none;
    border-radius: 5px;
    box-shadow: 1px 1px 3px 1px #62C15B;
    box-sizing: border-box;
    margin-right: 0.3rem;
    padding: 0 1%;
    text-align: center;
}

.makeTodo__add {
    display: inline-block;
    width: 12%;
    height: 30px;
    line-height: 30px;
    border: none;
    border-radius: 5px;
    background-color: #86E57F;
    box-shadow: 1px 1px 3px 1px #62C15B;
    cursor: pointer;
    font-weight: 600;
    color: #353535;
    vertical-align: bottom;
}

.makeTodo__addBtn {
    vertical-align: middle;
}
</style>

