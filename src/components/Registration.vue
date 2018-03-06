<template>
    <div>
        <form>
            <div class="form-group">
                <label for="exampleFormControlInput1">Email address</label>
                <input type="email" v-model="User.email" class="form-control" id="exampleFormControlInput1" placeholder="name@example.com">
            </div>
            <div class="form-group">
                <label for="exampleFormControlSelect1">Select country of origin</label>
                <select v-model="User.country" class="form-control" id="exampleFormControlSelect1">
                    <option>Kenya</option>
                    <option>Uganda</option>
                    <option>Tanzania</option>
                    <option>Ethopia</option>
                    <option>Rwanda</option>
                </select>
            </div>
            <div class="form-group">
                <label for="exampleFormControlSelect1">Preferred mode of communicaton</label>
                <div class="form-check">
                    <input class="form-check-input" type="checkbox" value="phone"   v-model="User.communication" id="defaultCheck1">
                    <label class="form-check-label" for="defaultCheck1">
                        Phone
                    </label>
                </div>
                <div class="form-check">
                    <input class="form-check-input" type="checkbox" v-model="User.communication" value="email" id="defaultCheck1">
                    <label class="form-check-label" for="defaultCheck1">
                       Email
                    </label>
                </div>
            </div>
            <div class="form-group">
                <label for="exampleFormControlSelect1">Gender</label>
                <div class="form-check">
                    <input class="form-check-input" type="radio" v-model="User.gender" name="gender" id="exampleRadios1" value="male">
                    <label class="form-check-label" for="exampleRadios1">
                       Male
                    </label>
                </div>
                <div class="form-check">
                    <input class="form-check-input" type="radio" name="gender" v-model="User.gender" id="exampleRadios1" value="female" >
                    <label class="form-check-label" for="exampleRadios1">
                        Female
                    </label>
                </div>
            </div>

            <div class="form-group">
                <label for="exampleFormControlTextarea1">Description</label>
                <textarea v-model="User.description" class="form-control" id="exampleFormControlTextarea1" rows="3"></textarea>
            </div>
            <button class="btn btn-primary"  @click.prevent="onsubmit()">Submit</button>
        </form>
        <div  v-if="isSubmitted">
            <h2>Your data</h2>
            <p>Email : {{User.email}}</p>
            <p>Country:{{User.country}}</p>
            <p>Descripition:{{User.description}}</p>
            <p>Communication:{{User.communication}}</p>
            <p>Gender:{{User.gender}}</p>
        </div>
    </div>
</template>

<script>
    export default{
        name: 'registration',
        data: function () {
            return {
                User:{
                    email:'',
                    country:'',
                    description:'',
                    communication:[],
                    gender:'',

                },
                isSubmitted:false,
            }

        },
        methods:{
            onsubmit(){
                this.isSubmitted=true;
                console.log(this.User);
                this.$http.post('https://requestb.in/1lbtlap1',this.User).
                then((response=>{
                    console.log(response)
                   }
                ));
            }
        }

    }
</script>