<template>
  <v-container>
    <v-layout align-center class="info_box">
      <v-flex sm2 x12 offset-sm9>
        <h1>You Basket</h1>
        <div>Buy what you want and enjoy your time in our's mall</div>
      </v-flex>
    </v-layout>
    <v-layout align-center class="info_box" row wrap>
      <v-flex sm2 xs12 offset-sm1>
        <h1>You Basket</h1>
        <div>Buy what you want and enjoy your time in our's mall</div>
      </v-flex>
      <v-flex sm2 xs12>
        <h1>You Basket</h1>
        <div>Buy what you want and enjoy your time in our's mall</div>
      </v-flex>
      <v-flex sm2 xs12>
        <h1>You Basket</h1>
        <div>Buy what you want and enjoy your time in our's mall</div>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.info_box .flex div {
  background-color: white;
  padding: 20px;
  margin: 8px;
}
.info_box .flex h1 {
  border-radius: 5px;  
  border: solid white;
  padding: 10px;
  margin-bottom: 5px;
  color: orangered;
  text-align: center;
  font-weight: bold;
  text-transform: uppercase;
  font-size: 16px
}
.layout:first-child {
  height: 40vh;
}
.layout:last-child {
  height: 40vh;
}
</style>>
