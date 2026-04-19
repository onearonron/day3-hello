# 회사 소개 웹사이트 구현 계획

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 부드럽고 친근한 회사 소개 싱글 페이지 웹사이트를 HTML + 순수 CSS로 구현한다.

**Architecture:** index.html에 모든 섹션(헤더, 서비스 소개, 연락처, 푸터)을 포함하고 style.css에서 CSS 변수와 Flexbox로 스타일을 관리하는 싱글 페이지 구조.

**Tech Stack:** HTML5, 순수 CSS (CSS Variables, Flexbox, 반응형)

---

## 파일 구조

| 파일 | 역할 |
|------|------|
| `index.html` | 메인 페이지. 모든 섹션 포함 |
| `style.css` | 전체 스타일. CSS 변수, 레이아웃, 반응형 |

---

### Task 1: CSS 기반 구조 생성

**Files:**
- Create: `style.css`

- [ ] **Step 1: style.css 생성 — CSS 변수, 리셋, 기본 스타일**

```css
/* CSS 변수 */
:root {
  --color-bg: #FAFAFA;
  --color-card: #FFFFFF;
  --color-primary: #5B8DEF;
  --color-accent: #FF8A80;
  --color-text: #2D3748;
  --color-text-sub: #718096;
  --font-stack: 'Pretendard', -apple-system, 'Segoe UI', sans-serif;
  --radius: 16px;
  --shadow: 0 4px 20px rgba(0, 0, 0, 0.06);
  --max-width: 1200px;
}

/* 리셋 */
*, *::before, *::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* 기본 스타일 */
body {
  font-family: var(--font-stack);
  font-size: 1rem;
  color: var(--color-text);
  background-color: var(--color-bg);
  line-height: 1.6;
}

a {
  text-decoration: none;
  color: inherit;
}

ul {
  list-style: none;
}

img {
  max-width: 100%;
  height: auto;
}

/* 컨테이너 */
.container {
  max-width: var(--max-width);
  margin: 0 auto;
  padding: 0 20px;
}

/* 섹션 공통 */
.section {
  padding: 80px 0;
}

.section-title {
  font-size: 2rem;
  font-weight: 700;
  text-align: center;
  margin-bottom: 48px;
  color: var(--color-text);
}
```

- [ ] **Step 2: 커밋**

```bash
git add style.css
git commit -m "feat: add CSS base with variables, reset, and common styles"
```

---

### Task 2: 헤더 (네비게이션) HTML + CSS

**Files:**
- Create: `index.html` (기존 파일 덮어쓰기)
- Modify: `style.css`

- [ ] **Step 1: index.html에 헤더 HTML 작성**

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="회사 소개 웹사이트">
  <title>우리 회사</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <!-- 헤더 -->
  <header class="header">
    <div class="container header-inner">
      <a href="/" class="logo">우리회사</a>
      <nav>
        <ul class="nav-list">
          <li><a href="#services" class="nav-link">서비스</a></li>
          <li><a href="#contact" class="nav-link">연락처</a></li>
        </ul>
      </nav>
    </div>
  </header>

  <main>
    <!-- 서비스 섹션과 연락처 섹션이 여기에 추가됨 -->
  </main>

  <!-- 푸터가 여기에 추가됨 -->
</body>
</html>
```

- [ ] **Step 2: style.css에 헤더 스타일 추가**

`style.css` 끝에 추가:

```css
/* 헤더 */
.header {
  position: sticky;
  top: 0;
  background-color: var(--color-card);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.04);
  z-index: 100;
}

.header-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 64px;
}

.logo {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--color-primary);
}

.nav-list {
  display: flex;
  gap: 24px;
}

.nav-link {
  font-size: 0.95rem;
  color: var(--color-text-sub);
  transition: color 0.2s;
}

.nav-link:hover {
  color: var(--color-primary);
}
```

- [ ] **Step 3: 브라우저에서 헤더가 sticky로 동작하는지 확인**

`index.html`을 브라우저에서 열어 헤더가 상단에 고정되고, 로고와 네비게이션 링크가 좌우로 배치되었는지 확인.

- [ ] **Step 4: 커밋**

```bash
git add index.html style.css
git commit -m "feat: add header with sticky navigation"
```

---

### Task 3: 서비스 소개 섹션 HTML + CSS

**Files:**
- Modify: `index.html` (main 태그 내부에 추가)
- Modify: `style.css`

- [ ] **Step 1: index.html의 `<main>` 태그 내부에 서비스 섹션 추가**

`<!-- 서비스 섹션과 연락처 섹션이 여기에 추가됨 -->` 주석을 다음으로 교체:

```html
    <!-- 서비스 소개 -->
    <section id="services" class="section">
      <div class="container">
        <h2 class="section-title">우리의 서비스</h2>
        <div class="services-grid">
          <article class="service-card">
            <div class="service-icon">&#x1F4BB;</div>
            <h3 class="service-name">웹 개발</h3>
            <p class="service-desc">고객의 비즈니스에 맞춘 맞춤형 웹 솔루션을 제공합니다.</p>
          </article>
          <article class="service-card">
            <div class="service-icon">&#x1F4F1;</div>
            <h3 class="service-name">모바일 앱</h3>
            <p class="service-desc">iOS와 Android를 아우르는 크로스 플랫폼 앱을 개발합니다.</p>
          </article>
          <article class="service-card">
            <div class="service-icon">&#x1F4CA;</div>
            <h3 class="service-name">데이터 분석</h3>
            <p class="service-desc">데이터 기반 인사이트로 비즈니스 의사결정을 돕습니다.</p>
          </article>
        </div>
      </div>
    </section>
```

- [ ] **Step 2: style.css에 서비스 섹션 스타일 추가**

`style.css` 끝에 추가:

```css
/* 서비스 섹션 */
.services-grid {
  display: flex;
  gap: 24px;
  justify-content: center;
  flex-wrap: wrap;
}

.service-card {
  background-color: var(--color-card);
  border-radius: var(--radius);
  box-shadow: var(--shadow);
  padding: 40px 28px;
  flex: 1 1 280px;
  max-width: 360px;
  text-align: center;
  transition: transform 0.2s, box-shadow 0.2s;
}

.service-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 30px rgba(0, 0, 0, 0.1);
}

.service-icon {
  font-size: 2.5rem;
  margin-bottom: 20px;
}

.service-name {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 12px;
  color: var(--color-text);
}

.service-desc {
  font-size: 0.95rem;
  color: var(--color-text-sub);
  line-height: 1.7;
}
```

- [ ] **Step 3: 브라우저에서 서비스 카드 3개가 가로로 배치되고, 둥근 모서리와 그림자가 적용되었는지 확인**

- [ ] **Step 4: 커밋**

```bash
git add index.html style.css
git commit -m "feat: add services section with card layout"
```

---

### Task 4: 연락처 섹션 HTML + CSS

**Files:**
- Modify: `index.html` (서비스 섹션 뒤에 추가)
- Modify: `style.css`

- [ ] **Step 1: index.html의 서비스 섹션 `</section>` 바로 뒤에 연락처 섹션 추가**

```html
    <!-- 연락처 -->
    <section id="contact" class="section" style="background-color: var(--color-card);">
      <div class="container">
        <h2 class="section-title">연락처</h2>
        <div class="contact-list">
          <div class="contact-item">
            <span class="contact-icon">&#x1F4CD;</span>
            <div>
              <h3 class="contact-label">주소</h3>
              <p class="contact-value">서울특별시 강남구 테헤란로 123</p>
            </div>
          </div>
          <div class="contact-item">
            <span class="contact-icon">&#x1F4DE;</span>
            <div>
              <h3 class="contact-label">전화</h3>
              <p class="contact-value">02-1234-5678</p>
            </div>
          </div>
          <div class="contact-item">
            <span class="contact-icon">&#x2709;&#xFE0F;</span>
            <div>
              <h3 class="contact-label">이메일</h3>
              <p class="contact-value">info@wooricompany.kr</p>
            </div>
          </div>
        </div>
      </div>
    </section>
```

- [ ] **Step 2: style.css에 연락처 섹션 스타일 추가**

`style.css` 끝에 추가:

```css
/* 연락처 섹션 */
.contact-list {
  max-width: 560px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: 28px;
}

.contact-item {
  display: flex;
  align-items: flex-start;
  gap: 16px;
}

.contact-icon {
  font-size: 1.5rem;
  flex-shrink: 0;
  margin-top: 2px;
}

.contact-label {
  font-size: 0.85rem;
  font-weight: 700;
  color: var(--color-primary);
  margin-bottom: 4px;
}

.contact-value {
  font-size: 1rem;
  color: var(--color-text);
}
```

- [ ] **Step 3: 브라우저에서 연락처 정보가 아이콘과 함께 세로로 나열되었는지 확인**

- [ ] **Step 4: 커밋**

```bash
git add index.html style.css
git commit -m "feat: add contact section with address, phone, and email"
```

---

### Task 5: 푸터 HTML + CSS

**Files:**
- Modify: `index.html` (main 태그 뒤에 추가)
- Modify: `style.css`

- [ ] **Step 1: index.html의 `</main>` 태그 뒤에 푸터 추가**

`<!-- 푸터가 여기에 추가됨 -->` 주석을 다음으로 교체:

```html
  <!-- 푸터 -->
  <footer class="footer">
    <div class="container footer-inner">
      <p class="footer-text">&copy; 2026 우리회사. All rights reserved.</p>
    </div>
  </footer>
</body>
</html>
```

- [ ] **Step 2: style.css에 푸터 스타일 추가**

`style.css` 끝에 추가:

```css
/* 푸터 */
.footer {
  background-color: var(--color-text);
  padding: 24px 0;
}

.footer-inner {
  text-align: center;
}

.footer-text {
  font-size: 0.85rem;
  color: #FFFFFF;
}
```

- [ ] **Step 3: 브라우저에서 푸터가 어두운 배경에 흰색 텍스트로 표시되는지 확인**

- [ ] **Step 4: 커밋**

```bash
git add index.html style.css
git commit -m "feat: add footer with copyright"
```

---

### Task 6: 반응형 스타일

**Files:**
- Modify: `style.css`

- [ ] **Step 1: style.css 끝에 반응형 미디어 쿼리 추가**

```css
/* 반응형 */
@media (max-width: 768px) {
  .header-inner {
    height: 56px;
  }

  .nav-list {
    gap: 16px;
  }

  .section {
    padding: 56px 0;
  }

  .section-title {
    font-size: 1.5rem;
    margin-bottom: 32px;
  }

  .services-grid {
    flex-direction: column;
    align-items: center;
  }

  .service-card {
    max-width: 100%;
  }
}
```

- [ ] **Step 2: 브라우저에서 창 크기를 768px 이하로 줄였을 때 서비스 카드가 세로로 스택되고 여백이 줄어드는지 확인**

- [ ] **Step 3: 커밋**

```bash
git add style.css
git commit -m "feat: add responsive styles for mobile"
```
