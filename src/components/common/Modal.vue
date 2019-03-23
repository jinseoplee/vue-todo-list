<template>
    <div class="myModal" v-if="visible">
        <div class="myModal__dialog">
            <header class="myModal__header">
                <span>Warning</span>
            </header>
            <div class="myModal__body">
                Please enter what you do.
            </div>
            <div class="myModal__footer">
                <button type="button" class="myModal__OK" v-on:click="modalClose">OK</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        visible: {
            type: Boolean,
            require: true,
            default: false
        },
        title: {
            tyle: String,
            require: false
        }
    },
    methods: {
        modalClose() {
            this.$emit("modalClose", false);
        }
    }
}
</script>

<style>
.myModal {
    background: rgba(0, 0, 0, .4);
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
}

.myModal__dialog {
    width: 300px;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    color: #000;
    background: #fff;
    border-radius: 5px;
    overflow: hidden;
    padding-bottom: 0.7rem;
}

.myModal__header {
    background: rgba(134, 229, 127, 1);
    padding: 0.7rem 0;
    color: #353535;
}

.myModal__body {
    margin: 1.5rem 0;
}

.myModal__OK {
    width: 7rem;
    background-color: #bdbdbd; 
    color: #fff;
    font-size: 0.8rem;
    font-weight: 700;
    padding: 0.3rem 0;
    border: none;
    border-radius: 5px;
    box-shadow: 1px 1px 3px 1px #999999;
    outline: none;
    cursor: pointer;
}
</style>
