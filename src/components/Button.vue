<template>
  <button class="button" :class="isDisable">
    <span class="button__text">
      {{ text }}
    </span>
  </button>
</template>

<script>
export default {
  props: {
    text: {
      type: String,
      required: true
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },

  computed: {
    isDisable() {
      return this.disabled ? "disabled" : "";
    }
  }
};
</script>

<style lang="scss">
.button {
  background: var(--bc);
  box-shadow: 0px 2px 4px rgba(44, 39, 56, 0.08),
    0px 4px 8px rgba(44, 39, 56, 0.08);
  border-radius: 6px;
  border: none;
  outline: none;
  padding: 18px;

  cursor: pointer;

  &__text {
    color: #ebf4f8;

    font-style: normal;
    font-weight: 500;
    font-size: 16px;
    line-height: 21px;
    text-align: center;
  }

  &:hover {
    box-shadow: 0px 12px 24px rgba(44, 39, 56, 0.08),
      0px 24px 48px rgba(44, 39, 56, 0.16);
  }

  &.disabled {
    background: #dbe2ea;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.08);
    cursor: not-allowed;

    .button__text {
      color: #2c2738;
      mix-blend-mode: normal;
      opacity: 0.5;
    }
  }
}
</style>
