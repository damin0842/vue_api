<template>
  <header id="header">
    <div className="header__left">
      <ul>
        <li>
          <router-link to="/About">About</router-link>
          <router-link to="/reference">Reference</router-link>
        </li>
      </ul>
    </div>

    <h1 className="header__center">
      <router-link to="/">API site</router-link>
    </h1>
    <div className="header__right">
      <ul>
        <li>
          <router-link to="/Youtube">Youtube</router-link>
        </li>
        <li>
          <router-link to="/Movie">Movie</router-link>
        </li>
        <li>
          <router-link to="/Unsplash">Unsplash</router-link>
        </li>
      </ul>
    </div>
  </header>
</template>

<style lang="scss">
#header {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  background: var(--bg-light);
  border-bottom: 1px solid var(--bg-dark-border);
  display: flex;
  align-items: center;
  padding: 0 10px;
  z-index: 1000;
  a {
    display: inline-block;
    color: var(--black);
    margin: 10px;
    position: relative;
    &::before {
      content: "";
      position: absolute;
      left: 0;
      bottom: 0;
      width: 100%;
      height: 1px;
      background: var(--white);
      transform: scaleX(0);
      transition: all 0.3s ease;
    }
    &:hover::before {
      transform: scaleX(1);
    }
  }
  li {
    display: inline-block;
  }
  .header__left {
    flex: 1 1 40%;
    font-family: var(--font-sub2);
  }
  .header__center {
    flex: 1 1 20%;
    text-align: center;
    font-size: 30px;
    font-family: var(--font-sub2);
    h1 a {
      padding: 10px 10px 12px 10px;
    }
  }
  .header__right {
    flex: 1 1 40%;
    text-align: right;
    font-family: var(--font-sub2);
  }
}
</style>
