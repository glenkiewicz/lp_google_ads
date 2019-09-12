<template>
    <section class="contact-form" v-loading="pending">
        <div class="form__sent" v-if="isSent">
            <h1>Formularz został wysłany</h1>
            <p>Nasi doradcy skontaktują się z Tobą w ciągu 48 godzin przedstawiając ofertę</p>
        </div>
        <el-form :model="form" :rules="rules" ref="form"  @submit.native.prevent="onSubmit" v-else data-netlify="true">
            <el-form-item prop="name">
                <el-input v-model="form.name" placeholder="Imię i Nazwisko"></el-input>
            </el-form-item>
            <el-form-item prop="email">
                <el-input v-model="form.email" placeholder="E-mail"></el-input>
            </el-form-item>
            <el-form-item prop="phone">
                <el-input v-model="form.phone" placeholder="Telefon"></el-input>
            </el-form-item>
            <el-form-item prop="accept">
                <el-checkbox v-model="form.accept">Wyraźam zgodę</el-checkbox>
            </el-form-item>
            <el-form-item>
                <el-button native-type="submit">Wyslij</el-button>
            </el-form-item>
        </el-form>
    </section>
</template>

<script>
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

<style>

</style>