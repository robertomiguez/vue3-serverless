<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{ users.name }}</h1>
  </div>
</template>

<script>
import { ref } from "vue"
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  setup(props) {
    console.log(props.msg);
    const users = ref([]);

    (async () => {
      try {
        const res = await axios.get("api/hello");
        users.value = res.data;
      } catch (error) {
          console.log('error:', error);
      }
    })()

    return {
      users
    }

}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
