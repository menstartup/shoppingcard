<template>
  <v-container>
    <v-row>
      <v-col offset-md="1" md="5">
        <h1>ALL OUR ITEMS</h1>
        <div class="pa-2" id="info">
          <v-simple-table>
            <template v-slot:default>
              <thead>
                <tr>
                  <th class="text-center">NAME OF ITEM</th>
                  <th class="text-center">Price</th>
                  <th class="text-center" width="20%">ADD TO BASKET</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in desserts" :key="item.name">
                  <td>
                    <span class="nameofitem">{{ item.name }}</span>
                    <br />
                    <span class="descriptionofitem">{{item.description}}</span>
                  </td>
                  <td>{{ item.price }}</td>
                  <td class="text-center">
                    <v-btn text color="orange" @click="addItem(item)">
                      <v-icon>mdi-plus-box</v-icon>
                    </v-btn>
                  </td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>
        </div>
      </v-col>
        <!-- basket item -->
      <v-col offset-md="1" md="4">
          <h1 class="text-left">YOUR BASKET</h1> 
        <div class="pa-2" id="info">
            <v-simple-table>
            <template v-slot:default>
              <thead>
                <tr>
                  <th class="text-center" width="30%">Quantity</th>
                  <th class="text-left" width="60%">NAME OF ITEM</th>
                  <th class="text-right" width="10%">Price</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in basket" :key="item.name">
                  <td class="text-center">
                      <v-icon color="orange" @click="increaseQtn(item)">mdi-plus-box</v-icon>
                    {{item.quantity}}
                      <v-icon color="orange" @click="deIncreaseQtn(item)">mdi-minus-box</v-icon>
                    </td>
                  <td>
                    <span class="nameofitem">{{ item.name }}</span>
                  </td>
                  <td class="text-right">{{ item.price }}</td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>
          <v-divider></v-divider>
          <v-row class="mt-4">
              <v-col>
                  <p>Subtotal:</p>
                  <p>Delivery:</p>
                  <p>Total amount:</p>
              </v-col>
              <v-col class="text-right">
                  <p>{{subTotal}} UKK</p>
                  <p>{{deliveryCharge}} UKK</p>
                  <p><b>{{totalAmount}} UKK</b> </p>
                  <v-spacer></v-spacer>
          <v-btn class="text-right" color="orange">check out</v-btn>
              </v-col>
          </v-row>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    desserts: [
      {
        name: "apple",
        price: 100,
        description:
          "Select your desired component from below and see the available props, slots, events and functions."
      },
      {
        name: "banana",
        price: 300,
        description:
          "Select your desired component from below and see the available props, slots, events and functions."
      },
      {
        name: "orange",
        price: 400,
        description:
          "Select your desired component from below and see the available props, slots, events and functions."
      },
      {
        name: "strawberry",
        price: 800,
        description:
          "Select your desired component from below and see the available props, slots, events and functions."
      }
    ],
    basket: [],
    
  }),
  computed: {
      subTotal() {
          var total = 0
          this.basket.forEach(res => {
              return total += res.price
          })
          return total
      },
      totalAmount() {
          return this.subTotal + this.deliveryCharge
      },
      deliveryCharge() {
          var shippingCharge = 0
          if(this.basket.length === 0) {
               shippingCharge = 0
          } else {
               shippingCharge = 10
          }
          return shippingCharge
      },
  },
  methods: {
      addItem(item) {
        //   var itemBasket = item;
        //   check if already exist item
        if(this.basket.find(res => {
            return res.name === item.name
        })) {
            item = this.basket.find(res => {
            return res.name === item.name
            })
            this.increaseQtn(item)
        } else {
            this.basket.push(
              {
                  name: item.name,
                  price: item.price,
                  stablePrice: item.price,
                  quantity: 1
              }
          )
        }
      },
      increaseQtn(item) {
          item.quantity++
          item.price = item.stablePrice * item.quantity
      },
      deIncreaseQtn(item) {
          item.quantity--
          item.price = item.stablePrice * item.quantity
          if(item.quantity === 0) {
            this.basket.splice(this.basket.indexOf(item),1)
          }
      }
  }
};
</script>
<style lang="scss" scoped>
#info {
  background-color: white;
}
.col h1 {
  color: black;
  border: solid 3px white;
  margin-bottom: 5px;
  font-size: 22px;
  text-align: right;
  padding: 8px;
}
.col tr td .nameofitem {
  font-weight: bold;
}
.col tr td .descriptionofitem {
  font-style: italic;
  font-size: 12px;
}
</style>