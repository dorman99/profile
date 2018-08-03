<template>
  <v-footer height="auto">
    <v-card
      flat
      tile
      class="red darken-4 white--text text-xs-center"
    >
      <v-card-text>
        <v-btn
          v-for="icon in icons"
          :key="icon"
          icon
          class="mx-3 white--text"
          @click="GoToSocialMedia"
        >
          <v-icon size="24px">{{ icon }}</v-icon>
        </v-btn>
      </v-card-text>
      <v-card-text class="white--text pt-0">
        Phasellus feugiat arcu sapien, et iaculis ipsum elementum sit amet. Mauris cursus commodo interdum. Praesent ut risus eget metus luctus accumsan id ultrices nunc. Sed at orci sed massa consectetur dignissim a sit amet dui. Duis commodo vitae velit et faucibus. Morbi vehicula lacinia malesuada. Nulla placerat augue vel ipsum ultrices, cursus iaculis dui sollicitudin. Vestibulum eu ipsum vel diam elementum tempor vel ut orci. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
      </v-card-text>
      <v-card-text class="white--text">
        &copy;2018 — <strong>Vuetify</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<script>
export default {
    data: ()=> ({
        icons:['fab fa-twitter', 'fab fa-linkedin', 'fab fa-instagram','fab fa-github']
    }),
    methods: {
        GoToSocialMedia(e) {
            console.log(e)
            let socialMedia = e.target.lastChild.className.split('-')[1]
            if(socialMedia == 'instagram') {
                console.log('go to instagram page')
            } else if(socialMedia == 'twitter') {
                console.log('go to twitter page')
            } else if(socialMedia == 'linkedin') {
                console.log('go to linkedin')
            } else if (socialMedia == 'github') {
                console.log('go to github')
            } 
        }
    }
}
</script>

<style>

</style>
