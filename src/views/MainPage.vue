<template>
  <div class="title">Invictus</div>
  <div class="poem-author">By William Renest Henley</div>

  <section class="content-wrap">
    <div class="checkbox-wrap">
      <CheckboxPoems
        v-for="(poem, index) in poems"
        :id="poem.id"
        v-model:value="poem.show"
        :disabled="activePoemsCount && poem.show"
      />
    </div>

    <div class="poems-wrap">
      <p
        v-for="poem in activePoems"
        class="poems-wrap__item"
        v-html="poem.text"
      ></p>
    </div>
  </section>
</template>

<script>
import CheckboxPoems from "../components/CheckboxPoems.vue";

export default {
  name: "MainPage",

  components: {
    CheckboxPoems,
  },

  data() {
    return {
      poems: [
        {
          id: 1,
          text: `Out of the night that covers me,<br/>
    &nbsp &nbsp &nbsp Black as the pit from pole to pole, <br/>
    I thank whatever gods may be <br/>
    &nbsp &nbsp &nbsp For my unconquerable soul.`,
          show: true,
        },
        {
          id: 2,
          text: `In the fell clutch of circumstance <br/>
        &nbsp &nbsp &nbsp I have not winced nor cried aloud.<br/>
        Under the bludgeonings of chance <br/>
        &nbsp &nbsp &nbsp My head is bloody, but unbowed.`,
          show: true,
        },
        {
          id: 3,
          text: `Beyond this place of wrath and tears <br/>
        &nbsp &nbsp &nbsp Looms but the Horror of the shade,<br/>
        And yet the menace of the years <br/>
        &nbsp &nbsp &nbsp Finds and shall find me unafraid.`,
          show: true,
        },
        {
          id: 4,
          text: `It matters not how strait the gate,<br/>
        &nbsp &nbsp &nbsp How charged with punishments the scroll,<br/>
        I am the master of my fate,<br/>
        &nbsp &nbsp &nbsp I am the captain of my soul.`,
          show: true,
        },
      ],
    };
  },

  computed: {
    activePoemsCount() {
      return this.activePoems.length === 1;
    },

    activePoems() {
      return this.poems.filter((poem) => poem.show);
    },
  },
};
</script>

<style lang="scss">
.title {
  font-weight: 600;
  font-size: 50px;
  text-align: center;

  @media (max-width: 1024px) {
    font-size: 36px;
  }

  @media (max-width: 720px) {
    font-size: 32px;
  }
}

.poem-author {
  font-weight: 500;
  font-size: 30px;
  text-align: right;
  margin-top: -20px;

  @media (max-width: 1024px) {
    font-size: 20px;
  }

  @media (max-width: 720px) {
    font-size: 20px;
    text-align: center;
    margin-top: 10px;
  }
}

.content-wrap {
  margin-top: 20px;

  @media (max-width: 720px) {
    margin-top: 10px;
  }
}

.checkbox-wrap {
  display: flex;
  position: absolute;
  gap: 35px;

  @media (max-width: 1024px) {
    gap: 10px;
  }

  @media (max-width: 720px) {
    justify-content: center;
    position: static;
  }
}

.poems-wrap {
  position: relative;
  max-width: 558px;
  margin: 0 auto;

  @media (max-width: 1024px) {
    max-width: 380px;
  }

  @media (max-width: 720px) {
    margin: 30px auto;
    width: 340px;
  }

  &__item {
    margin-bottom: 20px;
    font-size: 30px;
    line-height: 1.2;

    @media (max-width: 1024px) {
      font-size: 20px;
    }

    @media (max-width: 720px) {
      font-size: 18px;
    }
  }
}
</style>
