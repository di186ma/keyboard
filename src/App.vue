<template>
  <div id="app" class="container">
    <h1>Тренажер печати</h1>
    <p>{{ text }}</p>
    <input type="text" v-model="userInput" @input="checkInput" class="input-field">
    <p>{{ message }}</p>
    <p>Время: {{ time }} секунд</p>
    <p>Скорость: {{ speed }} символов в минуту</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: 'Привет, мир! Рыбный текст. Рыбный текст. Рыбный текст. Рыбный текст. Рыбный текст. Рыбный текст.',
      userInput: '',
      message: '',
      startTime: null,
      time: 0,
      speed: 0
    }
  },
  methods: {
    checkInput() {
      if (!this.startTime) {
        this.startTime = Date.now();
      }

      if (this.text[this.userInput.length - 1] !== this.userInput[this.userInput.length - 1]) {
        this.message = 'Неверный символ!';
      } else {
        this.message = '';
      }

      this.time = ((Date.now() - this.startTime) / 1000).toFixed(2);
      this.speed = (this.userInput.length / this.time * 60).toFixed(2);
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  box-shadow: 0 0 10px rgba(0,0,0,0.1);
  border-radius: 10px;
}

h1 {
  color: #333;
  font-size: 24px;
  text-align: center;
  margin-bottom: 20px;
}

.input-field {
  margin-top: 20px;
  padding: 10px;
  font-size: 16px;
  width: 100%;
  border: 1px solid #ccc;
  border-radius: 5px;
}

p {
  color: #666;
  font-size: 18px;
}
</style>
