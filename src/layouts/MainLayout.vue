<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="header">
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />
        <div class="text-h5">Пёсатели</div>
        <div class="dog">🐶</div>
      </q-toolbar>
    </q-header>

    <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="200"
        :breakpoint="400"
      >
        <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd">
          <q-list padding>

            <q-item  to="/main" exact active clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="main" />
              </q-item-section>

              <q-item-section>
                Главная
              </q-item-section>
            </q-item>

            <q-item to="/about" exact clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="about" />
              </q-item-section>

              <q-item-section>
                О нас
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="https://i.vimeocdn.com/video/1380652367-516f2a165cc2418e7308c116abf83d40a310162bfcd4530e9ec4cbb154e9d061-d_640x360.jpg" height="150px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="75px" class="q-mb-sm">
              <img src="https://avatarko.ru/img/kartinka/27/zhivotnye_sobaka_naushniki_labrador_retriever_26007.jpg">
            </q-avatar>
            <div class="text-weight-bold">Генерал Гав</div>
            <div>@gav</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
]

export default defineComponent({
  name: 'MainLayout',

  components: {
    
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>

<style>
.header{
  display: flex;
  justify-content: space-between;
}

.dog {
  font-size: 30px;
}

</style>