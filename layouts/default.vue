<template>
  <div class="wrapper">
    <header class="header">
        <a href="http://upmore.pl" target="_blank" class="header__logo" title="Audyt Google za 0 zł | Up&More"><img src="~/assets/logo.png"></a>
        <img src="~/assets/logos.png">
    </header>
    <nuxt />
    <footer class="footer">
        <a href="http://upmore.pl" target="_blank" class="footer__logo" title="Audyt Google za 0 zł | Up&More"><img src="~/assets/logo.png"></a>
        <p>Copyright 2019</p>
    </footer>
  </div>
</template>

<style lang="scss">

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
    padding: 15px 0 70px 0;
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
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
    .header {
        &__logo {
            max-width: 100px;
        }
        > img {
            max-width: 100px;
            display: block;
            height: auto;
        }
    }
}
</style>
