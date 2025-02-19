<template>
    <v-form @submit.prevent="saveProfile">
        <v-text-field v-model="id" label="Id"></v-text-field>
        <v-text-field v-model="getFullname" label="Full Name"></v-text-field>

        <h2>Basic Data</h2>

        <v-text-field v-model="basicData.firstName" label="First Name"></v-text-field>
        <v-text-field v-model="basicData.lastName" label="Last Name"></v-text-field>
        <v-text-field v-model="basicData.birthdate" label="Birthdate"></v-text-field>
        <v-text-field v-model="basicData.gender" label="Gender"></v-text-field>
        <v-text-field v-model="basicData.profession" label="Profession"></v-text-field>
        <v-text-field v-model="basicData.country" label="Country"></v-text-field>
        <v-text-field v-model="basicData.city" label="City"></v-text-field>
        <v-text-field v-model="basicData.state" label="State"></v-text-field>
        <v-text-field v-model="basicData.zipCode" label="Zip Code"></v-text-field>
        <v-text-field v-model="basicData.address" label="Address"></v-text-field>

        <h2>Contact</h2>

        <v-text-field v-model="contact.phone" label="Phone"></v-text-field>
        <v-text-field v-model="contact.email" label="Email"></v-text-field>
        <v-text-field v-model="contact.whatsapp" label="WhatsApp"></v-text-field>
        <v-text-field v-model="contact.facebook" label="Facebook"></v-text-field>
        <v-text-field v-model="contact.telegram" label="Telegram"></v-text-field>

        <h2>Work Experience</h2>

        <div v-for="(work, index) in workExperience" :key="index">
            <v-text-field v-model="work.position" label="Position"></v-text-field>
            <v-text-field v-model="work.company" label="Company"></v-text-field>
            <v-text-field v-model="work.startDate" label="Start Date"></v-text-field>
            <v-text-field v-model="work.endDate" label="End Date"></v-text-field>
            <v-text-field v-model="work.description" label="Description"></v-text-field>
        </div>

        <h2>Education</h2>

        <div v-for="(education, index) in education" :key="index">
            <v-text-field v-model="education.degree" label="Degree"></v-text-field>
            <v-text-field v-model="education.school" label="Institution"></v-text-field>
            <v-text-field v-model="education.startDate" label="Start Date"></v-text-field>
            <v-text-field v-model="education.endDate" label="End Date"></v-text-field>
            <v-text-field v-model="education.description" label="Description"></v-text-field>
        </div>

        <h2>Skills</h2>

        <div v-for="(skill, index) in skills" :key="index">
            <v-text-field v-model="skill.name" label="Skill Name"></v-text-field>
            <v-text-field v-model="skill.level" label="Skill Level"></v-text-field>
            <v-text-field v-model="skill.type" label="Skill type"></v-text-field>
            <v-text-field v-model="skill.categories" label="Categories"></v-text-field>
        </div>

        <div v-for="(portfolio, index) in portfolio" :key="index">
            <v-text-field v-model="portfolio.name" label="Portfolio Name"></v-text-field>
            <v-text-field v-model="portfolio.description" label="Description"></v-text-field>
            <v-text-field v-model="portfolio.startDate" label="Start Date"></v-text-field>
            <v-text-field v-model="portfolio.endDate" label="End Date"></v-text-field>
            <v-text-field v-model="portfolio.technologies" label="Technologies"></v-text-field>
            <v-text-field v-model="portfolio.appliedSkills" label="Applied Skills"></v-text-field>
            <v-text-field v-model="portfolio.url" label="URL"></v-text-field>
        </div>

        <h2>Hobbies</h2>

        <v-text-field v-model="hobbies" label="Hobbies"></v-text-field>

        <h2>References</h2>

        <div v-for="(reference, index) in references" :key="index">
            <v-text-field v-model="reference.name" label="Name"></v-text-field>
            <v-text-field v-model="reference.company" label="Company"></v-text-field>
            <v-text-field v-model="reference.position" label="Position"></v-text-field>
            <v-text-field v-model="reference.phone" label="Phone"></v-text-field>
            <v-text-field v-model="reference.email" label="Email"></v-text-field>
        </div>

        <h2>Profile Status</h2>

        <v-text-field v-model="recordStatus" label="Profile Status"></v-text-field>

        <v-btn type="submit">Save</v-btn>

    </v-form>
</template>

<script setup lang="ts">
</script>

<script>
import axios from 'axios';
import _ from 'lodash';
import process from 'process';

export default {
    data: () => (
        {
            id: "olaf",
            fullname: "Gustavo Olaf Felix Chan",
            basicData: {
                firstName: "Gustavo Olaf",
                lastName: "Felix Chan",
                birthdate: "2000-01-01",
                gender: "male",
                profession: "Ing. Sistemas Computacionales",
                country: "MX",
                city: "Monterrey",
                state: "Nuevo Leon",
                zipCode: "64400",
                address: "Calle 1"
            },
            contact: {
                phone: "+524100005403",
                email: "example@gmail.com",
                whatsapp: "+524100005403",
                facebook: "https://www.facebook.com/",
                telegram: "https://telegram.org/"
            },
            workExperience: [
                {
                    position: "Dev Team",
                    company: "AprendesFacil",
                    startDate: "2021-01-01",
                    endDate: "2022-01-01",
                    description: "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. Nullam dictum felis eu pede mollis pretium."
                },
                {
                    position: "Developer",
                    company: "Second Company",
                    startDate: "2021-01-01",
                    endDate: "2022-01-01",
                    description: "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. Nullam dictum felis eu pede mollis pretium."
                }
            ],
            education: [
                {
                    degree: "Lic. En Ingeniería en Sistemas Computacionales",
                    endDate: "2022-01-01",
                    startDate: "2017-01-01",
                    school: "Instituto Tecnológico Superior de Escárcega",
                    description: "Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Aenean commodo ligula eget dolor. Aenean massa. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus. Donec quam felis, ultricies nec, pellentesque eu, pretium quis, sem. Nulla consequat massa quis enim. Donec pede justo, fringilla vel, aliquet nec, vulputate eget, arcu. Nullam dictum felis eu pede mollis pretium."
                }
            ],
            skills: [
                {
                    name: "HTML",
                    level: "beginner",
                    type: "technical",
                    categories: [
                        "hard_skill",
                        "technology",
                        "web",
                        "frontend",
                        "programation"
                    ]
                },
                {
                    name: "CSS",
                    level: "medium",
                    type: "technical",
                    categories: [
                        "hard_skill",
                        "technology",
                        "web",
                        "frontend",
                        "programation"
                    ]
                },
                {
                    name: "JavaScript",
                    level: "advanced",
                    type: "technical",
                    categories: [
                        "hard_skill",
                        "technology",
                        "web",
                        "frontend",
                        "programation"
                    ]
                },
                {
                    name: "Python",
                    level: "expert",
                    type: "technical",
                    categories: ["hard_skill", "technology", "backend", "programation"]
                },
                {
                    name: "English",
                    level: "beginner",
                    type: "linguistic",
                    categories: ["hard_skill", "language"]
                },
                {
                    name: "Spanish",
                    level: "native",
                    type: "linguistic",
                    categories: ["hard_skill", "language"]
                },
                {
                    name: "Portuguese",
                    level: "medium",
                    type: "linguistic",
                    categories: ["hard_skill", "language"]
                },
                {
                    name: "Russian",
                    level: "advanced",
                    type: "linguistic",
                    categories: ["hard_skill", "language"]
                },
                {
                    name: "Leadership",
                    level: "basic",
                    type: "generic",
                    categories: ["soft_skill", "leadership"]
                }
            ],
            portfolio: [
                {
                    name: "Project 1",
                    description: "Description of the project",
                    startDate: "2021-01-01",
                    endDate: "2022-01-01",
                    technologies: ["HTML", "CSS", "JavaScript"],
                    url: "https://example.com"
                },
                {
                    name: "Project 2",
                    description: "Description of the project",
                    startDate: "2021-01-01",
                    endDate: "2022-01-01",
                    technologies: [],
                    appliedSkills: ["English"],
                    url: "https://example.com"
                }
            ],
            hobbies: ["Reading", "Playing video games", "Watching movies"],
            references: [
                {
                    name: "Reference 1",
                    description: "Description of the reference",
                    company: "AprendesFacil",
                    position: "Dev Team",
                    phone: "+524100005403",
                    email: "example@gmail.com"
                }
            ],
            recordStatus: "on"
        }
    ),
    methods: {
        async saveProfile() {
            const body = _.cloneDeep(this.$data);
            console.log(body);
            console.log(process.env.URL_GENERIC_API);

            const response = await axios.post(process.env.URL_GENERIC_API + '/profiles', body)
        }
    },
    computed: {
        getFullname: {
            get() {
                return `${this.basicData.firstName} ${this.basicData.lastName}`;
            }
        }
    }
}
</script>

<style lang="css"></style>