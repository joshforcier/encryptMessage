<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div>Message to Encrypt</div>
    <textarea v-model="message" cols="30" rows="10"/>
    <div>Key</div>
    <textarea v-model="myKey" cols="30" rows="10"/>
    <div>Encrypted Message</div>
    <textarea v-model="encryptedText" cols="30" rows="10"/>
    <div>Decrypted Message</div>
    <textarea v-model="decryptedText" cols="30" rows="10"/>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  data() {
    return {
      message: '',
      myKey: '',
    }
  },
  computed: {
    encryptedText() {
      if (this.message !== '' && this.myKey !== '') {
        return this.CryptoJS.AES.encrypt(this.message, this.myKey).toString();
      }
      return '';
    },
    decryptedText() {
      return this.CryptoJS.AES.decrypt(this.encryptedText, this.myKey).toString(this.CryptoJS.enc.Utf8)
    },
  }
}


</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
