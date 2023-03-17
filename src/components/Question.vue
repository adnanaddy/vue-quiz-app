
<script setup>
import { defineEmits, defineProps } from 'vue';
 
const emit = defineEmits(['selectOption'])
const {question} = defineProps(['question'])

const emitSelectedOption = (isCorrect) =>{
    emit('selectOption', isCorrect)
}
</script>

<template>
    <div class="question-container">
        <h1 class="question">
            {{ question.text }}
        </h1>
    </div>
    <div class="option-container">
        <div v-for="option in question.options" :key="option.id" @click="emitSelectedOption(option.isCorrect)" class="option">
            <p class="option-label">{{ option.label }}</p>
            <div class="option-value">
                <p>{{ option.text }}</p>
            </div>
        </div>
       
    </div>
</template>

<style scoped>
.question-container {
    margin-top: 20px;
}

.question {
    font-size: 40px;
    margin-bottom: 20px;
}

.option {
    display: flex;
    margin-bottom: 20px;
    cursor: pointer;
}

.option-label {
    color: black;
    background-color: bisque;
    width: 60px;
    height: 60px;
    font-size: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 16px 0 0 16px ;
}

.option-value {
    color: black;
    background-color: rgb(244, 239, 239);
    width: 100%;
    font-size: 30px;
    line-height: 60px;
    padding: 0 20px;
    border-radius: 0 16px 16px 0;
    align-items: center;
}</style>