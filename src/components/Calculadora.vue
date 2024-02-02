<template>
    <div id="app">
        <div class="calculadora">
            <p class="p">
            Digite os números e selecione o operador que deseja calcular:
            </p>
            <input class="input" type="number" v-model="valor1" @input="calculate" />
            <select class="btn" v-model="operator" @change="calculate">
            <option value="add">+</option>
            <option value="subtract">-</option>
            <option value="multiply">*</option>
            <option value="divide">÷</option>
            </select>
            <input class="input" type="number" v-model="valor2" @input="calculate" />
            <div class="resultado">
            Resultado = {{ result }}
            </div>
        </div>
        </div>
    </template>
    
    <script>
    export default {
        data() {
        return {
            valor1: 0,
            valor2: 0,
            operator: 'add',
            result: 0
        };
        },
        methods: {
        calculate() {
            switch (this.operator) {
            case 'add':
                this.result = parseFloat(this.valor1) + parseFloat(this.valor2);
                break;
            case 'subtract':
                this.result = parseFloat(this.valor1) - parseFloat(this.valor2);
                break;
            case 'multiply':
                this.result = parseFloat(this.valor1) * parseFloat(this.valor2);
                break;
            case 'divide':
                this.result = parseFloat(this.valor1) / parseFloat(this.valor2);
                break;
            default:
                this.result = 0;
            }
        }
        }
    };
    </script>
    
    <style scoped>
    .calculadora {
        margin: 0 auto;
        width: 200px;
        padding: 20px;
        font-size: 20px;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        border: 1px solid #ccc;
        background-color: rgb(3, 81, 88);
    }
    .input {
        margin: 10px;
        padding: 10px;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    }
    .resultado {
        margin-top: 10px;
        margin-bottom: 15px;
        color: #fff;
        margin-left: 22px;
    }
    .btn {
        width: 60px;
        margin-left: 60px;
    }
    .p {
        margin-left: 10px;
        color: #fff;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    }
    </style>