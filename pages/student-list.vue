<template>
  <div>
<<v-data-table
    :headers="headers"
    :items="studentData"
    :items-per-page="5"
    class="elevation-1"
  ></v-data-table>
</div>
</template>

<script>
export default {
    data () {
      return {
        headers: [
          {
            text: 'Student # ',
            align: 'start',
            sortable: false,
            value: 'attributes.student_no',
          },
          { text: 'Lastname', value: 'attributes.last_name' },
          { text: 'Firstname', value: 'attributes.first_name' },
          { text: 'Middlename', value: 'attributes.middle_name' },
          { text: 'Course', value: 'attributes.course' },
          { text: 'Section', value: 'attributes.section' },
        ],
        studentData: [],
      };
    },

    methods:{
      getStudentList() {
        this.$axios.get("http://localhost:1337/api/student-lists")
        .then(response => {
          console.log("Success!");
          console.log(response.data.data)
          this.studentData = response.data.data
        })

        .catch(error =>{
        console.log("Error!")
      })

      }
      
    },

    mounted(){
      console.log("Auto Run!")
      this.getStudentList();
    }

  };
</script>
