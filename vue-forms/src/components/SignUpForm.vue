<template>
    <form class="form" @submit.prevent="handleSubmit">
        <div class="info email">
            <label for="email">Email</label>
            <input type="email" required v-model="email" />
        </div>
        <div class="info password">
            <label for="password">Password</label>
            <input type="password" required v-model="password" />
        </div>
        <div class="role"><label for="role">Role:</label>
            <select name="role" v-model="role">
                <option value="Developer">Web Developer</option>
                <option value="Designer">Web Designer</option>
                <option value="Project manager">Project manager</option>
                <option value="UX Researcher">UX Researcher</option>
            </select>
        </div>
        <div class="terms">
            <input v-model="terms" type="checkbox" name="term" id="term">
            <label for="term">Accept terms and conditions</label>
        </div>
        <div class="true" v-if=terms>
            <p class="message">Congratulations! You may now proceed🚀</p>
        </div>
        <div class="names">
            <div class="name">
                <input type="checkbox" name="" value="Choice 1" v-model="names">
                <label for="Choice 1">Choice 1</label>
            </div>
            <div class="name">
                <input type="checkbox" name="" value="Choice 2" v-model="names">
                <label for="Choice 1">Choice 2</label>
            </div>
            <div class="name">
                <input type="checkbox" name="" value="Choice 3" v-model="names">
                <label for="Choice 1">Choice 3</label>
            </div>
            <div class="name">
                <input type="checkbox" name="" value="Choice 4" v-model="names">
                <label for="Choice 1">Choice 4</label>
            </div>
            <div class="name">
                <input type="checkbox" name="" value="Choice 5" v-model="names">
                <label for="Choice 1">Choice 5</label>
            </div>
        </div>
        <div class="info">
            <label for="Skill">Skill</label>
            <input class="Skill" type="Skill" v-model="tempSkill" @keyup.alt="addSkill" />
            <div class="skillList">
                <p class="skills pill" v-for="skill in skills" :key="skill" @click="removeSkill(skill)">{{ skill }}</p>
            </div>
            <div v-if="exists">Skill already exists</div>
        </div>
        <button type="submit" class="submit-button">Let's Go🚀</button>
    </form>
</template>

<script>
export default {
    name: "SignUpForm",
    data() {
        return {
            email: '',
            password: '',
            role: 'Project manager',
            terms: true,
            names: [],
            tempSkill: '',
            skills: [],
            exists: false,
        }
    },
    methods: {
        addSkill(e) {
            if (e.key === "Enter" && this.tempSkill && !this.skills.includes(this.tempSkill)) {
                this.exists = false;
                this.skills.push(this.tempSkill)
                this.tempSkill = ''
            } else if (this.skills.includes(this.tempSkill)) {
                this.exists = true;
                this.tempSkill = ''
            }
        },
        removeSkill(skill) {
            const index = this.skills.indexOf(skill);
            if (index > -1) {
                this.skills.splice(index, 1);
            }
        },
        handleSubmit () {
            console.log("Form submitted");
        }
    }
};

</script>

<!-- ############################################################################################## -->
<style scoped>
form {
    color: rgb(255, 255, 255);
    font-family: 'Roboto', sans-serif;
    width: 340px;
    margin: 0 auto;
    background: linear-gradient(60deg, #5f0f4077, #310e687e);
    padding: 3rem;
    border-radius: 16px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    border: 1px solid rgba(245, 245, 245, 0.43);

}

.info,
.role {
    margin: 1rem 0;
}

/* Form input fields */
input[type="text"],
input[type="email"],
input[type="password"],
textarea,
select,
.Skill {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: none;
    border-bottom: 1px solid #ccc;
    box-sizing: border-box;
    font-size: 16px;
    background-color: transparent;
    color: white;
    border-radius: 21px;
}

.true {
    /* width: 100%; */
    height: 1.5rem;
    padding: 0.5rem;
    background: rgba(0, 128, 0, 0.208);
    color: green;
    border-radius: 4px;
    margin-top: 1rem;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    font-size: 14px;
}

.pill {
    background-color: purple;
    color: white;
    height: 26px;
    padding: 0 16px;
    border-radius: 18px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 6px;
}

.terms,
.name,
.skillList {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-wrap: wrap;
}

/* Form labels */
label {
    display: block;
    /* margin-bottom: 8px; */
    font-weight: 500;
}

/* Form submit button */
button[type="submit"] {
    width: 100%;
    height: 2.5rem;
    border-radius: 1.25rem;
    background-color: #5f0f40;
    border: 1px solid white;
    transition: 300ms;
    color: white;
    font-size: 16px;
    font-weight: 500;
}

/* Form submit button hover effect */
button[type="submit"]:hover {
    background-color: #310e68;
}

/* Form error message */
.error-message {
    color: red;
    font-size: 14px;
    margin-top: 8px;
}
</style>