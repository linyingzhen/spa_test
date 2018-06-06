<template>
  <div>
      <div v-show="qrcodeUrl" class="response">
<qrcode 
:value="qrcodeUrl" 
v-if="qrcodeUrl" 
:options="{ size: 170 }">
</qrcode>
<p>请使用支付宝扫码支付</p>
</div>
  </div>
</template>


<script>
import Qrcode from 'vue-qrcode';
export default {
  name: "Two",
  props: {},
  data() {
    return {
      msg: "hello,Two"
    };
  },
  created() {
    let curthis = this;
    this.$http
      .get("/static/person.json")
      .then(function(res) {
        // console.log(res.data);
        curthis.msg = res.data;
        // console.log(curthis.msg);
      })
      .catch(function(err) {
        console.log(err);
      });
  },
  methods: {
    showMsg: function() {
      console.log(this.msg);
    }
  },
  mounted: function() {
    this.qrcode();
  },
  components: {
      qrcode: Qrcode
  }
};
</script>


<style lang="scss">
ul {
  .title {
    font-size: 36px;
    color: green;
  }
}
</style>
