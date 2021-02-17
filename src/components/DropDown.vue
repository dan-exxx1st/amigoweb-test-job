<template>
  <div class="drop-down">
    <span class="drop-down__label">{{ label }}</span>
    <div
      class="drop-down__field"
      :class="isActive"
      @click="$emit('toggleOpen')"
    >
      <span
        class="drop-down__placeholder"
        v-if="placeholder.length && currentValue.length === 0"
        >{{ label }}</span
      >
      <span class="drop-down__field__text" v-else>{{ currentValue }}</span>
      <svg
        width="16"
        height="9"
        viewBox="0 0 16 9"
        xmlns="http://www.w3.org/2000/svg"
        class="drop-down__field__icon"
      >
        <path
          d="M8 6.58579L14.2929 0.292893C14.6834 -0.0976311 15.3166 -0.0976311 15.7071 0.292893C16.0976 0.683418 16.0976 1.31658 15.7071 1.70711L8.70711 8.70711C8.31658 9.09763 7.68342 9.09763 7.29289 8.70711L0.292893 1.70711C-0.0976311 1.31658 -0.0976311 0.683418 0.292893 0.292893C0.683418 -0.0976311 1.31658 -0.0976311 1.70711 0.292893L8 6.58579Z"
          fill="#0880AE"
        />
      </svg>
    </div>
    <div class="drop-down__values">
      <ul class="drop-down__values__list">
        <li
          class="drop-down__values__list__item"
          v-for="value in values"
          :key="value"
          @click="selectValue(value)"
        >
          {{ value }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    values: {
      type: Array,
      default: () => []
    },
    currentValue: {
      type: String,
      default: "",
      required: true
    },
    opened: {
      type: Boolean,
      default: false
    },
    label: {
      type: String,
      default: ""
    },
    placeholder: {
      type: String,
      default: ""
    }
  },
  computed: {
    isActive() {
      return this.opened ? "active" : "";
    }
  },
  methods: {
    selectValue(value) {
      this.$emit("selectValue", value);
      this.$emit("toggleOpen");
    }
  }
};
</script>

<style lang="scss">
.drop-down {
  display: flex;
  flex-direction: column;
  position: relative;

  &__field {
    display: flex;
    justify-content: space-between;
    align-items: center;
    cursor: pointer;
    padding: 16px;
    background: #ffffff;
    border: 1px solid #dbe2ea;
    box-sizing: border-box;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
    border-radius: 6px;

    &__text {
      font-size: 16px;
      line-height: 21px;

      color: #2c2738;
    }

    &.active {
      border: 2px solid #0880ae;

      & ~ .drop-down__values {
        display: block;
      }
    }
  }

  &__label {
    font-weight: 500;
    font-size: 16px;
    line-height: 21px;

    color: #756f86;
  }

  &__placeholder {
    font-size: 16px;
    line-height: 21px;
    color: #7c9cbf;
  }

  &__values {
    position: absolute;
    top: 84px;
    display: none;
    background: #ffffff;
    border: 1px solid #dbe2ea;
    box-sizing: border-box;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04),
      0px 20px 20px rgba(44, 39, 56, 0.04);
    border-radius: 6px;
    z-index: 2;
    width: 100%;

    &__list {
      padding: 12px 0;
      &__item {
        padding: 12px 15px;
        list-style: none;
        cursor: pointer;

        font-size: 16px;
        line-height: 21px;

        color: #756f86;

        &:hover {
          background: #ebf4f8;
        }
      }
    }
  }
}
</style>
