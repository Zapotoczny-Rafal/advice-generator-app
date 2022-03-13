<template>
  <div class="app">
    <div class="container">
      <div class="container__advice">
        <p class="advice-id">Advice #{{ quote.slip.id }}</p>
      </div>
      <Advice :advice="quote.slip.advice"/>
      <div class="divide"></div>
    </div>
    <div class="random">
      <button class="random__btn" @click="getAdvice"></button>
    </div>
  </div>
</template>

<script>
import Advice from "./components/Advice.vue";


export default {
  name: 'App',
  components: { Advice },
  data() {
    return {
      quote: {}
    }
  },
  methods: {
    async getAdvice() {
      const res = await fetch('https://api.adviceslip.com/advice');
      const data = await res.json();

      this.quote = { ...data };
    },
  },
  async created() {
    const res = await fetch('https://api.adviceslip.com/advice');
    const data = await res.json();

    this.quote = { ...data };
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@800&display=swap');

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 90vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Manrope', sans-serif;
  background-color: hsl(218, 23%, 16%);
  height: auto;
}

.app {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  padding: 0 18px;
}

.container {
  border-radius: 12px;
  height: auto;
  width: 22em;
  background-color: hsl(217, 19%, 24%);
}

.container__advice {
  padding: 30px;
}

.container__advice .advice-id {
  position: relative;
  top: 5px;
  text-transform: uppercase;
  letter-spacing: 4px;
  color: hsl(150, 100%, 66%);
  font-size: 0.75rem;
}

.divide {
  background-image: url('images/pattern-divider-desktop.svg');
  background-repeat: no-repeat;
  background-position: center 0px;
  padding-bottom: 80px;
  margin: 0 25px;
}

.random {
  width: 60px;
  height: 60px;
  border-radius: 50%;
  position: relative;
  top: -30px;
  background-color: hsl(150, 100%, 66%);
}

.random .random__btn {
  position: relative;
  top: 0px;
  width: 60px;
  height: 60px;
  border: none;
  border-radius: 50%;
  cursor: pointer;
  background-color: #0000;
  background-image: url('images/icon-dice.svg');
  background-repeat: no-repeat;
  background-position: center;
  transition: .3s
}

.random .random__btn:hover {
  box-shadow: 0 0 40px 0 hsl(150, 100%, 66%);
  -webkit-box-shadow:0 0 40px 0 hsl(150, 100%, 66%);
}

@media screen and (min-width: 36em) {
  .container {
    width: 34em;
  }

  .container__advice .advice-id {
    font-size: 0.875rem;
  }

  .advice {
    padding-bottom: 40px;
  }

  .divide {
    padding-bottom: 100px;
  }
}
</style>
