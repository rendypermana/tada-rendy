<template>
<div>
    <div class="mainPage">
        <div class="container-fluid page-body-wrapper">
            <div class="theme-setting-wrapper">
                <div id="settings-trigger"><i class="ti-settings"></i></div>
            </div>
            <nav class="sidebar" id="sidebar">
                <!-- belom diisi    -->
            </nav>
            <div class="main-panel">
                <Nuxt />
            </div>
        </div>  
    </div>
    
</div>
    
</template>
<script>
export default {
    data() {
        return {
            data: [],
        }
    },
    mounted() {
        
    }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/variable.scss';
.mainPage {
    .page-body-wrapper {
        min-height: calc(100vh);
        display: -webkit-flex;
        display: flex;
        -webkit-flex-direction: row;
        flex-direction: row;
        padding-left: 0;
        padding-right: 0;
    }
    .page-body-wrapper.full-page-wrapper {
        width: 100%;
        min-height: 100vh;
        padding-top: 0;
    }  
    .sidebar {
        min-height: calc(100vh);
        background: #fff;
        font-family: "Nunito", sans-serif;
        font-weight: 500;
        padding: 0;
        width: 100px;
        background: $tada-light;
        z-index: 9999;
        @include breakpoint(mobileonly) {
            display: none;
        }
    }
    .main-panel {
        transition: width 0.25s ease, margin 0.25s ease;
        // width: calc(100% - 70px);
        padding: 15px;
        width: 100%;
        min-height: calc(100vh);
        display: -webkit-flex;
        display: flex;
        -webkit-flex-direction: column;
        flex-direction: column;
        background: $tada-dark;
        color: $white;
    }

}
</style>
