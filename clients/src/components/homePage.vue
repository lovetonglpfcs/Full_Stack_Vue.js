<template>
  <!-- Header -->
  <header id="home" class="header">
    <!-- Navigation -->
    <nav class="nav">
      <div class="navigation container">
        <div class="logo">
          <h1>KNW Clothes Shop</h1>
        </div>

        <div class="menu">
          <div class="top-nav">
            <div class="logo">
              <h1>KNW Clothes Shop</h1>
            </div>
            <div class="close">
              <i class="bx bx-x"></i>
            </div>
          </div>

          <ul class="nav-list">
            <li class="nav-item">
              <router-link to="/checkStock">Products</router-link>
            </li>
            <li></li><li></li><li></li>
             <li class="nav-item">
              <router-link to="/historySale">History</router-link>
            </li>
          </ul>
        </div>

        <a href="cart.html" class="cart-icon">
          <i class="bx bx-shopping-bag"></i>
        </a>

        <div class="hamburger">
          <i class="bx bx-menu"></i>
        </div>
      </div>
    </nav>

    <!-- Hero -->
    <img src="../assets/img/banner.png" alt="" class="hero-img" />

    <div class="hero-content">
      <h1>
        <span>Summer Vibes</span>
        <span>mode on</span>
      </h1>
      <router-link to="/makeOrder"><a class="btn">shop now</a></router-link>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      image: "",
    };
  },
};
</script>

<style scoped>
:root {
  --white: #fff;
  --black: #222;
  --pink: #f60091;
  --grey: #444;
  --grey2: #959595;
  --grey-alt: #d1e2e9;
  --yellow: #ffd800;
  --green: #59b210;
}

*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}

html {
  scroll-behavior: smooth;
  box-sizing: border-box;
  font-size: 62.5%;
}

body {
  font-family: "Poppins", sans-serif;
  font-size: 1.6rem;
  font-weight: 400;
  background-color: #fff;
  color: #243a6f;
  position: relative;
  z-index: 1;
}

h1,
h2,
h3,
h4 {
  font-weight: 500;
}

a {
  color: inherit;
  text-decoration: none;
}

img {
  max-width: 100%;
}

li {
  list-style: none;
}

.container {
  max-width: 120rem;
  margin: 0 auto;
}

.container-md {
  max-width: 100rem;
  margin: 0 auto;
}

@media only screen and (max-width: 1200px) {
  .container {
    padding: 0 3rem;
  }

  .container-md {
    padding: 0 3rem;
  }
}

/* Header */
.header {
  position: relative;
  width: 100%;
  min-height: 100vh;
  background-color: var(--grey-alt);
  overflow: hidden;
}

.nav {
  padding: 1.6rem 0;
}

.nav.fix-nav {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: #243a6f;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
  z-index: 999;
}

.nav.fix-nav .nav-link,
.nav.fix-nav .logo,
.nav.fix-nav .cart-icon,
.nav.fix-nav .hamburger {
  color: #fff;
}

.navigation {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo h1 {
  font-size: 2.5rem;
}

.nav-list {
  display: flex;
  align-items: center;
}

.nav-item:not(:last-child) {
  margin-right: 0.5rem;
}

.nav-link:link,
.nav-link:visited {
  padding: 0.8rem 1rem;
  transition: all 300ms ease-in-out;
}

.nav-link.icon {
  font-size: 3rem;
}

.top-nav {
  display: none;
}

.hamburger {
  display: none;
}

.cart-icon {
  display: none;
}

@media only screen and (max-width: 768px) {
  .menu {
    position: fixed;
    top: 0;
    left: -100%;
    width: 80%;
    max-width: 40rem;
    height: 100%;
    background-color: #fff;
    transition: all 500ms ease-in-out;
    z-index: 100;
  }

  .menu.show {
    left: 0;
  }

  .top-nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    background-color: #243a6f;
    padding: 1rem 1.6rem;
  }

  .top-nav .logo {
    color: #fff;
  }

  .top-nav .close {
    color: #fff;
    font-size: 3rem;
    padding: 1rem;
    cursor: pointer;
  }

  .cart-icon {
    display: block;
    font-size: 3rem;
  }

  .hamburger {
    display: block;
    font-size: 3rem;
    padding: 0.5rem;
    cursor: pointer;
  }

  .nav-link:link,
  .nav-link:visited {
    display: block;
    font-size: 1.7rem;
    padding: 1rem 0;
  }

  .nav.fix-nav .nav-link {
    color: #243a6f;
  }

  .nav-list {
    flex-direction: column;
    align-items: start;
    padding: 1rem 1.6rem;
  }

  body.show::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    z-index: 4;
  }

  .nav.show {
    background-color: rgba(0, 0, 0, 0.8);
  }

  .nav-link.icon {
    display: none;
  }
}

/* Hero */
.header .hero-img {
  position: absolute;
  bottom: -10%;
  right: -5%;
  height: 45rem;
  object-fit: contain;
}

.hero-content {
  position: absolute;
  top: 50%;
  transform: translate(25%, -50%);
}

.hero-content h2 {
  color: #b888ff;
  font-size: 3rem;
  font-weight: 700;
  margin-bottom: 1rem;
}

.hero-content .discount {
  color: #fbb419;
}

.hero-content h1 span {
  color: #253b70;
  font-size: 6rem;
  font-weight: 700;
  display: block;
  line-height: 1;
  text-shadow: 3px 3px 0 #f1f1f1, 4px 4px 0 #f1f1f1;
}

.btn {
  display: inline-block;
  background-color: #fc7c7c;
  padding: 1.2rem 4rem;
  color: #fff;
  font-weight: 600;
  text-transform: uppercase;
  margin-top: 3rem;
}

@media only screen and (max-width: 1200px) {
  .header .hero-img {
    right: -20%;
  }

  .hero-content {
    transform: translate(20%, -50%);
  }

  .hero-content h2 {
    font-size: 2rem;
  }

  .hero-content h1 span {
    font-size: 5rem;
  }
}

@media only screen and (max-width: 996px) {
  .header {
    min-height: 70vh;
  }

  .header .hero-img {
    height: 40rem;
    right: -10%;
  }
}

@media only screen and (max-width: 567px) {
  .header {
    min-height: 100vh;
  }

  .header .hero-img {
    height: 40rem;
    bottom: -15%;
  }

  .hero-content {
    top: 40%;
    transform: translate(15%, -50%);
  }

  .header .hero-img {
    right: 0%;
  }

  .hero-content h2 {
    font-size: 1.8rem;
  }

  .hero-content h1 span {
    font-size: 4rem;
  }

  .hero-content a {
    padding: 1rem 3rem;
  }
}
</style>