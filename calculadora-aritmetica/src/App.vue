<template>
  <div id="app" class="calculator">
    <h1>Calculadora Aritmética</h1>
    <div class="input-group">
      <input
        type="number"
        v-model="numero1"
        placeholder="Digite o primeiro número"
      />
      <select v-model="operacao">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
      </select>
      <input
        type="number"
        v-model="numero2"
        placeholder="Digite o segundo número"
      />
    </div>
    <div class="resultado">
      Resultado: <span>{{ calcularResultado() }}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero1: null,
      numero2: null,
      operacao: "+",
    };
  },
  methods: {
    calcularResultado() {
      const num1 = parseFloat(this.numero1);
      const num2 = parseFloat(this.numero2);
      if (isNaN(num1) || isNaN(num2)) return "";
      switch (this.operacao) {
        case "+":
          return num1 + num2;
        case "-":
          return num1 - num2;
        case "*":
          return num1 * num2;
        case "/":
          return num2 !== 0 ? num1 / num2 : "Erro: Divisão por zero";
        default:
          return 0;
      }
    },
  },
};
</script>

<style scoped>
.calculator {
  text-align: center;
  max-width: 400px;
  margin: 50px auto;
  padding: 20px;
  border-radius: 16px;
  background: #fff;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  font-family: "Roboto", sans-serif;
  transition: transform 0.3s, box-shadow 0.3s;
}

.calculator:hover {
  transform: translateY(-5px);
  box-shadow: 0 15px 35px rgba(0, 0, 0, 0.2);
}

h1 {
  font-size: 2.5rem;
  color: #333;
  margin-bottom: 20px;
  font-weight: 300;
}

.input-group {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 30px;
  gap: 15px;
}

input,
select {
  font-size: 1.2rem;
  padding: 10px 15px;
  border-radius: 8px;
  border: 1px solid #ddd;
  width: calc(33% - 10px);
  box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.1);
  text-align: center;
  transition: border-color 0.3s, box-shadow 0.3s;
}

input:focus,
select:focus {
  outline: none;
  border-color: #3f51b5;
  box-shadow: 0 0 8px rgba(63, 81, 181, 0.3);
}

.resultado {
  font-size: 1.8rem;
  font-weight: 400;
  color: #3f51b5;
  padding: 10px;
  background-color: #f0f0f0;
  border-radius: 8px;
  display: inline-block;
  min-width: 120px;
  transition: background-color 0.3s, box-shadow 0.3s;
}

.resultado span {
  display: inline-block;
  min-width: 50px;
  transition: opacity 0.3s;
}

.resultado:hover {
  background-color: #e8e8e8;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
}

.resultado span {
  animation: fadeIn 0.5s ease-in-out;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
