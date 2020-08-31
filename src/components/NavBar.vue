<template>
  <div class="nav-wrap">
    <b-navbar toggleable='lg' class='nav-bar'>
      <b-navbar-brand href='#'>
          <img src='../assets/header-logo/header-logo.png' class='logo' alt=''>
      </b-navbar-brand>
      <b-navbar-toggle target='nav-collapse'></b-navbar-toggle>
      <b-collapse id='nav-collapse' is-nav>
      <b-navbar-nav class='ml-auto' right>
          <div class="items-menu">
            <b-nav-item href='#' class="font-weight-bold" active>DOGS</b-nav-item>
            <b-nav-item href='#' disabled>FAGS</b-nav-item>
            <b-nav-item href='#' disabled>CONTACT US</b-nav-item>
          </div>
          <div class='img-emirates'>
            <img src='../assets/nav-bar/united-arab-emirates.svg' class='icon-nav-item' alt=''>
          </div>
          <b-button size='sm' class='my-2 my-sm-0 btn-sign-in'>
            SIGN IN</b-button>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: 'NavBar',
};
</script>

<style scoped>
    .nav-bar {
        background: white;
        color: #6B1D57;
    }
    .nav-item a {
        color: #6B1D57 !important;
        font-size: 1.17em;
    }
    .active {
      border-bottom: 3px solid #6B1D57;
    }
    .logo {
        width: 150px;
        height: 56px;
    }
    .icon-nav-item {
        width: 23.49px;
        height: 23.49px;
    }
    .items-menu {
      display: flex;
      width: 273px;
    }
    .nav-item {
      height: 29.5px;
    }
    .nav-wrap {
      width: 100%;
      height: 120px;
      background: white;
      display: flex;
      justify-content: center;
      flex-direction: column;
      align-items: center;
    }
    @media (min-width: 576px) {
        .navbar {
          width: 1189.59px;
        }
    }
    .navbar {
      width: 100%;
      margin-top: 18px;
    }
    .img-emirates {
      width: 80px;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .btn-sign-in {
      width: 119.59px;
      height: 48.82px;
      background: white !important;
      color: #6B1D57 !important;
      border: 2px solid #6B1D57;
    }
</style>
