<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <div class="container">
            <div class="encrypt">
                <h3>Message to Encrypt</h3>
                <textarea v-model="messageToEncrypt" cols="50" rows="10"/>
                <h3>Public Key</h3>
                <textarea v-model="publicKey" cols="50" rows="10"/><br />
                <button
                    @click="encryptText()"
                    type="submit"
                >
                    ENCRYPT
                </button>
            </div>
            <h3>Encrypted Message</h3>
            <textarea v-model="encryptedText" cols="50" rows="10"/>

            <div class="decrypt">
                <h3>Message to Decrypt</h3>
                <textarea v-model="messageToDecrypt" cols="50" rows="10"/>
                <h3>Private Key</h3>
                <textarea v-model="privateKey" cols="50" rows="10"/><br />
                <button
                    @click="decryptText()"
                    type="submit"
                >
                    DECRYPT
                </button>
            </div>
            <h3>Decrypted Message</h3>
            <textarea v-model="decryptedText" cols="50" rows="10"/>
        </div>
        <button
            @click="reset()"
            type="submit"
        >
            RESET
        </button>
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
            messageToEncrypt: '',
            messageToDecrypt: '',
            publicKey: 'MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCqGKukO1De7zhZj6+H0qtjTkVxwTCpvKe4eCZ0FPqri0cb2JZfXJ/DgYSF6vUpwmJG8wVQZKjeGcjDOL5UlsuusFncCzWBQ7RKNUSesmQRMSGkVb1/3j+skZ6UtW+5u09lHNsj6tQ51s1SPrCBkedbNf0Tp0GbMJDyR4e9T04ZZwIDAQAB',
            privateKey: 'MIICXAIBAAKBgQCqGKukO1De7zhZj6+H0qtjTkVxwTCpvKe4eCZ0FPqri0cb2JZfXJ/DgYSF6vUpwmJG8wVQZKjeGcjDOL5UlsuusFncCzWBQ7RKNUSesmQRMSGkVb1/3j+skZ6UtW+5u09lHNsj6tQ51s1SPrCBkedbNf0Tp0GbMJDyR4e9T04ZZwIDAQABAoGAFijko56+qGyN8M0RVyaRAXz++xTqHBLh3tx4VgMtrQ+WEgCjhoTwo23KMBAuJGSYnRmoBZM3lMfTKevIkAidPExvYCdm5dYq3XToLkkLv5L2pIIVOFMDG+KESnAFV7l2c+cnzRMW0+b6f8mR1CJzZuxVLL6Q02fvLi55/mbSYxECQQDeAw6fiIQXGukBI4eMZZt4nscy2o12KyYner3VpoeE+Np2q+Z3pvAMd/aNzQ/W9WaI+NRfcxUJrmfPwIGm63ilAkEAxCL5HQb2bQr4ByorcMWm/hEP2MZzROV73yF41hPsRC9m66KrheO9HPTJuo3/9s5p+sqGxOlFL0NDt4SkosjgGwJAFklyR1uZ/wPJjj611cdBcztlPdqoxssQGnh85BzCj/u3WqBpE2vjvyyvyI5kX6zk7S0ljKtt2jny2+00VsBerQJBAJGC1Mg5Oydo5NwD6BiROrPxGo2bpTbu/fhrT8ebHkTz2eplU9VQQSQzY1oZMVX8i1m5WUTLPz2yLJIBQVdXqhMCQBGoiuSoSjafUhV7i1cEGpb88h5NBYZzWXGZ37sJ5QsW+sJyoNde3xH8vdXhzU7eT82D6X/scw9RZz+/6rCJ4p0=',
            encryptedText: '',
            decryptedText: '',
        }
    },
    computed: {
    },
    methods: {
        encryptText() {
            if (this.messageToEncrypt !== '' && this.publicKey !== '') {
                this.encryptedText = this.CryptoJS.AES.encrypt(this.messageToEncrypt, 'key').toString();
            }
        },
        decryptText() {
            if (this.messageToDecrypt !== '' && this.privateKey !== '') {
                this.decryptedText = this.CryptoJS.AES.decrypt(this.encryptedText, 'key').toString(this.CryptoJS.enc.Utf8)
            }
        },
        reset() {
            this.messageToEncrypt = '';
            this.messageToDecrypt = '';
            this.encryptedText = '';
            this.decryptedText = '';
        }

    },
}
</script>

<style scoped>
.container {
    column-count: 2;
}

.decrypt {
    padding-top: 1px;
}

button {
    background-color: #4CAF50; /* Green */
    border: none;
    color: white;
    padding: 16px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    transition-duration: 0.4s;
    cursor: pointer;
    border: 2px solid #4CAF50;
    margin-bottom: 30px;
}

button:hover {
    border: 2px solid #4CAF50;
    background-color: white;
    color: #4CAF50;
}
</style>
