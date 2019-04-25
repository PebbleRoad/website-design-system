<template>
  <component :is="type" :class="['card', { 'border--show': border === true }]">
    <img v-if="media" :src="media" alt="card-media" />
    <div :class="padding"><slot /></div>
  </component>
</template>

<script>
/** Card explanation */
export default {
  name: "Card",
  props: {
    /**
     * <code>div</code> or <code>span</code>
     * */
    type: {
      type: String,
      default: "div",
      validator: value => value.match(/div|span/),
    },
    /** Specifies the media URL */
    media: {
      type: String,
      default: null,
    },
    border: {
      type: Boolean,
      default: false,
    },
    /**
     * Specifies <code>grid-gap</code>, options <code>s</code>, <code>m</code> or <code>l</code>
     * */
    padding: {
      type: String,
      default: null,
    },
  },
}
</script>

<style lang="scss" scoped>
.card {
  width: inherit;
  box-sizing: border-box;
}

img {
  width: inherit;
  object-fit: cover;
  height: 180px;
  align-content: center;
}

.border--show {
  border: 2px solid $color-grey;
}

.s {
  padding: 8px;
}

.m {
  padding: 16px;
}

.l {
  padding: 24px;
}
</style>

<docs>
  ```jsx
  <Grid columns="two" spacing="m">
    <Card border padding="s" media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Heading level="h4">Lorem Ipsum</Heading>
      <Paragraph>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras facilisis feugiat aliquam.</Paragraph>
    </Card>

    <Card media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Heading level="h4">Lorem Ipsum</Heading>
      <Paragraph>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras facilisis feugiat aliquam.</Paragraph>
    </Card>

    <Card border padding="s">
      <Paragraph>TAGLINE</Paragraph>
      <Heading level="h4">Lorem Ipsum</Heading>
      <Paragraph>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras facilisis feugiat aliquam.</Paragraph>
    </Card> 
  </Grid>

  ```
  </docs>
