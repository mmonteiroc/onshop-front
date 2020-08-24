<template>
  <div>
    <q-dialog v-model="open" persistent seamless>
      <q-card style="width: 20vw">
        <q-card-section class="flex justify-between full-width">
          <div class="text-h5 q-ma-md flex items-center">
            {{ $t('login') }}
          </div>
          <q-btn round flat icon="close" class="q-ma-md" color="grey-7" @click="closePopUp"></q-btn>
        </q-card-section>
        <q-card-section class="column flex q-pa-lg">
          <q-input :label="$t('email')" v-model="user.email" type="email" autofocus class="full-width q-my-sm"
                   outlined/>
          <q-input :label="$t('passwd')" v-model="user.passwd" type="password" class="full-width q-my-sm" outlined/>
        </q-card-section>
        <q-card-actions align="right">
          <q-btn :label="$t('access')" class="q-mr-md" unelevated color="secondary" @click="doLogin"/>
        </q-card-actions>

      </q-card>
    </q-dialog>
  </div>
</template>

<script>
export default {
  name: "LoginPopup",
  props: {
    open: {
      default: false,
    },
    successLogin: {
      default: function () {
      },
      type: Function
    }
  },
  data() {
    return {
      user: {
        email: null,
        passwd: null
      }
    }
  },
  methods: {
    closePopUp() {
      this.$emit("closed")
    },
    async doLogin() {

    }
  }
}
</script>

<style scoped>

</style>
