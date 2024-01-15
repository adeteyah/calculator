<script>
export default {
    data() {
        return {
            current: '',
            separator: ['/', '*', '-', '+']
        }
    },
    methods: {
        clear() {
            this.current = ''
        },
        sign() {
            this.current = this.current.charAt(0) === '-' ? this.current.slice(1) : `-${this.current}`;
        },
        percent() {
            this.current = `${parseFloat(this.current) / 100}`
        },
        append(_) {
            this.current = `${this.current}${_}`
        },
        dot() {
            if (this.current.indexOf('.') === -1) {
                this.append('.')
            }
        },
        divide() {
            this.operator = (a, b) => a / b;
            this.append('/')
        },
        times() {
            this.operator = (a, b) => a * b;
            this.append('*')
        },
        minus() {
            this.operator = (a, b) => a - b;
            this.append('-')
        },
        plus() {
            this.operator = (a, b) => a + b;
            this.append('+')
        },
        equal() {
            this.current = math.evaluate('1.2 * (2 + 4.5)')
        }
    }
}
</script>

<template>
    <div class="container">
        <div class="grid">
            <div class="result">{{ current || '0' }}</div>
            <button @click="clear" class="op">C</button>
            <button @click="sign" class="op">&plusmn;</button>
            <button @click="percent" class="op">%</button>
            <button @click="divide" class="op">&divide;</button>
            <button @click="append('7')" class="num">7</button>
            <button @click="append('8')" class="num">8</button>
            <button @click="append('9')" class="num">9</button>
            <button @click="times" class="op">&times;</button>
            <button @click="append('4')" class="num">4</button>
            <button @click="append('5')" class="num">5</button>
            <button @click="append('6')" class="num">6</button>
            <button @click="minus" class="op">&minus;</button>
            <button @click="append('1')" class="num">1</button>
            <button @click="append('2')" class="num">2</button>
            <button @click="append('3')" class="num">3</button>
            <button @click="plus" class="op">&plus;</button>
            <button @click="append('00')" class="num">00</button>
            <button @click="append('0')" class="num">0</button>
            <button @click="dot" class="op">.</button>
            <button @click="equal" class="op">=</button>
        </div>
    </div>
</template>
