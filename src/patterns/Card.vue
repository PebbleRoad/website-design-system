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
  box-sizing: border-box;

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
}

.m {
  padding: $space-s;
  @media #{$media-query-m} {
    padding: $space-m;
  }
}

.l {
  padding: $space-m;
  @media #{$media-query-m} {
    padding: $space-l;
  }
}
</style>

<docs>
  ```jsx
  <Grid columns="three" spacing="m">
    <Card border padding="s" media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem Ipsum</Paragraph>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      </Paragraph>
    </Card>
    <Card border padding="s" media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem Ipsum</Paragraph>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      </Paragraph>
    </Card>

    <Card media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem Ipsum</Paragraph>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      </Paragraph>
    </Card>

    <Card border padding="s">
      <Tag>Category</Tag>
      <Tag>Category</Tag>
       <Paragraph>      
        <Paragraph variation="medium" bold>Lorem Ipsum</Paragraph>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      </Paragraph>
    </Card> 

    <Card border padding="m">
      <Tag>Category</Tag>
      <Tag>Category</Tag>
       <Paragraph>      
        <Paragraph variation="medium" bold>Lorem Ipsum</Paragraph>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      </Paragraph>
    </Card> 

    <Card border padding="l">
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem Ipsum</Paragraph>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      </Paragraph>
      <div style="height:20px;"><Link>LINK</Link></div>
    </Card> 
  </Grid>

  ```
  </docs>
