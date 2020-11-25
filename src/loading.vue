<template>
  <div>
    <loading :active.sync="isLoading" 
            :can-cancel="true" 
            :on-cancel="onCancel"
            :is-full-page="fullPage"
            :width="90"
            :height="90"
            >
                
    </loading>
    <div style="text-align : center; position: absolute; top:40% ;left: 50%; transform:translateX(-50%);">
        <img src="./img/Spin.gif" alt="" width="100px;" style="">
        <p class="mt-4 pl-3">나랑 잘 맞는 화장품 분석중...</p>
    </div>
    

    <!-- <button @click="doAjax">
        1
    </button> -->
  </div>
</template>

<script>
import Loading from 'vue-loading-overlay'
import 'vue-loading-overlay/dist/vue-loading.css';



export default {
    created(){
        // console.log("Hello");
        this.$cookies.remove("key")
        window.addEventListener("load", this.doAjax)
    },
    props:{
        query : String
    },
    data() {
      return {
          isLoading: false,
          fullPage: true,
          result : this.query
      }
    },
    components: {
        Loading
    },
    methods: {
        doAjax() {
            // this.isLoading = true;
            // simulate AJAX
            setTimeout(() => {
                // this.isLoading = false
                window.open(`./result?id=${this.result}`,"_self")
            },3000)
        },
        onCancel() {
            // console.log('User cancelled the loader.')
        },
        pageChange(){
            this.isLoading = false
            // window.open(`./result?id=${this.result}`,"_self")
        }
    },
}
</script>

<style scoped>
    p{
        font-family: 'Noto Sans KR', sans-serif;
        font-size : 20px;
        font-weight : bold;
        color : #6e7da0;
    }
</style>