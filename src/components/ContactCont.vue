<template>
  <section className="cont_contact">
    <p>Let's create something new</p>
    <h3>LET'S Get IN <em>TOUBH</em></h3>
    <a href="mailto:webstoryboy@naver.com">Contact me</a>
  </section>
</template>
<style lang="scss">
// cont__contact
.cont_contact {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  color: var(--black);
  text-transform: uppercase;
  p {
    font-size: 20px;
    font-family: var(--font-main2);
    margin-bottom: 20px;
  }
  h3 {
    font-size: 9vw;
    font-family: var(--font-main);
    line-height: 1;
    text-align: center;
    em {
      display: block;
    }
  }
  a {
    font-size: 16px;
    font-family: var(--font-sub2);
    border: 1px solid var(--black);
    border-radius: 50px;
    padding: 1vw 4vw;
    color: var(--black);
  }
}
</style>