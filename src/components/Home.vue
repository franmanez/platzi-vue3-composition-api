<template>
  <div>Home: Composition API</div>
  <p>{{ text }}</p>
  <h1>Contador 1s - {{ counter }}</h1>
  <h1>Contador 0.5s - {{ obj.count }}</h1>
  <p>COMPUTED SAMPLE</p>
  <div>{{ firstName }} {{ lastName }}</div>
  <div>{{ fullName }} </div>
  <h2>{{ saludoDia }} </h2>
  <h3>nombre de usuario (provide-inject): {{ username }}</h3>
  <h3>template REFs</h3>
  <button ref="btn">Click!</button>
</template>

<script>

import { ref, reactive, onMounted, watch, computed, toRefs, inject } from 'vue'

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Home',
  props: {
    saludo: String,
    dia: Number
  },
  setup (props, ctx) {
    const text = ref('Hola vue')
    text.value = 'Hola vue modificado'
    const counter = ref(0)
    const obj = reactive({ count: 0 })

    const { saludo, dia } = toRefs(props)

    setInterval(() => counter.value++, 1000)
    setInterval(() => obj.count++, 500)

    const firstName = ref('Fran')
    const lastName = ref('Manez')

    const fullName = computed(() => {
      return `${lastName.value}, ${firstName.value}`
    })

    const saludoDia = computed(() => {
      return `Mi saludo es: ${saludo.value}, hoy es el dia ${dia.value}`
    })

    // provide inject
    const username = inject('username')
    console.log(username)

    // template ref
    const btn = ref(null)
    console.log(btn.value)

    // el primer parametro se pone en forma de función si se usa REACTIVE
    // el primer parametro se pone en forma de "parámetro normal" si se usa REF
    watch(() => obj.count, (newValue, oldValue) => {
      console.log(newValue, oldValue)
    })

    watch(btn, (valor) => {
      console.log(valor)
    })

    onMounted(() => {
      console.log('mounted')
    })

    return {
      text,
      counter,
      obj,
      firstName,
      lastName,
      fullName,
      saludoDia,
      username,
      btn
    }
  }
}
</script>
