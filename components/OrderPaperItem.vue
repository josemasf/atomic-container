<template>
    <!--vue component with a header of a white clipboard icon with a black background, a title section with black text, and a body section with white text-->
    <div class="flex flex-col items-center">
        <div class="flex flex-row items-center justify-center bg-dark p-7 rounded-full">                        
            <component :is="svgComponent" class="h-12 w-12 text-white fill-white" />             
        </div>
        <div class="mt-5 text-center">            
            <p class="text-dark text-2xl">{{title}}</p>
            <p class="font-light">{{body}}</p>        
        </div>
    </div>
</template>

<script setup lang="js">
import {  computed } from 'vue';

import Chat from '../assets/svg/Chat.vue';
import Atom from '../assets/svg/Atom.vue';
import CSharp from '../assets/svg/CSharp.vue';
import FolderCogOutline from '../assets/svg/FolderCogOutline.vue';
import TestTube from '../assets/svg/TestTube.vue';



const props = defineProps({
    icon: {
        type: String,
        default: 'Atom'
    },
    title: {
        type: String,
        default: 'Order Paper'
    },
    body: {
        type: String,
        default: 'Order Paper'
    }
})

const svgComponent = computed(() => {
    switch (props.icon) {
        case 'chat':
            return Chat;
        case 'clipboard':
            return Clipboard;
        case 'csharp':
            return CSharp;
        case 'foldercogoutline':
            return FolderCogOutline;
        case 'test-tube':
            return TestTube;
        default:
            return Atom;
    }
    
})

</script>