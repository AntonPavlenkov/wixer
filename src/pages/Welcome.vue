<template>
  <section>
    <md-snackbar :md-position="'top center'" ref="snackbar" :md-duration="5000">
      <p class="snack-message">Welcome Back!</p>
      <md-button @click="$refs.snackbar.close()">Close</md-button>
    </md-snackbar>
    <transition name="fade" appear>
  
      <div class="main-app ltr">
        <div class="welcome-message">
          <div>Create </div>
          <div>Your Own Dynamic </div>
  
          <div class="big-title">Wedding Invitation
            <div class="heart">
              <svg id="Layer_1" x="0px" y="0px" viewBox="0 0 250 250" enable-background="new 0 0 250 250" xml:space="preserve">
                <path class="path path1" fill="red" stroke="#FFFFFF" stroke-width="10" stroke-miterlimit="0" d="M50.3,87.7c2-4.3,9.5-12.8,18-18.8c10.2-7.2,26-13.2,25.9-30.2C94,7.6,60.9,2.6,50,28.3
                		C38.5,1.6,6,7.8,5.7,38.8c-0.1,17,15.5,23.4,25.9,30.2C41.7,75.7,48.9,84.7,50,88.5C50.1,88.3,50.2,88,50.3,87.7" />
              </svg>
            </div>
          </div>
          <br/>
  
          <button @click="$router.push('/page/edit')" class="start-btn">Get Started!
            <i></i>
          </button>
        </div>
  
      </div>
    </transition>
  
  </section>
</template>

<script>
import MainFooter from './MainFooter'
export default {
  name: 'Welcome',
  components: {
    MainFooter
  },
  data() {
    return {
    }
  },
  created() {
    this.$store.dispatch({ type: 'loadUser' })
  },
  computed: {
    isReturningUser() { return this.$store.state.isReturningUser },
  },
  watch: {
    isReturningUser: function (newVal) { this.$refs['snackbar'].open() }
  }
}
</script>

<style scoped lang="scss">
  .main-app {
  height: 100vh;
  width: 100%;
  margin: 0 auto;
  height: 60vh;
  text-align: center;
  display: flex;
  flex-flow: col wrap;
  justify-content: center;
  height: 100vh;
  // background-image: url(../assets/land2.png);
  // background-repeat: no-repeat;
  // transition: background-position 15000ms ease-out;
}

// .main-app.ltr {
//   background-position: 100% top;
// }

// .main-app.ltr:hover {
//   background-position: 0 top;
// }

.welcome-message {
  font-size: 4em;
  font-family: 'Dancing Script', cursive;
  font-weight: 900;
  line-height: 1.5em;
  letter-spacing: 0.1em;
  display: flex;
  flex-direction: column; // flex-flow: row wrap;
  justify-content: center;
  align-items: center;
  text-shadow: 4px 4px 8px rgba(154, 150, 150, 1);
  .big-title {
    font-size: 1.3em;
    position: relative;
  }
  .heart {
    position: absolute;
    left: 29%;
    top: -6.5%;
    width: 50px;
    height: 50px;
  }
}

#Layer_1 {
  width: 50px;
  height: 60px;
}




span {
  width: 100%;
  display: block;
  margin-top: 20px;
}

.snack-message {
  font-family: 'Handlee';
}


.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0
}


// shining start-btn 
@mixin fade-transition($element) {
  -webkit-transition: $element 0.15s ease-in-out;
  -moz-transition: $element 0.15s ease-in-out;
  -ms-transition: $element 0.15s ease-in-out;
  -o-transition: $element 0.15s ease-in-out;
  transition: $element 0.15s ease-in-out;
}

.start-btn {
  /*  styling */
  cursor: pointer;
  font-family: 'Dancing Script', cursive;
  font-size: 1em;
  margin-top: 50px;
  display: inline-block;
  text-decoration: none;
  letter-spacing: 5px;
  color: #FAFAFA;
  border: 3px solid #FAFAFA;
  border-radius: 15px;
  padding: 25px;
  /*  centering */
  position: relative;
  text-align: center; // left: 50%;
  // top: 50%;
  // transform: translate(-50%, -50%);
  background: rgba(0, 0, 0, 0.5);
  @include fade-transition(background);

  &:hover {
    background: rgba(8, 97, 76, 0.6);
  }
}


i {
  /*   positioning */
  position: absolute;
  opacity: 0;
  top: 0;
  left: 0;
  /*   gradient   */
  background: -moz-linear-gradient(left, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 0.03) 1%, rgba(255, 255, 255, 0.6) 30%, rgba(255, 255, 255, 0.85) 50%, rgba(255, 255, 255, 0.85) 70%, rgba(255, 255, 255, 0.85) 71%, rgba(255, 255, 255, 0) 100%);
  /* FF3.6+ */
  background: -webkit-gradient(linear, left top, right top, color-stop(0%, rgba(255, 255, 255, 0)), color-stop(1%, rgba(255, 255, 255, 0.03)), color-stop(30%, rgba(255, 255, 255, 0.85)), color-stop(50%, rgba(255, 255, 255, 0.85)), color-stop(70%, rgba(255, 255, 255, 0.85)), color-stop(71%, rgba(255, 255, 255, 0.85)), color-stop(100%, rgba(255, 255, 255, 0)));
  /* Chrome,Safari4+ */
  background: -webkit-linear-gradient(left, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 0.03) 1%, rgba(255, 255, 255, 0.6) 30%, rgba(255, 255, 255, 0.85) 50%, rgba(255, 255, 255, 0.85) 70%, rgba(255, 255, 255, 0.85) 71%, rgba(255, 255, 255, 0) 100%);
  /* Chrome10+,Safari5.1+ */
  background: -o-linear-gradient(left, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 0.03) 1%, rgba(255, 255, 255, 0.6) 30%, rgba(255, 255, 255, 0.85) 50%, rgba(255, 255, 255, 0.85) 70%, rgba(255, 255, 255, 0.85) 71%, rgba(255, 255, 255, 0) 100%);
  /* Opera 11.10+ */
  background: -ms-linear-gradient(left, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 0.03) 1%, rgba(255, 255, 255, 0.6) 30%, rgba(255, 255, 255, 0.85) 50%, rgba(255, 255, 255, 0.85) 70%, rgba(255, 255, 255, 0.85) 71%, rgba(255, 255, 255, 0) 100%);
  /* IE10+ */
  background: linear-gradient(to right, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 0.03) 1%, rgba(255, 255, 255, 0.6) 30%, rgba(255, 255, 255, 0.85) 50%, rgba(255, 255, 255, 0.85) 70%, rgba(255, 255, 255, 0.85) 71%, rgba(255, 255, 255, 0) 100%);
  /* W3C */
  filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#00ffffff', endColorstr='#00ffffff', GradientType=1);
  /* IE6-9 */
  /*  forming the shine element
    play around with the width, skew and gradient to get different effects
  */
  width: 15%;
  height: 100%;
  transform: skew(-10deg, 0deg);
  -webkit-transform: skew(-10deg, 0deg);
  -moz-transform: skew(-10deg, 0deg);
  -ms-transform: skew(-10deg, 0deg);
  -o-transform: skew(-10deg, 0deg);
  /*  animating it  */
  animation: move 2s;
  animation-iteration-count: infinite;
  animation-delay: 1s;
  -webkit-animation: move 2s;
  -webkit-animation-iteration-count: infinite;
  -webkit-animation-delay: 1s;
  -moz-transform: skew(-10deg, 0deg);
  -moz-animation: move 2s;
  -moz-animation-iteration-count: infinite;
  -moz-animation-delay: 1s;
  -ms-transform: skew(-10deg, 0deg);
  -ms-animation: move 2s;
  -ms-animation-iteration-count: infinite;
  -ms-animation-delay: 1s;
  -o-transform: skew(-10deg, 0deg);
  -o-animation: move 2s;
  -o-animation-iteration-count: infinite;
  -o-animation-delay: 1s;
}


@keyframes move {
  0% {
    left: 0;
    opacity: 0;
  }
  5% {
    opacity: 0.0
  }
  48% {
    opacity: 0.2
  }
  80% {
    opacity: 0.0
  }
  100% {
    left: 82%
  }
}

@-webkit-keyframes move {
  0% {
    left: 0;
    opacity: 0;
  }
  5% {
    opacity: 0.0
  }
  48% {
    opacity: 0.2
  }
  80% {
    opacity: 0.0
  }
  100% {
    left: 82%
  }
}

@-moz-keyframes move {
  0% {
    left: 0;
    opacity: 0;
  }
  5% {
    opacity: 0.0
  }
  48% {
    opacity: 0.2
  }
  80% {
    opacity: 0.0
  }
  100% {
    left: 88%
  }
}

@-ms-keyframes move {
  0% {
    left: 0;
    opacity: 0;
  }
  5% {
    opacity: 0.0
  }
  48% {
    opacity: 0.2
  }
  80% {
    opacity: 0.0
  }
  100% {
    left: 82%
  }
}

@-o-keyframes move {
  0% {
    left: 0;
    opacity: 0;
  }
  5% {
    opacity: 0.0
  }
  48% {
    opacity: 0.2
  }
  80% {
    opacity: 0.0
  }
  100% {
    left: 82%
  }
}

.path {
  stroke-dasharray: 500;
  stroke-dashoffset: 500;
  animation: dash 5s linear alternate infinite;
}


@keyframes dash {
  from {
    stroke-dashoffset: 1000;
  }
  to {
    stroke-dashoffset: 0;
  }
}

@media (max-width: 650px) {
  .welcome-message {
    font-size: 2em;
    font-family: 'Dancing Script', cursive;
    font-weight: 900;
    line-height: 1.2em;
    letter-spacing: 0.1em;
    display: flex;
    flex-direction: column; // flex-flow: row wrap;
    justify-content: center;
    align-items: center;
    text-shadow: 4px 4px 8px rgba(154, 150, 150, 1);
    .big-title {
      font-size: 1.3em;
    }
  }

  #Layer_1 {
    width: 35px;
    height: 45px;
  }
}
</style>


