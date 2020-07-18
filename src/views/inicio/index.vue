<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawerLeft"
      app
      clipped
    >
      <v-list dense>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-plus-circle-outline</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title
              @click="abrirTarefa()"
            >
              Nova Tarefa
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-view-dashboard</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Dashboard</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-cog</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Settings</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-navigation-drawer
      v-model="drawerRight"
      app
      clipped
      expand-on-hover
      mini-variant
      right
      absolute
      dark
    >
      <v-list dense>
        <v-list-item two-line class="ma-2 px-0">
          <v-list-item-avatar>
            <v-img src="http://igerp.com.br/imgs/logo.png"></v-img>
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title>Application</v-list-item-title>
            <v-list-item-subtitle>Subtext</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-list-item link>
          <v-list-item-content>
            <v-list-item-title class="title">Rafael Machado</v-list-item-title>
            <v-list-item-subtitle>rafmco@gmail.com</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <v-divider></v-divider>

      <v-list
        nav
        dense
      >
        <v-list-item link>
          <v-list-item-icon>
            <v-icon>mdi-folder</v-icon>
          </v-list-item-icon>
          <v-list-item-title>My Files</v-list-item-title>
        </v-list-item>
        <v-list-item link>
          <v-list-item-icon>
            <v-icon>mdi-account-multiple</v-icon>
          </v-list-item-icon>
          <v-list-item-title>Shared with me</v-list-item-title>
        </v-list-item>
        <v-list-item link>
          <v-list-item-icon>
            <v-icon>mdi-star</v-icon>
          </v-list-item-icon>
          <v-list-item-title>Starred</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

      <!-- shrink-on-scroll -->
    <v-app-bar
      app
      clipped-left
      clipped-right
      src="https://picsum.photos/1920/1080?random"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>
      <v-app-bar-nav-icon @click.stop="drawerLeft = !drawerLeft"></v-app-bar-nav-icon>
      <v-toolbar-title>Tarefas</v-toolbar-title>
    </v-app-bar>

    <v-main>
        <!-- class="fill-height" -->
      <v-container
        fluid
      >
        <v-row>
          <v-card
            class="d-flex justify-center"
            width="100%"
          >
            <v-card-title
              class="align center"
            >
              Lista de Tarefas
            </v-card-title>
          </v-card>
        </v-row>
        <v-row>
          <v-card
            class="overflow-auto"
            width="100%"
            ref="scroll"
            height="100%"
            flat
            dense
          >
              <!-- background-color="deep-purple accent-4" -->
            <v-tabs
              grow
              class="elevation-2"
              dark
              centered
              icons-and-text
            >
              <v-tab
                id="Home"
              >
                Tarefas
                <v-icon>mdi-home</v-icon>
              </v-tab>
              <v-tab
                id="List"
              >
                Projetos
                <v-icon>mdi-view-list</v-icon>
              </v-tab>
              <v-tab
                id="Calendar"
              >
                Item Three
                <v-icon>mdi-calendar</v-icon>
              </v-tab>

              <v-tab-item>
                Hoje, {{ new Date().toJSON().slice(0,10).replace(/-/g,'/') }}
                <v-card
                  tile
                  raised
                  outlined
                >
                  <v-card-text>
                    <v-list-item two-line class="pa-0 ma-0 pl-2 align-start">
                      <v-list-item-content class="pt-0">
                        <v-list-item-title class="font-weight-bold headline text-start d-inline-flex">
                          <v-icon
                            color='error'
                            class="px-1 ma-0"
                            left
                            size="20"
                          >
                            mdi-radiobox-blank
                          </v-icon>
                          <span><h6>Realizar Tarefa 1</h6></span>
                        </v-list-item-title>
                        <v-list-item-subtitle class="text-start ma-0 pa-0">
                          9:00 a.m.
                        </v-list-item-subtitle>
                      </v-list-item-content>
                    </v-list-item>
                  </v-card-text>
                </v-card>

                <v-card
                  tile
                  raised
                  outlined
                >
                  <v-card-text>
                    <v-list-item two-line class="pa-0 ma-0 pl-2 align-start">
                      <v-list-item-content class="pt-0">
                        <v-list-item-title class="font-weight-bold headline text-start d-inline-flex">
                          <v-icon
                            color='success'
                            class="px-1 ma-0"
                            left
                            size="20"
                          >
                            mdi-check-circle-outline
                          </v-icon>
                          <span><h6>Realizar Tarefa 2</h6></span>
                        </v-list-item-title>
                        <v-list-item-subtitle class="text-start ma-0 pa-0">
                          7:00 a.m.
                        </v-list-item-subtitle>
                      </v-list-item-content>
                    </v-list-item>
                  </v-card-text>
                </v-card>

                2020/07/14
                <v-card
                  tile
                  raised
                  outlined
                >
                  <v-card-text>
                    <v-list-item two-line class="pa-0 ma-0 pl-2 align-start">
                      <v-list-item-content class="pt-0">
                        <v-list-item-title class="font-weight-bold headline text-start d-inline-flex">
                          <v-icon
                            color='error'
                            class="px-1 ma-0"
                            left
                            size="20"
                          >
                            mdi-radiobox-blank
                          </v-icon>
                          <span><h6>Realizar Tarefa 3</h6></span>
                        </v-list-item-title>
                        <v-list-item-subtitle class="text-start ma-0 pa-0">
                          02:00 p.m.
                        </v-list-item-subtitle>
                      </v-list-item-content>
                    </v-list-item>
                  </v-card-text>
                </v-card>

                <!-- <div id="app">
                  <quill-editor
                    ref="myTextEditor"
                    v-model="content"
                    :config="editorOption">
                  </quill-editor>
                </div> -->
                <div id="app">
                  <!-- <img width="25%" src="./assets/logo.png"> -->
                  <quill v-model="content" output="html"/>
                </div>

              </v-tab-item>

              <v-tab-item>
                <v-card
                  class="d-inline-flex"
                >
                  <v-col>
                    <v-card
                      tile
                      raised
                      outlined
                      max-width="200"
                      min-width="200"
                      max-height="100"
                      min-height="100"
                    >
                      <v-list-item three-line class="pa-0 ma-0 pl-2 align-start">
                        <v-list-item-content class="pt-0">
                          <v-list-item-title class="font-weight-bold headline text-start">
                            <v-icon
                              color='blue'
                              class="px-1 ma-0"
                              left
                              size="20"
                            >
                              mdi-radiobox-marked
                            </v-icon>
                          </v-list-item-title>
                          <v-list-item-subtitle class="text-start ma-0 pa-0">
                            Frigon
                          </v-list-item-subtitle>
                          <v-card-text class="text-start ma-0 pa-0">
                            10 Tarefas
                          </v-card-text>
                        </v-list-item-content>
                      </v-list-item>
                    </v-card>
                  </v-col>
                  <v-col>
                    <v-card
                      tile
                      raised
                      outlined
                      max-width="200"
                      min-width="200"
                      max-height="100"
                      min-height="100"
                    >
                      <v-list-item two-line class="pa-0 ma-0 pl-2 align-start">
                        <v-list-item-content class="pt-0">
                          <v-list-item-title class="font-weight-bold headline text-start">
                            <v-icon
                              color='success'
                              class="px-1 ma-0"
                              left
                              size="20"
                            >
                              mdi-radiobox-marked
                            </v-icon>
                          </v-list-item-title>
                          <v-list-item-subtitle class="text-start ma-0 pa-0">
                            IGWMS
                          </v-list-item-subtitle>
                          <v-card-text class="text-start ma-0 pa-0">
                            5 Tarefas
                          </v-card-text>
                        </v-list-item-content>
                      </v-list-item>
                    </v-card>
                  </v-col>
                </v-card>
              </v-tab-item>

              <v-tab-item>
                <v-card
                  flat
                  tile
                >
                  <v-card-text>
                    <v-calendar
                      ref="calendar"
                      v-model="value"
                      :weekdays="weekday"
                      :type="type"
                      :events="events"
                      :event-overlap-mode="mode"
                      :event-overlap-threshold="30"
                      :event-color="getEventColor"
                      @change="getEvents"
                    ></v-calendar>
                  </v-card-text>
                </v-card>
              </v-tab-item>
            </v-tabs>
          </v-card>
        </v-row>
      </v-container>
    </v-main>
    <v-footer app>
      <span>Tarefas</span>
      <v-spacer></v-spacer>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>

    <modal
      :modal="modalTarefa"
      :maisOpcoes="false"

      @cancelar="resetInfo()"
      @fechar="resetInfo()"

      acaoForm
      cancelar
      titulo="Tarefa"
      largura="1200"
      ref="modalTarefa"
    >
      <!-- <div id="app">
        <quill-editor
          ref="myTextEditor"
          v-model="content"
          :config="editorOption">
        </quill-editor>
      </div> -->
      <div id="app">
        <!-- <img width="25%" src="./assets/logo.png"> -->
        <quill v-model="content" output="html"/>
      </div>

    </modal>

  </v-app>
</template>

<script>

export default {
  name: 'App',
  created () {
    this.$vuetify.theme.dark = true
  },
  props: {
    source: String
  },
  data: () => ({
    content: '<h1>Hello World</h1><p>Here is some text</p',
    editorOption: {},

    drawerLeft: null,
    drawerRight: null,

    type: 'month',
    types: ['month', 'week', 'day', '4day'],
    mode: 'stack',
    modes: ['stack', 'column'],
    weekday: [0, 1, 2, 3, 4, 5, 6],
    weekdays: [
      { text: 'Sun - Sat', value: [0, 1, 2, 3, 4, 5, 6] },
      { text: 'Mon - Sun', value: [1, 2, 3, 4, 5, 6, 0] },
      { text: 'Mon - Fri', value: [1, 2, 3, 4, 5] },
      { text: 'Mon, Wed, Fri', value: [1, 3, 5] }
    ],
    value: '',
    events: [],
    colors: ['blue', 'indigo', 'deep-purple', 'cyan', 'green', 'orange', 'grey darken-1'],
    names: ['Meeting', 'Holiday', 'PTO', 'Travel', 'Event', 'Birthday', 'Conference', 'Party'],

    modalTarefa: false
  }),

  methods: {
    getEvents ({ start, end }) {
      const events = []

      const min = new Date(`${start.date}T00:00:00`)
      const max = new Date(`${end.date}T23:59:59`)
      const days = (max.getTime() - min.getTime()) / 86400000
      const eventCount = this.rnd(days, days + 20)

      for (let i = 0; i < eventCount; i++) {
        const allDay = this.rnd(0, 3) === 0
        const firstTimestamp = this.rnd(min.getTime(), max.getTime())
        const first = new Date(firstTimestamp - (firstTimestamp % 900000))
        const secondTimestamp = this.rnd(2, allDay ? 288 : 8) * 900000
        const second = new Date(first.getTime() + secondTimestamp)

        events.push({
          name: this.names[this.rnd(0, this.names.length - 1)],
          start: first,
          end: second,
          color: this.colors[this.rnd(0, this.colors.length - 1)],
          timed: !allDay
        })
      }

      this.events = events
    },
    getEventColor (event) {
      return event.color
    },
    rnd (a, b) {
      return Math.floor((b - a + 1) * Math.random()) + a
    },
    resetInfo () {
      this.modalTarefa = false
    },
    async abrirTarefa () {
      this.loading = true
      console.log('tarefa')
      this.modalTarefa = true

      this.loading = false
    }
  }
}
</script>
