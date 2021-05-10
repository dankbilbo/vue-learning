<template>
    <h1>@{{username}}</h1>
    <h1>{{status.content}}</h1>
</template>

<script>

export default {
    name : 'Statuses',
    props : {
        username : {
            type : String,
            required : true
        },
        status : {
            type : Object,
            required : true
        }
    }
}
</script>
