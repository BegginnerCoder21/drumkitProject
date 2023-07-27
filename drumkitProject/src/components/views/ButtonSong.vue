<template>
    <div class="buttonStyle">
        <div v-for="(tabButton,index) in props.tabButtons" :key="tabButton.name">
            <button :class="{active:tabButton.style}"  v-on:click="playerAudio(index)" >{{ tabButton.letter }}</button>
            <audio id="lister">
                <source :src="getAudioPath(tabButton.nameSong)" type="audio/mpeg" />
            </audio>
        </div>
    </div>
</template>

<script setup lang="ts">
import type typeButton from '@/types';
import { onMounted, ref } from 'vue';
const player = ref()

const props = defineProps<{
    tabButtons:typeButton[]
}>();

const down = ref(false)


const playerAudio = (index:number) => {
    player.value[index].currentTime = 0;
    player.value[index].play();

}


const getAudioPath = (url:string) => {
    return new URL(`../../assets/${url}.wav`,import.meta.url).pathname;
}


onMounted(() => {
    player.value = document.querySelectorAll('#lister');

    document.addEventListener('keydown',(e) => {
        props.tabButtons.forEach((Song,index) => {
            if(e.key.toLowerCase() == Song.letter.toLowerCase()){
                Song.style = !Song.style;
                setTimeout(() => {
                    Song.style=false;
                },200)
                player.value[index].currentTime = 0;
                player.value[index].play();
            }
        });
    })
    
})


</script>

<style scoped>

.buttonStyle{
    display: flex;
    gap: 30px;
}


button{
    height: 70px;
    width: 70px;
    border: none;
    outline: none;
    border-radius: 10px;
    background-color: crimson;
    color: #fff;
    font-size: 30px;
    cursor: pointer;
    transition: .4s ease all;
}

.active,
button:hover{
    opacity: 0.7;
    transform: scale(0.95);
}

button:active,button.clicked{
    transform: scale(1.1);
}


</style>