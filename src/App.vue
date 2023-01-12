<template>
  <nav id="nav-bar">
    <div class="logo">SPORT™</div>
    <ul>
      <li><router-link style="text-decoration: none;" to="/">Home</router-link></li>
      <li><a href="#matches">Matches</a></li>
      <li><a href="#bookmark-history">BookMarks</a></li>
      <li><router-link style="text-decoration: none;" to="/Sign-up">My Account</router-link></li>
    </ul>
  </nav>
  <!-- #################################### -->
  <!-- #################################### -->
  <router-view/>
</template>

<style scoped>
@import './assets/css/reset-navigator.css';
@import './assets/css/appVue.css';
@import './assets/css/modal.css';
</style>

<script>
        window.onscroll = function (event) {
          var scroll = window.pageYOffset;
          if (scroll > 250) {
              document.getElementById('nav-bar').classList.add('scrolled');
          }
          if (scroll < 250) {
            document.getElementById('nav-bar').classList.remove('scrolled');
          } 
        }
</script>



