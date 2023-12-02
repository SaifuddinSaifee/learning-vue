<template>
    <form>
        <div class="info email">
            <label for="email">Email</label>
            <input type="email" required />
        </div>
        <div class="info password">
            <label for="password">Password</label>
            <input type="password" required />
        </div>
    </form>
</template>

<script>
export default {
    name: "SignUpForm",
};

</script>

<style scoped>
form {
    font-family: 'Roboto', sans-serif;
    width: 340px;
    margin: 0 auto;
    background-color: #fff;
    padding: 2rem;
    border-radius: 8px;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.info {
    margin: 1rem;
}

/* Form input fields */
input[type="text"],
input[type="email"],
input[type="password"],
textarea {
    width: 100%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    box-sizing: border-box;
    font-size: 16px;
    border-radius: 4px;
}

/* Form labels */
label {
    display: block;
    /* margin-bottom: 8px; */
    font-weight: 500;
}

/* Form submit button */
button[type="submit"] {
    background-color: #4285f4;
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    cursor: pointer;
    font-size: 16px;
    border-radius: 4px;
}

/* Form submit button hover effect */
button[type="submit"]:hover {
    background-color: #3367d6;
}

/* Form error message */
.error-message {
    color: red;
    font-size: 14px;
    margin-top: 8px;
}
</style>