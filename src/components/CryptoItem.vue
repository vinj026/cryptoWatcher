<template>
  <div class="itemContainer">
    <table class="Table">
      <thead>
        <tr>
          <th class="sticky">
            <p class="coinCell">Coin</p>
          </th>
          <th>Price</th>
          <th>1h</th>
          <th>24h</th>
          <th>7d</th>
          <th>Volume</th>
          <th>Market Cap</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items">
          <td class="sticky">
            <div class="coinCell">
              <img :src="item.image" class="cryptoImg" alt="Crypto Logo" />
              <p>{{ item.name }}</p>
            </div>
          </td>
          <td>{{ item.current_price }}</td>
          <td>
            {{ item.price_change_percentage_1h_in_currency.toFixed(2) }}
          </td>
          <td>
            {{ item.price_change_percentage_24h_in_currency.toFixed(2) }}
          </td>
          <td>
            {{ item.price_change_percentage_7d_in_currency.toFixed(2) }}
          </td>
          <td>{{ priceFormat(item.total_volume) }}</td>
          <td>{{ priceFormat(item.market_cap) }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const isLoading = ref(true);
const items = ref();

console.log(items.value);
onMounted(async () => {
  try {
    const response = await fetch(
      "https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=10&page=1&price_change_percentage=1h,24h,7d",
    );
    if (!response.ok) throw new Error(`ERROR Cuy, Status: ${response.status} `);
    const data = await response.json();
    items.value = data;
    console.log(items.value);
  } catch (err) {
    throw new Error(`Error Euy: ${err.message}`);
  } finally {
    isLoading.value = false;
  }
});

const priceFormat = (price) => {
  return price.toLocaleString("en-US");
};
</script>

<style lang="css" scoped>
.itemContainer {
  position: relative;
  display: flex;
  box-sizing: border-box;
  padding: 32px 52px;
  width: 100%;
  color: #fff;
  overflow-x: auto;
}

.Table {
  width: 100%;
  min-width: 100%;
  text-align: center;
  border-collapse: collapse;
}

.Table th {
  font-weight: 700;
  font-size: 1.2em;
}

.Table td {
  font-weight: 500;
  font-size: 1em;
  color: #e7e8e7;
}

.coinCell {
  display: flex;
  align-items: center;
  gap: 16px;
}

th.sticky,
td.sticky {
  align-items: center;
  gap: 16px;
}

th,
td {
  text-align: right;
}

.cryptoImg {
  width: 16px;
  height: 16px;
}

/* ===== Medium Screen (Tablet, 768px - 1024px) ===== */
@media (max-width: 1024px) {
  .itemContainer {
    width: 100%;
    padding: 16px;
  }

  th,
  td {
    text-align: right;
    padding: 0 20px;
  }
}

/* ===== Small Screen (Mobile, 480px - 768px) ===== */
@media (max-width: 768px) {
  body {
    font-size: 14px;
  }

  .itemContainer {
    width: 100%;
    padding: 0;
    overflow-x: auto;
  }

  .Table {
    min-width: 100%;
  }

  th,
  td {
    min-width: 75px;
    padding: 0 10px;
  }

  td.sticky,
  th.sticky {
    position: sticky;
    left: 0;
    background-color: #0a0a09;
    z-index: 1;
    text-align: left;
    padding: 0px 20px;
    box-shadow: inset -1px 0 #333;
  }

  th.sticky {
    background-color: #0a0a09;
    z-index: 2;
  }

  td.sticky {
    background-color: #0a0a09;
    z-index: 1;
  }
}
</style>
