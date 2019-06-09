
<template>
    <div>
        <button @click="back">back</button>
        <li>Whoa you logged in and this is your profile name.</li>  
             <li>*a super cool profile pic ha ha* <li>
             <li>*here's your obligatory latin or arrabic quote* </li>
            <li>a few pics and jokes right here</li>
    </div>
</template>

<script>
export default {
    name: "Profile",
    data() {
        return {

        }
    },
    methods: {
        back: function() {
            this.$router.go(-1);
        }
    }

}
</script>

