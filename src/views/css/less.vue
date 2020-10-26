<template>
  <div id="app-container">
    <div class="page-wrap">
      <div class="ct1"><p>nihao</p></div>
      <div class="ct2"><p>hello</p></div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Less',

  data() {
    return {
      size: 100
    }
  }
}
</script>

<style lang="less">
  @width: 100px;
  @height: @width + 20px;

  .fontSize {
    font-size: 26px;
  }

  .page-wrap {
    border: solid;
    width: @width;
    height: @height;
    .ct1 {
      p {
        .fontSize()
      }
    }

    .ct2 {
      p {
        .fontSize()
      }
    }

    & {
      content: '434';
      border: 1px solid red;
      background-color: #000 + 222;
    }
  }

</style>
