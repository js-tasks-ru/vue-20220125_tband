<template>
  <div class="dropdown" :class="{ dropdown_opened: opened }">
    <button
      type="button"
      class="dropdown__toggle"
      :class="{ dropdown__toggle_icon: hasIcon }"
      @click="opened = !opened"
    >
      <ui-icon v-if="!!selectedOption?.icon" :icon="selectedOption.icon" class="dropdown__icon" />
      <span>{{ selectedOption?.text ?? title }}</span>
    </button>

    <div v-show="opened" class="dropdown__menu" role="listbox">
      <button
        v-for="(item, index) in options"
        :key="index"
        class="dropdown__item"
        :class="{ dropdown__item_icon: hasIcon }"
        role="option"
        type="button"
        @click="selectOption(item.value)"
      >
        <ui-icon v-if="!!item.icon" :icon="item.icon" class="dropdown__icon" />
        {{ item.text }}
      </button>
    </div>

    <select v-show="false" :value="modelValue" @change="$emit('update:modelValue', $event.target.value)">
      <option v-for="(item, index) in options" :key="index" :value="item.value">
        {{ item.text }}
      </option>
    </select>
  </div>
</template>

<script>
import UiIcon from './UiIcon';

export default {
  name: 'UiDropdown',

  components: { UiIcon },

  props: {
    options: { type: Array, required: true },
    modelValue: { type: String },
    title: { type: String, required: true },
  },

  emits: ['update:modelValue'],

  data() {
    return {
      opened: false,
    };
  },

  computed: {
    selectedOption() {
      return this.modelValue ? this.options.find((item) => item.value == this.modelValue) : null;
    },

    hasIcon() {
      return this.options.some((it) => !!it.icon);
    },
  },

  methods: {
    selectOption(val) {
      this.$emit('update:modelValue', val);
      this.opened = false;
    },
  },
};
</script>

<style scoped>
.dropdown {
  position: relative;
  display: inline-block;
}

.dropdown__toggle {
  display: inline-block;
  background-color: var(--white);
  background-position: calc(100% - 10px) calc(100% - 10px);
  border: 2px solid var(--blue-light);
  border-radius: 8px;
  position: relative;
  padding: 10px 56px 10px 24px;
  font-weight: 500;
  font-size: 20px;
  line-height: 28px;
  color: initial;
  text-align: center;
  transition-duration: 0.2s;
  transition-property: background-color, fill, color;
  outline: none;
  box-shadow: none;
  cursor: pointer;
  text-decoration: none;
}

.dropdown__toggle:after {
  content: '';
  position: absolute;
  top: 15px;
  right: 16px;
  transform: none;
  background: url('~@/assets/icons/icon-chevron-down.svg') no-repeat;
  background-size: cover;
  display: block;
  width: 24px;
  height: 24px;
  transition: 0.2s transform;
}

.dropdown__toggle.dropdown__toggle_icon {
  padding-left: 56px;
}

.dropdown_opened .dropdown__toggle {
  border-color: var(--blue);
  border-bottom-color: transparent;
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0;
}

.dropdown_opened .dropdown__toggle:after {
  transform: rotate(180deg);
}

.dropdown__menu {
  margin: 0;
  width: 100%;
  padding: 0;
  border-radius: 0 0 8px 8px;
  left: 0;
  z-index: 95;
  background-clip: padding-box;
  display: none;
  flex-direction: column;
  border: 2px solid var(--blue);
  border-top: none;
  overflow: hidden;
}

.dropdown_opened .dropdown__menu {
  display: flex;
  position: absolute;
  transform: translate3d(0px, 52px, 0px);
  top: -1px;
  left: 0;
  will-change: transform;
  right: auto;
  bottom: auto;
}

.dropdown__item {
  padding: 8px 16px;
  font-weight: 500;
  font-size: 20px;
  line-height: 28px;
  background-color: var(--white);
  box-shadow: none;
  border: none;
  cursor: pointer;
  text-align: left;
  transition-duration: 0.2s;
  transition-property: background-color, border-color, color;
  outline: none;
  text-decoration: none;
}

.dropdown__item:hover,
.dropdown__item:focus {
  background-color: var(--grey-light);
}

.dropdown__item.dropdown__item_icon {
  padding-left: 56px;
  position: relative;
}

.dropdown__item.dropdown__item_icon .dropdown__icon,
.dropdown__toggle_icon .dropdown__icon {
  position: absolute;
  top: 50%;
  left: 16px;
  transform: translate(0, -50%);
}
</style>
