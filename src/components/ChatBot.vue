<template>
    <div id="ChatBot">
			<div class="ui container" v-for="item in msg" :key='item' id="container">
					<Message :from='item.from' :text='item.text'></Message>
			</div>
        <input type="hidden" name="key" value="a34c1a9b-a514-4dda-a5bd-6bfac9c5ec91">
        <input type="hidden" name="lc" value="vn">
            <!-- <div class="form-group">
                <label for="text">Message:</label>
                <input type="text" class="form-control" id="text" name="text" placeholder="Message..." v-model="text">
            </div> -->
        
        <div class="ui container chat">
            <div class="ui fluid labeled action input">
                <div class="ui label">Message: </div>
                <input type="text" id="text" name="text" placeholder="Message..." v-model="text" @keyup.enter="chat()">
                <button class="ui primary button" v-on:click="chat()">Send</button>
            </div>
        </div>
    </div>
    
</template>

<script>
    import Message from './MessageComponent.vue';
    export default {
        name: 'ChatBot',
        data() {
            return {
                res: '',
                text: '',
                API: {
                    HOST: 'http://sandbox.api.simsimi.com/request.p?',
                    KEY: 'be0c80cc-5fa0-467f-83af-8e1f0ca4d757',
                    LC: 'vn'
                },
                msg: [{'from':'bot', 'text':'Xin chào'}]
            }
            
        },
        methods: {
            chat: function() {
                this.msg.push({'from':'user','text':this.text});
                var string = "key="+this.API.KEY+"&lc="+this.API.LC+"&text="+this.text;
                console.warn(this.msg.length)
                var xhttp = new XMLHttpRequest();
                var grep;
                var response;
                var arr = this.msg;
                xhttp.onreadystatechange = function() {
                    if (this.readyState == 4 && this.status == 200) {
                        grep = this.responseText;
                        response = JSON.parse(grep);
                        arr.push({'from':'bot', 'text':response.response});
                    }
                };
                xhttp.open('GET', this.API.HOST+string, true);
                xhttp.send();
                this.msg = arr;
            }
        },
        components: {
            Message
        }
    }
</script>

<style scoped>
	.chat {
			position: sticky;
			bottom: 5px;
	}
	.main-container {
		height: 500px;
	}
</style>