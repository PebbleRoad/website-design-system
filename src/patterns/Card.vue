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
  status: "prototype",
  release: "1.0.0",
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
  @include reset;
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
  box-shadow: $shadow-s;
}

.s {
  padding: $space-s;
}

.m {
  padding: $space-m;
}

.l {
  padding: $space-l;
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

    <Card border padding="m">
      <Heading level="h4">Lorem Ipsum</Heading>
      <Paragraph>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras facilisis feugiat aliquam.</Paragraph>
      <Tag>Category</Tag>
      <Tag>Category</Tag>
    </Card> 

    <Card border padding="l">
      <Heading level="h4">Lorem Ipsum</Heading>
      <Paragraph>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras facilisis feugiat aliquam.</Paragraph>
      <Tag>Category</Tag>
      <Tag>Category</Tag>
    </Card> 
  </Grid>

  ```
  </docs>
