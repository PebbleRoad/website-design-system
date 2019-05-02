<template>
  <component :is="type" :href="href" :type="submit" :class="['button', state, variation]">
    <slot />
  </component>
</template>

<script>
const req = require.context("@/assets/icons/", true, /^\.\/.*\.svg$/)

/**
 * Buttons are generally used for interface actions. Suitable for all-purpose use.
 * Defaults to appearance that has white background with grey border.
 * Primary style should be used only once per view for main call-to-action.
 */
export default {
  name: "Button",
  status: "prototype",
  release: "3.5.0",
  props: {
    /**
     * The html element used for the button.
     * `button, a`
     */
    type: {
      type: String,
      default: "button",
      validator: value => {
        return value.match(/(button|a)/)
      },
    },
    href: {
      type: String,
      default: null,
    },
    /**
     * Set the button’s type to “submit”.
     */
    submit: {
      type: String,
      default: null,
      validator: value => {
        return value.match(/(null|submit)/)
      },
    },
    /**
     * Manually trigger various states of the button.
     * `hover, active, focus`
     */
    state: {
      type: String,
      default: null,
      validator: value => {
        return value.match(/(hover|active|focus|disabled)/)
      },
    },
    /**
     * Style variation to give additional meaning.
     * `primary, secondary`
     */
    variation: {
      type: String,
      default: "primary",
      validator: value => {
        return value.match(/(primary|secondary)/)
      },
    },
  },
  data() {
    return {
      svg: req("./" + this.name + ".svg").replace(/^<svg /, `<svg style="fill: ${this.fill}" `),
    }
  },
}
</script>

<style lang="scss" scoped>
.button {
  @include reset;
  @include stack-space($space-m);
  @include inline-space($space-xs);
  @include inset-squish-space($space-xs);
  will-change: transform;
  transition: all 0.2s ease;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  padding: $space-xs $space-s;
  font-weight: $weight-semi-bold;
  font-size: $size-s;
  font-family: $font-text;
  line-height: $line-height-m;
  text-decoration: none;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  border: 0;
  box-shadow: inset 0 0 0 2px $color-asphalt;
  border-radius: $radius-default;
  background: transparent;
  color: $color-asphalt;
  cursor: pointer;
  &:hover,
  &.hover {
    color: $color-white;
    background: $color-asphalt;
  }
  &:active,
  &.active {
    background: $color-grey-darker;
    box-shadow: $shadow-xl;
    color: $color-white;
    transform: translateZ(0) scale(1);
  }
  &:focus,
  &.focus {
    background: $color-asphalt;
    box-shadow: $shadow-focus;
    color: $color-white;
    outline: 0;
  }

  &:disabled,
  &.disabled {
    cursor: not-allowed;
    color: $color-grey-dark;
    background-color: $color-grey;
    border: none;
  }

  //For icons inside buttons
  .icon {
    margin: 0 0 $space-xxxs/-2 $space-xxs;
  }

  // Primary button
  &.primary {
    background: $color-asphalt;
    color: $color-white;
    box-shadow: none;
    border: 1px solid $color-asphalt;
    &:hover,
    &.hover {
      transform: translateZ(0) scale(1.03);
      box-shadow: $shadow-m;
    }
    &:active,
    &.active {
      background-color: $color-grey-darker;
      transition: none;
    }
    &:focus,
    &.focus {
      box-shadow: $shadow-focus;
    }
    &:disabled,
    &.disabled {
      cursor: not-allowed;
      color: $color-grey-dark;
      background-color: $color-grey;
      border: none;
    }
  }

  // Secondary button
  &.secondary {
    background: $color-white;
    color: $color-asphalt;
    box-shadow: none;
    border: 1px solid $color-asphalt;
    &:hover,
    &.hover {
      transform: translateZ(0) scale(1.03);
      box-shadow: $shadow-m;
    }
    &:active,
    &.active {
      background-color: $color-sand;
      transition: none;
    }
    &:focus,
    &.focus {
      box-shadow: $shadow-focus;
    }
    &:disabled,
    &.disabled {
      cursor: not-allowed;
      color: $color-grey-dark;
      background-color: $color-grey;
      border: none;
    }
  }
}
</style>

<docs>
  ```jsx
  <div>
    <Button>Default Button</Button>
    <Button>
      Under review
      <Icon name="review" fill="#ffffff" size="small" class="icon" />
    </Button>
    <br />
    <Button variation="primary">Default Primary Button</Button>
    <Button variation="primary" state="hover">:hover</Button>
    <Button variation="primary" state="active">:active</Button>
    <Button variation="primary" state="focus">:focus</Button>
    <Button variation="primary" state="disabled">:disabled</Button>
    <br />
    <Button variation="secondary">Default Secondary Button</Button>
    <Button variation="secondary" state="hover">:hover</Button>
    <Button variation="secondary" state="active">:active</Button>
    <Button variation="secondary" state="focus">:focus</Button>
    <Button variation="secondary" state="disabled">:disabled</Button>
      </div>
  ```
</docs>
