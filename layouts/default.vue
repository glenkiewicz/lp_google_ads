<template>
  <div class="wrapper">
    <header class="header">
        <a href="/" class="header__logo" title="Audyt Google za 0 zł | Up&More"><img src="~/assets/logo.png"></a>
    </header>
    <nuxt />
    <footer class="footer">
        <a href="/" class="footer__logo" title="Audyt Google za 0 zł | Up&More"><img src="~/assets/logo.png"></a>
        <p>Copyright 2019</p>
    </footer>
  </div>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Lato:300,400&display=swap');
@import url('https://fonts.googleapis.com/css?family=Maven+Pro:400,900&display=swap');

$base-blue: #00a0e3;
$base-dark: #3c484c;

* {
    box-sizing: border-box;
}
body {
    color: $base-dark;
    font-family: 'Lato', sans-serif;
}
.wrapper {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
}
.header {
    padding-bottom: 70px;
    &__logo {
        display: block;
        max-width: 200px;
        img {
            width: 100%;
        }
    }
}
.footer {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
    align-items: center;
    padding-top: 70px;
    &__logo {
        display: block;
        max-width: 160px;
        img {
            width: 100%;
        }
    }
}
@media screen and (max-width: 1024px) {
    .wrapper {
        width: 100%;
        padding: 0 20px;
    }
}
</style>
