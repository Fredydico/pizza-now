<template>
  <div v-if="isVisible" class="modal-overlay">
    <div class="modal-content">
      <img src="../../assets/image/OrderSuccess.png" alt="Success Image" />
      <h3>Order Success</h3>
      <p>Thank you, we have received your order successfully.</p>
      <button @click="closeModal" class="buttonClose">Close</button>
    </div>
  </div>
</template>

<script setup>
const props = defineProps(["isVisible"]);
const emit = defineEmits(["close"]);

const closeModal = () => {
  emit("close");
};
</script>

<style>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.modal-content {
  width: 300px;
  background: white;
  padding: 20px;
  border-radius: 8px;
  text-align: center;
  z-index: 1001;
}

img {
  width: 150px;
  margin: auto;
}

h3 {
  font-weight: bold;
}

p {
  font-size: 17px;
}

.buttonClose {
  color: white;
  font-size: 1.3rem;
  font-weight: 500;
  margin-top: 25px;
  background-color: #e77e23;
  width: 100%;
  height: 40px;
  text-align: center;
  border-radius: 50px;
  border: none;
}
</style>
