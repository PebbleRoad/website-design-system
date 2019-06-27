<template>
  <component :is="wrapper" :class="['textarea', { 'textarea-expand': width === 'expand' }]">
    <label :for="id" v-if="label">{{ label }}</label>
    <textarea
      :id="id"
      :disabled="disabled"
      :class="state"
      :placeholder="placeholder"
      @input="onInput($event.target.value)"
      @focus="onFocus($event.target.value)"
      v-model="value"
    />
  </component>
</template>

<script>
/**
 * Textareas are used to allow users to provide text input when the expected
 * input is long. Textarea has a range of options. For shorter input,
 * use the `Input` element.
 */
export default {
  name: "Textarea",
  status: "ready",
  release: "3.5.0",
  props: {
    /**
     * Text value of the form textarea.
     */
    value: {
      type: String,
      default: null,
    },
    /**
     * The placeholder value for the form textarea.
     */
    placeholder: {
      type: String,
      default: null,
    },
    /**
     * The label of the form textarea.
     */
    label: {
      type: String,
      default: null,
    },
    /**
     * The html element name used for the wrapper.
     * `div, section`
     */
    wrapper: {
      type: String,
      default: "div",
      validator: value => {
        return value.match(/(div|section)/)
      },
    },
    /**
     * Unique identifier of the form textarea.
     */
    id: {
      type: String,
      default: null,
    },
    /**
     * The width of the form textarea.
     * `auto, expand`
     */
    width: {
      type: String,
      default: "expand",
      validator: value => {
        return value.match(/(auto|expand)/)
      },
    },
    /**
     * Whether the form textarea is disabled or not.
     * `true, false`
     */
    disabled: {
      type: Boolean,
      default: false,
    },
    /**
     * Manually trigger various states of the textarea.
     * `hover, active, focus`
     */
    state: {
      type: String,
      default: null,
      validator: value => {
        return value.match(/(hover|active|focus)/)
      },
    },
  },
  methods: {
    onInput(value) {
      this.$emit("change", value)
    },
    onFocus(value) {
      this.$emit("focus", value)
    },
  },
}
</script>

<style lang="scss" scoped>
// Design Tokens with local scope
$color-placeholder: $color-grey-dark;

.textarea {
  @include stack-space($space-s);
  font-weight: $weight-normal;
  font-family: $font-text;
  font-size: $size-s;
  line-height: $line-height-xs;
  width: auto;
  &-expand {
    width: 100%;
  }
  label {
    cursor: pointer;
    display: block;
    font-size: $size-xs;
    color: $color-asphalt;
    @include stack-space($space-xxs);
  }
  textarea {
    @include reset;
    @include inset-squish-space($space-s);
    transition: all 0.2s ease;
    -webkit-appearance: none;
    appearance: none;
    resize: vertical;
    min-height: $space-xl;
    font-size: $size-s;
    font-family: $font-text;
    background: $color-white;
    border-radius: $radius-default;
    color: $color-asphalt;
    width: 100%;
    margin: 0;
    border: 1px solid $color-asphalt;
    box-shadow: 0;
    &::-webkit-input-placeholder {
      -webkit-font-smoothing: antialiased;
      color: $color-placeholder;
    }
    &:-ms-input-placeholder {
      color: $color-placeholder;
    }
    &::-moz-placeholder {
      color: $color-placeholder;
      -moz-osx-font-smoothing: grayscale;
      opacity: 1;
    }
    &:hover,
    &.hover {
      box-shadow: $shadow-s;
    }
    &:focus,
    &.focus {
      transition: box-shadow 0.2s ease;
      box-shadow: $shadow-focus;
      outline: 0;
    }
    &[disabled] {
      -webkit-font-smoothing: antialiased;
      box-shadow: 0 0 0 1px tint($color-grey-darker, 80%);
      background: lighten($color-placeholder, 42%);
      color: $color-asphalt;
      cursor: not-allowed;
      opacity: 0.7;
      background: $color-grey;
      border: 1px solid $color-grey;
    }
  }
}
</style>

<docs>
  ```jsx
  <div>
    <Textarea label="Default textarea" placeholder="Write your text" id="textarea-1" />
    <Textarea label=":focus" state="focus" placeholder="Write your text" id="textarea-2" />
    <Textarea label="[disabled] with no placeholder" disabled id="textarea-3" />
    <Textarea label="[disabled] with placeholder" disabled value="Disabled text" id="textarea-3" />
  </div>
  ```
</docs>
