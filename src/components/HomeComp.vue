<template>
    <div class="fundo">
        <h1>João Lucas</h1><br>
        <div class="calculadora">
            <h1>Calculadora</h1>
            <p id="resultado">{{resultado}}</p>
            <table>
                <tr>
                    <td><v-btn color="grey-darken-2" class="botao" @click="clear()">C</v-btn></td>
                    <td><v-btn color="grey-darken-2" class="botao" @click="backspace()"> <v-icon
                        start
                        icon="mdi-arrow-left"
                      ></v-icon></v-btn></td>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('/')">/</v-btn></td>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('*')">X</v-btn></td>
                </tr>
                <tr>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('7')">7</v-btn></td>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('8')">8</v-btn></td>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('9')">9</v-btn></td>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('-')" >-</v-btn></td>
                </tr>
                <tr>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('4')">4</v-btn></td>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('5')">5</v-btn></td>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('6')">6</v-btn></td>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('+')">+</v-btn></td>
                </tr>
                <tr>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('1')">1</v-btn></td>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('2')">2</v-btn></td>
                    <td><v-btn color="grey-darken-2" class="botao" @click="insert('3')">3</v-btn></td>
                    <td rowspan=4><v-btn color="grey-darken-2" class="botao" style="height: 80px;" @click="calculate()">=</v-btn></td>
                </tr>
                <tr>
                    <td colspan="2"><v-btn color="grey-darken-2" class="botao" style="width: 130px; height: 40px;" @click="insert('0')">0</v-btn></td>
                    <td ><v-btn color="grey-darken-2" class="botao" style="height: 40px;" @click="insert('.')">.</v-btn></td>
                </tr>
            </table>
        </div>
    </div>    
</template>

<style>
*{
    margin: 0;
    padding: 0;
}
.fundo{
    background-image: linear-gradient(45deg, black, crimson);
    height: 100vh;
    color: white;
    font-family: Arial, Helvetica, sans-serif;
}
.calculadora{
    position: absolute;
    background-color: black;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    border-radius: 15px;
    padding: 15px;
    height: 400px;
    width: 300px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
.botao{
    font-size: 20px;
    cursor: pointer;
    margin: 1px;
    
    
}
.botao:hover{
    background-color: black;
}
.calculadora h1{
    margin-bottom: 35px;
}
#resultado{
    background-color: white;
    width: 260px;
    height: 40px;
    margin: 10px;
    margin-top: -15px;
    font-size: 30px;
    color: black;
    text-align: right;
    
}
</style>

<script>

export default {
    name: 'HomeComp',
    data() {
    return {
      resultado: '0' // Inicialize o resultado com um valor padrão
    };
  },
  methods: {
    insert(num) {
      if (this.resultado === '0') {
        this.resultado = num; // Se o resultado for 0, substitua pelo número clicado
      } else {
        this.resultado += num; // Caso contrário, adicione o número clicado ao resultado
      }
    },
    clear(){
        this.resultado = "0";
    },
    backspace() {
      if (this.resultado.length > 1) {
        this.resultado = this.resultado.slice(0, -1); // Remove o último caractere
      } else {
        this.resultado = '0'; // Se houver apenas um caractere, volte para '0'
      }
    },
    calculate(){
        try {
            // Use eval() para calcular a expressão
            this.resultado = eval(this.resultado);
        } catch (error) {
            // Lida com erros de avaliação
            this.resultado = 'Erro';
        }
    }
  }
}


</script>

