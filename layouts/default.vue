<template>
  <div class="wrapper">
    <header class="header">
        <a href="http://upmore.pl" target="_blank" class="header__logo" title="Audyt Google za 0 zł | Up&More"><img src="~/assets/logo.png"></a>
        <aside><img src="~/assets/logos.png"></aside>
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

/* lato-regular - latin-ext */
@font-face {
  font-family: 'Lato';
  font-style: normal;
  font-weight: 400;
  font-display: swap;
  src: url('/fonts/lato-v16-latin-ext-regular.eot'); /* IE9 Compat Modes */
  src: local('Lato Regular'), local('Lato-Regular'),
       url('/fonts/lato-v16-latin-ext-regular.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
       url('/fonts/lato-v16-latin-ext-regular.woff2') format('woff2'), /* Super Modern Browsers */
       url('/fonts/lato-v16-latin-ext-regular.woff') format('woff'), /* Modern Browsers */
       url('/fonts/lato-v16-latin-ext-regular.ttf') format('truetype'), /* Safari, Android, iOS */
       url('/fonts/lato-v16-latin-ext-regular.svg#Lato') format('svg'); /* Legacy iOS */
}
/* lato-300 - latin-ext */
@font-face {
  font-family: 'Lato';
  font-style: normal;
  font-weight: 300;
  font-display: swap;
  src: url('/fonts/lato-v16-latin-ext-300.eot'); /* IE9 Compat Modes */
  src: local('Lato Light'), local('Lato-Light'),
       url('/fonts/lato-v16-latin-ext-300.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
       url('/fonts/lato-v16-latin-ext-300.woff2') format('woff2'), /* Super Modern Browsers */
       url('/fonts/lato-v16-latin-ext-300.woff') format('woff'), /* Modern Browsers */
       url('/fonts/lato-v16-latin-ext-300.ttf') format('truetype'), /* Safari, Android, iOS */
       url('/fonts/lato-v16-latin-ext-300.svg#Lato') format('svg'); /* Legacy iOS */
}

/* maven-pro-900 - latin-ext */
@font-face {
  font-family: 'Maven Pro';
  font-style: normal;
  font-weight: 900;
  font-display: swap;
  src: url('/fonts/maven-pro-v13-latin-ext-900.eot'); /* IE9 Compat Modes */
  src: local('Maven Pro Black'), local('MavenPro-Black'),
       url('/fonts/maven-pro-v13-latin-ext-900.eot?#iefix') format('embedded-opentype'), /* IE6-IE8 */
       url('/fonts/maven-pro-v13-latin-ext-900.woff2') format('woff2'), /* Super Modern Browsers */
       url('/fonts/maven-pro-v13-latin-ext-900.woff') format('woff'), /* Modern Browsers */
       url('/fonts/maven-pro-v13-latin-ext-900.ttf') format('truetype'), /* Safari, Android, iOS */
       url('/fonts/maven-pro-v13-latin-ext-900.svg#MavenPro') format('svg'); /* Legacy iOS */
}

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
        aside {
            max-width: 120px;
            img {
                width: 100%;
            }
        }
    }
}
@media screen and (max-width: 480px) {
    .wrapper {
        padding: 0 10px;
    }
}
</style>
