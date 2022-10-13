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
                { id: id++, path: './../assets/foggy-lake.jpg', flexGrow: 1 },
                { id: id++, path: './../assets/fox.jpeg', flexGrow: 1 },
                { id: id++, path: './../assets/hike.jpeg', flexGrow: 1 },
                { id: id++, path: './../assets/sky.jpeg', flexGrow: 1 },
                { id: id++, path: './../assets/winter-mountain.jpeg', flexGrow: 1 }
            ]
        }
    },
    methods: {
        expandHandle(value)
        {
            for(let i=0; i<this.images.length; i++)
            {
                if(this.images[i].id === value)
                {
                    this.images[i].flexGrow = 4;
                }
                else
                {
                    this.images[i].flexGrow = 1;
                }
            }
        }
    }
}
</script>

<template>
    <div class="container">
        <FlexImage v-for="image in images" :key="image.id" :path="image.path" :flexGrow="image.flexGrow" @imageExpand="expandHandle"/>
    </div>
</template>

<style scoped>
    .container {
        min-height: 100vh;
        display: flex;
        flex-direction: row;
    }
</style>