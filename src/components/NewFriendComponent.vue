<template>

    <p>Name : {{ friend.name }}</p>
    <label for="Name">Name</label>
    <!-- <input type="text" id="Name" v-model="friend.name"> -->
    <input type="text" id="Email" @input="event => friend.name = event.target.value">

    <p>Email : {{ friend.email }}</p>
    <!-- <label for="Email">Email</label>
    <input type="text" id="Email" v-model="friend.email">  -->
    
    <label for="Email">Email</label>
    <input type="text" id="Email" @input="event => friend.email = event.target.value">

    <p>Contact : {{ friend.contactNumber }}</p>
    <label for="Number">Number</label>
    <input type="text" id="Number" v-on:input="OnSetContact($event)">

    <button @click="AddFriend">Add Friend</button>

</template>

<script>

export default ({
    data() {
        return {
            friend: {
                name: String,
                email: String,
                contactNumber: String,
            }
        };
    },
    emits : {
        'add-friend' : function(value){  if (value == 0) {
                return true
            }else{
                console.log('Value is Missing');
                return false
            }}
    },
    methods: {
        OnSetContact(eventData) {
            this.friend.contactNumber = eventData.target.value
        },
        AddFriend() {
            console.log('friend Name', this.friend.name);
            console.log('friend email', this.friend.email);
            console.log('friend contact', this.friend.contactNumber);
            this.$emit('add-friend', this.friend)
            this.friend.name = ""
            this.friend.email = ""
            this.friend.contactNumber = ""
        }
    }
})
</script>

<style scoped></style>