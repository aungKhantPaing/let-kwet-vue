<template>
  <div class="container" tabindex="-1">
    <div class="key-container">
      <div class="row1">
        <!-- <KeyCap f-key esc-key :is-down="keysState.get(27)" />
        <KeyCap label="F1" f-key />
        <KeyCap label="F2" f-key />
        <KeyCap label="F3" f-key />
        <KeyCap label="F4" f-key />
        <KeyCap label="F5" f-key />
        <KeyCap label="F6" f-key />
        <KeyCap label="F7" f-key />
        <KeyCap label="F8" f-key />
        <KeyCap label="F9" f-key />
        <KeyCap label="F10" f-key />
        <KeyCap label="F11" f-key />
        <KeyCap label="F12" f-key />
        <span class="touchID f-keys"></span> -->
      </div>

      <div class="row2">
        <KeyCap label="`" side-label="~" :is-down="keysState.get(192)" />
        <KeyCap label="1" side-label="!" :is-down="keysState.get(49)" />
        <KeyCap label="2" side-label="@" :is-down="keysState.get(50)" />
        <KeyCap label="3" side-label="#" :is-down="keysState.get(51)" />
        <KeyCap label="4" side-label="$" :is-down="keysState.get(52)" />
        <KeyCap label="5" side-label="%" :is-down="keysState.get(53)" />
        <KeyCap label="6" side-label="^" :is-down="keysState.get(54)" />
        <KeyCap label="7" side-label="&amp;" :is-down="keysState.get(55)" />
        <KeyCap label="8" side-label="*" :is-down="keysState.get(56)" />
        <KeyCap label="9" side-label="(" :is-down="keysState.get(57)" />
        <KeyCap label="0" side-label=")" :is-down="keysState.get(48)" />
        <KeyCap label="-" side-label="_" :is-down="keysState.get(189)" />
        <KeyCap label="=" side-label="+" :is-down="keysState.get(187)" />
        <KeyCap delete-key :is-down="keysState.get(8)" />
      </div>

      <div class="row3">
        <KeyCap tab-key :is-down="keysState.get(9)" />
        <KeyCap label="Q" :is-down="keysState.get(81)" />
        <KeyCap label="W" :is-down="keysState.get(87)" />
        <KeyCap label="E" :is-down="keysState.get(69)" />
        <KeyCap label="R" :is-down="keysState.get(82)" />
        <KeyCap label="T" :is-down="keysState.get(84)" />
        <KeyCap label="Y" :is-down="keysState.get(89)" />
        <KeyCap label="U" :is-down="keysState.get(85)" />
        <KeyCap label="I" :is-down="keysState.get(73)" />
        <KeyCap label="O" :is-down="keysState.get(79)" />
        <KeyCap label="P" :is-down="keysState.get(80)" />
        <KeyCap label="[" side-label="{" :is-down="keysState.get(219)" />
        <KeyCap label="]" side-label="}" :is-down="keysState.get(221)" />
        <KeyCap label="\" side-label="|" :is-down="keysState.get(220)" />
      </div>

      <div class="row4">
        <KeyCap cap-key :cap-on="capOn" :is-down="keysState.get(20)" />
        <KeyCap label="A" :is-down="keysState.get(65)" />
        <KeyCap label="S" :is-down="keysState.get(83)" />
        <KeyCap label="D" :is-down="keysState.get(68)" />
        <KeyCap label="F" :is-down="keysState.get(70)" />
        <KeyCap label="G" :is-down="keysState.get(71)" />
        <KeyCap label="H" :is-down="keysState.get(72)" />
        <KeyCap label="J" :is-down="keysState.get(74)" />
        <KeyCap label="K" :is-down="keysState.get(75)" />
        <KeyCap label="L" :is-down="keysState.get(76)" />
        <KeyCap label=";" side-label=":" :is-down="keysState.get(186)" />
        <KeyCap label="'" side-label='"' :is-down="keysState.get(222)" />
        <KeyCap return-key :is-down="keysState.get(13)" />
      </div>

      <div class="row5">
        <KeyCap shift-key-left :is-down="keysState.get(16.1)" />
        <KeyCap label="Z" :is-down="keysState.get(90)" />
        <KeyCap label="X" :is-down="keysState.get(88)" />
        <KeyCap label="C" :is-down="keysState.get(67)" />
        <KeyCap label="V" :is-down="keysState.get(86)" />
        <KeyCap label="B" :is-down="keysState.get(66)" />
        <KeyCap label="N" :is-down="keysState.get(78)" />
        <KeyCap label="M" :is-down="keysState.get(77)" />
        <KeyCap label="," side-label="&lt;" :is-down="keysState.get(188)" />
        <KeyCap label="." side-label=">" :is-down="keysState.get(190)" />
        <KeyCap label="/" side-label="?" :is-down="keysState.get(191)" />
        <KeyCap shift-key-right :is-down="keysState.get(16.2)" />
      </div>

      <div class="row6">
        <KeyCap fn-key />
        <KeyCap
          label="control"
          side-label="^"
          ctrl-key
          :is-down="keysState.get(17.1)"
        />
        <KeyCap
          label="option"
          side-label="⌥"
          ctrl-key
          :is-down="keysState.get(18.1)"
        />
        <KeyCap label="command" side-label="⌘" ctrl-key cmd-key />
        <KeyCap spacebar :is-down="keysState.get(32)" />
        <KeyCap label="command" side-label="⌘" ctrl-key cmd-key />
        <KeyCap
          label="option"
          side-label="⌥"
          ctrl-key
          :is-down="keysState.get(18.2)"
        />
        <KeyCap label="&lt;" :is-down="keysState.get(37)" />
        <div class="arrow-key-cont">
          <KeyCap arrow-key :is-down="keysState.get(38)" />
          <KeyCap arrow-key :is-down="keysState.get(40)" down-arrow />
        </div>
        <KeyCap label=">" :is-down="keysState.get(39)" />
      </div>
    </div>
    <!-- <div class="trackpad"></div> -->
  </div>
</template>

<script lang="ts">
import KeyCap from '@/components/KeyCap.vue'
import { keycodes } from '@/assets/keycodes.ts'
import Vue from 'vue'

export default Vue.extend({
  components: {
    KeyCap,
  },

  props: {
    highlight: Number,
    auto: Boolean,
  },

  data() {
    return {
      keysState: new Map(
        Object.entries(keycodes).map(([_, keycode]) => [keycode, false])
      ),
      capOn: false,
    }
  },

  computed: {
    cleanKeysState() {
      return new Map(
        Object.entries(keycodes).map(([_, keycode]) => [keycode, false])
      )
    },
  },

  watch: {
    highlight: {
      handler(n: number) {
        const key = Math.trunc(n)
        const shiftKey = ((n * 10) % 10) / 10 + 16
        this.keysState = new Map([
          ...this.cleanKeysState,
          [key, true],
          [shiftKey, true],
        ])
      },
      immediate: true,
    },
  },

  mounted() {
    if (this.auto) {
      document.addEventListener('keydown', (event) => {
        const keyId = event.keyCode + event.location / 10
        if (!this.keysState.get(keyId)) {
          // let changedValue = new Map([[keyId, true]]);
          this.keysState = new Map([...this.keysState, [keyId, true]])

          if (keyId === 9) event.preventDefault() // prevent from tabbing out
          if (keyId === 20)
            this.capOn =
              event.getModifierState && !event.getModifierState('CapsLock')
        }
      })
      document.addEventListener('keyup', (event) => {
        const keyId = event.keyCode + event.location / 10

        // let changedValue = new Map([[keyId, false]]);
        this.keysState = new Map([...this.keysState, [keyId, false]])
      })
    }
  },
})
</script>

<style lang="scss" scoped>
$rose-gold: #202124;
$key-color: #202124;

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 854px;
  height: 397px;
  border: 2px solid $rose-gold;
  border-radius: 35px;
  background: $rose-gold;
  padding: 0px;
  box-sizing: unset;
}

.key-container {
  display: grid;
  grid-template-rows: repeat(7, auto);
  // border: 1px solid #a87961;
  // box-shadow: inset 0px 2px 2px 0px #a87961, inset 2px 0px 2px 0px #a87961,
  //   inset -2px 2px 2px 0px #a87961, inset 0px -2px 2px 0px #a87961;
  width: 780px;
  height: 330px;
  margin: 3.5% 0 0 0;
  border-radius: 12px;
}

.row1 {
  display: flex;
  justify-content: space-around;
  margin: 1% 0.5% 0 0.5%;
}

.row2,
.row3,
.row4,
.row5 {
  display: flex;
  justify-content: space-around;
  margin: 0 0.5% 0 0.5%;
}

.row6 {
  display: flex;
  justify-content: space-around;
  margin: 0 0.5% 0% 0.5%;
}

.touchID {
  width: 23px;
  border-radius: 5px;
  // f-keys style
  font-size: 0.5em !important;
  letter-spacing: -0.05em;
  display: flex;
  justify-content: center;
  align-items: flex-end;
  background: $key-color;
  border-radius: 5px;
  border: 2px solid black;
  padding: 0;
  height: 23px;
  // width: 48px;
}

.arrow-key-cont {
  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 5px;
  font-size: 0.9em;
  height: 49px;
  background-color: $rose-gold;
}

.row3 > div,
.row4 > div,
.row5 > div,
.row6 > div {
  justify-content: center;
}

.row4 > .caps {
  align-items: flex-start;
  width: 82px;
}

.trackpad {
  margin: 1% 0;
  width: 320px;
  height: 220px;
  border: 1px solid #9f6e57;
  border-radius: 10px;
}
</style>
