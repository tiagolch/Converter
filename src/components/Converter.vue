<template>
  <div class="convert">
    <h2>{{ currencyA }} to {{ currencyB }}</h2>
    <input type="text" v-model="valueCurrencyA" :placeholder="currencyA" />
    <input type="button" value="Convert" @click="convert" />
    <h2>{{ valueCurrencyB }}</h2>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Convert",
  props: ["currencyA", "currencyB"],
  data() {
    return {
      valueCurrencyA: "",
      valueCurrencyB: 0,
    };
  },
  methods: {
    convert() {
      let from = `${this.currencyA}`;
      let to = `${this.currencyB}`;
      let url =
        "https://api.exchangerate.host/convert?from=" +
        from +
        "&to=" +
        to +
        "&compact=y";

      fetch(url)
        .then((res) => {
          return res.json();
        })
        .then((json) => {
          let quotation = json["result"];
          this.valueCurrencyB = (
            quotation * parseFloat(this.valueCurrencyA)
          ).toFixed(2);
        });
    },
  },
};
</script>

<style scoped>
.convert {
  padding: 20px;
  margin-top: 20px;
  max-width: 300px;
  box-shadow: 0 4px 8px 0 rgba(10, 0, 145, 0.658);
  border-radius: 5px;
  background-color: #ecf1f8;
  text-align: center;
}
</style>