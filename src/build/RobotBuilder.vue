<template>
    <div>
        <div class="top-row">
            <div class="top part">
                <img  :src="selectedRobot.head.src" :title="selectedRobot.head.title"/>
                <button  @click="changeRobotPart('prev', 'head', 'heads')" class="prev-selector">&#9668;</button>
                <button  @click="changeRobotPart('next', 'head', 'heads')" class="next-selector">&#9658;</button>
            </div>
        </div>
        <div class="middle-row">
            <div class="left part">
                <img  :src="selectedRobot.leftArm.src" :title="selectedRobot.leftArm.title"/>
                <button  @click="changeRobotPart('prev', 'leftArm', 'arms')" class="prev-selector">&#9650;</button>
                <button  @click="changeRobotPart('next', 'leftArm', 'arms')" class="next-selector">&#9660;</button>
            </div>
            <div class="center part">
                <img  :src="selectedRobot.torso.src" :title="selectedRobot.torso.title"/>
                <button  @click="changeRobotPart('prev', 'torso', 'torsos')" class="prev-selector">&#9668;</button>
                <button  @click="changeRobotPart('next', 'torso', 'torsos')" class="next-selector">&#9658;</button>
            </div>
            <div class="right part">
                <img  :src="selectedRobot.rightArm.src" :title="selectedRobot.rightArm.title"/>
                <button  @click="changeRobotPart('prev', 'rightArm', 'arms')" class="prev-selector">&#9650;</button>
                <button  @click="changeRobotPart('next', 'rightArm', 'arms')" class="next-selector">&#9660;</button>
            </div>
        </div>
        <div class="bottom-row">
            <div class="bottom part">
                <img  :src="selectedRobot.base.src" :title="selectedRobot.base.title"/>
                <button  @click="changeRobotPart('prev', 'base', 'bases')" class="prev-selector">&#9668;</button>
                <button  @click="changeRobotPart('next', 'base', 'bases')" class="next-selector">&#9658;</button>
            </div>
        </div>
    </div>
</template>

<script>
    import robotParts from '../assets/data/parts'
    function getNextIndex(collection, index) {
        return collection.length - 1 > index
            ? index + 1
            : 0;
    }

    function getPrevIndex(collection, index) {
        return 0 < index
            ? index - 1
            : collection.length - 1;
    }

    export default {
        name: "RobotBuilder",
        data() {
            return {
                robotParts,
                robotState: {
                    head: 0,
                    leftArm: 0,
                    rightArm: 0,
                    torso: 0,
                    base: 0,
                }
            }
        },
        methods: {
            changeRobotPart(direction, robotPartName, collectionName) {
                switch (direction) {
                    case 'next':
                        this.robotState[robotPartName] = getNextIndex(this.robotParts[collectionName], this.robotState[robotPartName]);
                        break;
                    case 'prev':
                        this.robotState[robotPartName] = getPrevIndex(this.robotParts[collectionName], this.robotState[robotPartName]);
                        break;
                }
            }
        },
        computed: {
            selectedRobot() {
                return {
                    head: robotParts.heads[this.robotState.head],
                    leftArm: robotParts.arms[this.robotState.leftArm],
                    rightArm: robotParts.arms[this.robotState.rightArm],
                    torso: robotParts.torsos[this.robotState.torso],
                    base: robotParts.bases[this.robotState.base],
                }
            }
        }
    }
</script>

<style scoped>
    .part {
        position: relative;
        width: 165px;
        height: 165px;
        border: 3px solid #aaa;
    }

    .part img {
        width: 165px;
    }

    .top-row {
        display: flex;
        justify-content: space-around;
    }

    .middle-row {
        display: flex;
        justify-content: center;
    }

    .bottom-row {
        display: flex;
        justify-content: space-around;
        border-top: none;
    }

    .head {
        border-bottom: none;
    }

    .left {
        border-right: none;
    }

    .right {
        border-left: none;
    }

    .left img {
        transform: rotate(-90deg);
    }

    .right img {
        transform: rotate(90deg);
    }

    .bottom {
        border-top: none;
    }

    .prev-selector {
        position: absolute;
        z-index: 1;
        top: -3px;
        left: -28px;
        width: 25px;
        height: 171px;
    }

    .next-selector {
        position: absolute;
        z-index: 1;
        top: -3px;
        right: -28px;
        width: 25px;
        height: 171px;
    }

    .center .prev-selector, .center .next-selector {
        opacity: 0.8;
    }

    .left .prev-selector {
        top: -28px;
        left: -3px;
        width: 144px;
        height: 25px;
    }

    .left .next-selector {
        top: auto;
        bottom: -28px;
        left: -3px;
        width: 144px;
        height: 25px;
    }

    .right .prev-selector {
        top: -28px;
        left: 24px;
        width: 144px;
        height: 25px;
    }

    .right .next-selector {
        top: auto;
        bottom: -28px;
        left: 24px;
        width: 144px;
        height: 25px;
    }

    .right .next-selector {
        right: -3px;
    }
</style>