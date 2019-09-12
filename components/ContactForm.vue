<template>
    <section class="contact-form" v-loading="pending">
        <form name="contact" method="POST" data-netlify="true">
  <p>
    <label>Your Name: <input type="text" name="name" /></label>   
  </p>
  <p>
    <label>Your Email: <input type="email" name="email" /></label>
  </p>
  <p>
    <label>Your Role: <select name="role[]" multiple>
      <option value="leader">Leader</option>
      <option value="follower">Follower</option>
    </select></label>
  </p>
  <p>
    <label>Message: <textarea name="message"></textarea></label>
  </p>
  <p>
    <button type="submit">Send</button>
  </p>
</form>
    </section>
</template>

<script>
import axios from "axios";
export default {

    data() {
        return {
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
                "https://festive-bartik-f195dc.netlify.com/",
                this.encode({
                "form-name": "lpform",
                ...this.form
                }),
                axiosConfig
            );
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