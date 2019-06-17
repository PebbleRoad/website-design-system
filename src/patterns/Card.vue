<template>
  <component :is="type" :class="[{ 'border--show': border === true }, 'card']">
    <img v-if="media" :src="media" alt="card-media" />
    <div :class="[padding ? padding : 'content']">
      <div>
        <slot />
      </div>
      <div>
        <slot name="bottomAlign" />
      </div>
    </div>
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
$card-height: 255px;

.card {
  @include reset;
  width: inherit;
  height: 100%;
  box-sizing: border-box;
}

.s {
  padding: $space-s;
  height: $card-height;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.m {
  padding: $space-s;
  height: $card-height;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.l {
  padding: $space-m;
  height: $card-height;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.content {
  padding-top: $space-s;
  height: $card-height;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

img {
  width: inherit;
  object-fit: cover;
  height: $card-height;
  align-content: center;
}

@media #{$media-query-m} {
  .m {
    padding: $space-m;
  }

  .l {
    padding: $space-l;
  }
}

.border--show {
  box-shadow: $shadow-s;
}
</style>

<docs>
  ```jsx
  <Grid columns="three" spacing="m">
      <Card border padding="s" media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Paragraph variation="xsmall">Categories</Paragraph>
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem ipsum.
        </Paragraph>
      </Paragraph>
      <Paragraph slot="bottomAlign" variation="xsmall">Date</Paragraph>
    </Card>

      <Card border padding="m" media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Paragraph variation="xsmall">Categories</Paragraph>
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        </Paragraph>
      </Paragraph>
      <Paragraph slot="bottomAlign" variation="xsmall">Date</Paragraph>    </Card>

    <Card border padding="l" media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Paragraph variation="xsmall">Categories</Paragraph>
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ip
        </Paragraph>
      </Paragraph>
      <Paragraph slot="bottomAlign" variation="xsmall">Date</Paragraph>    
    </Card>

    <Card media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Paragraph variation="xsmall">Categories</Paragraph>
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ip
        </Paragraph>
      </Paragraph>
      <Paragraph slot="bottomAlign" variation="xsmall">Date</Paragraph>    
    </Card>

    <Card media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Paragraph variation="xsmall">Categories</Paragraph>
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        </Paragraph>
      </Paragraph>
      <Paragraph slot="bottomAlign" variation="xsmall">Date</Paragraph>    
    </Card>

    <Card media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Paragraph variation="xsmall">Categories</Paragraph>
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Lorem ipsum dolor sit amet, consectetur adipiscing elit.Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        </Paragraph>
      </Paragraph>
      <Paragraph slot="bottomAlign" variation="xsmall">Date</Paragraph>    
    </Card>
  </Grid>

  ```
  </docs>
