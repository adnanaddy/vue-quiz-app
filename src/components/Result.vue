<script setup>

const { totalQuestions, correctAnswers } = defineProps(['totalQuestions', 'correctAnswers'])

</script>

<template>
    <div class="results">
        <p>Your Results...</p>
        <h1>
            {{ correctAnswers }} / {{ totalQuestions }}
        </h1>
        <router-link to="/">Go Back</router-link>
    </div>
</template>

<style scoped>
.results {
    text-align: center;
    padding: 100px 0;
}

p {
    font-size: 25px;
}

h1 {
    font-size: 80px;
}
</style>