<template>
  <div>
      <h1>Contact</h1>
      <h2>{{address}}</h2>
      <hello-world msg="Hello1"></hello-world>
      <UserProfile></UserProfile>

      </div>
</template>

<script>
import HelloWorld from '@/components/HelloWorld.vue'
import UserProfile from '@/components/UserProfile.vue'

export default {
data() {
    return {
        address : "80 m1. PSU PHUKET"
    }
},
components :{
    HelloWorld,
    UserProfile
}
}
</script>

<style>

</style>