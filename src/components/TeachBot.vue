<template>
    <div id="TeachBot" class="container">
        <h3 class="text-info">Teach Bot</h3>
        <form action="http://sandbox.api.simsimi.com/teach" method="POST">
            <input type="hidden" name="key" value="a34c1a9b-a514-4dda-a5bd-6bfac9c5ec91">
            <input type="hidden" name="lc" value="vn">
            <div class="form-group">
                <label for="req">Request:</label>
                <input type="text" class="form-control" id="req" name="req" placeholder="Request string" v-model="req">
            </div>
            <div class="form-group">
                <label for="req">Response:</label>
                <input type="text" class="form-control" id="res" name="res" placeholder="Response text" v-model="res">
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
        </form>
        <h6 class="text-warning">{{text}}</h6>
    </div>
</template>

<script>
    export default {
        name: 'TeachBot',
        data() {
            return {
                req: '',
                res: '',
                text: '',
                API: {
                    HOST: 'http://sandbox.api.simsimi.com/teach',
                    KEY: 'a34c1a9b-a514-4dda-a5bd-6bfac9c5ec91',
                    LC: 'vn'
                }
            }
            
        },
        methods: {
            teach: function() {
                var xhttp = new XMLHttpRequest() || ActiveXObject("Microsoft.XMLHTTP");
                var grep;
                xhttp.onreadystatechange = function() {
                    if (this.readyState == 4 && this.status == 200) {
                        grep = this.responseText;
                    }
                };
                this.text = grep;
                xhttp.open('POST', this.API.HOST, true);
                xhttp.setRequestHeader("Content-type", "application/javascript");
                var string = "key="+this.API.KEY+"&lc="+this.API.LC+"&req="+this.req+"&res="+this.res;
                console.warn(encodeURI(string));
                console.warn(this.API);
                xhttp.send(encodeURI(string));

            }
        }
    }
</script>