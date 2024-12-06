<template>
  <div class="pizza-container">
    <label :for="`pizza-${pizza.id}`" class="pizza-card d-flex" :class="{ selected: isSelected }">
      <div class="row text-center">
        <img :src="imageUrl(pizza.name)" :alt="`${pizza.name} Image`" class="pizza-card-image" height="125" />
      </div>
      <div>
        <div class="pizza-card-body">
          <h3 class="h5">
            {{ pizza.name }}
          </h3>
          <div class="price">
            <span>{{ toCurrency(pizza.discount.final_price) }}</span>
            <span class="ms-2 opacity-75" v-if="pizza.discount.is_active">
              <del>{{ toCurrency(pizza.price) }}</del>
            </span>
          </div>
        </div>
      </div>

      <img v-if="pizza.discount.is_active" class="pizza-card-ribbon" src="@/assets/image/ribbon.svg" alt="offer-ribbon" />
    </label>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  pizza: {
    type: Object,
    required: true,
  },
  isSelected: {
    type: Boolean,
    default: false,
  },
});

const imageUrl = (imageName) => {
  return new URL(`../../assets/image/${imageName}.png`, import.meta.url).href;
};

const toCurrency = (value) => {
  return `$${value.toFixed(2)}`;
};
</script>

<style>
.pizza-container {
  display: flex;
  justify-content: space-between;
  width: 100%;
}

.pizza-card {
  position: relative;
  overflow: hidden;
  border-radius: 25px;
  border: 1px solid rgba(51, 51, 51, 0.2);
  cursor: pointer;
  z-index: 90;
  display: flex;
  transition: background-color 0.3s ease-in-out, border-color 0.3s ease-in-out;
  font-size: 1.125rem;
  height: 175px;
  width: 300px;
}

.pizza-card.selected {
  background-color: #e77e23;
  color: white;
}

.pizza-card.selected:hover {
  background-color: #e77e23;
  color: white;
}

.pizza-card:hover {
  background-color: rgba(231, 126, 35, 0.3);
}

.pizza-card-image {
  margin: auto;
  transition: transform 0.3s ease-in-out;
}

.pizza-card:hover .pizza-card-image {
  transform: rotate(15deg);
}

.pizza-card-body {
  display: flex;
  height: 100%;
  flex-direction: column;
  justify-content: center;
}

.pizza-card-ribbon {
  position: absolute;
  inset: 0 0 auto auto;
  max-height: 60%;
  max-width: 50%;
}

.h5 {
  font-size: 1.5rem;
  padding-left: 10px;
}

.price{
  display: flex;
  align-items: center;
  font-size: 1.3rem;
  padding-left: 10px;
}
</style>
