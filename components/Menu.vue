<template>
    <nav class="menu">
        <input type="checkbox" href="#" class="menu-open" name="menu-open" id="menu-open"/>
        <label class="menu-open-button" for="menu-open">
            <span class="hamburger hamburger-1"></span>
            <span class="hamburger hamburger-2"></span>
            <span class="hamburger hamburger-3"></span>
        </label>
        
        <a href="javascript:void(0)" @click="$emit('action', 'add')" class="menu-item"><font-awesome-icon :icon="['fa', 'plus']" /></a>
        <!-- <a href="#" class="menu-item"><font-awesome-icon :icon="['fa', 'info']" /></a> -->
    </nav>
</template>

<style lang="scss">
@import '~compass-mixins/lib/compass/css3';

//vars
$fg:#526488;
$pi: 3.14;

//config
$menu-items: 1;
$open-distance: 20px;
$opening-angle: $pi*2;

%goo {
    filter:url('#shadowed-goo');
    // debug 
    //background:rgba(255,0,0,0.2);
}

%ball {
    background: $fg;
    border-radius: 100%;
    width: 70px;
    height: 70px;
    position: absolute;
    top: 30px;
    left: 30px;
    color: white;
    text-align: center;
    line-height: 80px;
    transform: translate3d(-100px, -100px, 0);
    transition: transform ease-out 200ms, left ease-out 200ms, top ease-out 200ms;
}

.menu {
    width: 200px;
    height: 200px;
    position: absolute;
    left: 0;
    top: 0;
    &:hover {
        .menu-open-button {
            left: 30px;
            top: 30px;
        }
        .menu-item {
            transform: translate3d(0, 0, 0);
        }
    }
}

.menu-open {
    display: none;
}

.menu-item {
    @extend %ball;
}

.hamburger {
    $width: 25px;
    $height: 3px;
    width: $width;
    height: $height;
    background :white;
    display: block;
    position: absolute;
    top: 50%;
    left: 50%;
    margin-left: -$width/2;
    margin-top: -$height/2;
    transition: transform 200ms;
}
$hamburger-spacing: 8px;
.hamburger-1 {
    transform:translate3d(0, -$hamburger-spacing, 0);
}
.hamburger-2 {
    transform:translate3d(0,0,0);
}
.hamburger-3 {
    transform:translate3d(0, $hamburger-spacing, 0);
}
.menu-open:checked+.menu-open-button {
    left: 30px;
    top: 30px;
    .hamburger-1 {
        transform:translate3d(0,0,0) rotate(45deg); 
    }
    .hamburger-2{
        transform:translate3d(0,0,0) scale(0.1,1);
    }
    .hamburger-3{
        transform:translate3d(0,0,0) rotate(-45deg); 
    }
}

.menu {
    @extend %goo;
    font-size: 20px;
    text-align: left;
}

.menu-item {
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 30px;
    &:hover {
        background-color: #41b883;
    }
    @for $i from 1 through $menu-items {
        &:nth-child(#{$i+2}) {
            transition-duration: 180ms;
        }
    }
}

.menu-open-button {
    @extend %ball;
    z-index: 2;
    transition-timing-function: cubic-bezier(0.175, 0.885, 0.320, 1.275);
    transition-duration: 400ms;
    transform: scale(1.1,1.1) translate3d(0,0,0);
    left: -50px;
    top: -50px;
    cursor: pointer;
}
.menu-open-button:hover {
    transform: scale(1.2,1.2) translate3d(0,0,0);
}
.menu-open:checked+.menu-open-button {
    transition-timing-function: linear;
    transition-duration: 200ms;
    transform: translate3d(0,0,0);
}

.menu-open:checked~.menu-item {
    transition-timing-function: cubic-bezier(0.165, 0.840, 0.440, 1.000);
    @for $i from 1 through $menu-items{
        &:nth-child(#{$i+2}) {
            transition-duration: 90ms+(100ms*$i);
            transform: translate3d(90px*$i,0,0);
        }
    }
}
</style>