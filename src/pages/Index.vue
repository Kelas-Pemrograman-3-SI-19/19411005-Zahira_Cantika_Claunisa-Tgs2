<template>
<div class="q-pa-md" style="max-width: 400px">

    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="form.name"
        label="Nama Lengkap *"
        hint="Nama Lengkap"
        lazy-rules=""
        :rules="[ val => val && val.length > 0 || 'Nama lengkap tidak boleh kosong']"
      />

      <q-input
        filled
        type="number"
        v-model="form.age"
        label="Umur *"
        lazy-rules=""
        :rules="[
          val => val !== null && val !== '' || 'Umur tidak boleh kosong']"
      />

      <q-input
        filled
        v-model="form.hobby"
        label="Hobby *"
        lazy-rules=""
        :rules="[ val => val && val.length > 0 || 'Harus Punya hobby']"
      />

      <q-toggle v-model="accept" label="I accept the license and terms" />

      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
      <div>
        {{ biodata.name }}<br>
        {{ biodata.age }}<br>
        {{ biodata.hobby }}
      </div>
    </q-form>

  </div>
</template>

<script>
export default {
  data () {
    return {
      form: {
        name: null,
        age: null,
        hobby: null
      },
      biodata: {
        name: null,
        age: null,
        hobby: null
      },

      accept: false
    }
  },

  methods: {
    onSubmit () {
      this.biodata = this.form
      console.log(this.biodata)
    },

    onReset () {
      this.form.name = null
      this.form.age = null
      this.form.hobby = null
      this.accept = false
    }
  }
}
</script>
