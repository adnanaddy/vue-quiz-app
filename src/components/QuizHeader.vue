<script setup>
import { defineProps } from 'vue';

const { questionStatus, barPercentage } = defineProps(['questionStatus', 'barPercentage'])
</script>

<template>
    <header>
        <h4>Question {{ questionStatus }}</h4>
        <div class="bar">
            <div class="completion" :style="{ width: barPercentage }"></div>
        </div>
    </header>
</template>


<style scoped>
header {
    margin-top: 20px;
}

header h4 {
    font-size: 30px;
}

.bar {
    height: 20px;
    border: 2px solid bisque;
    background-color: #ffe4c442;
    border-radius: 6px;
}

.completion {
    height: 100%;
    width: 0%;
    background-color: bisque;
    border-radius: 4px;
    -webkit-transition: width 600ms ease-in-out;
    -moz-transition: width 600ms ease-in-out;
    -o-transition: width 600ms ease-in-out;
    transition: width 600ms ease-in-out;
}
</style>