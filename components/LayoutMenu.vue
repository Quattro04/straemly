<template>
    <div class="overlay absolute h-full">
        <div class="sidemenu h-full p-5 bg-dark">
            <p class="text-white text-xl p-3">Select streams layout...</p>
            <div class="flex h-24">
                <div class="layout flex w-1/2 flex-col p-2" @click="$emit('layout', 1)">
                    <div class="layout-block flex-1 flex justify-center items-center">1</div>
                </div>
            </div>
            <div class="flex h-24">
                <div class="layout flex w-1/2 flex-col p-2" @click="$emit('layout', 2)">
                    <div class="layout-block flex-1 flex justify-center items-center">1</div>
                    <div class="layout-block flex-1 flex justify-center items-center mt-1">2</div>
                </div>
                <div class="layout flex w-1/2 p-2" @click="$emit('layout', 3)">
                    <div class="layout-block flex-1 flex justify-center items-center">1</div>
                    <div class="layout-block flex-1 flex justify-center items-center ml-1">2</div>
                </div>
            </div>
            <div class="flex h-24">
                <div class="layout flex w-1/2 flex-col p-2" @click="$emit('layout', 4)">
                    <div class="layout-block flex-1 flex justify-center items-center">1</div>
                    <div class="flex flex-1 mt-1">
                        <div class="layout-block flex-1 flex justify-center items-center">2</div>
                        <div class="layout-block flex-1 flex justify-center items-center ml-1">3</div>
                    </div>
                </div>
                <div class="layout flex w-1/2 p-2" @click="$emit('layout', 5)">
                    <div class="layout-block flex-1 flex justify-center items-center">1</div>
                    <div class="flex flex-1 flex-col ml-1">
                        <div class="layout-block flex-1 flex justify-center items-center">2</div>
                        <div class="layout-block flex-1 flex justify-center items-center mt-1">3</div>
                    </div>
                </div>
            </div>
            <div class="flex h-24">
                <div class="layout flex w-1/2 flex-wrap p-2" @click="$emit('layout', 6)">
                    <div class="screen-4 layout-block w-1/2 flex justify-center items-center">1</div>
                    <div class="screen-4 layout-block w-1/2 flex justify-center items-center">2</div>
                    <div class="screen-4 layout-block w-1/2 flex justify-center items-center">3</div>
                    <div class="screen-4 layout-block w-1/2 flex justify-center items-center">4</div>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss">
.overlay {
    width: 400px;
    left: -300px;
    top: 0;
    transition: left .3s;
    &:hover {
        left: 0;
    }
}
.sidemenu {
    width: 300px;
    border-right: 1px solid #526488;
    .screen-4:nth-child(odd) {
        border-right: 2px solid #060b0e;
    }
    .screen-4:nth-child(even) {
        border-left: 2px solid #060b0e;
    }
    .screen-4:nth-child(1),
    .screen-4:nth-child(2) {
        border-bottom: 2px solid #060b0e;
    }
    .screen-4:nth-child(3),
    .screen-4:nth-child(4) {
        border-top: 2px solid #060b0e;
    }
    .layout {
        cursor: pointer;
        .layout-block {
            background-color: #526488;
        }
        &:hover .layout-block {
            background-color: #41b883;
        }
    }
}
</style>