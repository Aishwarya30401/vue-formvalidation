<template>
<div class='card'>
    <h3 class="card-header text-center">Register Form</h3>
    <div class="card-body">
    <form>
        <div class="form-group col-md-6">
            <label>firstname</label>
            <input type="text" class="form-control" 
            v-model.trim="$firstname.$model" :class="{
                'is-invalid ': $v.firstname.$error, 'is-valid': !$v.fristname$invalid}">
            <div class ="valid-feedback">your first name is valid</div>
            <div class ="valid-feedback">your first name is in-valid</div>
            <span v-if ="$v.firstname.required">fistname is required</span>
            <span v-if ="!$v.fristname.minLength">firstname must have atleast{{
                $v.firstname.$params.minLength.min}} letters.</span>
            <span v-if ="!$v.fristname.mixLength">firstname must have atmost{{
                $v.firstname.$params.maxLength.man}} letters.</span>
        </div>
         <div class="form-group col-md-6">
            <label>lasttname</label>
            <input type="text" class="form-control" 
            v-model.trim="$firstname.$model" :class="{
                'is-invalid': $v.lastname.$error, 'is-valid': !$v.lastname$invalid}">
            <div class ="valid-feedback">your lasr name is valid</div>
            <div class ="valid-feedback">your last name is in-valid</div>
            <span v-if ="$v.lasttname.required">last name is required</span>
            <span v-if ="!$v.lasttname.minLength">lastname must have atleast{{
                $v.lasttname.$params.minLength.min}} letters.</span>
            <span v-if ="!$v.lasttname.mixLength">firstname must have atmost{{
                $v.lasttname.$params.maxLength.man}} letters.</span>
        </div>
        <!-- age -->
         <div class="form-group col-md-6">
            <label>age</label>
            <input type="number" class="form-control" 
            v-model.number.lazy="$firstname.$model" :class="{
                'is-invalid ': $v.age.$error, 'is-valid' : !$v.age.$invalid}">
            <div class ="valid-feedback">your age is valid</div>
            <span v-if="!$v.age.between">must be between{{$v.age.$params.between.min}}and{{$v.age.$params.between.max}}></span>
        </div>
    </form>
    </div>
</div>
</template>

<script>
import { required, minLenght, maxLenght, between } from 'vuelidate/lib/validators'

export default{
    name: 'FormValidation',
    data(){
        return {
            firstname: '',
            lastname: '',
            age: 0
        }
    },
    validations: {
    firstname:{
        required,
        minLength: minLenght(3),
        maxLenght: maxLenght(10)
      },
    lastname: {
        required,
        minLenght: minLenght(5),
        maxLenght: maxLenght(12)
    },
    age: {
        between: between(15,40)
    }
}
}
</script>

<style scoped>

</style>