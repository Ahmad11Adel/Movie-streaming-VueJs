<script setup>
import InputSearch from "@/components/InputSearch.vue";



</script>
<template>
  <header>
    <div class="container">
      <div class="navbar">
        <div class="header-logo">
          <router-link to="/">
           <!-- Header  Movies Logo -->
            <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTPQDYau3Hs4-xw1i8jVSUY4BlF4FLmg8lQqg&usqp=CAU"
             alt="Movie" >
          </router-link>
      
        </div>
         <!-- Navbar Page List  -->
        <nav class="header-bar" >
          <div>
            <router-link active-class="actives" to="/">Home</router-link>
            <router-link active-class="actives" to="/movie"> Movie</router-link>
            <router-link active-class="actives" to="/actor">Actor</router-link>
          </div>
        </nav>

        <nav class="login" :class="{ active: isShow == true }">
          <div>
            <router-link active-class="actives" to="/login">Login</router-link>
            <router-link active-class="actives" to="/register"
              >Register</router-link
            >
             <!-- Search Input-->
            <InputSearch  />
          </div>
        </nav>
      </div>
    </div>
  </header>
</template>













<style lang="scss" scoped>
a {
  text-decoration: none;
}

header {
  display: flex;
  padding: 5px;
  background: black;
  align-items: center;
  border-bottom: 1px solid white;

  .header-logo {
    display: flex;

    img {
      width: 50px;
      height: 55px;
    }

    .hamburger-btn {
      display: none;

      .open-menu {
        color: white;
        background: #fff;
      }

      .close-menu {
        color: white;
        fill: white;
      }
    }
  }

  .navbar {
    display: flex;
    justify-content: space-around;
    align-items: center;

    .header-bar {
      padding: 5px;
      margin-left: 10px;

      div {
        display: flex;
        align-items: center;
      }

      a {
        color: white;
        margin-right: 10px;
        padding: 10px;
        font-size: 18px;

        &:hover {
          background: #3fb883;
          color: white;
        }
      }
    }

    .login {
      div {
        display: flex;
      }

      a {
        color: white;
        padding: 10px;
        margin-left: 18px;
        font-size: 18px;

        &:hover {
          background: #3fb883;
          color: white;
        }
      }
    }
  }
}

@media screen and (max-width: 750px) {
  .header-logo {
    width: 100%;
    justify-content: space-between;
    align-items: center;

    .hamburger-btn {
      display: flex !important;

      svg {
        margin-top: 10px;
      }
    }
  }

  .navbar {
    flex-direction: column;
    margin-bottom: 20px;

    .header-bar {
      width: 100%;
      display: none;

      div {
        flex-direction: column;
        text-align: center;
      }

      a {
        width: 100%;
        margin-bottom: 10px;
        text-align: center;
      }
    }

    .login {
      width: 100%;
      display: none;

      div {
        flex-direction: column;
        align-items: center;
        text-align: center;
      }

      a {
        width: 100%;
        margin-bottom: 8px;
        margin-right: 18px;
      }

      input {
        margin-right: 5px;
        width: 90%;
      }
    }
  }

  .active {
    display: flex !important;
    flex-direction: column;
    text-align: center;
  }
}
</style>
