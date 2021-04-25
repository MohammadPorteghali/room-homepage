<template>
  <header>
    <nav>
      <a class="title" href="#">room</a>
      <ul>
        <a href="#"><li>home</li></a>
        <a href="#"><li>shop</li></a>
        <a href="#"><li>about</li></a>
        <a href="#"><li>contact</li></a>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
header {
  width: 100vw;

  nav {
    width: 100%;
    position: absolute;
    z-index: 2;
    display: flex;
    padding: 7vh 5vw;
    color: #fff;
    align-items: center;

    .title {
      font-size: 1.55em;
      margin-right: 20px;
    }

    ul {
      display: flex;
      align-items: center;

      li {
        margin-left: 40px;
        font-size: .7em;
        position: relative;
        
        &:hover::before {
          content: "";
          display: block;
          position: absolute;
          z-index: 2;
          bottom: -12px;
          left: 50%;
          transform: translateX(-50%);
          width: 30px;
          height: 2px;
          background-color: #fff;
        }
      }
    }
  }
} 
</style>