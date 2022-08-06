<template>
  <div class="hello">
    <h1 class="text-center animate__animated animate__bounce">{{ msg }}</h1>
    <span>{{ this.prefix + Number.parseFloat(this.value).toFixed(this.precision) }}</span>
  </div>
</template>

<script>
export default {
  name: 'PriceItem',
  props: {
    msg: String,
    value: Number,
        prefix: {
            type: String,
            default: 'Rp'
        },
        precision: {
            type: Number,
            default: 2
        }
  }
}
</script>

