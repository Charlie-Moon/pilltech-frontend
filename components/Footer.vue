<template>
  <footer class="pill-footer">
    <div class="container">
      <div class="row no-gutters pt-5 border-bottom">
        <div class="col-12 col-md-6">
          <div class="title-footer">
            <h6>{{$i18n.locale=='en' ? footer.footer_title_en : footer.footer_title_kh}}</h6>
            <p v-html="$i18n.locale=='en' ? footer.address_en : footer.address_kh"></p>
          </div>
        </div>
        <div class="col-12 col-md-3">
          <div class="title-footer">
            <h6>{{ $i18n.locale=='en' ? footer.useful_title_en : footer.useful_title_kh }}</h6>
            <ul>
              <li v-for="(usl, index) in footer.useful_link" :key="index">
                <nuxt-link
                  :to="usl.link_url"
                >{{ $i18n.locale=='en' ? usl.link_title_en : usl.link_title_kh }}</nuxt-link>
              </li>
            </ul>
          </div>
        </div>
        <div class="col-12 col-md-3">
          <div class="title-footer">
            <h6>{{ $i18n.locale=='en' ? footer.about_title_en : footer.about_title_kh }}</h6>
            <ul>
              <li v-for="(abt, index) in footer.about_us" :key="index">
                <nuxt-link
                  :to="localePath(`${abt.link_url}`)"
                >{{ $i18n.locale=='en' ? abt.link_title_en : abt.link_title_kh }}</nuxt-link>
              </li>
            </ul>
          </div>
        </div>
      </div>
      <div class="pill-footer-bot pt-3 pb-3">
        <p v-html=" $i18n.locale=='en' ? footer.copy_right_en : footer.copy_right_kh "></p>
      </div>
    </div>
    <!-- <button class="chat-now">
      <span>
        <svg id="Layer_1" x="0" y="0" viewBox="0 0 15 16" xml:space="preserve" aria-hidden="true">
          <title />
          <path
            d="M1.3,16c-0.7,0-1.1-0.3-1.2-0.8c-0.3-0.8,0.5-1.3,0.8-1.5c0.6-0.4,0.9-0.7,1-1c0-0.2-0.1-0.4-0.3-0.7c0,0,0-0.1-0.1-0.1 C0.5,10.6,0,9,0,7.4C0,3.3,3.4,0,7.5,0C11.6,0,15,3.3,15,7.4s-3.4,7.4-7.5,7.4c-0.5,0-1-0.1-1.5-0.2C3.4,15.9,1.5,16,1.5,16 C1.4,16,1.4,16,1.3,16z M3.3,10.9c0.5,0.7,0.7,1.5,0.6,2.2c0,0.1-0.1,0.3-0.1,0.4c0.5-0.2,1-0.4,1.6-0.7c0.2-0.1,0.4-0.2,0.6-0.1 c0,0,0.1,0,0.1,0c0.4,0.1,0.9,0.2,1.4,0.2c3,0,5.5-2.4,5.5-5.4S10.5,2,7.5,2C4.5,2,2,4.4,2,7.4c0,1.2,0.4,2.4,1.2,3.3 C3.2,10.8,3.3,10.8,3.3,10.9z"
          />
        </svg>
      </span>
      {{ $i18n.locale=='en' ? footer.chat_now_en : footer.chat_now_kh }}
    </button> -->
    <!-- Load Facebook SDK for JavaScript -->
        <div id="fb-root"></div>
        <script>
            window.fbAsyncInit = function() {
                FB.init({
                xfbml            : true,
                version          : 'v8.0'
                });
            };
            (function(d, s, id) {
                var js, fjs = d.getElementsByTagName(s)[0];
                if (d.getElementById(id)) return;
                js = d.createElement(s); js.id = id;
                js.src = 'https://connect.facebook.net/en_US/sdk/xfbml.customerchat.js';
                fjs.parentNode.insertBefore(js, fjs);
            }(document, 'script', 'facebook-jssdk'));
        </script>

        <!-- Your Chat Plugin code -->
        <div class="fb-customerchat"
            attribution=setup_toolπ
            page_id="106274377680035"
            theme_color="#4290CC"
            logged_in_greeting="Hello and thank you for contacting PillTech, your pharmacy online ordering solution.  How may we assist you?"
            logged_out_greeting="Hello and thank you for contacting PillTech, your pharmacy online ordering solution.  How may we assist you?">
        </div>
  </footer>
</template>
<script>
import axios from "axios";
export default {
  name: 'footer',
  data() {
    return {
      footer: [],
    };
  },
  methods: {
    async fetchFooter() {
      let payload = await this.$axios.$get("/footer");
      this.footer = payload;
    },
  },
  mounted() {
    this.fetchFooter();
  },
};
</script>