<template>
    <div class="row full-width justify-center">
      <div
      class="col-6 items-center">
        <q-card
        class="my-card">
          <q-card-section class="collumn col-12 full-width">
            <q-input
            v-model="email"
            class="q-mb-md"
            color="blue-grey-10"
            type="email"
            label="E-mail"
            :error-message="mensaError('email')"
            :error="$v.email.$invalid"
            counter
            maxlength="30"
            />
            <q-input
            v-model="pass"
            class="q-mb-md"
            color="blue-grey-10"
            type="password"
            label="Contraseña"
            :error-message="mensaError('pass')"
            :error="$v.pass.$invalid"
            counter
            maxlength="10"
            />
            </q-card-section>
        </q-card>
      </div>
    </div>
</template>

<script>
import { required, email, minLength } from 'vuelidate/lib/validators'
export default {
  name: 'Formulario',
  data () {
    return {
      email: '',
      pass: ''
    }
  },
  validations: {
    email: { required, email },
    pass: { required, minLength: minLength(4) }
  },
  methods: {
    mensaError (campo) {
      if (campo === 'email') {
        if (!this.$v.email.email) return 'Debe ser un email'
        if (!this.$v.email.required) return 'Campo requerido'
      }
      if (campo === 'pass') {
        if (!this.$v.pass.minLength) return 'Tamaño minimo 4 caracteres'
        if (!this.$v.pass.required) return 'Campo requerido'
      }
    }
  }
}
</script>
