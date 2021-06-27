<template>
<div id="my-navbar" :class="{mobile:isMobile}">


<nav>
  <div class="container now-wrapper">
    <div class="brand">
      <img src="https://img.icons8.com/material-outlined/24/000000/mac-os--v2.png"/>
      <span><strong>Apple</strong> </span>
    </div>
    <div @click="isOpen=!isOpen" class="hamburger">
      <span :key="i" v-for="i in 3" :class="{cross: isOpen}"></span> 
     
    </div>
    <ul class="nav-list" :class="{open: isOpen}">
      <li class="active">
        <a href="home">Home</a>
      </li>
      <li class="">
        <a href="home">About</a>
      </li>
      <li class="">
        <a href="home">Services</a>
          <ul class="dropdown-list">
            <li>
              <a href=""> Service 0</a>
            </li>
             <li>
              <a href="">Service 1</a>
            </li>
             <li>
              <a href=""> Service 3</a>
            </li>
             <li>
              <a href=""> Service 4</a>
            </li>
          </ul>
      </li>
      <li>
        <a href="">QnA</a>
      </li>
      <li>
        <a href="">Contact</a>
      </li>
      <li>
        <button class="btn">Login</button>
      </li>
    </ul>
  </div>
</nav>
</div>
</template>

<script>
  export default {
       created() {
        window.addEventListener('resize', this.handleResize);
        this.handleResize();
    },
    destroyed() {
        window.removeEventListener('resize', this.handleResize);
    },
    data() {
        return {
          isOpen:false,
          isMobile:false,
           window: {
            width: 0,
        } ,
        // links:{
        //   'Home' :'Home',
        //   'About': 'About',
        //   'Services':{
        //     'link1': 'Service 1',
        //     'link2': 'Service 2',
        //     'link3': 'Service 3',
        //   },
        //   'QnA': 'QnA',
        //   'Contact':'Contact'
        // }
        
        }
      },
    
    methods: {
        handleResize() {
            this.window.width = window.innerWidth;
            if(this.window.width<800){
              this.isMobile= true
            }
        }
    }
    
  }
</script>

<style  scoped>
:root{
  --primary: #933ded;
  --dark: #232323;
  --pure: #fff;
  --smoke: whitesmoke;
  --dark-gray:#999;
}

.container{
  width: 100%;
  /* for mobiles */
  max-width: 100%;
  margin:0 auto;
  background: rgb(104, 102, 102);

}
.now-wrapper{
display: flex;
justify-content: space-between;
align-items: center;

}
.brand{
  display: flex;
  align-items: center;
  color: white;
  font-weight: bolder;
  font-size: 1.5rem;
}

.brand img{
  height: 30px;
  margin-right: 10px;
}
.now-wrapper ul.nav-list{
list-style: none;
display: flex;
align-items: center;

}
.now-wrapper ul.nav-list li {
margin-left: 30px;
padding: 20px 0;
position: relative;
font-size: 1.4rem;
}
.now-wrapper ul.nav-list li a{
text-decoration: none;
color: white;
letter-spacing: 1px;
}
/* //having class active chnage color */
.now-wrapper ul.nav-list li.active a{

color: rgb(255, 255, 255);
font-weight: bolder;
font-weight: bolder;
text-decoration: underline;

}


.btn{
  background: var(--primary);
  color:var(--pure);
  outline: none;
  padding: 8px 20px;
  font-size: 14px;
  cursor: pointer;
  letter-spacing: 1px;
  border:none;
  background: yellow;
  border-radius: 10px;
  padding: .8rem 1rem;
}

nav ul.dropdown-list{
  display: block;
  background: black;
  padding:6px 16px ;
  color: white;
  width: max-content;
  position: absolute;
  z-index: 999;
  left: 50%;
  transform: translateX(-50%); 
  opacity: 0;
  pointer-events: none;

}
.now-wrapper ul.dropdown-list li{
margin-left: 0;
padding:5px 0;
list-style: none;

}

.now-wrapper ul.nav-list li:hover .dropdown-list{
  opacity: 1;
  pointer-events: auto;
  transition: .5s;
  animation: dropdown .5s ease-in-out forwards;
  
}

@keyframes dropdown{
  0%{
    opacity: 0;
      transform: translateX(-50px) translateY(50px);
  }
  100%{
    opacity: 1;
     transform: translateX(-50px)  translateY(20px);
  }
}
.hamburger{
  display: none;
}
.mobile .hamburger {
  display: flex;
  flex-direction: column;
  padding: 20px 0;
  cursor: pointer;
}
.mobile .hamburger span{
  background: rgb(255, 255, 255);
  width: 28px;
  height: 2px;
  margin-bottom: 8px;
  transition: all .3s;
}
.mobile ul.nav-list {
background: linear-gradient(45deg,#c7c7ff,rgb(54, 54, 54));
position: fixed;
width: 100%;
height: 100%;
top:0;
left:0;
display: flex;
flex-direction: column;
padding-top: 80px;
opacity: 0;
pointer-events: none;
transition:all .3s ease-in-out;


}
.hamburger ,.brand{
  z-index: 999;

}
.mobile ul.nav-list.open{
  opacity: 1;
  pointer-events: auto;
}
.cross:nth-child(1){
transform: rotateZ(45deg);
transform-origin: left;
}
.cross:nth-child(2){
  transform: rotateX(90deg);
}
.cross:last-child{
transform: rotateZ(-45deg);
transform-origin: left;
}
.mobile ul.nav-list li a{
  font-size: 20px;
}
/* 57min */

/* .mobile ul.dropdown-list{
  position: relative;
  background: transparent;
  text-align: center;
  overflow-y: hidden ;
  height: 0;
  padding-top: 0;
  transition: opacity .3s ease-in-out ;

}
.mobile .nav-wrapper ul li:hover .dropdown-list{
height: max-content;
padding-top: 6px;
} */




</style>