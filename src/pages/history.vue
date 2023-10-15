<script setup>
//import { RouterLink, RouterView } from 'vue-router'
import headermuf from "../views/headermuf.vue";
import { useShoppingStore } from "../store/movies";
const list = useShoppingStore();
</script>

<template>
  <RouterView></RouterView>
  <headermuf class="fixed-top"></headermuf>
  <div style="margin-top: 150px"></div>
  <h1 class="text-center fw-bold m-3">Order History</h1>
  <div class="main m-3 p-3 row">
    <table class="table text-center">
      <thead>
        <tr>
          <th scope="col">
            <img
              src="https://cdn-icons-png.flaticon.com/128/2664/2664691.png"
              alt=""
              style="max-width: 40px"
            />
          </th>
          <th scope="col"></th>
          <th scope="col">Name</th>
          <th scope="col">Price of movie</th>
          <th scope="col">Order</th>
          <th scope="col">Total price</th>
        </tr>
      </thead>
      <tbody v-for="(m, index) in list.total" :key="index" class="text-center">
        <tr v-for="(i, index) in list.order_history[index]" :key="index">
          <th>{{ index + 1 }}</th>
          <td>
            <div class="container">
              <img
                :src="i.img"
                class="m-3 rounded-4"
                alt="..."
                style="max-width: 150px"
              />
              <div class="middle">
                <div class="texts rounded-pill">คลิกเพื่อรับชม</div>
              </div>
            </div>
          </td>
          <td>{{ i.name }}</td>
          <td>{{ i.price }} Bath per month</td>
          <td>{{ i.quantity }} Month</td>
          <td>{{ i.price * i.quantity }} Bath</td>
        </tr>
        <tr class="rounded-pill shadow">
          <td class="va m-3 p-3" scope="row">
            total price <br />discount 10%<br />
            Order Total( {{ m[0] }} Month)
          </td>
          <td class="va m-3"></td>
          <td class="va m-3"></td>
          <td class="va m-3"></td>
          <td class="va m-3"></td>
          <td class="m-3" style="background-color: #b6def9">
            {{ m[2] }} Bath <br />{{ m[1] }} Bath <br />{{ m[2] - m[1] }} Bath
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped>
.flybt {
  position: fixed;
  right: 0px;
  bottom: 0px;
  margin: 1rem;
}
.va {
  background-color: #f9eeb6;
}
.container  {
  position: relative;
  width: 50%;
}

.image {
  opacity: 1;
  display: block;
  width: 100%;
  height: auto;
  transition: 0.5s ease;
  backface-visibility: hidden;
}

.middle {
  transition: 0.5s ease;
  opacity: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
  text-align: center;
}

.container:hover .image {
  opacity: 0.3;
}

.container:hover .middle {
  opacity: 0.6;
}

.texts {
  background-color: black;
  text-align: center;
  color: white;
  font-size: 16px;
  padding: 50px;
}
</style>
