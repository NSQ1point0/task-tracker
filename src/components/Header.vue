<template>
    <header>
        <h1>{{ title }}</h1>
        <Button @toggle-add-task="$emit('toggle-add-task')" text="Add User" color="#29bb89"/>
    </header>
</template>

<script>
import Button from "./Button"

export default {
    name: "Header",
    props: {
        title: String,
    },
    components: {
        Button,
    },
}
</script>