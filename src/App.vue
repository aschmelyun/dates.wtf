<template>
  <div id="app">
    <header>
      <img class="logo" src="/static/img/dates-wtf-logo.svg">
    </header>
    <main>
      <date-picker></date-picker>
    </main>
    <footer>
      <div class="credit">Built by <a href="https://twitter.com/aschmelyun">@aschmelyun</a> &mdash; Vue + Netlify</div>
    </footer>
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
footer {
  text-align: center;
  font-size: 14px;
  font-weight: 400;
  color: #808E9B;
  position: fixed;
  right: 1rem;
  bottom: 1rem;
}
footer a {
  text-decoration: none;
  font-weight: 700;
  color: #485460;
}
</style>
