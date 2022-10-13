<script>
export default {
    props: {
        path: {
            type: String,
            required: true
        },
        flexGrow: {
            type: Number,
            required: true
        }
    },
    computed: {
        imgSrc() 
        {
            return new URL(this.path, import.meta.url);
        }
    },
    emits: ['imageExpand'],
    methods: {
        clickHandle()
        {
            this.$emit('imageExpand', this.$.vnode.key);
        }
    }
}
</script>

<template>
    <div class="img-box" ref="div" :style="{ flexGrow: flexGrow, backgroundImage: `url(${imgSrc})`}" @click="clickHandle"></div>
</template>

<style scoped>
    .img-box {
        min-height: 100%;
        transition: all .5s ease;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
    }

    .img-box:hover {
        cursor: pointer;
    }
</style>