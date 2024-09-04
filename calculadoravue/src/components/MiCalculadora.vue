<template>
  <div class="calc">
    <h1>{{ msg }}</h1>
    <div class="Calculadora">
      <h1 class="Display">{{ displayValue }}</h1> <!-- Display muestra el valor reactivo -->
      <div class="Num">
        <div class="Numeros">
          <table>
            <tr>
              <td @click="appendNumber('1')">1</td>
              <td @click="appendNumber('2')">2</td>
              <td @click="appendNumber('3')">3</td>
            </tr>
            <tr>
              <td @click="appendNumber('4')">4</td>
              <td @click="appendNumber('5')">5</td>
              <td @click="appendNumber('6')">6</td>
            </tr>
            <tr>
              <td @click="appendNumber('7')">7</td>
              <td @click="appendNumber('8')">8</td>
              <td @click="appendNumber('9')">9</td>
            </tr>
            <tr>
              <td colspan="2" @click="appendNumber('0')">0</td> <!-- El 0 ocupa dos columnas -->
              <td @click="appendNumber('.')">.</td> <!-- Punto decimal -->
            </tr>
          </table>
        </div>
        <div class="Operaciones">
          <div class="Operacion" @click="clearDisplay">AC</div>
          <div class="Operacion" @click="deleteLastEntry">C</div>
          <div class="Operacion" @click="appendNumber('+')">+</div>
          <div class="Operacion" @click="appendNumber('-')">-</div>
          <div class="Operacion" @click="appendNumber('*')">*</div>
          <div class="Operacion" @click="appendNumber('/')">/</div>
          <div class="Operacion" @click="calculateResult">=</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MiCalculadora',
  data() {
    return {
      displayValue: '' // Estado reactivo para almacenar el valor del display
    };
  },
  methods: {
    appendNumber(number) {
      this.displayValue += number; // Añadir el número o carácter al display
    },
    calculateResult() {
      try {
        this.displayValue = eval(this.displayValue); // Calcular el resultado usando eval
      } catch (error) {
        this.displayValue = "Error"; // Mostrar un error si la expresión no es válida
      }
    },
    clearDisplay() {
      this.displayValue = ''; // Limpiar el display
    },
    deleteLastEntry() {
      this.displayValue = this.displayValue.slice(0, -1); // Borrar el último carácter
    }
  }
}
</script>

<style scoped>
.calc {
  display: grid;
  justify-content: center;
  align-items: center;
}

.Calculadora {
  border: 4px solid black;
  text-align: center;
  width: 800px;
  height: 600px;
  display: grid;
  grid-template-rows: 100px auto; /* Define las filas del grid */
}

.Display {
  color: aqua;
  height: 100px;
  width: auto;
  padding: 0;
  border: 0;
  font-size: 36px; /* Ajustar el tamaño de la fuente para el display */
  line-height: 100px; /* Centrar el texto verticalmente */
}

.Num {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 columnas iguales */
  width: 100%;
  border: black solid 2px;
}

.Numeros {
  grid-column: span 2; /* Ocupa 2 columnas */
}

.Numeros table {
  width: 100%;
  height: 100%;
  border-collapse: collapse;
}

.Numeros td {
  border: 1px solid black;
  text-align: center;
  font-size: 24px;
  padding: 20px;
  cursor: pointer;
}

.Operaciones {
  grid-column: span 1; /* Ocupa 1 columna */
  display: grid;
  grid-template-rows: repeat(7, 1fr); /* 7 filas iguales para las operaciones */
}

.Operacion {
  border: 1px solid black;
  text-align: center;
  font-size: 24px;
  padding: 20px;
  cursor: pointer;
}
</style>
