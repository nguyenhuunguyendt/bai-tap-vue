<template>
   <tr>
      <th scope="row">{{stt}}</th>
      <td>{{person.first_name}}</td>
      <td>{{person.last_name}}</td>
      <td><CpButton colorButton="btn-danger" :type="'delete'" @deletePerson="deletePerson" text="Danger"/></td>
    </tr>
</template>

<script>
import CpButton from "./button.vue"
export default {
  components: {
    CpButton,
  },
  name: 'CpItemPerson',
  props: {

   person:{
    type:Object,
    default:()=>{},
   },

   stt:{
   },
  },
  methods:{
    deletePerson(){
      this.$emit('deletePerson',this.stt)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
