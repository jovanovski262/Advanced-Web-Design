<template>
    <div>
        <h1>Blog Editor</h1>
        <div class="field">
            <label for="title">Title</label>
            <input type="text" id="title" v-model="title" />
        </div>
        <div class="field">
            <label for="slug">Blog id</label>
            <input type="text" id="slug" v-model="id" />
        </div>
        <div class="field">
            <label for="author">Author</label>
            <input type="text" id="author" v-model="author" />
        </div>
        <div class="field">
            <label for="content">Content</label>
            <textarea id="content" v-model="content"></textarea>
        </div>
        <div class="field">
            <button @click="save">Save</button>
        </div>
    </div>
</template>
<script setup>
import { ref } from 'vue';

const title = ref('');
const author = ref('');
const content = ref('');
const id = ref('');
const date = ref('');

const emits = defineEmits(['addNewItem']);

const now = new Date();

const save = () => {
    emits('addNewItem', ({
        title: title.value,
        author: author.value,
        content: content.value,
        id: id.value,
        date: now
    }));

    title.value = '';
    author.value = '';
    content.value = '';
    id.value = '';
    date.value = '';
};
</script>
 