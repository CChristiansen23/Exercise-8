<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Directives Exercise</h1>
                <!-- Exercise -->
                <!-- Build a Custom Directive which works like v-on (Listen for Events) -->
                <p v-my-directive="alertClick">
                    Click meeee!
                </p>
            </div>
        </div>
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Filters & Mixins</h1>
                <!-- Exercise 1) -->
                <!-- Build a local Filter which reverses the Text it is applied on -->
                <p>{{ text }}<br />{{ text | reverse }}</p>

                <!-- Exercise 2 -->
                <!-- Build a global Filter which counts the length of a word and it appends it -->
                <!-- Like this: "Test" => Gets Filtered to => "Test (4)" -->
                <p>{{ text | length }}</p>

                <!-- Exercise 3 -->
                <!-- Do the same as in Exercises 1 & 2, now with Computed Properties -->
                <p>Computed: {{ computedText }}</p>

                <!-- Exercise 4 -->
                <!-- Share the Computed Property rebuilding Exercise 2 via a Mixin -->
                <p>computedTextLength: {{ computedTextLength }}</p>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        directives: {
            'my-directive': {
                bind(el, binding) {
                    el.onclick = () => {
                        binding.value()
                    }
                }
            }
        },
        methods: {
            alertClick() {
                window.alert('A click occurred')
            }
        },
        data() {
            return {
                text : 'Text to be reversed'
            }
        },
        filters: {
            reverse(value) {
                return value.split('').reverse().join('')
            }
        },
        computed: {
            computedText() {
                return this.text.split('').reverse().join('') + ' ('+ this.text.length+')';
            }
        }
    }
</script>

<style>
</style>
