<script>
export default {
    data() {
        return {
            current: '123',
        }
    },
    methods: {
        clear() {
            this.current = ''
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="grid">
            <div class="result">{{ current || '0' }}</div>
            <button class="op">AC</button>
            <button class="op">%</button>
            <button class="op" @click="clear">C</button>
            <button class="op">&divide;</button>
            <button class="num">1</button>
            <button class="num">2</button>
            <button class="num">3</button>
            <button class="op">&times;</button>
            <button class="num">4</button>
            <button class="num">5</button>
            <button class="num">6</button>
            <button class="op">&minus;</button>
            <button class="num">7</button>
            <button class="num">8</button>
            <button class="num">9</button>
            <button class="op">&plus;</button>
            <button class="num">00</button>
            <button class="num">0</button>
            <button class="op">.</button>
            <button class="op">=</button>
        </div>
    </div>
</template>
