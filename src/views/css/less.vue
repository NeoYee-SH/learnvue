<template>
  <div id="app-container">
    <div class="page-wrap">
      <div class="ct1"><p>nihao</p></div>
      <div class="ct2"><p>hello</p></div>
      <viewer :images="handImg">
        <img v-for="src in handImg" :key="src" :src="src" width="50" height="50px" :alt="src">
      </viewer>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Less',

  data() {
    return {
      size: 100,
      handImg: [
        'http://test.img.zhian-design.com/img/20/09/21/4d408b95-0947-4fa8-8119-ec371bb1cec5.jpg',
        'http://test.img.zhian-design.com/img/20/09/21/c4bef533-80a7-4798-b630-28d7652fa0d3.jpg',
        'http://test.img.zhian-design.com/img/20/09/21/3434603c-efec-4330-9f04-b0f35d142621.png'
      ]
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
