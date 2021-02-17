<template>
  <label class="checkbox">
    <input
      type="checkbox"
      class="checkbox__input"
      @change="$emit('input', $event.target.checked)"
      :checked="checked"
    />
    <span class="checkbox__label"></span>
  </label>
</template>

<script>
export default {
  props: {
    checked: {
      type: Boolean,
      default: false
    }
  }
};
</script>

<style lang="scss">
.checkbox {
  position: relative;
  display: flex;

  cursor: pointer;

  &__input {
    display: none;

    &:checked ~ span {
      border: 2px solid var(--bc);
      width: 26px;
      height: 26px;

      &:after {
        visibility: visible;
      }
    }
  }

  &__label {
    display: inline-block;
    width: 28px;
    height: 28px;
    background: #ffffff;
    border: 1px solid #dbe2ea;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
    border-radius: 4px;
    transition: all linear 0.2s;

    &:after {
      content: "";
      position: absolute;
      top: 6px;
      left: 12px;
      border-bottom: 2px solid var(--bc);
      border-right: 2px solid var(--bc);
      height: 14px;
      width: 6px;
      transform: rotate(45deg);
      visibility: hidden;
    }
  }
}
</style>
