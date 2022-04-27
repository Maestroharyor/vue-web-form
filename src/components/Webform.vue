<template lang="">
    <div class="bg-gray-100 h-[100vh] p-5 md:p-10">
        <form class="max-w-[600px] mx-auto rounded-lg bg-white py-5 px-10" @submit="submitForm">
            <h1 class="text-3xl font-bold mb-8">Enter your details</h1>
            <div class="flex flex-col gap-5">
                <div class="flex flex-col gap-2 text-left">
                    <label class="block text-sm">NAME:</label>
                   <input class="block text-xl px-3 py-1 border-b" v-model="name" /> 
                </div>
                <div class="flex flex-col gap-2 text-left">
                    <label class="block text-sm">PASSWORD:</label>
                   <input class="block text-xl px-3 py-1 border-b" type="password" v-model="password" /> 
                </div>
                <div class="flex flex-col gap-2 text-left">
                    <label class="block text-sm">JOB:</label>
                    <select class="bg-white block text-xl px-3 py-1 border-b" v-model="job">
                        <option value="frontend">Frontend Web Developer</option>
                        <option value="backend">Backend Web Developer</option>
                        <option value="mobileapp">Mobile App Developer</option>
                        <option value="blockchain">Blockchain Developer</option>
                    </select>
                </div>
                <div class="flex flex-col gap-2 text-left">
                    <label class="block text-sm">SKILLS:</label>
                   <input class="block text-xl px-3 py-1 border-b" v-model="skillsSingle" @keyup="addSkill" /> 

                   <ul v-if="skillsList.length > 0" class="inline-flex gap-3 flex-wrap mt-2">
                       <li v-for="(item, index) in skillsList" :key="index" @click="deleteSkill" class="px-5 py-1.5 rounded-full bg-gray-50">{{ item }}</li>
                   </ul>
                </div>
                <div class="flex gap-2 text-left">
                    <input type="checkbox" v-model="terms"  />
                    <label class="text-sm">ACCEPT TERMS AND CONDITIONS</label>
                </div>

                <div class="flex align-center justify-center">
                    <input type="submit" value="Submit" class="bg-blue-700 hover:bg-blue-800 cursor-pointer px-6 py-2 rounded-full text-white transition duration-300 ease-in-out block w-full" />
                </div>


            </div>
            
        </form>
        
    </div>
</template>
<script>
export default {
  data() {
    return {
      name: "",
      password: "",
      job: "",
      terms: true,
      skillsSingle: "",
      skillsList: [],
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "Enter" && this.skillsSingle) {
        if (!this.skillsList.includes(this.skillsSingle)) {
          this.skillsList.push(this.skillsSingle);
        }

        this.skillsSingle = "";
      }
    },
    deleteSkill(e) {
      //   console.log(e.target.textContent)
      const newSkillsList = this.skillsList.filter(
        (skill) => skill !== e.target.textContent
      );
      //   console.log(newSkillsList)
      this.skillsList = newSkillsList;
    },
    submitForm(e){
        e.preventDefault();
    }
  },
  updated() {
    // console.log(this.skillsSingle);
  },
};
</script>
<style lang="">
</style>