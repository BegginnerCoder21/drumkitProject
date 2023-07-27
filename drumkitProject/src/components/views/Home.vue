<template>
    <div class="drumkt">
        <h2>Vue DrumKit</h2>
        <ButtonSong :tabButtons="tabButtons" />
    </div>
</template>

<script setup lang="ts">
import ButtonSong from './ButtonSong.vue';

import { ref } from 'vue';
import type typeButton from '@/types/index';


const tabButtons = ref<typeButton[]>([
    {
        name:'boom',
        letter:'A',
        nameSong:'boom',
        style:false
    },
    {
        name:'clap',
        letter:'S',
        nameSong:'clap',
        style:false
    },
    {
        name:'hihat',
        letter:'D',
        nameSong:'hihat',
        style:false
    },
    {
        name:'kick',
        letter:'F',
        nameSong:'kick',
        style:false
    },
    {
        name:'openhat',
        letter:'G',
        nameSong:'openhat',
        style:false
    },
    {
        name:'ride',
        letter:'H',
        nameSong:'ride',
        style:false
    },
    {
        name:'snare',
        letter:'J',
        nameSong:'snare',
        style:false
    },
    {
        name:'tink',
        letter:'K',
        nameSong:'tink',
        style:false
    },
    {
        name:'tom',
        letter:'L',
        nameSong:'tom',
        style:false
    },
]);

</script>

<style  scoped >


.drumkt{
    display: flex;
    align-items: center;
    flex-direction: column;
}
</style>