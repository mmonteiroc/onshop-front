<template>
  <q-layout view="lHh Lpr lFf">
    <q-drawer
      show-if-above
      content-class="bg-deep-purple-7 flex column justify-between q-pa-lg"
      content-style="border-top-right-radius: 40px; border-bottom-right-radius:40px"
    >
      <div class="text-white   flex flex-center vertical-middle items-center content-center text-center">
        <q-icon name="fas fa-shopping-bag" size="1.7em"/>
        <div class="q-ml-xs text-h4">
          OnShop
        </div>
      </div>

      <div class="text-white  flex column justify-between q-pl-md">
        <div class="flex q-my-sm items-center cursor-pointer q-px-md q-py-sm " style="border-radius: 15px">
          <q-icon name="fas fa-home" size="1.7em"/>
          <div style="font-size: 1.6em" class="q-ml-lg">{{ $t('home') }}</div>
        </div>
        <div class="flex q-my-sm items-center cursor-pointer q-px-md q-py-sm bg-deep-purple-5" style="border-radius: 15px">
          <q-icon name="fas fa-shopping-basket" size="1.7em"/>
          <div style="font-size: 1.6em" class="q-ml-lg">{{ $t('categories') }}</div>
        </div>
        <div class="flex q-my-sm items-center cursor-pointer q-px-md q-py-sm" style="border-radius: 15px">
          <q-icon name="fas fa-shopping-cart" size="1.7em"/>
          <div style="font-size: 1.6em" class="q-ml-lg">{{ $t('cart') }}</div>
        </div>
        <div class="flex q-my-sm items-center cursor-pointer q-px-md q-py-sm" style="border-radius: 15px">
          <q-icon  name="fas fa-user" size="1.7em"/>
          <div style="font-size: 1.6em" class="q-ml-lg">{{ $t('userProfile') }}</div>
        </div>
        <div class="flex q-my-sm items-center cursor-pointer q-px-md q-py-sm" style="border-radius: 15px">
          <q-icon name="fas fa-cog" size="1.7em"/>
          <div style="font-size: 1.6em" class="q-ml-lg">{{ $t('settings') }}</div>
        </div>

      </div>
      <div>
        hello
      </div>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'MainLayout',
  data () {
    return {

    }
  }
}
</script>
