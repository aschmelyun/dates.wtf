<template>
  <div id="app">
    <header>
      <img class="logo" src="/static/img/dates-wtf-logo.svg">
    </header>
    <main>
      <date-picker></date-picker>
    </main>
  </div>
</template>

<script>
import DatePicker from './components/DatePicker'

export default {
  name: 'app',
  components: {
    DatePicker
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: 'Lato', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
main {
  text-align: center;
  margin-top: 40px;
}
header {
  margin: 0;
  padding: 2rem 0;
  text-align: center;
}
</style>
