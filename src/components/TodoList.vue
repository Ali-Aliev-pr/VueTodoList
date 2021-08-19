<template>
  <div class="father">
<!--    <ul>-->
<!--      <li v-for="(todo, a) of todos">{{todo}}: {{a + 1}}</li>-->
<!--    </ul>-->
<!--    <TodoItem name="Nikita"/>-->
    <div id="productRegistration">
      <h4>{{productName}}</h4>
      <input
          id="Input"
          type="text"
          v-bind:placeholder="namePlaceHolder"
          v-model="nameValue"
      />
      <h4>{{productDescription}}</h4>
      <textarea
          v-bind:placeholder="dexscriptionPlaceHolder"
          v-model="descriptionValue"
          class="description"
      ></textarea>
      <h4>{{imgSrc}}</h4>
      <input
          id="Input"
          type="text"
          v-bind:placeholder="imgSrcPlaceHolder"
          v-model="imgSrcValue"
      />
      <h4>{{productPrice}}</h4>
      <input
          id="Input"
          type="text"
          v-bind:placeholder="productPricwPlaceHolder"
          v-model="priceValue"
      />
      <button id="btn" v-on:click="notesAdd">{{buttonPlaceHolder}}</button>
    </div>
    <div class="products">
      <!--        <p>Cards</p>-->
      <TodoItem
          v-for="(product) in products"
          :key="product.id"
          :product="product"
          @del="del"
      />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";
export default {
  name: 'TodoList',
  components: {TodoItem},
  data() {
    return {
      nameValue: '',
      imgSrcValue: '',
      descriptionValue: '',
      priceValue: '',

      products: [{
        id: 0,
        name: 'Car',
        description: 'Big Red Car Whit Wheals And With Machine',
        imgUrl: 'http://wpsites.net/wp-content/uploads/2013/09/logo-2.png',
        price: '100'
      }],

      productName: 'Наименование товара',
      productDescription: 'Описание Товара',
      dexscriptionPlaceHolder: 'Введите описнание товара',
      namePlaceHolder: 'Введите наименование товара',
      imgSrc: 'Ссылка на изображения товара',
      imgSrcPlaceHolder: 'Введите ссылку',
      productPrice: 'Цена товара',
      productPricwPlaceHolder: 'Введите цену',
      buttonPlaceHolder: 'Добавить Товар'
    }
  },
  methods: {
    notesAdd() {
      if (this.priceValue === '') {
        alert('Есть пустое поле')
      } else if (this.nameValue === '') {
        alert('Есть пустое поле')
      } else if (this.descriptionValue === '') {
        alert('Есть пустое поле')
      } else {
        this.products.push({
          id: this.products.length,
          name: this.nameValue,
          description: this.descriptionValue,
          imgUrl: this.imgSrcValue,
          price: this.priceValue
      })
    }
    },
    del(id) {
      this.products = this.products.filter(product => {
        if (product.id !== id)
          return product
      })
    }
  }
}
</script>

<style>
  ul {
    list-style: none;
    display: flex;
    flex-wrap: wrap;
  }

  .products {
    display: flex;
    flex-wrap: wrap;
  }

  h4 {
    margin-left: 30px;
  }

  #productRegistration {
    padding-top: 5px;
    width: 350px;
    height: 600px;
    box-shadow: 0px 5px 8px 0px rgba(0, 0, 0, 0.15);
    box-sizing: border-box;
  }

  .father {
    display: flex;
    margin-left: 40px;
  }

  #Input {
    width: 200px;
    padding: 10px 10px;
    border: none;
    box-shadow: 0px 5px 8px 0px rgba(0, 0, 0, 0.15);
    margin-left: 30px;
    border-radius: 20px;
    outline: none;
  }

  .description {
    padding: 10px 10px;
    width: 244px;
    height: 108px;
    border: none;
    box-shadow: 0px 5px 8px 0px rgba(0, 0, 0, 0.15);
    margin-left: 30px;
    border-radius: 20px;
  }

  #btn {
    background-color: lightgrey;
    color: black;
    margin-left: 30px;
    margin-top: 30px;
    width: 293px;
    height: 30px;
    box-shadow: 0px 5px 8px 0px rgba(0, 0, 0, 0.15);
    border: none;
    border-radius: 20px;
  }

  #btn:hover {
    cursor: pointer;
  }

</style>