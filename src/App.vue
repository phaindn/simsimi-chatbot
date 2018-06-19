<template>
  <div id="app" class="ui container">
    <div class="ui center aligned container">
      <h1 class="ui massive red inverted header">Chat bot</h1>
    </div>
    <ChatBot></ChatBot>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import TeachBot from './components/TeachBot'
import ChatBot from './components/ChatBot'
import Msgg from './components/MessageComponent'

export default {
  name: 'App',
  components: {
    HelloWorld,
    TeachBot,
    ChatBot,
    Msgg
  }
}
</script>

<style>
  @import url('../node_modules/semantic-ui/dist/semantic.min.css');
</style>
