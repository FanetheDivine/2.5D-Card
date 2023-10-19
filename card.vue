<template>
    <div class="card-2-5d">
        <slot></slot>
    </div>
</template>
<script setup>
import { computed } from 'vue'
const props = defineProps({
    'h-offset':{
        default:'0px'
    },
    'v-offset':{
        default:'0px'
    },
    'blur':{
        default:'5px'
    },
    'spread':{
        default:'0px'
    },
    'color':{
        default:'gray'
    },
    'h-offset-hover':{
        default:'1px'
    },
    'v-offset-hover':{
        default:'2px'
    },
    'blur-hover':{
        default:'7px'
    },
    'spread-hover':{
        default:'1px'
    },
    'color-hover':{
        default:undefined
    },
    'rotateX':{
        default:'-5deg'
    },
    'rotateY':{
        default:'2deg'
    }
})
const rotate= computed(()=>`rotateX(${props.rotateX} rotateY(${props.rotateY})`)
console.log(props)

</script>
<style scoped>
.card-2-5d {
    border-radius: 10px;
    transform-origin: 0 0;
    transition-duration: 100ms;
    box-shadow: var(--shadow-h-offset) var(--shadow-v-offset) var(--shadow-blur) var(--shadow-spread) var(--shadow-color);
    --shadow-h-offset: v-bind(props.hOffset);
    --shadow-v-offset: v-bind(props.vOffset);
    --shadow-blur: v-bind(props.blur);
    --shadow-spread: v-bind(props.spread);
    --shadow-color: v-bind(props.color);
}

.card-2-5d:hover {
    transform: v-bind(rotate);
    --shadow-h-offset: v-bind(props.hOffsetHover);
    --shadow-v-offset: v-bind(props.vOffsetHover);
    --shadow-blur: v-bind(props.blurHover);
    --shadow-spread: v-bind(props.spreadHover);
    --shadow-color: v-bind(props.colorHover??props.color);
}
</style>