<!-- Список должников -->
<template>
  <div>
    <h2>Таблица долгов:</h2>
    <br>
    <table class="table">
        <thead>
            <tr>
              <th scope="col">ID Должника</th>
              <th scope="col">ID Задолжности</th>
              <th scope="col">ID Портфеля</th>
              <th scope="col">Сумма задолжности</th>
            </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in info" :key="index">
              <td scope="row">{{item.id_person}}</td>
              <td>{{item.id_debt}}</td>
              <td>{{item.id_portfolio}}</td>
              <td>{{item.debt_sum}}</td>
          </tr>
        </tbody>
    </table>
  </div>

  
</template>

<script>
import Axios from 'axios';

export default {
  data() {
    return {
      info: null
    };
  },
  mounted() {
    Axios
      .get('/api/v1/debt')
      .then(response => (this.info = response.data.data));
  }
}
</script>