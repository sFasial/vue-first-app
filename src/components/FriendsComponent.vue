<template>
    <p>I am Friend Component</p>
    <p>friendsAppVueComponent : {{ friendsAppVueComponent }}</p>

    <p>counter : {{counter}}</p>
    <button @click="ToggleCounter">Toggle Counter</button>

    <div>
        <ul v-for="friend in friendsAppVueComponent" :key="friend.id">
            <div v-if="DetailsAreVisible">
                <li><strong>Frined Name : </strong> {{ friend.name }} </li>
                <li><strong>Frined Email : </strong> {{ friend.email }} </li>
                <li><strong>Frined Contact : </strong> {{ friend.number }} </li>
            </div>
            <li>-----------------------------------------------</li>
            <button @click="ToggleDetails">Toggle</button>
        </ul>
    </div>

    <div>
        <!-- <ul v-for="car in cars" :key="car.id">
            <li>{{ car }}</li>
        </ul> -->
        <p>car{{ cars }}</p>
        <!-- <p>Car Id : {{ cars.id }}</p>
        <p>Car Name : {{ cars.name }}</p> -->
    </div>

    <p>counter : {{counter}}</p>
    <button @click="ToggleCounter">Toggle Counter</button>

</template>

<script>
export default {
    data() {
        return {
            value : 0,
            friends: [
                {
                    id: 1,
                    name: 'Sabrina',
                    email: 'sabrina@gmail.com',
                    number: '123456789'
                },
                {
                    id: 2,
                    name: 'Marry Williams',
                    email: 'marry@gmail.com',
                    number: '912345678'
                }
            ],
            DetailsAreVisible: true,
        };
    },
    props: {
        friendsAppVueComponent: {
            type: Object,
            required: false
        },
        cars : {
            type:Object,
            required:false
        }  ,
        counter : {
            type:Number,
            required:false
        }
    },
    //     props:[
    //         friendsAppVueComponent 
    // ],
    emits : {
        "counter-will-increase" : function(value){
            console.log('Event Validation value', value);
            if (value == 0) {
                return true
            }else{
                console.log('Value is Missing');
                return false
            }
            
        }
    },
    methods: {
        ToggleDetails() {
            this.DetailsAreVisible = !this.DetailsAreVisible
        },
        ToggleCounter(){
             this.value = this.counter;
             console.log('this.value', this.value++);
            this.$emit('counter-will-increase',this.value++)
        }
    }
}
</script>

<style>
* {
    box-sizing: border-box;
}

html {
    font-family: 'Jost', sans-serif;
}

body {
    margin: 0;
}

header {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    margin: 3rem auto;
    border-radius: 10px;
    padding: 1rem;
    background-color: #58004d;
    color: white;
    text-align: center;
    width: 90%;
    max-width: 40rem;
}

#app ul {
    margin: 0;
    padding: 0;
    list-style: none;
}

#app li {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    margin: 1rem auto;
    border-radius: 10px;
    padding: 1rem;
    text-align: center;
    width: 90%;
    max-width: 40rem;
}

#app h2 {
    font-size: 2rem;
    border-bottom: 4px solid #ccc;
    color: #58004d;
    margin: 0 0 1rem 0;
}

#app button {
    font: inherit;
    cursor: pointer;
    border: 1px solid #ff0077;
    background-color: #ff0077;
    color: white;
    padding: 0.05rem 1rem;
    box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
    background-color: #ec3169;
    border-color: #ec3169;
    box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}
</style>