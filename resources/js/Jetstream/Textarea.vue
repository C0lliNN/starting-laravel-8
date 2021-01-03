<template>
    <textarea
        class="form-input rounded-md shadow-sm"
        rows="4"
        :value="value"
        @input="$emit('input', $event.target.value)"
    ></textarea>
</template>

<script>
export default {
    props: ['value'],

    methods: {
        focus() {
            this.$refs.input.focus();
        },
    },
};
</script>
