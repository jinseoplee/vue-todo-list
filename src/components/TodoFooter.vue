<template>
    <button class="removeAll" v-on:click="removeAll">Clear All</button>
</template>

<script>
export default {
    methods: {
        removeAll() {
            this.$emit("removeAll");
        }
    }
}
</script>

<style>
.removeAll {
    width: 8.5rem;
    background-color: #FF8383; 
    color: #fff;
    font-size: 1rem;
    padding: 0.5rem 0;
    text-align: center;
    border: none;
    border-radius: 5px;
    box-shadow: 1px 1px 3px 1px #F15F5F;
    margin: 0 auto 3rem;
    outline: none;
    cursor: pointer;
}
</style>
