<template>
  <div class="hello">
    <img :class="gender" :src="picture" :alt="`${firstName} ${lastName}`" />
    <div>{{ firstName }} {{ lastName }}</div>
    <button :class="gender" @click="getUser()">Get Random User</button>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {},
  data() {
    return {
      firstName: "John",
      lastName: "Doe",
      email: "john.doe@gmail.com",
      gender: "male",
      picture: "https://randomuser.me/api/portraits/men/11.jpg",
    };
  },
  methods: {
    async getUser() {
      const user = await fetch("https://randomuser.me/api");
      const res = await user.json();
      const { results } = res;
      this.firstName = results[0].name.first;
      this.lastName = results[0].name.last;
      this.email = results[0].email;
      this.gender = results[0].gender;
      this.picture = results[0].picture.large;
    },
  },
};
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
img {
  border-radius: 50%;
  align-content: center;
}

img.male {
  border: 4px solid steelblue;
}

img.female {
  border: 4px solid pink;
}

button {
  padding: 0.3rem;
  color: white;
}

button.male {
  background: steelblue;
}

button.female {
  background: pink;
}
</style>
