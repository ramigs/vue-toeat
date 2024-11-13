<script setup lang="ts">
import { ref, type Ref } from 'vue'

type Diet = 'vegan' | 'gluten-free' | 'pescatarian'

interface Dish {
  name: string
  diet?: Diet
}

// type RestaurantStatus = 'Want to try' | 'Recommended' | 'Do not recommend' | 'Must try'

enum RestaurantStatus {
  WantToTry = 'Want to try',
  Recommended = 'Recommended',
  DoNotRecommend = 'Do not recommend',
  MustTry = 'Must try',
}

//type RestaurantStatusUnion = `${RestaurantStatus}`

interface Restaurant {
  name: string
  status: RestaurantStatus
  dishes: Dish[]
}

const restaurantList: Ref<Array<Restaurant>> = ref([])
//const restaurantList = ref<Restaurant[]>([])
//const restaurantList = ref<Array<Restaurant>>([])
const newRestaurant: Ref<Restaurant> = ref({
  name: '',
  // why no complain about non existing address with : Ref<Restaurant>? but with ref<Restaurant> it does
  address: '',
  status: RestaurantStatus.WantToTry,
  dishes: [],
})

/* const newRestaurant = ref<Restaurant>({
  name: '',
  address: '',
  status: RestaurantStatus.WantToTry,
  dishes: [],
}) */

const addRestaurant = () => {
  restaurantList.value.push(newRestaurant.value)
  newRestaurant.value = {
    name: '',
    // why no complain?
    status: RestaurantStatus.WantToTry,
    dishes: [],
  }
}
</script>

<template>
  <main>
    <pre>{{ newRestaurant }}</pre>
    <form @submit.prevent="addRestaurant">
      <div>
        <label for="restaurant-name">Restaurant Name</label>
        <input type="text" id="restaurant-name" v-model="newRestaurant.name" />
      </div>
      <div>
        <label for="restaurant-status">Restaurant Status</label>
        <select id="restaurant-status" v-model="newRestaurant.status">
          <option v-for="status in Object.values(RestaurantStatus)" :key="status" :value="status">
            {{ status }}
          </option>
        </select>
      </div>
      <button type="submit">Add Restaurant</button>
    </form>
    <ul>
      <li v-for="restaurant in restaurantList" :key="restaurant.name">
        {{ restaurant.name }} - {{ restaurant.status }}
      </li>
    </ul>
  </main>
</template>
