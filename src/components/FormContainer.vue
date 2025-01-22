<template>
    <div @mouseover="neonHover"
    @mouseout="neonUnHover"
    @mousemove="throttledRgb"
    :class="['container-main', { neon: containerHover }]">

    <!-- Content Goes Here -->
    <LoginForm :hovered="containerHover" />
    </div>
</template>

<script>
    import { throttle } from 'lodash';
    import LoginForm from './LoginForm.vue';

    export default {
        name: 'FormContainer',
        components: {
            LoginForm
        },
        data() {
            return {
                containerHover : false
            }
        },
        methods: {
            neonHover() {
                this.containerHover = true
            },
            neonUnHover() {
                this.containerHover = false
            },
            rgbNeon() {
                if (this.containerHover) {
                    let colorR, colorG, colorB;
                    const containerMain = document.querySelector(".neon");

                    if (containerMain) {
                        do {
                            colorR = Math.round(Math.random() * 200);
                            colorG = Math.round(Math.random() * 200);
                            colorB = Math.round(Math.random() * 200);

                            var contrast = Math.abs(colorR - colorG) + Math.abs(colorR - colorB) + Math.abs(colorG - colorB);
                            
                        } while (contrast < 300); 

                        containerMain.style.setProperty('--color-1', colorR);
                        containerMain.style.setProperty('--color-2', colorG);
                        containerMain.style.setProperty('--color-3', colorB);
                    }
                }
            }
        },
        created () {
            this.throttledRgb = throttle(this.rgbNeon, 500);
        }
    }
</script>

<style scoped>
    .container-main {
        backdrop-filter: blur(5px);
        margin-top: 30px;
        width: 400px;
        height: 270px;
        border-radius: 20px;
        box-shadow: 1px 1px 20px rgba(255, 255, 255, 1) ;
        background-color: transparent;
        overflow: hidden;
        transition: all 0.5s;
        position: relative;
        z-index: 2;
    }
    .neon {
        position: relative;
        background-color: rgba(239, 243, 247, 0.9);
        z-index: 2;
    }
    .neon::before {
        content: "";
        position: absolute;
        z-index: 1;
        opacity: 0;
        border-radius: 50%;
        box-shadow: 0 0 4px 14px rgba(var(--color-1, 204), var(--color-2, 57), var(--color-3, 57), 0.7);
        animation: moveBeforeAround 1.5s infinite;
    }
    .neon::after {
        content: "";
        position: absolute;
        z-index: 1;
        opacity: 0;
        border-radius: 50%;
        box-shadow: 0 0 4px 14px rgba(var(--color-1, 204), var(--color-2, 57), var(--color-3, 57), 0.7);
        animation: moveAfterAround 1.5s infinite;
    }

    @keyframes moveBeforeAround {
        0%, 100% {
            top: 0%;
            left: 10%;
            width: 0%;
            opacity: 0;
        }
        1% {
            opacity: 1;
        }
        24% {
            left: 10%;
            width: 80%;
        }
        44% {
            opacity: 1;
        }
        48% {
            left: 90%;
            top: 0%;
            width: 0%;
            opacity: 0;
        }
        50% {
            top: 10%;
            left: 100%;
            opacity: 0;
            height: 0%;
        }
        51% {
            opacity: 1;
        }
        74% {
            top: 10%;
            height: 80%;
        }
        94%{
            opacity: 1;
        }
        98%{
            top: 90%;
            height: 0%;
            opacity: 0;
        }
        99% {
            left: 100%;
            opacity: 0;
        }
    }
    @keyframes moveAfterAround {
        0%, 100% {
            top: 100%;
            left: 90%;
            width: 0%;
            opacity: 0;
        }
        1% {
            opacity: 1;
        }
        24% {
            left: 10%;
            width: 80%;
        }
        44% {
            opacity: 1;
        }
        48% {
            left: 10%;
            top: 100%;
            width: 0%;
            opacity: 0;
        }
        50% {
            top: 90%;
            left: 0%;
            opacity: 0;
            height: 0%;
        }
        51% {
            opacity: 1;
        }
        74% {
            top: 10%;
            height: 80%;
        }
        94%{
            opacity: 1;
        }
        98%{
            top: 10%;
            height: 0%;
            opacity: 0;
        }
        99% {
            left: 0%;
            opacity: 0;
        }
    }
</style>