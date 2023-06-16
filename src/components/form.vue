<template>
  <div>
    <h2>Form:</h2>
    <div class="input-group flex-nowrap">
      <span class="input-group-text" id="addon-wrapping">@</span>
      <input
        type="text"
        class="form-control"
        placeholder="FirstName"
        aria-label="FirstName"
        @input="handleChangeInput($event, 'first_name')"
        aria-describedby="addon-wrapping"
        v-model="firstName"
      />
    </div>
    <div class="input-group flex-nowrap">
      <span class="input-group-text" id="addon-wrapping">@</span>
      <input
        type="text"
        class="form-control"
        placeholder="LastName"
        aria-label="LastName"
        aria-describedby="addon-wrapping"
        @input="handleChangeInput($event, 'last_name')"
        v-model="lastName"
      />
    </div>
    <div :class="messageClass">{{ text }}</div>

    <br />

    <div ml-2>
      <CpButton colorButton="btn-success" type="add" text="Add" @addPerson="addPerson" />
    </div>
  </div>
</template>

<script>
import CpButton from "./button.vue";
export default {
  components: {
    CpButton,
  },
  name: "formComponent",
  props: {
    messageClass: {
      default: "",
      type: String,
    },
    text: {
      default: "",
      type: String,
    },
    isResetData: {},
  },
  data() {
    return {
      lastName: "",
      firstName: "",
    };
  },
  methods: {
    addPerson() {
      this.$emit("addPerson", );
    },
    handleChangeInput(e, field) {
      this.$emit("changeInput", e.target.value, field);
    },
    deletePerson(index){
      this.$emit("deletePerson", index);
    }
  },
  watch: {
    isResetData() {
      this.firstName = "";
      this.lastName = "";
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
