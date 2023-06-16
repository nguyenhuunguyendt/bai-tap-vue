<template>
  <div id="app">
    <formComponent
      :messageClass="messageClass"
      :text="message"
      @addPerson="addPerson"
      @changeInput="changeInput"
      :isResetData="is_reset_data"
      @deletePerson="deletePerson"
    />
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">First</th>
          <th scope="col">Last</th>
          <th scope="col">Handle</th>
        </tr>
      </thead>
      <tbody>
        <CpItemPerson
          v-for="(item, index) in list_person"
          :person="item"
          :key="index"
          :stt="index"
          @deletePerson="deletePerson"
        />
      </tbody>
    </table>
  </div>
</template>

<script>
import CpItemPerson from "../src/components/item_person.vue";
import formComponent from "../src/components/form.vue";

export default {
  name: "App",
  data() {
    return {
      list_person: [
        { first_name: "Mark", last_name: "Otto" },
        { first_name: "Jacob", last_name: "Thornton" },
        { first_name: "Lazy", last_name: "Bird" },
      ],
      first_name: "",
      last_name: "",
      message: "",
      messageClass: "",
      is_reset_data: 0,
    };
  },
  components: {
    CpItemPerson,
    formComponent,
  },
  methods: {
    addPerson() {
      console.log(this.first_name);
      console.log(this.last_name);
      if (!this.first_name || !this.last_name) {
        this.messageClass = "messageError";
        return (this.message = "data not emty 😔 !");
      }

      this.messageClass = "messageSuccess";
      this.list_person.push({
        first_name: this.first_name,
        last_name: this.last_name,
      });
      this.first_name = "";
      this.last_name = "";
      this.message = "add data success 😍 ";
      this.is_reset_data++;
    },
    changeInput(value, text) {
      console.log(value,text);
      this[text] = value;
       this.message=""
    },
    deletePerson(index) {
      this.list_person.splice(index, 1);
      this.message = "";
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.messageError {
  color: red;
}

.messageSuccess {
  color: green;
}
</style>
