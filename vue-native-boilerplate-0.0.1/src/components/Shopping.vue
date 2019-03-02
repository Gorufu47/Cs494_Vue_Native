<template>
  <center>
    <div>
      <section>
        <b-button-group>
          <b-btn variant="danger" v-b-toggle.cart>Cart</b-btn>
          <b-btn variant="success" v-b-toggle.products>Products</b-btn>
        </b-button-group>
        <hr>
        <h5>Total Price: {{ getTotalPrice() }} Baht</h5>
      </section>
      <b-collapse accordion="shoppingOne" id="cart" :visible="false">
        <section>
          <b-button-group>
            <b-btn variant="success" :disabled="isEmpty() ? '' : undefined">Purchase All</b-btn>
            <b-btn
              variant="danger"
              :disabled="isEmpty() ? '' : undefined"
              @click="emptyCart"
            >Empty Cart</b-btn>
          </b-button-group>
        </section>
        <section :class="'shopping-cart'">
          <h5 v-if="isEmpty()" class="empty-text">Empty Cart</h5>
          <b-card-group deck :style="{'padding':'15px'}">
            <b-card v-for="(order,index) in cart" :key="index" no-body :class="'fixed-width'">
              <b-card-header>
                <h4>{{order.product.name}}</h4>
              </b-card-header>
              <b-card-img :src="order.product.imgSrc"></b-card-img>
              <b-card-body>
                <p>Quantity: {{order.quantity}}</p>
                <p>Total: {{order.quantity * order.product.price}} Baht</p>
              </b-card-body>
              <b-card-footer>
                <b-btn-group>
                  <b-btn
                    variant="danger"
                    @click="removeOneFromCart(order)"
                  >Remove One ({{order.quantity}})</b-btn>
                  <b-btn variant="danger" @click="removeAllFromCart(order)">Remove All</b-btn>
                </b-btn-group>
              </b-card-footer>
            </b-card>
          </b-card-group>
        </section>
      </b-collapse>
      <b-collapse accordion="shoppingOne" visible id="products">
        <center>
          <section>
            <b-card-group deck>
              <b-card
                v-for="(product,index) in products"
                :key="index"
                no-body
                :class="'fixed-width'"
              >
                <b-card-img :src="product.imgSrc"></b-card-img>
                <b-card-header>
                  <h4>{{product.name}}</h4>
                </b-card-header>

                <b-card-body>
                  <p>{{product.description}}</p>
                  <p>Price: {{product.price}} Baht</p>
                </b-card-body>
                <b-card-footer>
                  <b-btn variant="primary" @click="addToCart(product)">Buy</b-btn>
                </b-card-footer>
              </b-card>
            </b-card-group>
          </section>
        </center>
      </b-collapse>
    </div>
  </center>
</template>
<script>
export default {
  name: "ShoppingCart",
  props: {},
  data() {
    return {
      cart: [],
      products: [
        {
          imgSrc: (() => require("@/assets/product1.png"))(),
          name: "iPhone Xr",
          description:
            "All-screen design. Longest battery life ever in an iPhone.",
          price: 28000
        },
        {
          name: "Samsung Galaxy Note 9",
          imgSrc: (() => require("@/assets/product5.png"))(),
          description:
            "Galaxy Note has always put powerful technology in the hands of those who demand more.",
          price: 33000
        },
        {
          imgSrc: (() => require("@/assets/product4.png"))(),
          name: "Honor",
          description:
            "Edge-to-edge all-screen design with a high screen-to-body ratio and 2160 x 1080 FHD+ resolution.",
          price: 12000
        },
        {
          imgSrc: (() => require("@/assets/product3.png"))(),
          name:
            "iPhone X",
          description:
            "iPhone X introduces a revolutionary design with a stunning all-screen ",
          price: 33000
        },
        {
          imgSrc: (() => require("@/assets/product2.png"))(),
          name:
            "iPhone Xs",
          description:
            "Apple Design",
          price: 39000
        },
      ],
      isEmpty() {
        return this.cart.length == 0;
      }
    };
  },
  methods: {
    addToCart(product) {
      let find = this.cart.findIndex(x => x.product == product);
      if (find != -1) {
        this.cart[find].quantity++;
      } else {
        this.cart.push({
          product: product,
          quantity: 1
        });
      }
    },
    emptyCart() {
      this.cart = [];
    },
    removeOneFromCart(order) {
      let find = this.cart.findIndex(x => x == order);
      if (find != -1) {
        if (this.cart[find].quantity == 1) this.cart.splice(find, 1);
        else this.cart[find].quantity--;
      }
    },
    removeAllFromCart(order) {
      let find = this.cart.findIndex(x => x == order);
      if (find != -1) {
        this.cart.splice(find, 1);
      }
    },
    getTotalPrice() {
      let sum = 0;
      this.cart.forEach(order => {
        sum += order.quantity * order.product.price;
      });
      return sum;
    }
  }
};
</script>
<style scoped>
section {
  margin-bottom: 25px;
}
.shopping-cart {
  border: dashed rgb(224, 34, 34) 2px;
  border-radius: 5px;
  min-height: 350px;
}
.shopping-cart > .empty-text {
  line-height: 350px;
  user-select: none;
  width: 100%;
  text-align: center;
  padding: 15px;
}
.fixed-width {
  min-width: 300px;
  max-width: 300px;
}
</style>