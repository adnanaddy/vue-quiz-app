<script setup>
import { computed, ref } from 'vue';
import { useRoute } from 'vue-router';
import Question from '../components/Question.vue';
import QuizHeader from '../components/QuizHeader.vue';
import Result from '../components/Result.vue';
import quizez from '../data/quizes.json';
const route = useRoute()

const quizId = parseInt(route.params.id)

const quiz = quizez.find(q => q.id === quizId)

const currentQuestionindex = ref(0)
const numberOfCorrectAnswers = ref(0)
const showResults = ref(false)

// const questionStatus = ref(`${currentQuestionindex.value}/${quiz.questions.length}`)

// watch(() => currentQuestionindex.value, () => {
//     questionStatus.value = `${currentQuestionindex.value}/${quiz.questions.length}`
// })
const questionStatus = computed(() => `${currentQuestionindex.value}/${quiz.questions.length}`)
const barPercentage = computed(() => `${currentQuestionindex.value / quiz.questions.length * 100}%`)
const onSelectedOption = (isCorrect) => {
    if (isCorrect) {
        numberOfCorrectAnswers.value++
    }
    if (quiz.questions.length - 1 === currentQuestionindex.value) {
        showResults.value = true
    }
    currentQuestionindex.value++
}

</script>

<template>
    <div>
        <QuizHeader :questionStatus="questionStatus" :barPercentage="barPercentage" />
        <div>
            <Question v-if="!showResults" @selectOption="onSelectedOption"
                :question="quiz.questions[currentQuestionindex]" />
            <Result v-else :totalQuestions="quiz.questions.length" :correctAnswers="numberOfCorrectAnswers" />
        </div>
    </div>
</template>
