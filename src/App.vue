<template>
  <div class="chuseok-container">
    <!-- 밤하늘의 별들 -->
    <div class="stars"></div>
    <div class="twinkling"></div>

    <!-- 은은하게 빛나는 보름달 -->
    <div class="moon"></div>

    <!-- 메인 콘텐츠 영역 -->
    <div class="content">
      <h1 class="title">풍요로운 한가위 보내세요</h1>
      <p class="subtitle">보름달을 보며 소원을 빌어보세요.</p>

      <!-- 소원 입력 폼 -->
      <form @submit.prevent="addWish" class="wish-form">
        <input
            type="text"
            v-model="newWish"
            placeholder="여기에 소원을 적어보세요..."
            class="wish-input"
        />
        <button type="submit" class="wish-button">소원 빌기</button>
      </form>
    </div>

    <!-- 소원 등불들이 떠다니는 영역 -->
    <div class="wishes-container">
      <div
          v-for="wish in wishes"
          :key="wish.id"
          class="wish-lantern"
          :style="wish.style"
      >
        {{ wish.text }}
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

// 소원 정보를 담을 인터페이스 정의
interface Wish {
  id: number;
  text: string;
  style: {
    left: string;
    animationDuration: string;
    animationDelay: string;
  };
}

// 사용자가 입력할 새로운 소원을 위한 ref
const newWish = ref<string>('');
// 빌었던 소원 목록을 담을 ref 배열
const wishes = ref<Wish[]>([]);

// 소원 추가 함수
const addWish = () => {
  if (newWish.value.trim() === '') return;

  const id = Date.now();
  // 등불의 수평 위치, 애니메이션 속도, 시작 딜레이를 랜덤으로 설정하여 자연스러움을 더합니다.
  const wish: Wish = {
    id,
    text: newWish.value,
    style: {
      left: `${Math.random() * 80 + 10}%`, // 10% ~ 90% 사이
      animationDuration: `${Math.random() * 5 + 8}s`, // 8초 ~ 13초 사이
      animationDelay: `${Math.random() * 2}s`, // 0초 ~ 2초 사이
    },
  };

  wishes.value.push(wish);
  newWish.value = '';

  // 애니메이션이 끝난 후 DOM에서 등불을 제거하여 최적화합니다. (15초 후)
  setTimeout(() => {
    wishes.value = wishes.value.filter(w => w.id !== id);
  }, 15000);
};
</script>

<style scoped>
/* 구글 폰트 'Gowun Dodum' 가져오기 */
@import url('https://fonts.googleapis.com/css2?family=Gowun+Dodum&display=swap');

/* 전체 컨테이너 스타일 */
.chuseok-container {
  font-family: 'Gowun Dodum', sans-serif;
  position: relative;
  width: 100vw;
  height: 100vh;
  background: linear-gradient(to bottom, #020107, #0b0f20, #191c3e);
  overflow: hidden;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: white;
}

/* 콘텐츠 영역 */
.content {
  z-index: 10;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  background: rgba(0, 0, 0, 0.2);
  border-radius: 20px;
  backdrop-filter: blur(5px);
}

.title {
  font-size: clamp(2.5rem, 6vw, 4rem);
  font-weight: 600;
  text-shadow: 0 0 15px rgba(255, 255, 255, 0.7);
  margin: 0;
}

.subtitle {
  font-size: clamp(1rem, 2.5vw, 1.5rem);
  margin: 1rem 0 2rem 0;
  opacity: 0.9;
}

/* 보름달 스타일 */
.moon {
  position: absolute;
  top: 15%;
  left: 50%;
  transform: translateX(-50%);
  width: clamp(150px, 30vw, 300px);
  height: clamp(150px, 30vw, 300px);
  background-color: #f7f3e1;
  border-radius: 50%;
  box-shadow: 0 0 40px #f7f3e1, 0 0 80px #f7f3e1, 0 0 120px #fff, inset -20px -10px 40px #d4c8a9;
  z-index: 1;
  animation: gentle-glow 8s infinite alternate;
}

/* 달이 은은하게 빛나는 애니메이션 */
@keyframes gentle-glow {
  from {
    box-shadow: 0 0 30px #f7f3e1, 0 0 60px #f7f3e1, 0 0 90px #fff, inset -20px -10px 40px #d4c8a9;
  }
  to {
    box-shadow: 0 0 45px #f7f3e1, 0 0 90px #f7f3e1, 0 0 140px #fff, inset -15px -15px 40px #d4c8a9;
  }
}

/* 소원 입력 폼 스타일 */
.wish-form {
  display: flex;
  gap: 10px;
  width: 100%;
  max-width: 500px;
}

.wish-input {
  flex-grow: 1;
  padding: 15px;
  font-size: 1rem;
  font-family: 'Gowun Dodum', sans-serif;
  border: 1px solid rgba(255, 255, 255, 0.3);
  border-radius: 10px;
  background-color: rgba(255, 255, 255, 0.1);
  color: white;
  outline: none;
  transition: all 0.3s ease;
}

.wish-input::placeholder {
  color: rgba(255, 255, 255, 0.6);
}

.wish-input:focus {
  background-color: rgba(255, 255, 255, 0.2);
  border-color: rgba(255, 255, 255, 0.8);
}

.wish-button {
  padding: 15px 25px;
  font-size: 1rem;
  font-family: 'Gowun Dodum', sans-serif;
  font-weight: 600;
  border: none;
  border-radius: 10px;
  background-color: #ffda79;
  color: #333;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(255, 218, 121, 0.3);
}

.wish-button:hover {
  background-color: #ffcb42;
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(255, 218, 121, 0.5);
}

/* 소원 등불 컨테이너 */
.wishes-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none; /* 클릭 방지 */
  z-index: 5;
}

/* 소원 등불 개별 스타일 */
.wish-lantern {
  position: absolute;
  bottom: -100px;
  background: rgba(255, 234, 167, 0.8);
  color: #594500;
  padding: 10px 15px;
  border-radius: 10px;
  box-shadow: 0 0 15px rgba(255, 234, 167, 0.7);
  white-space: nowrap;
  animation: floatUp linear forwards;
}

/* 등불이 떠오르는 애니메이션 */
@keyframes floatUp {
  0% {
    transform: translateY(0) scale(0.8);
    opacity: 0;
  }
  10% {
    transform: translateY(-10vh) scale(1);
    opacity: 1;
  }
  90% {
    opacity: 1;
  }
  100% {
    transform: translateY(-90vh) scale(0.5);
    opacity: 0;
  }
}


/* --- 별 배경 애니메이션 --- */
@keyframes move-twink-back {
  from {background-position:0 0;}
  to {background-position:-10000px 5000px;}
}

.stars, .twinkling {
  position:absolute;
  top:0;
  left:0;
  right:0;
  bottom:0;
  width:100%;
  height:100%;
  display:block;
}

.stars {
  background:#000 url(https://www.script-tutorials.com/demos/360/images/stars.png) repeat top center;
  z-index:0;
}

.twinkling{
  background:transparent url(https://www.script-tutorials.com/demos/360/images/twinkling.png) repeat top center;
  z-index:0;
  animation:move-twink-back 200s linear infinite;
}

</style>

