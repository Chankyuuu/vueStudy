<template>
  <nav class="navbar sticky-top navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid">
      <!-- Home 항목 항상 표시 -->
      <a class="navbar-brand" href="/">Home</a>

      <!-- 햄버거 메뉴 버튼, 오른쪽 정렬 -->
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

      <!-- 햄버거 메뉴 내부 -->
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav ms-auto">
          <!-- 로그인 전: Login과 Signup 표시 -->
          <li class="nav-item" v-if="!isLoggedIn">
            <a class="nav-link" href="/Login">Login</a>
          </li>
          <li class="nav-item" v-if="!isLoggedIn">
            <a class="nav-link" href="/Signup">Signup</a>
          </li>

          <!-- 로그인 후: MyPage 표시 -->
          <li class="nav-item" v-if="isLoggedIn">
            <a class="nav-link" href="/MyPage">MyPage</a>
          </li>

          <li class="nav-item">
            <a class="nav-link" href="/AvailableRoom">AvailableRooms</a>
          </li>

          <!-- 로그인 후: LogOut 표시 -->
          <li class="nav-item" v-if="isLoggedIn">
            <a class="nav-link" @click="logout" href="#">LogOut</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
    name : 'HeaderComponent',
    data () {
        return {
            isLoggedIn: !!localStorage.getItem('token') // 토큰이 있는지 여부 확인
        };
    },
    methods: {
      logout() {
        localStorage.removeItem('token'); // 토큰 삭제
        this.isLoggedIn = false; // 로그인 상태를 false로 설정
        // 로그아웃 후 추가적인 로직이 필요한 경우 여기에 작성
      }
    }
}
</script>

<style>
    Navbar {
        margin : 0;
        padding : 0;
    }
</style>
