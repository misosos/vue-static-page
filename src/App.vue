<template>
  <main>
    <header>
      <h1>가장 밝은 달이 뜨는 날, 소중한 사람들과 행복을 나누세요.</h1>
    </header>
    <!-- 1) 한가위 소개 -->
    <section>
      <h2>가을의 중심, 한가위를 맞이하다.</h2>
      <p>
        한가위는 음력 8월 15일로, 가을의 한가운데에 있는 가장 큰 날이라는 뜻의 순우리말입니다.
        예로부터 땀 흘려 가꾼 곡식과 과일의 수확을 감사하고, 조상의 차례상에 햇곡식을 올리며
        마음을 전하는 우리의 가장 큰 명절 중 하나입니다.
        넉넉한 인심과 웃음소리가 가득한 한가위의 유래와 의미를 알아보세요.
      </p>
    </section>

    <!-- 2) 음식 소개 -->
    <section>
      <h2>오감을 깨우는 한가위 음식 이야기</h2>
      <p>
        한가위가 다가오면 온 동네에 고소한 기름 냄새와 달콤한 음식 내음이 가득합니다.
        갓 수확한 재료로 정성껏 만든 음식에는 저마다 특별한 의미와 이야기가 담겨 있습니다.
      </p>
    </section>

    <!-- 음식 아이콘 -->
    <section class="icons">
      <figure @click="showFood(songpyeon)">
        <figcaption>송편</figcaption>
        <svg width="40" height="40" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="송편 아이콘">
          <ellipse cx="12" cy="19" rx="9" ry="2.2" fill="#CABBA0" fill-opacity="0.25" stroke="none" />
          <path d="M4 16.5c0 2.6 3.6 3.5 8 3.5s8-.9 8-3.5H4z" fill="#F9E8D2" stroke="#B87C4F" stroke-width="0.6" />
          <path d="M6.2 14.2c2.2 0 4-1.9 4-4.2 0 0-4 .4-4 4.2z" fill="#C7B0E0" stroke="#7E5CA6" stroke-width="0.5" />
          <path d="M10.5 15c2.4 0 4.2-2 4.2-4.4 0 0-4.2.5-4.2 4.4z" fill="#A8D39C" stroke="#5D8F52" stroke-width="0.5" />
          <path d="M14.8 14.2c2.2 0 4-1.9 4-4.2 0 0-4 .4-4 4.2z" fill="#F5A9B8" stroke="#C06A7A" stroke-width="0.5" />
        </svg>
      </figure>

      <figure @click="showFood(tolansoup)">
        <figcaption>토란국</figcaption>
        <svg width="40" height="40" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="토란국 아이콘">
          <path d="M7.5 5c0 1.2.8 1.8.8 3M11.5 5c0 1.2.8 1.8.8 3M15.5 5c0 1.2.8 1.8.8 3" stroke="#C0B59B" stroke-width="0.9" stroke-linecap="round" />
          <ellipse cx="12" cy="13" rx="8" ry="3" fill="#F2EFE6" stroke="#B5A586" stroke-width="0.8" />
          <path d="M4 13c0 3.5 3.6 6 8 6s8-2.5 8-6" fill="#F2EFE6" stroke="#B5A586" stroke-width="0.8" />
        </svg>
      </figure>

      <figure @click="showFood(modumjeon)">
        <figcaption>모둠전</figcaption>
        <svg width="40" height="40" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="모둠전 아이콘">
          <circle cx="12" cy="12" r="9" fill="#F9E8D2" stroke="#B87C4F" stroke-width="0.8" />
          <circle cx="8" cy="10" r="1.8" fill="#F9D14C" stroke="#C29523" stroke-width="0.5" />
          <rect x="10.4" y="9" width="3.5" height="2" rx="0.5" fill="#A5D85C" stroke="#6BA637" stroke-width="0.5" />
          <circle cx="9" cy="14" r="1.6" fill="#D46A4E" stroke="#A2422E" stroke-width="0.5" />
        </svg>
      </figure>
    </section>

    <!-- 음식 정보 표시 -->
    <section id="foodInfo" v-if="selectedFood">
      <h3>{{ selectedFood.title }}</h3>
      <p>{{ selectedFood.description }}</p>
      <p>{{ selectedFood.story }}</p>
    </section>

    <!-- 3) 전통 놀이 소개 -->
    <section>
      <h2>마당을 채우는 웃음소리, 한가위 전통 놀이</h2>
      <p>
        배를 든든히 채웠다면 이제는 신나게 즐길 시간! 보름달 아래 함께 어울리며 즐겼던 우리의 전통 놀이는 명절을 더욱 풍성하게 만들어 줍니다.
      </p>
    </section>

    <!-- 전통 놀이 아이콘 -->
    <section class="icons">
      <!-- 강강술래 -->
      <figure @click="showPlay(ganggangsulla)">
        <figcaption>강강술래</figcaption>
        <svg width="40" height="40" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="강강술래 아이콘">
          <circle cx="12" cy="7" r="3.5" fill="#F9D67A" />
          <circle cx="12" cy="16" r="6" fill="none" stroke="#8C6C4E" stroke-width="1.2" />
          <circle cx="12" cy="10" r="0.8" fill="#8C6C4E" />
          <circle cx="9"  cy="16" r="0.8" fill="#8C6C4E" />
          <circle cx="15" cy="16" r="0.8" fill="#8C6C4E" />
        </svg>
      </figure>

      <!-- 씨름 -->
      <figure @click="showPlay(ssileum)">
        <figcaption>씨름</figcaption>
        <svg width="40" height="40" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="씨름 아이콘">
          <ellipse cx="12" cy="19.2" rx="8.5" ry="1.4" fill="#CABBA0" fill-opacity="0.35"/>
          <path d="M8 10c1.2 0 2-.8 2-2s-.8-2-2-2-2 .8-2 2 .8 2 2 2zm8 0c1.2 0 2-.8 2-2s-.8-2-2-2-2 .8-2 2 .8 2 2 2z" fill="#C06A7A"/>
          <path d="M6.5 15l2.5-2.5L12 14l3-1.5L18 15" fill="none" stroke="#A2422E" stroke-width="1.2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </figure>

      <!-- 줄다리기 -->
      <figure @click="showPlay(juldaligi)">
        <figcaption>줄다리기</figcaption>
        <svg width="40" height="40" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="줄다리기 아이콘">
          <path d="M3 12h18" stroke="#8C6C4E" stroke-width="2" stroke-linecap="round"/>
          <circle cx="6" cy="12" r="1.2" fill="#D46A4E"/>
          <circle cx="18" cy="12" r="1.2" fill="#A5D85C"/>
          <path d="M6 12l3-2m9 2l-3-2" stroke="#8C6C4E" stroke-width="1.2" stroke-linecap="round"/>
        </svg>
      </figure>
    </section>

    <!-- 전통 놀이 정보 표시 -->
    <section id="playInfo" v-if="selectedPlay">
      <h3>{{ selectedPlay.title }}</h3>
      <p>{{ selectedPlay.description }}</p>
      <p>{{ selectedPlay.story }}</p>
    </section>

  </main>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface ChuseokItem {
  title: string
  description: string
  story: string
}

/* 음식 */
const songpyeon: ChuseokItem = {
  title: '보름달을 닮고 싶은 반달의 꿈',
  description: '한 해의 수확에 감사하며 햅쌀로 만드는 대표적인 추석 음식입니다. 솔잎을 깔고 쪄내 은은한 솔 향이 배어있는 것이 특징이죠.',
  story: '송편을 반달 모양으로 빚는 이유는 무엇일까요? 가득 찬 보름달은 곧 기울기 시작하지만, 반달은 앞으로 차오를 희망과 발전을 상징하기 때문입니다. 또한, "송편을 예쁘게 빚으면 예쁜 딸을 낳는다"는 속설이 있어 온 가족이 모여 누가 더 예쁘게 만드나 이야기꽃을 피우기도 했습니다.'
}

const tolansoup: ChuseokItem = {
  title: '땅속의 보물, 가을의 건강을 담다',
  description: '알"이라는 뜻의 토란(土卵)은 가을에 수확하는 대표적인 식재료입니다. 맑게 끓여낸 토란국은 담백하고 부드러워 명절 내내 기름진 음식을 먹은 속을 편안하게 달래줍니다.',
  story: '동그란 토란은 흙 속에서 많은 알뿌리를 틔워 다산과 풍요를 상징했습니다. 조상들은 토란국을 함께 나눠 먹으며 자손 번창과 가정의 화목을 기원했습니다.'
}

const modumjeon: ChuseokItem = {
  title: '풍요로움을 지글지글 부쳐내다',
  description: '동태전, 육원전, 꼬치전, 호박전 등 다채로운 재료로 만드는 전은 명절의 풍성함을 상징합니다.',
  story: '전 부치는 소리가 마치 경쾌한 음악처럼 들려 명절의 흥을 돋우고, 온 가족이 둘러앉아 갓 부친 따끈한 전을 나눠 먹으며 돈독한 정을 나누는 매개체가 되어주었습니다.'
}

/* 놀이 */
const ganggangsulla: ChuseokItem = {
  title : '달빛 아래, 하나 되는 손과 노래',
  description : '여성들이 손을 맞잡고 둥글게 서서 노래에 맞춰 춤을 추는 놀이입니다. 풍요와 다산을 기원하는 의미를 담고 있으며, 유네스코 인류무형문화유산에도 등재되었습니다.',
  story : '임진왜란 당시, 이순신 장군이 왜군에게 우리 군사의 수가 많아 보이게 하려고 부녀자들을 모아 강강술래를 돌게 했다는 이야기는 유명합니다. 단순한 놀이를 넘어, 나라를 지키는 지혜로 활용되기도 한 것이죠.'
}

const ssileum: ChuseokItem = {
  title : '힘과 기술의 대결, 천하장사를 가리다',
  description : '두 사람이 샅바를 잡고 힘과 기술을 겨루어 상대를 넘어뜨리는 경기입니다. 마을의 축제에서 빠질 수 없는 구경거리였죠.',
  story : '씨름 대회의 최종 우승자에게는 \'천하장사\'라는 칭호와 함께 황소를 상품으로 주었습니다. 당시 황소는 집안의 가장 큰 자산이었기에, 씨름은 단순한 운동 경기를 넘어 온 마을 사람들의 관심이 집중되는 큰 이벤트였습니다.'
}

const juldaligi: ChuseokItem = {
  title : '풍년을 기원하는 공동체의 함성',
  description : '여러 사람이 양편으로 나뉘어 굵은 줄을 마주 당겨 승부를 겨루는 놀이입니다. 마을 사람들의 화합과 단결을 도모하고, 풍년을 기원하는 농경 의식의 하나였습니다.',
  story : '줄다리기는 단순한 힘겨루기가 아니었습니다. 암줄과 수줄을 결합하는 행위를 통해 암수의 결합, 즉 농사의 풍요를 기원하는 깊은 의미가 담겨 있었습니다. 이기는 쪽 마을에 풍년이 든다는 믿음이 있어 모두가 한마음으로 줄을 당겼습니다.'
}

const selectedFood = ref<ChuseokItem | null>(null)
const showFood = (item: ChuseokItem) => {
  selectedFood.value = item
  selectedPlay.value = null // 놀이 정보 닫기
}

const selectedPlay = ref<ChuseokItem | null>(null)
const showPlay = (item: ChuseokItem) => {
  selectedPlay.value = item
  selectedFood.value = null // 음식 정보 닫기
}
</script>

<style>

:root{
  --fg-strong: #fffdf7;         /* 제목용 흰빛 아이보리 */
  --fg-body:   #fff4de;         /* 본문 텍스트 */
  --glass:     rgba(255,255,255,.14);
  --glass-dark:rgba(20,20,20,.55);
  --hero-space: clamp(140px, 22vh, 260px); /* 헤더가 절대 안 잘리도록 위 여백 */
}

html, body{
  margin:0; padding:0;
  min-height: 100dvh;
  background:#0d2131 url('assets/bg.png') no-repeat center/cover fixed;
  font-family:'Pretendard', system-ui, -apple-system, Segoe UI, Roboto, sans-serif;
  color:var(--fg-body);
}

main{
  position:relative; z-index:1;
  max-width:1100px; margin:0 auto;
  padding-inline:2rem;
  padding-block-start: calc(env(safe-area-inset-top, 0px) + var(--hero-space)) !important;
  padding-block-end:4rem;
}
section{ margin-top:2.2rem; line-height:1.85; text-align:center; }
section:first-of-type{ margin-top:1.2rem; }

header::before{
  content:""; position:absolute; inset:.15rem -1rem; z-index:-1;
  background: rgba(187, 187, 187, 0.35);          /* 과하지 않게 */
  border-radius:16px;
}
h1{
  margin:0; padding:.9rem 1.25rem;
  font-size: clamp(1.8rem, 3vw + .6rem, 3rem);
  color: #ffffff;
  text-shadow:
      0 0 18px rgba(56, 56, 56, 0.85),
      0 0 8px rgba(4, 11, 28, 0.6),
      0 2px 4px rgba(80, 80, 80, 0.9);
}

h2, h3{
  color:#fff7e8;
  text-shadow: 0 1px 4px rgba(0,0,0,.4), 0 0 10px rgba(0, 0, 0, 0.35);
}
p{
  max-width:720px; margin:.5rem auto 0;
  color: var(--fg-body);
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.45);
}

.icons{
  display:flex; justify-content:center; align-items:center;
  gap:2.2rem; flex-wrap:wrap; margin-top:1.6rem;
}
figure{
  width:112px; padding:.9rem 1rem;
  display:flex; flex-direction:column; align-items:center; text-align:center;
  border-radius:14px; backdrop-filter:blur(6px);
  background:var(--glass);
  box-shadow:0 6px 14px rgba(0,0,0,.30);
  cursor:pointer;
  transition:transform .22s ease, box-shadow .22s ease, background-color .22s ease, opacity .22s ease;
}
figure:hover{ transform:translateY(-2px) scale(1.04); background:rgba(255,255,255,.20); box-shadow:0 10px 22px rgba(0,0,0,.40); }
figure svg{ filter:drop-shadow(0 2px 6px rgba(0,0,0,.35)); }
figcaption{ margin-top:.55rem; font-size:.98rem; font-weight:600; color:#fff; text-shadow:0 1px 4px rgba(0,0,0,.7); }

#foodInfo, #playInfo{
  width:84%; max-width:720px; margin:2.4rem auto 0;
  background: rgba(255,255,255,.18);
  color:#fffaf2;
  backdrop-filter: blur(12px);
  border: 1px solid rgba(255,255,255,.18);
  border-radius:18px;
  padding:1.8rem 1.6rem;
  box-shadow:0 10px 24px rgba(0,0,0,.35);
  animation:fadeIn .35s ease;
}
@keyframes fadeIn{ from{opacity:0; transform:translateY(8px);} to{opacity:1; transform:translateY(0);} }

@media (prefers-color-scheme: dark){
  #foodInfo, #playInfo{ background: rgba(255,255,255,.16); }
  figure{ background: rgba(255,255,255,.12); }
  figure:hover{ background: rgba(255,255,255,.20); }
}

@media (max-width: 820px){
  main{ padding-inline:1.4rem; }
  figure{ width:98px; }
}
@media (max-width: 560px){
  :root{ --hero-space: clamp(110px, 18vh, 160px); }
  header::before{ inset:.15rem -.6rem; }
  h1{ font-size: clamp(1.5rem, 4.2vw + .5rem, 2rem); padding:.75rem .9rem; }
  p{ max-width:90%; font-size:.95rem; }
  .icons{ gap:1.4rem; }
  figure{ width:88px; padding:.7rem .8rem; }
}
</style>