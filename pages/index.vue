<template>
  <section class="article-bloc" :class="mode">
      <h1 class="article-title">Combien d'oreillers dans votre vie ?</h1>
      <div class="article-img">
        <img :src="setPillowImg" alt="pretty pillow" title="pretty pillow">
      </div>
      <div class="article-quantity-bloc">
        <button v-if="quantity > 1" class="button-less" @click="setQuantity(-1)">-</button>
        <p class="quantity">{{ quantity }}</p>
        <button v-if="quantity <= 9" class="button-more" @click="setQuantity(1)">+</button>
      </div>
  </section>
</template>

<script>
import "@/assets/cart.css"

export default {
    data () {
      return {
        quantity: 1,
        mode: 'white'
      }
    },
    computed: {
      setPillowImg () {
        return '/img/pillows/' + this.quantity + '.png'
      }
    },
    mounted () {
      this.switchBackground(this.quantity)
    },
    methods: {
      setQuantity (value) {
        this.$set(this, 'quantity', this.quantity += value)
        this.switchBackground(this.quantity)
      },
      switchBackground (value) {
        if (value%2 === 0) {
          this.$set(this, 'mode', 'pink')
        } else {
          this.$set(this, 'mode', 'white')
        }
      }
    }
}
</script>

