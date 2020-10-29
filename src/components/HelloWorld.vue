<template>
  <div class="hello">
    <p>
      Тестовое задание Vue.js

Необходимо реализовать компонент с методом validate.
Компонент может быть вложен сам в себя.

При вызове метода validate, необходимо что - бы компонент вызывал данный метод у своих непосредственных детей.

Схематично:

<pre v-text="vtext"></pre>

Вызов метода validate у компонента 1 должен вызвать данный метод у компонентов 2,3,5.
Вызов метода у компонента 3 должен вызвать метод у компонента 4.

Вложенность компонентов может быть неограничена.

    </p>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      vtext: `
<!-- 1 -->  <validate-component>
              <some-component>
    <!-- 2 -->  <validate-component></validate-component>
              </some-component>
              <some-component>
    <!-- 3 -->  <validate-component>
      <!-- 4 -->  <validate-component/>
                </validate-component>
              </some-component>
<!-- 5 -->  <validate-component></validate-component>
            </validate-component>`,
    };
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
