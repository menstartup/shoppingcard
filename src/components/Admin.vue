<template>
  <v-container>
    <v-row>
      <v-col offset-md="1" md="5">
        <h1>ADMIN PAGE</h1>
        <div class="pa-2" id="info">
          <v-simple-table>
            <template v-slot:default>
              <thead>
                <tr>
                  <th class="text-center">NAME OF ITEM</th>
                  <th class="text-center">Price</th>
                  <th class="text-center">Edit</th>
                  <th class="text-center">Remove</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in adminData" :key="item.name">
                  <td>
                    <span class="nameofitem">{{ item.name }}</span>
                    <br />
                    <span class="descriptionofitem">{{item.description}}</span>
                  </td>
                  <td>{{ item.price }}</td>
                  <td class="text-center">
                    <v-btn text color="orange" @click="editItem(item)">
                      <v-icon>mdi-pencil</v-icon>
                    </v-btn>
                  </td>
                  <td class="text-center">
                    <v-btn text color="orange" @click="deleteItem(item)">
                      <v-icon>mdi-delete</v-icon>
                    </v-btn>
                  </td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
    data: () => ({
    adminData: [
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
    })
};
</script>

<style>
</style>