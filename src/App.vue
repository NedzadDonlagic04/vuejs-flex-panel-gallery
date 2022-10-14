<script>
import FlexImage from './components/FlexImage.vue';

let id = 0;

export default {
    components: {
        FlexImage
    },
    data() 
    {
        return {
            images: [
                { id: id++, path: './../assets/foggy-lake.jpg', flexGrow: 1, topText: "hey", middleText: "let's", bottomText: "dance" },
                { id: id++, path: './../assets/fox.jpeg', flexGrow: 1, topText: "give", middleText: "take", bottomText: "receive" },
                { id: id++, path: './../assets/hike.jpeg', flexGrow: 1, topText: "experience", middleText: "it", bottomText: "today" },
                { id: id++, path: './../assets/sky.jpeg', flexGrow: 1, topText: "give", middleText: "all", bottomText: "you can" },
                { id: id++, path: './../assets/winter-mountain.jpeg', flexGrow: 1, topText: "life", middleText: "in", bottomText: "motion" }
            ]
        }
    },
    methods: {
        expandHandle(value)
        {
            for(let i=0; i < this.images.length; i++)
            {
                const image = this.images[i];
                image.flexGrow = (image.id === value) ? 4 : 1;
            }
        }
    }
}
</script>

<template>
    <div class="container">
        <FlexImage v-for="image in images" 
            :key="image.id" 
            :path="image.path" 
            :flexGrow="image.flexGrow" 
            :topText="image.topText"
            :middleText="image.middleText"
            :bottomText="image.bottomText"
            @imageExpand="expandHandle"/>
    </div>
</template>

<style scoped>
    .container {
        min-height: 100vh;
        display: flex;
        flex-direction: row;
    }
</style>