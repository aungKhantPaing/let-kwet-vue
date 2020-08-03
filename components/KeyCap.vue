<template>
  <span
    v-if="fKey"
    class="f-keys"
    :class="{ esc: escKey, 'keydown-style': isDown }"
  >
    <span v-if="escKey">esc</span>
    {{ label }}
  </span>
  <div
    v-else-if="spacebar"
    class="square-key-cont spacebar"
    :class="{ 'keydown-style': isDown }"
  ></div>
  <span
    v-else-if="arrowKey"
    class="arrow-content"
    :class="{ 'down-arrow': downArrow, 'keydown-arrow': isDown }"
  >
    ^
  </span>
  <div
    v-else
    class="square-key-cont"
    :class="{
      delete: deleteKey,
      tab: tabKey,
      caps: capKey,
      return: returnKey,
      'shift-left': shiftKeyLeft,
      'shift-right': shiftKeyRight,
      fn: fnKey,
      cmd: cmdKey,
      'keydown-style': isDown,
    }"
  >
    <span v-if="sideLabel" class="square-content">
      {{ sideLabel }}
    </span>
    <span
      v-if="capKey"
      class="square-content period"
      :style="{ opacity: capOn ? 1 : 0 }"
    >
      .
    </span>
    <span :class="{ 'square-content': sideLabel, ctrl: ctrlKey }">
      {{ label }}
    </span>

    <span v-if="deleteKey">
      delete
    </span>
    <span v-else-if="tabKey">
      tab
    </span>
    <span v-else-if="capKey" class="square-content lock">
      caps lock
    </span>
    <span v-else-if="returnKey" class="return-span">return</span>
    <span v-else-if="shiftKeyLeft || shiftKeyRight">
      shift
    </span>
    <span v-else-if="fnKey">
      fn
    </span>
  </div>
</template>

<script>
// import { Howl, Howler } from 'howler';
export default {
  props: {
    label: {
      type: String,
    },
    sideLabel: {
      type: String,
      default: '',
    },
    deleteKey: {
      type: Boolean,
      default: false,
    },
    tabKey: {
      type: Boolean,
      default: false,
    },
    capKey: {
      type: Boolean,
      default: false,
    },
    capOn: {
      type: Boolean,
      default: false,
    },
    returnKey: {
      type: Boolean,
      default: false,
    },
    shiftKeyLeft: {
      type: Boolean,
      default: false,
    },
    shiftKeyRight: {
      type: Boolean,
      default: false,
    },
    fnKey: {
      type: Boolean,
      default: false,
    },
    ctrlKey: {
      type: Boolean,
      default: false,
    },
    cmdKey: {
      type: Boolean,
      default: false,
    },
    spacebar: {
      type: Boolean,
      default: false,
    },
    fKey: {
      type: Boolean,
      default: false,
    },
    escKey: {
      type: Boolean,
      default: false,
    },
    arrowKey: {
      type: Boolean,
      default: false,
    },
    downArrow: {
      type: Boolean,
      default: false,
    },
    isDown: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style lang="scss" scoped>
$rose-gold: #ffffff;
$key-color: #202124;

//* KEYDOWN STYLES
.keydown-style {
  // border: 2px solid $rose-gold !important;
  background: $rose-gold !important;
  color: black !important;
}
.keydown-arrow {
  // border: 2px solid $rose-gold !important;
  // border-bottom: 1px solid $rose-gold !important;
  background: $rose-gold !important;
  color: black !important;
}

.square-key-cont {
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 2px solid black;
  background: $key-color;
  height: 45px;
  width: 45px;
  border-radius: 5px;
  font-size: 0.9em;
  color: white;
}
.square-content {
  height: 100%;
}

//* DELETE
.delete {
  font-size: 0.7em !important;
  justify-content: flex-end !important;
  align-items: flex-end !important;
  width: 70px !important;
}
.delete > span:last-of-type {
  margin: 0 4% 4% 0;
}

//* TAB
.tab {
  align-items: flex-start;
  justify-content: flex-end;
  width: 70px;
}
.tab > span:last-of-type {
  margin: 0 0 4% 4%;
  font-size: 0.7em;
}

//* CAPS
.caps {
  align-items: flex-start;
  width: 82px;
}
.lock {
  margin: 0 0 4% 4%;
  font-size: 0.7em;
}
.period {
  margin: 0 0 11% 4%;
}

//* RETURN
.return {
  font-size: 0.7em;
  justify-content: flex-end !important;
  align-items: flex-end;
  width: 82px;
}
.return > span:last-of-type {
  margin: 0 4% 4% 0;
}

//* SHIFT
.shift-left {
  width: 110px !important;
  font-size: 0.7em !important;
  display: flex !important;
  align-items: flex-start !important;
  justify-content: flex-end !important;
}
.shift-left > span:last-of-type {
  margin: 0 0 4% 4%;
}
.shift-right {
  width: 110px !important;
  font-size: 0.7em !important;
  display: flex !important;
  align-items: flex-end !important;
  justify-content: flex-end !important;
}
.shift-right > span {
  margin: 0 4% 4% 0;
}

//* Fn
.fn {
  font-size: 0.7em !important;
  display: flex !important;
  align-items: flex-start !important;
  justify-content: flex-end !important;
  width: 45px !important;
}
.fn > span {
  margin: 0 0 4% 6%;
}

//* CTRL
.ctrl {
  margin-top: 20%;
  font-size: 0.7em;
}

//* CMD
.cmd {
  width: 55px !important;
}

//*SPACE
.spacebar {
  width: 260px !important;
}

//* F
.f-keys {
  font-size: 0.5em;
  letter-spacing: -0.05em;
  display: flex;
  justify-content: center;
  align-items: flex-end;
  background: $key-color;
  border-radius: 5px;
  border: 2px solid black;
  padding: 0;
  height: 23px;
  width: 48px;
}

//* ESC
.esc {
  display: flex;
  justify-content: flex-start !important;
  align-items: center !important;
  font-size: 0.7em !important;
}
.esc > span:first-of-type {
  margin: 0 0 0 4% !important;
}

//* ARROW
.arrow-content {
  flex-direction: column;
  background: $key-color;
  align-items: center;
  border: 2px solid black;
  border-bottom: 1px solid black;
  display: flex;
  border-radius: 5px 5px 0px 0px;
  height: 22.5px;
  width: 45px;
}

.down-arrow {
  transform: rotate(180deg);
}
</style>
