<template>
  <form @change="emitContact">
    <div class="address">
      <div class="row q-col-gutter-x-md">
        <div class="col-md-2 col-sm-6 col-xs-12">
          <q-select
            outlined
            v-model="c.gender"
            color="$blue"
            :options="options"
            label="Anrede"
            :rules="[true]"
            @change="emitContact"
          />
        </div>
        <div class="col-md-10 col-sm-6 col-xs-6" />
        <div class="col-md-6 col-sm-6 col-xs-12">
          <q-input
            outlined
            label="Vorname"
            v-model="c.firstname"
            lazy-rules
            :rules="[val => !!val || 'Pflichtfeld']"
          />
        </div>
        <div class="col-md-6 col-sm-6 col-xs-12">
          <q-input
            outlined
            label="Nachname"
            v-model="c.lastname"
            lazy-rules
            :rules="[val => !!val || 'Pflichtfeld']"
          />
        </div>
        <div class="col-lg-10 col-sm-6 col-xs-12">
          <q-input
            outlined
            v-model="c.street"
            label="Strasse"
            lazy-rules
            :rules="[val => !!val || 'Pflichtfeld']"
          />
        </div>
        <div class="col-lg-2 col-sm-6 col-xs-12">
          <q-input
            outlined
            v-model="c.housenumber"
            label="Hausnr."
            lazy-rules
            :rules="[val => !!val || 'Pflichtfeld']"
          />
        </div>
        <div class="col-lg-2 col-sm-6 col-xs-12">
          <q-input
            outlined
            v-model="c.postalcode"
            label="Plz."
            lazy-rules
            :rules="[val => !!val || 'Pflichtfeld']"
          />
        </div>
        <div class="col-lg-10 col-sm-6 col-xs-12">
          <q-input
            outlined
            v-model="c.city"
            label="Ort"
            lazy-rules
            :rules="[val => !!val || 'Pflichtfeld']"
          />
        </div>
        <div class="col-lg-12 col-sm-6 col-xs-12">
          <q-input
            outlined
            type="email"
            label="E-Mail*"
            lazy-rules
            :rules="[val => !!val || 'Pflichtfeld']"
            v-model="c.email"
          >
            <template v-slot:before>
              <q-icon name="mail" />
            </template>
          </q-input>
        </div>
        <div class="col-lg-12 col-sm-6 col-xs-12">
          <q-input
            outlined
            type="tel"
            label="Telefon"
            v-model="c.phone"
           >
           <template v-slot:before>
              <q-icon name="phone" />
            </template>
          </q-input>
        </div>
      </div>
    </div>
  </form>
</template>

<script lang="javascript">

export default {
  name: 'Address',
  props: {
    c: {
      default: () => ({
        gender: '',
        phone: '',
        email: '',
        postalcode: '',
        city: '',
        housenumber: '',
        firstname: '',
        lastname: '',
        street: ''
      })
    }
  },
  data () {
    return {
      options: [
        'Herr', 'Frau'
      ]
    }
  },
  methods: {
    emitContact (event) {
      console.log('emit ' + this.c)
      this.$emit('Contact', this.c)
    }
  }
}
</script>
