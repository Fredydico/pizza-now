<template>
  <div class="formOrder">
    <div class="container d-flex">
      <div class="pizza-selection">
        <section>
          <h2 class="">Choose Your Pizza</h2>
          <div class="row d-flex flex-wrap" id="pizza-list">
            <div v-for="pizza in PizzaData" :key="pizza.id" class="col-4 d-flex justify-content-center">
              <input type="radio" :id="`pizza-${pizza.id}`" :value="pizza" v-model="form.pizza" class="btn-check" @change="setDefaultSize" />
              <pizza-card :pizza="pizza" :isSelected="form.pizza && form.pizza.id === pizza.id"></pizza-card>
            </div>
          </div>
        </section>
        <h2 class="">Custom Pizza</h2>
        <h3 class="h4">Size</h3>
        <div class="d-flex">
          <div class="form-check size-list" v-for="size in SizeData" :key="size.id">
            <input type="radio" class="form-check-input custom-radio" :id="`size-${size.id}`" :value="size" v-model="form.size" :disabled="!form.pizza" />
            <label class="form-check-label" :for="`size-${size.id}`">
              {{ size.name }}
              <span class="text-muted" v-if="size.extra_price > 0"> (+ {{ toCurrency(size.extra_price) }}) </span>
            </label>
          </div>
        </div>

        <h3 class="h4 mt-4">Toppings</h3>
        <div class="row">
          <div class="col-6 col-md-4 col-lg-3 col-xl-2 mb-4" v-for="topping in ToppingData" :key="topping.id">
            <input type="checkbox" class="btn-check" :id="`topping-${topping.name}`" autocomplete="off" v-model="form.toppings" :value="topping" :disabled="!form.pizza || !form.pizza.toppings.includes(topping.id)" />
            <label class="btn d-block rounded-pill btn-topping" :for="`topping-${topping.name}`">
              {{ topping.name }}
            </label>
          </div>
        </div>
      </div>

      <div class="order-invoice">
        <h3 class="paySum">Payment Summary</h3>
        <div class="summary-item">
          <div v-if="form.pizza">{{ form.pizza.name }}</div>
          <div v-if="form.pizza">{{ toCurrency(form.pizza.discount.final_price) }}</div>
        </div>
        <div class="summary-item">
          <div v-if="form.size">Size - {{ form.size.name }}</div>
          <div v-if="form.size">{{ toCurrency(form.size.extra_price) }}</div>
        </div>
        <div class="summary-item" v-for="topping in form.toppings" :key="topping.id">
          <div>{{ topping.name }}</div>
          <div>{{ toCurrency(topping.price) }}</div>
        </div>
        <div class="d-flex justify-content-between total">
          <h3 class="totalDef">Total Price</h3>
          <h3 class="totalPr">{{ toCurrency(countTotalPrice) }}</h3>
        </div>
        <button class="nav-link" id="order" @click="showModal">Order Now</button>
      </div>
    </div>

    <OrderSuccessModal :isVisible="isModalVisible" @close="isModalVisible = false" />
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import PizzaList from "@/assets/json/pizza-list.json";
import SizeList from "@/assets/json/size-list.json";
import ToppingList from "@/assets/json/topping-list.json";
import PizzaCard from "@/components/pages/PizzaCard.vue";
import OrderSuccessModal from "@/components/pages/OrderSuccessModal.vue"; // Adjust the path as necessary

const PizzaData = ref(PizzaList.data);
const SizeData = ref(SizeList.data);
const ToppingData = ref(ToppingList.data);

const form = ref({
  pizza: null,
  size: null,
  toppings: [],
});

const isModalVisible = ref(false);

const showModal = () => {
  isModalVisible.value = true;
};

const setDefaultSize = () => {
  if (form.value.pizza) {
    form.value.size = SizeData.value[0];
    form.value.toppings = [];
  }
};

const countTotalPrice = computed(() => {
  let total = 0;

  if (form.value.pizza) {
    total += form.value.pizza.discount.final_price || 0;
  }

  if (form.value.size) {
    total += form.value.size.extra_price || 0;
  }

  if (form.value.toppings.length > 0) {
    form.value.toppings.forEach((topping) => {
      total += topping.price || 0;
    });
  }

  return total;
});

const toCurrency = (value) => {
  return `$${value.toFixed(2)}`;
};
</script>

<style>
.formOrder {
  margin: 8.875rem;
}

.container {
  display: flex;
}

.pizza-selection {
  flex: 1;
}

.order-invoice {
  margin-left: 2rem;
  padding: 1rem;
  width: 300px;
  padding-top: 20px;
  border: none;
}

.paySum {
  color: #e77e23;
  font-weight: bold;
  font-size: 25px;
}

.summary-item {
  display: flex;
  justify-content: space-between;
  margin-bottom: 0.5rem;
  padding-top: 10px;
  color: #6e6e6e;
  font-size: 18px;
}

.total {
  padding-top: 35px;
}

.totalDef {
  font-weight: 100;
  font-size: 25px;
}

.totalPr {
  color: orange;
}

#order {
  color: white;
  font-size: 1.3rem;
  font-weight: 500;
  margin-top: 25px;
  background-color: #e77e23;
  width: 100%;
  height: 40px;
  text-align: center;
  border-radius: 50px;
}

.formOrder h2 {
  margin-bottom: 2.25rem;
  color: orange;
  font-size: 45px;
  font-weight: bold;
}

.formOrder section {
  margin-bottom: 6.875rem;
}

.size-list {
  font-size: 17px;
}

.row {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.col-4 {
  flex: 1 1 30%;
  max-width: 30%;
}

#pizza-list {
  width: 1000px;
  height: auto;
}

.btn-topping {
  border: 1px solid #e77e23;
  color: #e77e23;
  padding: 0.5rem 1rem;
  border-radius: 50px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s ease-in-out, color 0.3s ease-in-out;
  background-color: #fff;
  width: 100%;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 10px;
  text-transform: capitalize;
}

.custom-radio {
  display: none;
}

.custom-radio + .form-check-label {
  position: relative;
  padding-left: 30px;
  cursor: pointer;
}

.custom-radio + .form-check-label::before {
  content: "";
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  width: 20px;
  height: 20px;
  border: 1px solid #e77e23;
  border-radius: 50%;
  background: white;
  transition: background 0.3s, border-color 0.3s;
}

.custom-radio:checked + .form-check-label::before {
  border: 5px solid #e77e23;
}
</style>
