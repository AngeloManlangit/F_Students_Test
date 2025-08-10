<template>
    <button
        @click.prevent="changeAudio()">
        <img :src="audio[audio_index].icon">
    </button>
</template>

<script>
import noAudio from '../assets/speakerphone/no_audio.svg';
import halfAudio from '../assets/speakerphone/half_audio.svg';
import fullAudio from '../assets/speakerphone/full_audio.svg';
import muteAudio from '../assets/speakerphone/mute_audio.svg';
import fStudentAudioFile from '../assets/f_students_audio.mp3';
import burningMemoryAudioFile from '../assets/Burning_memory.mp3';

export default {
    props: {
        file_index: Number,
    },
    data() {
        return {
            audio_index: 0,
            audio: [
                {
                    icon: noAudio,
                    volume: 0
                },
                {
                    icon: halfAudio,
                    volume: 25
                },
                {
                    icon: fullAudio,
                    volume: 75
                },
                {
                    icon: muteAudio,
                    volume: 0
                }
            ],
            audioPlayer: null,
            file: [ fStudentAudioFile, burningMemoryAudioFile ],
        }
    },
    mounted() {
        this.audioPlayer = new Audio(this.file[this.file_index]);
    },
    watch: {
        file_index(newIndex) {
            if (this.audioPlayer) {
                this.audioPlayer.pause();
            }
            
            this.audioPlayer = new Audio(this.file[newIndex]);
            this.audio_index = 0;
        }
    },
    methods: {
        changeAudio() {
            if (this.audio_index == 0 || this.audio_index >= 3) {
                this.playAudio();
                this.audio_index = 1;
                this.audioPlayer.volume = this.audio[this.audio_index].volume / 100;
                this.audioPlayer.loop = true;
            }
            else {
                this.audio_index++;
                this.audioPlayer.volume = this.audio[this.audio_index].volume / 100;
            }
        },
        playAudio() {
            if (this.audioPlayer) {
                this.audioPlayer.currentTime = 0;
                this.audioPlayer.play();
            }
        }
    }
}
</script>

<style scoped>
button {
    position: fixed;
    top: 20px;
    right: 20px;

    background-color: rgba(175, 244, 161, 0.551);
    border: 0;
    border-radius: 50%;
    cursor: pointer;
    box-shadow: 0px 0px 0px black;

    transition: all 250ms;
}

button:hover {
    box-shadow: 5px 5px black;
}

button:active {
    background-color: rgba(119, 223, 98, 0.551);
}

img {
    margin: 10px;
    height: 60px;
}
</style>

