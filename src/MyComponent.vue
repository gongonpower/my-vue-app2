<template>
    <div>{{message}}</div>
</template>

<script>
export default {
    props:['msg'],
    data: function() {
        return {
            message: this.msg
        }
    }
}
</script>
