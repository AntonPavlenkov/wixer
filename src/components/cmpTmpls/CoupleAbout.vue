<template>
    <section class="couple-about cmp-father" :style="cmp.style" :class="{'mark-class': isEditMode}">
        <div class="content">
            <div class="about-1">
                <span @blur="updateText('aboutName1')" :contenteditable="isEditMode" class="about-1-name">{{cmp.data.aboutName1}}</span>
                <img @click="setImg('aboutImgUrl1')" :src="cmp.data.aboutImgUrl1" class="about-1-img" width="100px" height="200px">
                <span @blur="updateText('aboutInfo1')" :style="cmp.style" :contenteditable="isEditMode" class="about-1-info">{{cmp.data.aboutInfo1}}</span>
            </div>
            <div class="main-img-container">
                <img @click="setImg('mainImgUrl')" class="main-img" :src="cmp.data.mainImgUrl">
            </div>
            <div class="about-2">
                <span @blur="updateText('aboutName2')" :contenteditable="isEditMode" class="about-2-name">{{cmp.data.aboutName2}}</span>
                <img @click="setImg('aboutImgUrl2')" :src="cmp.data.aboutImgUrl2" class="about-2-img" width="100px" height="200px">
                <span @blur="updateText('aboutInfo2')" :style="cmp.style" :contenteditable="isEditMode" class="about-2-info">{{cmp.data.aboutInfo2}}</span>
            </div>
        </div>

        <!--edit butttons-->
        <modify-btns @deleteCmp="deleteCmp" @toggleEditMode="toggleEditMode"></modify-btns>

        <transition name="fade">
            <edit-console :cmp="cmp" v-if="isEditMode" @toggleEditMode="toggleEditMode" v-draggable>
                <couple-toolbar v-if="selectedImgType!==''" :cmp="cmp" :selectedImgType="selectedImgType" @update="updateCmp"></couple-toolbar>
                <txt-toolbar :cmp="cmp" @update="updateCmp"></txt-toolbar>
                <general-edit :cmp="cmp" :isFirst="isFirst" :isLast="isLast" @delete="deleteCmp" @move="moveCmp" @update="updateCmp"></general-edit>
            </edit-console>
        </transition>
    </section>
</template>

<script>
import ModifyBtns from '../toolbars/ModifyBtns'
import TxtToolbar from '../toolbars/TxtToolbar'
import GeneralEdit from '../toolbars/generalEditToolbar'
import EditConsole from '../toolbars/EditConsole'
import CoupleToolbar from '../toolbars/CoupleToolbar'
import EditableFuncs from '../mixins/EditableFuncs'

export default {
    name: 'CoupleAbout',
    mixins: [EditableFuncs],
    props: {
        cmp: { type: Object, required: true },
        isFirst: Boolean, 
        isLast: Boolean
    },
    components: {
        ModifyBtns,
        TxtToolbar,
        GeneralEdit,
        EditConsole,
        CoupleToolbar
    },
    data() {
        return {
            selectedImgType: ''
        }
    },
    methods: {
        setImg(imgType) {
            this.selectedImgType = imgType
            console.log(this.selectedImgType)
        },
        updateText(text) {
            this.cmpToEdit.data[text] = event.target.innerText;
            this.updateCmp(this.cmpToEdit);
        },
        // updateColor: function (event) {
        //     this.color = event.color;
        // },
    }
}
</script>


<style scoped lang="scss">
.couple-about {
    position: relative;
}

.content {
    box-sizing: content-box;
    padding: 30px;
    display: flex;
    flex-flow: row nowrap;
}

.input-newUrl {
    width: 80%;
}

.about-1,
.about-2 {
    width: 40%;
    text-align: center;
    line-height: 100%;
}

.about-1-img:hover {
    opacity: .5;
    cursor: pointer;
}

.about-2-img:hover {
    opacity: .5;
    cursor: pointer;
}

.main-img:hover {
    opacity: .5;
    cursor: pointer;
}

.about-1-img,
.about-2-img {
    width: 20%;
    display: block;
    border-radius: 50%;
    margin: 20px auto;
}

.main-img-container {
    width: 30%;
}

.main-img {
    border-radius: 50%;
}

.fade-enter-active,
.fade-leave-active {
    transition: opacity .5s
}

.fade-enter,
.fade-leave-to {
    opacity: 0
}


@media (max-width: 650px) {
    .content {
        box-sizing: content-box;
        padding: 5px;
        ;
        display: flex;
        flex-flow: column nowrap;
    }
    .main-img-container {
        width: 100%;
        display: flex;
        justify-content: center;
        .main-img {
            height: 300px;
        }
    }
    .about-1,
    .about-2 {
        width: 100%;
        text-align: center;
        line-height: 100%;
    }

    .about-1-img,
    .about-2-img {
        display: block;
        border-radius: 0;
    }
    .main-img {
        border-radius: 0;
    }
}
</style>
