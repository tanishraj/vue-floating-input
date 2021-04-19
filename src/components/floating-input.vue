<template>
  <div class="floating-input" :class="[textFlag, accessStatus, config.valid]">
    <label :for="config.id">
      {{ config.label }}
    </label>
    <input
      class="input-text"
      :class="config.customClass"
      :id="config.id"
      v-model="inputValue"
      @focus="inputFocus"
      @blur="inputBlur"
      @input="inputChange"
    />
  </div>
</template>

<script>
import "../assets/styles/_fonts.scss";
export default {
  name: "FloatingInput",
  props: {
    config: Object,
  },
  computed: {},
  data() {
    return {
      inputValue: null,
      textFlag: null,
      accessStatus: null,
    };
  },
  methods: {
    inputBlur() {
      this.accessStatus = "";
    },

    inputFocus() {
      this.accessStatus = "active";
    },

    inputChange() {
      if (this.inputValue.length > 0) {
        this.textFlag = "dirty";
      } else {
        this.textFlag = null;
      }
    },
  },
};
</script>

<style scoped lang="scss">
.floating-input {
  font-family: "Gentona Book";
  font-size: 18px;
  line-height: 24px;
  border: 1.5px solid rgba(0, 0, 0, 0.12);
  background: #fff;
  position: relative;

  label {
    color: rgba(0, 0, 0, 0.36);
    position: absolute;
    top: calc(50% - 12px);
    left: 16px;
    cursor: text;
    transition: all 0.3s;
  }

  .input-text {
    box-sizing: border-box;
    border: none;
    outline: none;
    padding: 16px 16px;
    width: 100%;
    font-family: "Gentona Medium";
    font-size: 18px;
    line-height: 24px;
    transition: all 0.3s;
  }

  &.active {
    border: 1.5px solid #16aa51;
  }

  &.dirty {
    label {
      font-family: "Gentona Medium";
      font-size: 12px;
      top: calc(50% - 20px);
      line-height: 1;
      transition: all 0.3s;
    }
    .input-text {
      padding: 24px 16px 8px;
      transition: all 0.3s;
    }

    &.active {
      label {
        color: #16aa51;
      }
    }
  }

  &.notValid {
    border-color: #c91a3a;
    label {
      color: #c91a3a;
    }
    &.active {
      @extend .notValid;
    }
  }
}
</style>
