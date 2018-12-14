<template>
  <div class="home-component sponsor-section-wrapper">
    <div class="container">
      <h2 class="mega-rainbow">Sponsors</h2>
      <h4 class="subtitle">Platinum</h4>
      <div class="sponsors-wrapper platinum-wrapper">
        <a
          :href="sponsor.website"
          class="sponsor-logo"
          v-if="getSponsors && sponsor.status === 'Platinum'"
          v-for="sponsor in getSponsors"
          :key="sponsor.id"
          :title="sponsor.name"
        >
          <img :src="sponsor.logo" :alt="sponsor.name" :title="sponsor.name">
        </a>
      </div>

      <a href="#" class="view-more">View all sponsors</a>

      <div
        class="tribute-text"
      >Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquam ea itaque magni, omnis cum reprehenderit possimus laudantium, doloribus veritatis dolorem repellat explicabo odio quas architecto nobis error nisi. Molestiae, sunt.</div>
    </div>

    <div class="button-center">
      <button-waw
        :theme="'#97d0e1'"
        :size="'80px'"
        :link="'https://github.com/mscraftsman/devcon2019/raw/master/assets/DevCon2019-SponsorshipProposal.pdf'"
      >Become a Sponsor</button-waw>
    </div>
  </div>
</template>
<script>
import { mapGetters, mapActions } from "vuex";

import { FETCH_SPONSORS } from "@/store";

export default {
  data() {
    return {
      sponsorsSample: [
        { "id": "1", "name": "Jochen Kirstätter", "logo": "https://raw.githubusercontent.com/mscraftsman/devcon2019/dev/web/app/src/assets/sample-sponsors/mcb.svg", "website": "http://jochen.kirstaetter.name", "status": "Platinum" },
        { "id": "2", "name": "Sandeep R", "logo": "https://raw.githubusercontent.com/mscraftsman/devcon2019/dev/web/app/src/assets/sample-sponsors/sdworx.svg", "website": "http://barfii.net", "status": "Gold" },
        { "id": "3", "name": "Sandeep R", "logo": "https://raw.githubusercontent.com/mscraftsman/devcon2019/dev/web/app/src/assets/sample-sponsors/sdworx.svg", "website": "http://barfii.net", "status": "Gold" }
      ]
    }
  },
  created() {
    this.FETCH_SPONSORS();
  },

  computed: {
    ...mapGetters(["getSponsors"])
  },

  methods: {
    ...mapActions([FETCH_SPONSORS])
  }
};
</script>


<style lang="scss" scoped>
.home-component {
  padding: $section-spacer 0;
}
.sponsors-wrapper {
  display: grid;
  padding: 50px 0;
  border-bottom: 1px solid rgba(#fff, 0.3);

  .sponsor-logo {
    img {
      display: block;
      width: 250px;
      height: auto;
      margin: 0 auto;
    }
  }
}
.platinum-wrapper {
  grid-template-columns: 1fr 1fr;

  @media screen and (max-width: $tablet) {
    grid-template-columns: 1fr;
    grid-row-gap: 40px;
  }
}

.view-more {
  padding: $gutter * 2 0;
}

.button-center {
  // width: 300px;
  margin: $gutter auto;
}
</style>
