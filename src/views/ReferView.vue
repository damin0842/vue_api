<template>
  <div>
    <HeaderCont />
    <TitleCont name1="reference" name2="api" />

    <section className="cont__Refer">
      <div className="container">
        <div className="refer__inner">
          <h2>CSS</h2>
          <ul className="refer__list">
            <li v-for="refer in refers" :key="refer.title">
              <a href="#">
                <span>{{ refer.num }}</span>
                <span>{{ refer.title }}</span>
                <span>{{ refer.desc }}</span>
                <span>{{ refer.descStar }}</span>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </section>
    <ContactCont />
    <FooterCont />
  </div>
</template>
<script>
import HeaderCont from "@/components/HeaderCont.vue";
import TitleCont from "@/components/TitleCont.vue";
import FooterCont from "@/components/FooterCont.vue";
import ContactCont from "@/components/ContactCont.vue";
import { ref } from "vue";
export default {
  components: {
    HeaderCont,
    FooterCont,
    TitleCont,
    ContactCont,
  },
  setup() {
    const refers = ref([]);
    const references = () => {
      fetch(
        "https://raw.githubusercontent.com/Parkhyeonshin/react_api/main/src/utils/reference.json"
      )
        .then((response) => response.json())
        //.then((result) => console.log(result.cssRefer))

        .then((result) => (refers.value = result.cssRefer))
        .catch((error) => console.log("error", error));
    };
    references();
    return {
      refers,
      references,
    };
  },
};
</script>
<style lang="scss">
.refer__inner {
  padding-bottom: 200px;
  h2 {
    font-size: 30px;
    color: var(--white);
  }
}
.refer__list {
  border: 1px solid var(--bg-dark-border);

  li {
    border-bottom: 1px solid var(--bg-dark-border);
    a {
      display: flex;
      align-items: center;
      width: 100%;
      color: var(--black);
      padding: 10px;
      span {
        display: inline-block;
        padding: 15px 20px;
      }
      .num {
        flex: 1 1 5%;
        text-align: center;
        border-right: 1px solid var(--bg-dark-border);
      }
      .name {
        flex: 1 1 20%;
      }
      .desc {
        flex: 1 1 65%;
      }
      .star {
        flex: 1 1 10%;
        text-align: center;
      }
    }
  }
}
</style>