<script setup lang="ts">
import { ref } from "vue";
</script>

<template>
    <main>
        <div class="container">
            <h1>People invited to my Party</h1>
            <div class="input-container">
                <input type="text" placeholder="Name..." />

                <select>
                    <option>Male</option>
                    <option>Female</option>
                </select>
            </div>
        </div>
    </main>
</template>

<style scoped>
main {
    display: flex;
    height: 100vh;
    align-items: center;
    justify-content: center;
    background-color: #e3f2ff;
}

h1 {
    font-size: 3rem;
    font-weight: bold;
}

.container {
    padding: 3rem;
}

input,
select {
    width: 100%;
    padding: 1rem;
    margin-bottom: 0.5rem;
    font-size: 1.5rem;
    border: 1px solid #222;
}
</style>
