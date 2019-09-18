<template>
    <div class="main">
        <section  class="content">
            <section class="content__text">
                <h1 class="content__title">Audyt<br> Google Ads<br> za <span>0 zł</span></h1>
                <h2 class="content__subtitle">Zwiększymy liczbę Twoich<br>Klientów bez podnoszenia budżetu</h2>
                <ul>
                    <li>Sprawdzimy najważniejsze elementy<br>prowadzonych kampanii</li>
                    <li>Zaproponujemy gotowe rozwiązania,<br>które zwiększą efektywność kampanii</li>
                    <li>Skonsultujemy z Tobą rekomendacje<br>i wyznaczymy cele do realizacji</li>
                </ul>
            </section>
            <contact-form></contact-form>
        </section>
        <section class="opinions">
            <h3 class="opinions__title">Zaufaj tym, którzy nas sprawdzili</h3>
            <article class="opinions__item">
                <p class="opinions__text">„Zwracając uwagę na efekty wdrażanej strategii oraz wyniki prowadzonych kampanii i realizowanych audytów, zdecydowaliśmy się na kontynuację działań promocyjnych powierzanych Up&More. Dostrzegamy potrzebę generowania jeszcze większego zainteresowania naszą ofertą, a poprzez rekomendowaną analizę i sprawdzoną współpracę wierzymy, że to będzie kolejny krok w sukcesywnym rozwoju naszej firmy.”</p>
                <p class="opinions__info"><strong>Michał Pryshliak</strong>, Marketing Specialist z firmy <strong>AmeriGas</strong></p>
                <img src="~/assets/amerigas.png">
            </article>
            <article class="opinions__item">
                <p class="opinions__text">„Specyfika branży self storage wymaga od agencji reklamowych dużej elastyczności oraz nieszablonowego podejścia. Zespół Up&More pokazał, że potrafi w działaniach wyjść poza schematy, dlatego zdecydowaliśmy się na nawiązanie współpracy.”</p>
                <p class="opinions__info"><strong>Przemek Główczewski</strong>, Dyrektor Zarządzający <strong>Kangu Self Storage </strong></p>
                <img src="~/assets/kangu.png">
            </article>
            <article class="opinions__item">
                <p class="opinions__text">„2019 rok będzie dla nas kluczowy w zakresie rozwoju firmy, zarówno w kontekście wynajmu aut, jak i car sharingu. Po zmianie dotychczasowego partnera w zakresie promocji w sieci, długo szukaliśmy podmiotu, któremu będziemy mogli powierzyć nasze działania. Agencja Up&More pokazała, że warto dać jej kredyt zaufania.”</p>
                <p class="opinions__info"><strong>Katarzyna Panek</strong>, Dyrektor Marketingu <strong>Panek S.A.</strong></p>
                <img src="~/assets/panek.png">
            </article>
        </section>
    </div>
</template>

<script>
import ContactForm from '../components/ContactForm';
export default {
	components: {
    	ContactForm,
    }
};
</script>

<style lang="scss">

$base-blue: #00a0e3;
$base-dark: #3c484c;

.content {
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-between;
    &__text {
        width: (740px*100%)/1200px;
        background: url('~assets/plane.png') center right no-repeat;
    }
    &__title {
        font-family: 'Maven Pro', sans-serif;
        font-size: 6vh;
        font-weight: 900;
        line-height: 85%;
        text-transform: uppercase;
        margin: 0;
        span {
            color: $base-blue;
        }
    }
    &__subtitle {
        font-weight: 300;
        padding-bottom: 30px;
    }
    ul {
        margin-left: 20px;
        padding: 0;
        li {
            font-weight: 300;
            padding: 5px 0;
        }
    }
}
.opinions {
    width: 100%;
    &__title {
        font-family: 'Maven Pro', sans-serif;
    }
    &__item {
        border: 1px solid #f6f6f6;
        border-radius: 10px;
        width: (740px*100%)/1200px;
        padding: 20px;
        margin: 10px 0;
    } 
    &__text {
        font-style: italic;
        font-weight: 300;
    }
}

@media screen and (max-width: 1024px) {
    .content {
        flex-flow: column wrap;
        &__text {
            width: 100%;
        }
    }
    .opinions {
        &__title {
            text-align: center;
        }
        &__item {
            width: 100%;
        }
    }
}
@media screen and (max-width: 767px) {
    .content {
        &__text {
            background: none;
        }
    }
}
</style>
