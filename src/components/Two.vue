<template>
	<div>
		<ul>
			<button @click="showMsg">show msg</button>
			{{msg}}  
		</ul>
    

	</div>
</template>

<script>
import QRCode from "qrcode";
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