<template>
  <footer id="footer">
    <div className="footer__inner">
      <div>
        <h3>Email</h3>
        <a href="mailto:damin0842@gmail.com">damin0842@gmail.com</a>
      </div>
      <div>
        <h3>Kakao</h3>
        <a href="mailto:damin0842@gmail.com">damin0842</a>
      </div>
      <div>
        <h3>Soclal</h3>
        <ul>
          <a href="mailto:damin0842@gmail.com">youtube</a>
          <a href="mailto:damin0842@gmail.com">instagram</a>
          <a href="mailto:damin0842@gmail.com">blog</a>
          <a href="mailto:damin0842@gmail.com">asd</a>
        </ul>
      </div>
    </div>
  </footer>
</template>
<style lang="scss">
#footer {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  color: var(--black);
  background-color: var(--bg-light);
  border-top: 1px solid var(--bg-dark-border);
  z-index: 1000;
}
.footer__inner {
  display: flex;
  align-items: center;
  font-family: var(--font-sub2);

  div {
    text-align: center;
    &:nth-child(1) {
      flex: 1 1 30%;
      border-right: 1px solid var(--bg-dark-border);
    }
    &:nth-child(2) {
      flex: 1 1 30%;
      border-right: 1px solid var(--bg-dark-border);
    }
    &:nth-child(3) {
      flex: 1 1 40%;
    }
  }
  h3,
  ul,
  li {
    display: inline-block;
  }
  a {
    display: inline-block;
    margin: 23px;
    color: var(--black);
    opacity: 0.6;
    position: relative;
    transition: opacity 0.8;
    text-transform: capitalize;

    &:hover {
      opacity: 1;
    }

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
}
</style>
