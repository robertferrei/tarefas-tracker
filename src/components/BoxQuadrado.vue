<template>
    <div class="box" has-text-weight-bold>
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name:'BoxQuadrado'
})
</script>


<style scoped>
 .box{
    background-color: #faf0ca;
 }
 

</style>