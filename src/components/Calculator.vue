<script>
import * as math from 'mathjs'

export default {
    data() {
        return {
            current: ''
        }
    },
    mounted() {
        document.addEventListener('keydown', this.handleKeyDown)
    },
    methods: {
        clearAll() {
            this.current = ''
        },
        clear() {
            this.current = this.current.slice(0, this.current.length - 1)
        },
        percent() {
            this.current = `${parseFloat(this.current) / 100}`
        },
        append(expr) {
            this.current = `${this.current}${expr}`
        },
        equal() {
            try {
                this.current = math.evaluate(this.current)
            } catch (error) {
                alert('Numbers expression is not calculatable')
            }
        },
        handleKeyDown(event) {
            if (
                (event.keyCode >= 48 && event.keyCode <= 57) || // Numbers 0-9
                (event.keyCode >= 96 && event.keyCode <= 105) || // Numpad 0-9
                event.keyCode === 106 || // Numpad *
                event.keyCode === 107 || // Numpad +
                event.keyCode === 109 || // Numpad -
                event.keyCode === 111 || // Numpad /
                event.keyCode === 170 || // *
                event.keyCode === 187 || // +
                event.keyCode === 189 || // -
                event.keyCode === 191 // /
            ) {
                if (event.key != '=') {
                    this.append(event.key)
                    console.log('pressed: ', event.key)
                }
            } else if (event.keyCode === 13) {
                this.equal()
                console.log('calculate')
            } else if (event.keyCode === 8) {
                this.clear()
                console.log('clear a digit')
            } else if (event.keyCode === 46) {
                this.clearAll()
                console.log('clear all')
            }
        },
    }
}
</script>

<template>
    <div class="container">
        <div class="grid">
            <div class="result">{{ current.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',') || '0' }}</div>
            <div @click="clearAll" class="op">AC</div>
            <div @click="append('%')" class="op">%</div>
            <div @click="clear" class="op">C</div>
            <div @click="append('/')" class="op">&divide;</div>
            <div @click="append('7')" class="num">7</div>
            <div @click="append('8')" class="num">8</div>
            <div @click="append('9')" class="num">9</div>
            <div @click="append('*')" class="op">&times;</div>
            <div @click="append('4')" class="num">4</div>
            <div @click="append('5')" class="num">5</div>
            <div @click="append('6')" class="num">6</div>
            <div @click="append('-')" class="op">&minus;</div>
            <div @click="append('1')" class="num">1</div>
            <div @click="append('2')" class="num">2</div>
            <div @click="append('3')" class="num">3</div>
            <div @click="append('+')" class="op">&plus;</div>
            <div @click="append('00')" class="num">00</div>
            <div @click="append('0')" class="num">0</div>
            <div @click="append('.')" class="op">.</div>
            <div @click="equal" class="op">=</div>
        </div>
    </div>
</template>
