<template>
    <div class="home">
        <span>Message: {{  msg  }}</span>
        <span v-once>This will never change: {{  msg  }}</span>

        <p>Using mustaches: {{  rawHtml  }}</p>
        <p>Using v-html directive: <span v-html="rawHtml"></span></p>

        <div v-bind:id="dynamicId">A div with a uniqueID</div>

        {{  3 + 3 + 2  }}
        {{  msg.split('').reverse().join('')  }}

        <div v-bind:class="[activeClass, errorClass]">Class binding</div>

        <div v-bind:style="[baseStyles, otherStyles]">Style binding using an array of style objects</div>

        <!-- conditional rendering -->
        <div v-if="type === 'A'"> A </div>
        <div v-else-if="type === 'B'"> B </div>
        <div v-else-if="type === 'C'"> C </div>
        <div v-else> Not A/B/C </div>

        <template v-if="ok">
            <h1>Title</h1>
            <p>Paragraph 1</p>
            <p>Paragraph 2</p>
        </template>

        <template v-if="loginType === 'username'">
            <label>Username</label>
            <input placeholder="Enter your username" key="username-input">
        </template>
        <template v-else>
            <label>Email</label>
            <input placeholder="Enter your email address" key="email-input">
        </template>


        <!-- list rendering -->
        <ul id="list">
            <li v-for="(item, index) in items">
                {{  parentMessage  }} - {{  index  }} - {{  item.message  }}
            </li>
        </ul>

        <div v-for="(value, name, index) in object" v-bind:key="item.id">
            {{  index  }}. {{  name  }}: {{  value  }}
        </div>

        <!-- Event handling -->
        <button v-on:click="log">
            Click: Component Method
        </button>

        <form v-on:submit.stop.prevent="log('clicked!', $event)">
            <button type="Submit">
                Click
            </button>
        </form>

        <input v-on:keyup.enter="submit">

        <input v-model="message" placeholder="edit">
        <p>Message is: {{  message  }}</p>

        <input type="checkbox" v-model="toggle">

        <input v-model.lazy="msg">

        <input v-model.number="age" type="number">

        <input v-model.trim="msg">

    </div>

</template>

<script>
export default {
    name: 'HomePage',
    props: {
        msg: String,
        rawHtml: String,
        dynamicID: String,
        data: {
            activeClass: 'active',
            errorClass: 'text-danger',
            parentMessage: 'Parent',
            items: [
                { message: 'Foo' },
                { message: 'Bar' }
            ]
        }
    },

    methods: {
        log() {
            console.log('Button clicked!');
        }

    }

}
</script>

<style scoped>
</style>