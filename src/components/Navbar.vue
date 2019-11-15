//src/components/Navbar.vue
<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="dark">
      <b-navbar-brand href="#">创意空间</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item-dropdown id="dropdown-1" text="创意工坊" class="m-2">
            <b-dropdown-item @click="vitrulazation()">地图可视化</b-dropdown-item>
            <b-dropdown-item>全国票房查看</b-dropdown-item>
            <b-dropdown-item>深圳房价可视化</b-dropdown-item>
            <b-dropdown-item @click="labzone()">各种实验区域</b-dropdown-item>
            <b-dropdown-divider></b-dropdown-divider>
            <b-dropdown-item active>Active action</b-dropdown-item>
            <b-dropdown-item disabled>Disabled action</b-dropdown-item>
          </b-nav-item-dropdown >
        </b-navbar-nav>

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <b-nav-form>
            <b-form-input size="sm" class="mr-sm-2" placeholder="Search"></b-form-input>
            <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
          </b-nav-form>

          <b-nav-item-dropdown text="Lang" right>
            <b-dropdown-item href="#">EN</b-dropdown-item>
            <b-dropdown-item href="#">ES</b-dropdown-item>
            <b-dropdown-item href="#">RU</b-dropdown-item>
            <b-dropdown-item href="#">FA</b-dropdown-item>
          </b-nav-item-dropdown>

          <b-nav-item-dropdown right>
            <!-- Using 'button-content' slot -->
            <template v-slot:button-content>
              <em>User</em>
            </template>
            <b-dropdown-item href="#">Profile</b-dropdown-item>
            <b-dropdown-item href="#">Sign Out</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <v-Content v-if="flag"></v-Content>
  </div>
</template>

<script>
  import VueEvent from '../model/VueEvent.js';
  import axios from "axios";
  export default {
    data() {
      return {
        msg: '这是Navbar的msg',
        flag: 1
      }
    },
    methods: {
      vitrulazation() {
        //console.log(this.flag)
        VueEvent.$emit('to-content', this.flag)
      },
      labzone() {
        console.log("This is lab zone")
      }
    },
    mounted() {
      axios
        .get("https://www.themealdb.com/api/json/v1/1/categories.php")
        .then(response => {
        this.meals = response.data.categories;
      })
        .catch(err => {
        console.log(err);
      });
    }
  };
</script>