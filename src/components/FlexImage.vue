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
        },
        topText: {
            type: String,
            required: true
        },
        middleText: {
            type: String,
            required: true
        },
        bottomText: {
            type: String,
            required: true
        }
    },
    computed: {
        imgSrc() 
        {
            return new URL(this.path, import.meta.url);
        },
        fontSize()
        {
            return (this.flexGrow === 1)? '4' : '6';
        },
        position()
        {
            return (this.flexGrow === 1)? '-30%' : '15%';
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
    <div class="img-box" ref="div" :style="{ flexGrow: flexGrow, backgroundImage: `url(${imgSrc})`}" @click="clickHandle">
        <p class="top-text" :style="{ top: position}">{{topText}}</p>
        <p class="middle-text" :style="{ fontSize: fontSize + 'rem' }">{{middleText}}</p>
        <p class="bottom-text" :style="{ bottom: position}">{{bottomText}}</p>
    </div>
</template>

<style scoped>
    .img-box {
        min-height: 100%;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center;
        position: relative;
    }

    .img-box:hover {
        cursor: pointer;
    }

    p {
        text-transform: uppercase;
        color: white;
        position: absolute;
        text-shadow: -2px 0px 10px black;
    }

    .img-box,
    p {
        transition: all .5s ease;
    }

    .top-text {
        font-size: 3rem;
        left: 50%;
        transform: translate(-50%, -15%);
    }

    .middle-text {
        font-size: 4rem;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    .bottom-text {
        font-size: 3rem;
        left: 50%;
        transform: translate(-50%);
    }
</style>