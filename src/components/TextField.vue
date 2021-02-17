<template>
  <div class="text-field">
    <span class="text-field__label">{{ label }}</span>
    <input
      type="text"
      class="text-field__input"
      :placeholder="placeholder"
      :value="value"
      @input="$emit('input', $event.target.value)"
    />
    <span class="text-field__validation">{{ validationMessage }}</span>
  </div>
</template>

<script>
export default {
  props: {
    placeholder: {
      type: String,
      default: ""
    },
    validationMessage: {
      type: String,
      default: ""
    },
    value: {
      type: String,
      default: ""
    },
    label: {
      type: String,
      default: ""
    }
  }
};
</script>

<style lang="scss">
.text-field {
  display: flex;
  flex-direction: column;

  &__label {
    font-style: normal;
    font-weight: 500;
    font-size: 16px;
    line-height: 21px;
    color: var(--gc);
    margin-bottom: 7px;
  }

  &__input {
    background: #ffffff;
    border: 1px solid #dbe2ea;
    box-sizing: border-box;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
    border-radius: 6px;
    outline: none;

    padding: 16px;

    font-style: normal;
    font-weight: normal;
    font-size: 16px;
    line-height: 21px;
    color: #2c2738;

    &::placeholder {
      color: #7c9cbf;
    }

    &:focus {
      border: 2px solid var(--bc);
      border-radius: 6px;
    }
  }

  &__validation {
    margin-top: 8px;

    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 18px;
    color: #ff7171;
  }
}
</style>
