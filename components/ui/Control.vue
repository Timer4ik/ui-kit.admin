<template>
  <div class="control" :class="[{ invalid }, { valid }]">
    <div v-if="label" class="control__label">
      {{ label }}
    </div>
    <div class="control__wrap">
      <slot />
      <div v-if="rightIcon" class="control__icon">
        <component :is="rightIcon" />
      </div>
      <div v-if="$slots.rightIcon" class="control__icon">
        <slot name="rightIcon" />
      </div>
    </div>
    <div class="control__message" v-if="message" :class="[{ show: !!message }]">
      {{ message }}
    </div>
  </div>
</template>

<script setup lang="ts">
defineComponent({
  inheritAttrs: false,
});

import { InputHTMLAttributes } from "nuxt/dist/app/compat/capi";

interface Props extends /* @vue-ignore */ InputHTMLAttributes {
  label?: string;
  rightIcon?: any;
  message?: any;
  invalid?: boolean;
  valid?: boolean;
}

defineProps<Props>();
</script>

<style lang="scss">
// Для стандартного контрола без ошибок
.control {
  position: relative;
  padding-bottom: 22px;

  display: block;
  font-family: Inter, ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto,
    Helvetica Neue, Arial, Noto Sans, Liberation Sans, sans-serif,
    Apple Color Emoji, Segoe UI Emoji, Segoe UI Symbol, Noto Color Emoji;
  transition: all 0.2s linear;

  &__wrap {
    position: relative;
  }

  &__label {
    transition: all 0.2s linear;
    margin-bottom: 0.5rem;
    font-size: 0.875rem;
    font-weight: 500;
    opacity: 0.7;
    color: #16192c;
  }

  &__message {
    transition: all 0.2s linear;
    margin-top: 0.5rem;
    font-size: 0.8rem;
    font-weight: 500;
    opacity: 0.7;
    color: #16192c98;
    position: absolute;
    bottom: 0px;
  }

  .control__field {
    transition: all 0.2s linear;
  }

  &__icon {
    position: absolute;
    top: 50%;
    right: 18px;
    transform: translate(0, -50%);
    height: 18px;
    width: 18px;

    img,
    svg {
      opacity: 0.7;
      object-fit: contain;
      width: 100%;
      height: 100%;
    }
  }
}
// Для контрола с ошибкой
.invalid.control {
  transition: all 0.2s linear;

  .control__label {
    transition: all 0.2s linear;
    color: #ff0000;
  }

  .control__message {
    transition: all 0.2s linear;
    color: #ff0000;
  }

  .control__field::-webkit-input-placeholder {
    transition: all 0.2s linear;
    color: #ff0000;
    opacity: 0.7;
  }

  .control__field,
  .control__textarea {
    transition: all 0.2s linear;
    color: #ff0000;
    background-color: #fee;
    border-color: #ff6464;
    outline: 0;
    box-shadow: 0px 1px 2px rgba(71, 50, 50, 0.08),
      0 0 0 3px rgba(245, 92, 92, 0.25);
  }

  .control__checkbox {
    transition: all 0.2s linear;

    .checkbox__input {
      transition: all 0.2s linear;
      background-color: #fee;
      border-color: #ff6464;
      outline: 0;
      box-shadow: 0px 1px 2px rgba(71, 50, 50, 0.08),
        0 0 0 3px rgba(245, 92, 92, 0.25);
    }

    .checkbox__label {
      color: #ff0000;
    }
  }

  .control__fileloader {
    .fileloader__input {
      transition: all 0.2s linear;
      color: #ff0000;
      background-color: #fee;
      border-color: #ff6464;
      outline: 0;
      box-shadow: 0px 1px 2px rgba(71, 50, 50, 0.08),
        0 0 0 3px rgba(245, 92, 92, 0.25);
    }

    .fileloader__input::file-selector-button {
      background-color: #fee;
      color: #ff0000;
    }
  }

  .control__datepicker .dp__input {
    transition: all 0.2s linear;
    color: #ff0000;
    background-color: #fee;
    border-color: #ff6464;
    outline: 0;
    box-shadow: 0px 1px 2px rgba(71, 50, 50, 0.08),
      0 0 0 3px rgba(245, 92, 92, 0.25);
  }

  .control__textarea::-webkit-input-placeholder {
    transition: all 0.2s linear;
    color: #ff0000;
    opacity: 0.7;
  }

  .control__photoloader {
    transition: all 0.2s linear;
    color: #ff0000;
    background-color: #fee;
    border-color: transparent;
    outline: 0;
    box-shadow: 0px 1px 2px rgba(71, 50, 50, 0.08),
      0 0 0 3px rgba(245, 92, 92, 0.25);

    .photoloader__title,
    .photoloader__subtitle {
      color: #ff0000;
    }
  }
}
// Для корректного контрола
.valid.control {
  .control__label {
    color: #279f47;
  }

  .control__message {
    color: #279f47;
  }

  .control__field::-webkit-input-placeholder {
    color: #279f47;
    opacity: 0.7;
  }

  .control__field {
    color: #279f47;
    background-color: #fff;
    border-color: #1eff00;
    outline: 0;
    box-shadow: 0px 1px 2px rgba(50, 71, 50, 0.08),
      0 0 0 3px rgba(92, 245, 107, 0.25);
  }
}
</style>
