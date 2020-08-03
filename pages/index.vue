<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <v-card class="text-card">
        <v-card-title>
          Type This...
        </v-card-title>
        <v-card-text class="character-container" v-html="highlightedText">
        </v-card-text>
      </v-card>
      <Keyboard :highlight="nextKeycode" class="my-4" />
    </v-flex>
    <v-dialog :value="finished" persistent max-width="400px">
      <v-card>
        <v-card-title>
          <v-icon left v-text="'mdi-flag-outline'" />
          Finished
        </v-card-title>
        <v-card-actions>
          <v-spacer />
          <v-btn text @click="writtenText = ''"> Reset</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-layout>
</template>

<script lang="ts">
// import Logo from '~/components/Logo.vue'
// import VuetifyLogo from '~/components/VuetifyLogo.vue'
import { keycodeToKey, keyToKeycode } from '@/assets/keymaps.ts'
import Keyboard from '@/components/Keyboard.vue'
import Vue from 'vue'

export default Vue.extend({
  components: {
    Keyboard,
  },
  data() {
    return {
      // text: `သီဟိုဠ်မှ ဉာဏ်ကြီးရှင်သည် အာယုဝဍ္ဎနဆေးညွှန်းစာကို ဇလွန်ဈေးဘေး ဗာဒံပင်ထက် အဓိဋ္ဌာန်လျက် ဂဃနဏဖတ်ခဲ့သည်။`,
      text: `In one study of average computer users, the average rate for transcription was 33 words per minute, and 19 words per minute for composition. In the same study, when the group was divided into 'fast', 'moderate' and 'slow' groups, the average speeds were 40 wpm, 35 wpm, and 23 wpm respectively. An average professional typist reaches 50 to 80 wpm, while some positions can require 80 to 95 wpm (usually the minimum required for dispatch positions and other typing jobs), and some advanced typists work at speeds above 120 wpm. Two-finger typists, sometimes also referred to as 'hunt and peck' typists, commonly reach sustained speeds of about 37 wpm for memorized text and 27 wpm when copying text, but in bursts may be able to reach speeds of 60 to 70 wpm. From the 1920s through the 1970s, typing speed (along with shorthand speed) was an important secretarial qualification and typing contests were popular and often publicized by typewriter companies as promotional tools.`,
      writtenText: '',
    }
  },
  computed: {
    highlightedText(): string {
      return Array.from(this.text)
        .map((c, i) => {
          const writtenC = this.writtenText[i]
          if (i === this.writtenText.length)
            return `<b class="primary">${c}</b>`
          if (!writtenC) return c
          if (writtenC === c)
            return `<b class="teal--text teal--text--darken-1">${writtenC}</b>`
          else return `<b class="error">${writtenC}</b>`
        })
        .reduce((p, c) => p + c)
    },
    array(): Array<String> {
      return Array.from(this.text)
    },
    finished(): boolean {
      return this.writtenText.length === this.text.length
    },
    nextKeycode(): number {
      return keyToKeycode[this.text[this.writtenText.length]]
    },
  },
  mounted() {
    document.addEventListener('keydown', (e) => {
      if (e.keyCode === 8) {
        this.writtenText = this.writtenText.slice(
          0,
          this.writtenText.length - 1
        )
      } else if (keycodeToKey[e.keyCode]) {
        this.writtenText += e.key
      }
      // prevent space scrolling and tabbing out
      if (e.keyCode === 32 || e.keyCode === 9) e.preventDefault()
    })
  },
})
</script>

<style lang="scss" scoped>
$font-size: 1.5em;
.text-card {
  overflow: hidden;
}
.character-container {
  max-height: 30vh;
  overflow-y: scroll;
  min-width: 400px;
  max-width: 1000px;
  font-size: $font-size;
  line-height: $font-size;
  font-family: 'Courier New', Courier, monospace;
  white-space: break-spaces;
}
</style>
