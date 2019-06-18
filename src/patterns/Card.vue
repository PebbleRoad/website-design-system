<template>
  <component :is="type" :class="[{ 'border--show': border === true }, 'card']">
    <img v-if="media" :src="media" alt="card-media" />
    <div
      :class="[
        'content',
        padding ? padding : 'padding--default',
        { 'fix--height': fixedHeight === true },
      ]"
    >
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
    /**
     * Adds a border around the card
     * */
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
     * Fixes height to 255px
     * */
    fixedHeight: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style lang="scss" scoped>
$card-height: 235px;
$card-height-tablet: 255px;

.card {
  @include reset;
  width: inherit;
  height: 100%;
  box-sizing: border-box;
}

.fix--height {
  height: $card-height;
}

.padding--default {
  padding-top: $space-xs;
}

.s {
  padding: $space-s;
}

.m {
  padding: $space-s;
}

.l {
  padding: $space-m;
}

.content {
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-top: -4px;
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

  .padding--default {
    padding-top: $space-s;
  }

  .fix--height {
    height: $card-height-tablet;
  }
}

.border--show {
  box-shadow: $shadow-s;
}
</style>

<docs>
  ```jsx
  <Grid columns="three" spacing="m">
      <Card border fixedHeight padding="s" media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Paragraph variation="xsmall">Categories</Paragraph>
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem ipsum.
        </Paragraph>
      </Paragraph>
      <Paragraph slot="bottomAlign" variation="xsmall">Date</Paragraph>
    </Card>

      <Card border fixedHeight padding="m" media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
      <Paragraph variation="xsmall">Categories</Paragraph>
      <Paragraph>      
        <Paragraph variation="medium" bold>Lorem ipsum dolor sit amet, consectetur adipiscing elit.
        </Paragraph>
      </Paragraph>
      <Paragraph slot="bottomAlign" variation="xsmall">Date</Paragraph>    </Card>

    <Card border fixedHeight padding="l" media="https://media.giphy.com/media/l3V0ca6GTvdB7CzJK/giphy.gif">
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
