<template>
  <div id="app">
    <!-- Hero 區塊 -->
    <section class="hero text-white text-center d-flex align-items-center">
      <div class="container">
        <h1 class="display-3 fw-bold">{{ title }}</h1>
        <p class="lead" v-html="subtitle"></p>
        <!-- <a href="#about" class="btn btn-outline-light btn-lg mt-3">了解更多</a> -->
      </div>
    </section>

    <!-- 關於我們 -->
    <!-- <section id="about" class="py-5">
      <div class="container">
        <h2 class="text-center fw-bold mb-4">關於我們</h2>
        <div class="row align-items-center">
          <div class="col-lg-6">
            <p class="lead">{{ aboutText }}</p>
          </div>
          <div class="col-lg-6 text-center">
            <img
              :src="aboutImage"
              alt="關於我們圖片"
              class="img-fluid rounded shadow about-img"
              @click="openImage"
            />
          </div>
        </div>
      </div>
    </section> -->

    <!-- 服務項目 -->
    <section id="services" class="py-5 bg-light">
      <div class="container">
        <h2 class="text-center fw-bold mb-4">服務項目</h2>
        <div class="row row-cols-1 row-cols-md-3 g-4">
          <div v-for="service in services" :key="service" class="col">
            <div class="card h-100 shadow-sm border-0">
              <div class="card-body text-center">
                <h5 class="card-title">{{ service }}</h5>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 聯絡我們 -->
    <section id="contact" class="contact py-5 text-white bg-dark">
      <div class="container text-center">
        <h2 class="fw-bold mb-4">聯絡我們</h2>
        <p class="mb-1">
          <i class="bi bi-envelope-fill"></i> 信箱：{{ contact.email }}
        </p>
        <p class="mb-1">
          <i class="bi bi-telephone-fill"></i> 聯絡電話：{{ contact.phone }}
        </p>
        <p class="mb-1">
          <i class="bi bi-telephone-fill"></i> 聯絡地址：{{ contact.address }}
        </p>
        <p class="mb-1">
          <i class="bi bi-person-fill"></i> 名字：{{ contact.name }}
        </p>
      </div>
    </section>

    <!-- 放大圖片 -->
    <div v-if="isImageOpen" class="overlay" @click="closeImage">
      <img :src="aboutImage" class="large-img" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "公司介紹",
      subtitle:
        "我們成立於2023,主營項目為電子料的排單&現貨銷售(電子料包含主動IC/被動元件/連接器/感測器/模組...等等)<br>" +
        "我們提供的產品適用於各種產業應用領域。<br>" +
        "例如IC測試廠、SMT廠、通訊、電腦、消費電子、醫療、工控、穿戴装置、AI等等。",
      aboutText:
        "我們專注於技術創新，致力於提供高品質的解決方案，幫助企業數位轉型。",
      aboutImage: new URL("@/assets/page1.PNG", import.meta.url).href,
      services: [
        "全球電子料採購供應鏈與銷售服務(主動IC/被動元件/連接器/感測器/模組..)",
        "提供急單/散料/現貨/排單需求",
        "為專案批量試產的客户備齊BOM上電子料",
        "提供客户BOM表優化方案(協尋停產料/替代料)",
        "代銷呆滞存(貨源:代理商/終端客户)",
      ],
      contact: {
        email: "XXXX@example.com",
        phone: "0987-654-321",
        address: "xxx",
      },
      isImageOpen: false,
    };
  },
  methods: {
    openImage() {
      this.isImageOpen = true;
    },
    closeImage() {
      this.isImageOpen = false;
    },
  },
};
</script>

<style>
/* HERO 區塊 */
.hero {
  background: linear-gradient(135deg, #42b983, #2a7f5f);
  min-height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.hero a {
  transition: all 0.3s;
}
.hero a:hover {
  background: white;
  color: #42b983;
}

/* 關於我們圖片 */
.about-img {
  width: 80%;
  max-width: 400px;
  cursor: pointer;
  transition: transform 0.3s;
}
.about-img:hover {
  transform: scale(1.1);
}

/* 服務項目卡片 */
.card {
  transition: transform 0.3s, box-shadow 0.3s;
}
.card:hover {
  transform: scale(1.05);
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.2);
}

/* 放大的圖片 */
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.8);
  display: flex;
  align-items: center;
  justify-content: center;
}
.large-img {
  max-width: 90%;
  max-height: 90%;
  border-radius: 10px;
  box-shadow: 2px 2px 10px rgba(255, 255, 255, 0.5);
}

/* 響應式設計 */
@media (max-width: 768px) {
  .hero h1 {
    font-size: 2.2em;
  }
  .hero p {
    font-size: 1.2em;
  }
}
</style>
