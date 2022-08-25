<template>
    <div class="all_display">
        
        <div class="container h-100">
            <div class="row h-100 align-items-center">

                <div class="col-12 text-center">
                    <h3>scroll to start</h3>
                    <i class="icon-pixel-down"></i>
                    <i class="icon-pixel-down mt-3"></i>
                </div>
                
            </div>
        </div>
    </div>
</template>

<script>

export default {
    data(){
        return {

        }
    }, // end of data
    mounted(){

    }, // end of mounted
    methods: {

    }, // end of methods

}
</script>

<style lang="scss">
@import 'src/styles/main.scss';

    .all_display {
        background-color: $bg_blue;
        color: $yellow;
        font-family: $start;
        .col-12 {
            position: relative;      
            h3 {
                text-transform:capitalize;
            }
            .icon-pixel-down {
                animation-name: chevron_down;
                animation-duration: 850ms;
                animation-iteration-count: infinite;
                animation-timing-function: steps(4, end);
                left: 50%;
                transform: translate(-50%, 0);
            }
        }
    }

</style>