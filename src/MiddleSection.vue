<template>
    <div id="MiddleSection" class="mt-3 mb-3">
        <div class="container">
            <div class="row">
                <div class="col-lg-6 col-sm-12">
                    <h1>Basic information</h1>
                
                    <table class="table table-striped">
  <thead>
    <tr>
      <th scope="col">ID</th>
      <th scope="col">Name</th>
      <th scope="col">Username</th>
      <th scope="col">E-mail</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(user, index) in arrayUsers" v-bind:key="index" v-on:click="specificUser(user.id)">
      <td>{{ user.id }}</td>
      <td>{{ user.name }}</td>
      <td>{{ user.username }}</td>
      <td>{{ user.email }}</td>
    </tr>
  </tbody>
</table>
                </div>
            
              <div class="col-lg-6 col-sm-12">
                <h2>{{ h2Text }}</h2>
                <div>
                  <!--Only show if on click-->
                  <ul class="list-group" v-if="info">
                    <li class="list-group-item"><span class="font-weight-bold">ID:</span> {{ info.id }}</li>
                    <li class="list-group-item"><span class="font-weight-bold">Name:</span> {{ info.name }}</li>
                    <li class="list-group-item"><span class="font-weight-bold">Username:</span> {{ info.username }}</li>
                    <li class="list-group-item"><span class="font-weight-bold">E-mail:</span> {{ info.email }}</li>
                    <li class="list-group-item"><span class="font-weight-bold">Address:</span> {{ info.address.street }}, {{ info.address.suite }}, {{ info.address.city }}, {{ info.address.zipcode }}, {{ info.address.geo.lat }}, {{ info.address.geo.lng }}</li>
                    <!--
                    <li class="list-group-item">{{ info.address.suite }}</li>
                    <li class="list-group-item">{{ info.address.city }}</li>
                    <li class="list-group-item">{{ info.address.zipcode }}</li>
                    <li class="list-group-item">{{ info.address.geo.lat }}</li>
                    <li class="list-group-item">{{ info.address.geo.lng }}</li>
                    -->
                    <li class="list-group-item"><span class="font-weight-bold">Phone:</span> {{ info.phone }}</li>
                    <li class="list-group-item"><span class="font-weight-bold">Webiste:</span> {{ info.website }}</li>
                    <li class="list-group-item"><span class="font-weight-bold">Company name:</span> {{ info.company.name }}<br>
                    <span class="font-weight-bold">Company catchphrase:</span> {{ info.company.catchPhrase }}<br>
                    <span class="font-weight-bold">Company bs:</span> {{ info.company.bs }}</li>
                    <!--
                    <li class="list-group-item">{{ info.company.catchPhrase }}</li>
                    <li class="list-group-item">{{ info.company.bs }}</li>

                    -->
                  </ul>
                </div>
              </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MiddleSection',

    data(){
        return{
          //empty array to store json data
          arrayUsers: [],
          //null info for if statement
          info: null,
          h2Text: 'Click on a user to see more information'
        }
    },

    methods:{
      specificUser(userID){
        //js for of loop userID
        for(let user of this.arrayUsers) {
          if(user.id == userID) {
            this.info = user
            //console.log(user.name)
          }
        }

        //change text
        if(this.h2Text == 'Click on a user to see more information'){
          this.h2Text = 'All information for this user:';
        }
      }
    },

    created(){
        const url = 'https://jsonplaceholder.typicode.com/users';

        fetch(url)
        .then((res) => {
            return res.json()
        })
        .then((data) => {
            console.log(data)
            this.arrayUsers = data
        })
        .catch((error) => {
            console.log(error)
        })
    }
    
}
</script>