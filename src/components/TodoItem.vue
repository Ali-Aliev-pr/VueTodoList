<template>
  <div class="card">
  <div class="forBtn">
      <button class="btn trash" v-on:click="$emit('del', product.id)">
        <img class="trash-img" src="../assets/del.svg" >
      </button>
    </div>
    <img class="card__image" v-bind:src="product.imgUrl" width="332px" height="200px">
    <h2>{{product.name}}</h2>
    <h4>{{product.description}}</h4>
    <h4>{{product.price}}$</h4>
  </div>
</template>

<script>

export default {
  name: 'TodoItem',
  props: {
    product: {},
    methods: {}
  }
}
</script>

<style>
.btn {
  width: 50px;
  border: none;
  cursor: pointer;
  position: absolute;
  z-index: 14;
  right: -20px;
  top: -20px;
  display: none;
  justify-content: center;
  align-items: center;
  background-color: transparent !important;
}

.card {
  margin-bottom: 40px;
  margin-left: 40px;
  width: 332px;
  height: 423px;
  display: flex;
  flex-direction: column;
  box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
  border-radius: 4px;
  box-sizing: border-box;
  position: relative;
}
.card__image {
  border-top-left-radius: 4px;
  border-top-right-radius: 4px;
}
.card:hover .btn {
  display: flex;
}

.forBtn {
  display: flex;
  justify-content: flex-end;
}

h2 {
  text-align: center;
}
</style>