<template>
  <component
    :is="type"
    :class="[{ 'border--show': border === true }, { 'fix--height': fixedHeight === true }, 'card']"
  >
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
    /**
     * Fixes height of card to 255px
     * */
    fixedHeight: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style lang="scss" scoped>
$card-height: 255px;

.card {
  @include reset;
  width: inherit;
  height: 100%;

  &.fix--height {
    height: $card-height;

    div {
      height: 100%;
      box-sizing: border-box;
    }
  }
}

img {
  width: inherit;
  object-fit: cover;
  height: $card-height;
  align-content: center;
}

.border--show {
  box-shadow: $shadow-s;
}

.s {
  padding: $space-s;
  height: inherit;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.m {
  padding: $space-m;
  height: inherit;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.l {
  padding: $space-l;
  height: inherit;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>

<docs>
  ```jsx
  <Grid columns="three" spacing="m">
    <Card border padding="s" media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Heading level="h4">Lorem Ipsum</Heading>
      <Paragraph>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras facilisis feugiat aliquam.</Paragraph>
    </Card>
    <Card border padding="s" media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Heading level="h4">Lorem Ipsum</Heading>
      <Paragraph>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras facilisis feugiat aliquam.</Paragraph>
    </Card>

    <Card media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Heading level="h4">Lorem Ipsum</Heading>
      <Paragraph>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras facilisis feugiat aliquam.</Paragraph>
    </Card>

    <Card border padding="s">
      <Heading level="h4">Lorem Ipsum</Heading>
      <Paragraph>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras facilisis feugiat aliquam.</Paragraph>
      <Tag>Category</Tag>
      <Tag>Category</Tag>
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

    <Card border fixedHeight padding="l">
      <Heading level="h4">Lorem Ipsum</Heading>
      <Paragraph>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras facilisis feugiat aliquam.</Paragraph>
      <Link>LINK</Link>
    </Card> 

    <Card border fixedHeight padding="l">
      <Heading level="h4">Lorem Ipsum</Heading>
      <Paragraph>Lorem ipsum dolor sit amet</Paragraph>
      <Link>LINK</Link>
    </Card> 

  </Grid>

  ```
  </docs>
