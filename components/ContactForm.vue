<template>
    <section class="contact-form" v-loading="pending">
        <div class="form__sent" v-if="isSent">
            <h1>Formularz został wysłany</h1>
        </div>
        <el-form 
            name="lpform"
            :model="form" 
            :rules="rules" 
            ref="form"  
            @submit.native.prevent="onSubmit" 
            v-else
            >
            <h3>Chcesz otrzymać<br>bezpłatny audyt?</h3>
            <p>Skontaktuj się z nami!</p>
            <el-form-item prop="name">
                <el-input v-model="form.name" placeholder="Imię i Nazwisko" class="name"></el-input>
            </el-form-item>
            <el-form-item prop="email">
                <el-input v-model="form.email" placeholder="E-mail" class="email"></el-input>
            </el-form-item>
            <el-form-item prop="phone">
                <el-input v-model="form.phone" placeholder="Telefon" class="phone"></el-input>
            </el-form-item>
            <el-form-item prop="accept">
                <el-checkbox v-model="form.accept">Administratorem Państwa danych osobowych jest Up&More sp. z o.o.</el-checkbox>
            </el-form-item>
            <el-form-item>
                <el-button native-type="submit">Wyślij!</el-button>
            </el-form-item>
        </el-form>
    </section>
</template>

<script>
import axios from "axios";
export default {
    data() {
        return {
            isSent: false,
            pending: false,
            visible: false,
            form: {
                name: '',
                email: '',
                phone: '',
                accept: null
            }
        }
    },
    computed: {
        rules() {
            return {
                name: [
                    { required: true, message: 'Wprowadź imię i nazwisko'  },
                    { type: 'string', message: 'Imię i nazwisko jest za krótkie lub przekracza 64 znaków',
                      min: 3, max: 64, whitespace: true
                    }
                ],
                phone: [
                    { required: true, message: 'Tylko 9 cyfrowe numery telefonu',
                        pattern: /^\d{9}$/,
                        transform: (value) => (''+value).replace(/[ ]/g, '').trim()
                    },
                ],
                email: [
                    { required: true, message: 'Wprowadź email' },
                    { type: 'email',  message: 'Wprowadź poprawny email' }
                ],
                accept: [
                    { required: true, message: 'Zgoda musi być zaznaczona'}
                ]
            }
        }
    },
    methods: {

        encode (data) {
            return Object.keys(data)
                .map(
                    key => `${encodeURIComponent(key)}=${encodeURIComponent(data[key])}`
                )
                .join("&");
        },
        validateForm(ref = 'form', error) {
            return new Promise((resolve, reject) => {
                this.$refs[ref].validate(valid => {
                    valid ? resolve() : reject(error)
                })
            })
        },

        onSubmit() {
            this.pending = true;
            this.validateForm()
                .then(this.onSuccess)
                .catch(this.onError)
                .then(() => this.pending = false)
        },

        onSuccess() {
            const axiosConfig = {
                header: { "Content-Type": "application/x-www-form-urlencoded" }
            };
            axios.post(
                "/",
                this.encode({
                "form-name": "lpform",
                ...this.form
                }),
                axiosConfig
            );
            this.isSent = true;
        },

        onError(err) {
            err && this.$message({
                message: 'Wystąpił nieoczekiwany błąd',
                type:    'error'
            });
        }
        
    }
}
</script>

<style lang="scss">

$base-blue: #00a0e3;
$base-dark: #3c484c;

.contact-form {
    padding: 30px;
    background-color: $base-blue;
    border-radius: 10px;
    max-width: 400px;
    min-width: 400px;
    h3 {
        color: #fff;
        text-transform: uppercase;
        font-weight: 900;
        text-align: center;
        font-family: 'Maven Pro', sans-serif;
        font-size: 3vh;
        margin: 0;
    }
    p {
        color: #fff;
        font-weight: 300;
        text-align: center;
        font-family: 'Maven Pro', sans-serif;
    }
    .el-form {
        &-item {
            &__error {
                text-align: center;
                width: 100%;
                color: $base-dark;
                font-weight: 700;
            }
        } 
        .el-button {
            background-color: $base-dark;
            color: #fff;
            text-transform: uppercase;
            font-weight: 900;
            font-family: 'Maven Pro', sans-serif;
            border-radius: 30px;
            border: none;
            display: block;
            margin: 0 auto;
            font-size: 1.2em;
            padding: 15px 30px;
        }
        .el-input {
            &.name {
                .el-input__inner {
                    background: url('~assets/user.png') 20px center no-repeat;
                    background-color: #fff;
                    padding-left: 50px
                }
            }
            &.email {
                .el-input__inner {
                    background: url('~assets/mail.png') 20px center no-repeat;
                    background-color: #fff;
                    padding-left: 50px
                }
            }
            &.phone {
                .el-input__inner {
                    background: url('~assets/phone.png') 20px center no-repeat;
                    background-color: #fff;
                    padding-left: 50px
                }
            }
            &__inner {
                border-radius: 30px;
                border: none;
            }
        }
        .el-checkbox {
            display: flex;
            flex-flow: row nowrap;
            justify-content: space-between;
            align-items: center;
            &__input {
                &.is-checked {
                    &__inner {
                        background-color: #fff;
                    }
                }
            }
            &__inner {
                border: none;
                border-radius: 15px;
                width: 20px;
                height: 20px;
                &::after {
                    border-color: $base-blue;
                    top: 5px;
                    left: 7px;
                }
            }
            &__label {
                white-space: pre-line;
                color: #fff;
            }
        }
        .el-checkbox__input.is-checked .el-checkbox__inner, .el-checkbox__input.is-indeterminate .el-checkbox__inner {
            background-color: #fff;
        }
    }
}

@media screen and (max-width: 1024px) {
    .contact-form {
        max-width: 600px;
        margin: 20px auto;
    }
}
</style>