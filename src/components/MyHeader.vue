<template>
  <div class="header" :class="[viewMobileMenu ? 'header__mb' : '']">
    <div class="container-fluid header__wrapper">
      <div class="header__logo">
        <h1>LOGO <span style="color: #fc732f">IPSUM</span></h1>
      </div>
      <div class="header__menu">
        <MenuIcon
          @click="toggleMenu()"
          class="header__menu__bar"
          style="text-align: right"
        />
        <ul class="menu" :class="[viewMobileMenu ? 'menu__mb' : '']">
          <li class="menu__item active">Dashboard</li>
          <li class="menu__item">Events</li>
          <li class="menu__item">Help</li>
          <li class="menu__item">Logout</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import MenuIcon from "./MenuIcon.vue";
export default {
  data() {
    return {
      viewMobileMenu: false,
    };
  },
  components: {
    MenuIcon,
  },
  watch: {
    viewMobileMenu(val) {
      if (val) {
        document.body.style.overflow = "hidden";
      } else {
        document.body.style.overflow = "auto";
      }
    },
  },
  methods: {
    toggleMenu() {
      console.log("here");
      this.viewMobileMenu = !this.viewMobileMenu;
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  background: #5c524d;
  &__mb {
    width: 100vw;
    height: 100vh;
  }
  &__logo {
    @media (max-width: 780px) {
      display: none;
      // background: green;
    }
  }
  &__wrapper {
    display: flex;
    justify-content: space-between;
    color: white;
    padding: 20px;
  }
  &__menu {
    // display: contents;
    // display: flex;
    width: 40%;
    font-style: normal;
    font-weight: 800;
    font-size: 36px;
    &__bar {
      display: none;
      @media (max-width: 780px) {
        width: 100%;
        display: block;
      }
    }
    @media (max-width: 780px) {
      width: 100%;
      // display: block;
    }
  }
}

.menu {
  display: inline-flex;
  justify-content: space-around;
  list-style: none;
  width: 100%;
  font-weight: 300;
  font-size: 20px;

  @media (max-width: 780px) {
    display: none;
  }

  &__mb {
    display: block;
  }
  &__item {
    padding: 2px 10px;
    &__mb {
      padding: 12px;
    }

    // padding: 20px;
  }
}
.active {
  border-bottom: 4px solid #86eaae;
}
</style>
