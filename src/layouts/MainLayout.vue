<template>
  <q-layout view="lHh Lpr lFf">
    <q-drawer
      show-if-above
      content-class="bg-deep-purple-7 flex column justify-between q-pa-lg"
      content-style="border-top-right-radius: 40px; border-bottom-right-radius:40px;"
    >
      <div class="text-white   flex flex-center vertical-middle items-center content-center text-center">
        <q-icon name="fas fa-shopping-bag" size="1.7em"/>
        <div class="q-ml-xs text-h4">
          OnShop
        </div>
      </div>

      <div class="text-white  flex column justify-between q-pl-md">


        <div v-for="link in linksMenu"
             :class="link.active?'flex q-my-sm items-center cursor-pointer q-px-md q-py-sm bg-deep-purple-5':'flex q-my-sm items-center cursor-pointer q-px-md q-py-sm'"
             style="border-radius: 15px"
             @click="goTo(link)">
          <q-icon :name="link.icon" size="1.5em"/>
          <div style="font-size: 1.4em" class="q-ml-lg">{{ $t(link.name) }}</div>
        </div>
        <q-separator color="white" inset="" spaced=""/>
        <q-select dense bg-color="deep-purple-5" color="white" popup-content-class="text-white bg-deep-purple-5" options-selected-class="text-white"  outlined rounded :label="$t('language')" v-model="lang" :options="languageOptions"
                  @input="changeLanguage">
          <template v-slot:prepend v-if="lang!==null">
            {{ lang.flag }}
          </template>
        </q-select>

      </div>
      <div class="q-pl-md">

        <div class="flex q-my-sm items-center cursor-pointer q-px-md q-py-sm bg-deep-purple-5 text-white"
             style="border-radius: 15px">
          <q-icon name="fas fa-sign-out-alt" size="1.5em"/>
          <div style="font-size: 1.4em" class="q-ml-lg">Log out</div>
        </div>
      </div>
    </q-drawer>
    <div class="bg-amber-1 text-accent"></div>
      
    <q-page-container>
      <router-view/>
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'MainLayout',
  created() {
    /*
    * Pick saved lang
    * */
    if (localStorage.getItem('language') != null) {
      this.lang = JSON.parse(localStorage.getItem('language'))
      this.changeLanguage(this.lang)
    } else {
      this.changeLanguage(this.lang)
    }

    /*
    * Pick current path
    * */
    const path = this.$route.path;
    this.activeLink = this.linksMenu.filter(link => link.link === path)[0]
  },
  data() {
    return {
      lang: null,
      userIsLogged: false,
      activeLink: null,
      linksMenu: [
        {
          name: 'home',
          link: '/',
          needsToBeLogged: false,
          active: true,
          icon: 'fas fa-home'
        },
        {
          name: 'categories',
          link: '/categories',
          needsToBeLogged: false,
          active: false,
          icon: 'fas fa-shopping-basket'
        },
        {
          name: 'cart',
          link: '/cart',
          needsToBeLogged: false,
          active: false,
          icon: 'fas fa-shopping-cart'
        },
        {
          name: 'userProfile',
          link: '/profile',
          needsToBeLogged: true,
          active: false,
          icon: 'fas fa-user'
        },
        {
          name: 'settings',
          link: '/settings',
          needsToBeLogged: true,
          active: false,
          icon: 'fas fa-cog'
        }
      ],
      languageOptions: [
        {
          label: 'English',
          value: 'en-us',
          flag: '🇺🇸'
        },
        {
          label: 'Spanish',
          value: 'es',
          flag: '🇪🇸'
        },

      ]

    }
  },
  methods: {
    goTo(toPath) {
      this.activeLink.active = false;
      toPath.active = true;
      this.activeLink = toPath
      console.log(this.activeLink)
    },
    changeLanguage(lang) {
      this.lang = lang
      localStorage.setItem('language', JSON.stringify(lang))
      this.$i18n.locale = lang.value
    }
  },

}
</script>
