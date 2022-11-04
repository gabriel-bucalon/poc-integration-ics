<template>
  <div id="app">
    <button @click="goRoute">Genesis</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  methods: {
    async goRoute() {
      const data = JSON.stringify({
        user: 'a',
        password: 'a',
      });

      const config = {
        method: 'post',
        url: 'http://localhost:4000/api/auth/login',
        headers: {
          Accept: 'application/json, text/plain, */*',
          'Accept-Language': 'en-US,en;q=0.9,pt;q=0.8',
          Connection: 'keep-alive',
          'Content-Type': 'application/json',
          Cookie:
            'auth.strategy=local; i18n_redirected=pt-BR; sessionId=9cfe2192441cb1b7f8bbe9cdae5f1eeeaa4f653ec2c3a387fdd34e19b1ad921491fdcbd4a321e605216e1f7fdd1ba8661d91860945c518ea8b14bc02f4aafece; timestamp=1667575688303; auth._token.local=false; auth._token_expiration.local=false; auth.redirect=%2F; sessionId=76951ed7ec028b69846d3f4b9b2ef34059467406df4756d50b583726d1aaec49b309f7f66e7cd0e0f9caafff310a9b77f28ff960e9722c28600d61fdca702c47; timestamp=1667576328886',
          Origin: 'http://localhost:3000',
          Referer: 'http://localhost:3000/login',
          'Sec-Fetch-Dest': 'empty',
          'Sec-Fetch-Mode': 'cors',
          'Sec-Fetch-Site': 'same-origin',
          'User-Agent':
            'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/107.0.0.0 Safari/537.36',
          'sec-ch-ua':
            '"Google Chrome";v="107", "Chromium";v="107", "Not=A?Brand";v="24"',
          'sec-ch-ua-mobile': '?0',
          'sec-ch-ua-platform': '"Linux"',
        },
        data,
      };

      axios(config)
        .then((response) => {
          console.log(response.data);
          window.location.href = `http://localhost:4000/historico-faturas?token=${response.data.sessionId}`;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
