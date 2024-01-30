<template>
    <div id="app"> <!-- -->
        <div class="calculadora">
            <p class="p">
                Digite os números e selecione o operador que deseja calcular:
            </p>
            <input class="input" type="number" v-model="valor1" @input="calculate" /> <!-- Primeiro número (input) digitado pelo usuário -->
            <!-- @input é acionado quando o usuário digita o número, com o método calculate para fazer o calculo -->
            <select class="btn" v-model="operator" @change="calculate"> <!-- Abrindo uma caixinha para escolha da conta aritmética -->
                <option value="add">+</option> <!-- Opções de escolhas para usuário: Mais, menos, multiplicação e divisão -->
                <option value="subtract">-</option> 
                <option value="multiply">*</option>
                <option value="divide">÷</option>
            </select>
            <input class="input" type="number" v-model="valor2" @input="calculate" /> <!-- Segundo número a ser preenchido pelo usuário -->
            <div class="resultado">
                Resultado = {{ result }} <!-- Mostrar resultado -->
            </div>
        </div>
    </div>
</template>

<script>
export default (await import('vue')).defineComponent({
    data() {
        return {
        valor1: 0,
        valor2: 0,
        operator: 'add',
        result: 0
        };
    },

    methods: {/*Métodos para realizar os calculos selecionados */
        calculate() {
            switch (this.operator) {
                case 'add': // Adição
                    this.result = parseFloat(this.num1) + parseFloat(this.num2);
                    break;
                case 'subtract': // Subtração
                    this.result = parseFloat(this.num1) - parseFloat(this.num2);
                    break;
                case 'multiply': // Multiplicação
                    this.result = parseFloat(this.num1) * parseFloat(this.num2);
                    break;
                case 'divide': // Divisão
                    this.result = parseFloat(this.num1) / parseFloat(this.num2);
                    break;
                default: // Se nenhuma operação válida for selecionada, o resultado é 0
                    this.result = 0;
            }
        }
    },
})
</script>

<style scoped>
    .calculadora {
        margin: 0 auto;
        width: 200px;
        padding: 20px;
        font-size: 20px;
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        border: 1px solid #ccc;
        background-color: rgb(3, 81, 88);
    }
    .input {
        margin: 10px;
        padding: 10px;
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
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
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    }
    
    </style>