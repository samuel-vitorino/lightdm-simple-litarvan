<template>
    <div id="intro">
        <div class="bg blurred fixed absolute" :style="{ 'background-image': 'url(' + background + ')' }">
        </div>
            <div id="content" v-if="show">
                <img v-if="state === 'initial'" id="logo" src="../assets/images/os.png" />
                <p v-else id="power-text">
                    {{ text }}
                </p>
            </div>
    </div>
</template>

<script>
    import { trans } from '@/translations';
    import { settings } from '@/settings';
    import { background } from '@/themer';

    export default {
        name: 'l-intro',

        mounted() {
            if (settings.disableIntro && this.state === 'initial') {
                this.$router.push(settings.disableSplash ? '/base/login' : '/base/splash');
                return;
            }

            if (this.state === 'login') {
                return;
            }

            this.show = true;

            if (this.state === 'initial') {
                setTimeout(() => {
                    this.show = false;
                    this.$router.push(settings.first ? '/setup' : (settings.disableSplash ? '/base/login' : '/base/splash'));
                }, 2000);
            }
        },

        data() {
            return {
                background,
                show: false,
                state: this.$route.params.state,
                text: trans(this.$route.params.state)
            };
        }
    };
</script>

<style lang="scss" scoped>
    @import '../theme';

    #intro {
        display: flex;
        align-items: center;
        text-align: center;
    }

    #content {
        margin-left: auto;
        margin-right: auto;
    }

    #logo {
        height: 250px;
    }

    #power-text {
        font-family: 'Inter';
        font-weight: bold;
        color: $outer-foreground;
        font-size: 58px;
    }

    .logo-fade-enter-active, .logo-fade-leave-active {
        transition: opacity 1s;
    }

    .logo-fade-enter, .logo-fade-leave-to {
        opacity: 0;
    }

    #power-icon {
        width: 50px;

        margin-bottom: -5px;
        margin-right: 4px;
    }

    .bg {
        background-size: cover;
        left: 0;
        right: 0;

        display: block;
        width: 100%;
        height: 100vh;

        z-index: -1;

        color: $secondary-color;

        &.absolute {
            position: absolute;
        }

        &.fixed {
            position: fixed;
        }
        
        &.blurred {
            filter: blur(10px);
        }
    }
</style>
