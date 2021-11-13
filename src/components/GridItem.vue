<template>
    <div @click="handleClick" class="grid-item" :class="{selected: selected}">
        <div>
        {{item.type}}
        </div>
    </div>
</template>

<script>
export default {
    name: 'GridItem',
    props: {
        
        item: {
            type: Object,
            required: true
        },
        selected: {
            type: Boolean,
            default: false
        },
    },
    methods: {
        handleClick() {
            this.$emit('click', this.item);
        }
    }
}
</script>

<style>
    .grid-item{
        user-select: none;
        cursor: pointer;
        border: 1px solid #ccc;
        padding: 20px;
        height: 150px;
        width: 150px;
        display: flex;
        justify-content: center;
        align-items: center;
        background-color: rgba(0,0,0,0.2);
        border: 1px dashed #565656;
        color: #565656;
        font-weight: 700;
        font-size: 72px;
        font-family: 'Fira Code';
    }
    .grid-item.selected{
        color: white;
        border: 1px dashed white;
    }
</style>