<template>
  <div>
    <table>
      <tr>
        <th>股票id</th>
        <th>股票名</th>
        <th>股票价格</th>
        <th>股票涨跌幅</th>
      </tr>
      <tr v-for="stock in stocks">
        <td>
          {{ stock.id }}
        </td>
        <td>
          {{ stock.name }}
        </td>
        <td>
          {{ stock.price }}
        </td>
        <td>
          {{ stock.rate }}
        </td>
      </tr>
    </table>
    {{ msg }}
  </div>
</template>

<script>
export default {
  name: "Stock",
  data() {
    return {
      msg: 'Hello Vue',
      stocks: [
        // {
        //   id: 1,
        //   name: "科技",
        //   price: 35.11,
        //   rate: +5.12
        // }, {
        //   id: 2,
        //   name: "药业",
        //   price: 55.2,
        //   rate: -1.2
        // }
      ]
    }
  },
  created() {
    const _this = this;
    axios.get('http://localhost:8081/stock/findAll').then(function (resp) {
      _this.stocks = resp.data;
    })
  }
}

</script>

<style scoped>

</style>