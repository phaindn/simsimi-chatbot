<template>
    <div id="MessageComponent">
        <div :class="parents">
            <div :class="classes">    
                <span>{{text}}</span>
            </div>
        </div>
            
    </div>
</template>

<script>
    export default {
        name: 'MessageComponent',
        props: ['from', 'text'],
        data() {
            return {
                class: 'pointing label'
            }
        },
        computed: {
            classes: function() {
                var prefix = 'ui big';
                var middle = ' rounded circular ';
                if (this.from === 'bot')
                    return (prefix + middle + ' left ' +this.class);
                else return (prefix + ' right aligned ' + middle + ' blue right ' + this.class);
            },
            parents: function() {
                var prefix = 'ui';
                var affix = 'aligned container';
                if (this.from === 'bot')
                    return (prefix + ' left ' + affix);
                else return (prefix + ' right ' + affix);
            }
        }
    }
</script>

<style scoped>
    #MessageComponent {
        margin: 5px 10px;
        padding: 4px;
    }
</style>