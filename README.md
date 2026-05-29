<!-- Header Wave -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:1a3a5c,100:0d1117&height=220&section=header&text=Yongseong%20Kim&fontSize=52&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Backend%20Developer&descSize=20&descAlignY=58&descColor=60a5fa" />
</div>

<!-- Typing Animation -->
<div align="center">
  <a href="https://github.com/ys06o">
    <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=500&size=18&duration=2800&pause=1200&color=60A5FA&center=true&vCenter=true&multiline=true&width=560&height=64&lines=☕+Java+%26+Spring+Boot+Backend+Developer;🔧+기본에+충실하게%2C+함께+만드는+개발" alt="Typing SVG" />
  </a>
</div>

<br/>

<!-- About Me -->
## 🧑‍💻 About Me

```yaml
name     : 김용성 (Yongseong Kim)
role     : Backend Developer (신입)
school   : 성결대학교 (Sungkyul University)
stack    : [ Java, Spring Boot, JPA, MySQL ]
interests: [ REST API 설계, 안정적인 서버 구조, 협업 ]
motto    : "기본에 충실하게, 안정적으로 동작하는 구조를 고민합니다."
contact  : wlehrja5753@gmail.com
```

<br/>

---

## 🛠 Tech Stack

<div align="center">

  **Backend**<br/>
  <img src="https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=openjdk&logoColor=white"/>
  <img src="https://img.shields.io/badge/Spring_Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white"/>
  <img src="https://img.shields.io/badge/Spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white"/>
  <img src="https://img.shields.io/badge/JPA-59666C?style=for-the-badge&logo=hibernate&logoColor=white"/>

  <br/><br/>

  **Database**<br/>
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/>

  <br/><br/>

  **Frontend** *(협업)*<br/>
  <img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black"/>
  <img src="https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white"/>

  <br/><br/>

  **Tools & Infra**<br/>
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white"/>
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>
  <img src="https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black"/>
  <img src="https://img.shields.io/badge/IntelliJ_IDEA-000000?style=for-the-badge&logo=intellijidea&logoColor=white"/>

</div>

<br/>

---

## 📂 Projects

### 🏛 우리동네 국회의원 · OurAssembly

> 위치 기반으로 지역구 국회의원 정보를 확인하고,  
> 관심 의원을 팔로우하면 관련 뉴스를 **푸시 알림**으로 받는 시민 참여 서비스

| | |
|---|---|
| **기간** | 2024 |
| **역할** | Backend (FCM · 팔로우 시스템 · 스케줄러) |
| **스택** | `Spring Boot` `MySQL` `Firebase FCM` `JWT` `React` `Vite` |

**핵심 구현**

- 🔔 **FCM 푸시 알림** — `MulticastMessage` 500건 단위 배치 발송, 실패 토큰 자동 정리
- ⏰ **Spring Scheduler** — 매일 오전 9시 공공데이터 API 크롤링 → 팔로워 알림 자동 발송
- 👥 **팔로우 시스템** — JWT 기반 팔로우/언팔로우, `FollowRepository` JPQL 설계
- 🔐 **JWT 인증** — 로그인 시 FCM 토큰 저장 및 인증 필터 구성

<details>
<summary>📎 FCM 핵심 코드 보기</summary>

```java
// 관심사 기반 팔로워에게 MulticastMessage 배치 발송
public void sendToFollowers(String topic, String title, String body) {
    List<String> tokens = followRepository.findFcmTokensByTopic(topic);

    for (int i = 0; i < tokens.size(); i += 500) {
        List<String> batch = tokens.subList(i, Math.min(i + 500, tokens.size()));

        MulticastMessage message = MulticastMessage.builder()
            .putData("title", title)
            .putData("body", body)
            .addAllTokens(batch)
            .build();

        BatchResponse response = FirebaseMessaging.getInstance()
            .sendEachForMulticast(message);

        cleanUpInvalidTokens(batch, response); // 실패 토큰 정리
    }
}
```

</details>

<br/>

### 🌿 PlantCare

> 식물 등록, 성장 기록, 센서 데이터 확인 기능을 갖춘 식물 관리 팀 프로젝트

| | |
|---|---|
| **역할** | 백엔드 API 개발, DB 설계 |
| **스택** | `Spring Boot` `MySQL` |

- 식물 등록 및 성장 기록 REST API 설계
- 센서 데이터 연동 구조 구현 및 DB 모델링

<br/>

---

## 📈 GitHub Stats

<div align="center">
  <img height="170" src="https://github-readme-stats.vercel.app/api?username=ys06o&show_icons=true&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=60a5fa&icon_color=60a5fa&text_color=94a3b8&rank_icon=github" />
  &nbsp;
  <img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=ys06o&layout=compact&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=60a5fa&text_color=94a3b8&langs_count=6" />
</div>

<br/>

<div align="center">
  <img src="https://streak-stats.demolab.com?user=ys06o&theme=github-dark-blue&hide_border=true&background=0d1117&ring=60a5fa&fire=60a5fa&currStreakLabel=60a5fa&sideLabels=94a3b8&dates=4b5563&currStreakNum=ffffff&sideNums=ffffff" />
</div>

<br/>

<div align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=ys06o&theme=github-compact&bg_color=0d1117&color=60a5fa&line=1d4ed8&point=60a5fa&area=true&hide_border=true" />
</div>

<br/>

---

## 🏆 Trophy

<div align="center">
  <img src="https://github-profile-trophy.vercel.app/?username=ys06o&theme=onestar&no-frame=true&no-bg=true&column=6&margin-w=4" />
</div>

<br/>

---

## 🐍 Contribution Snake

<div align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/ys06o/ys06o/output/github-snake-dark.svg" />
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/ys06o/ys06o/output/github-snake.svg" />
    <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/ys06o/ys06o/output/github-snake.svg" />
  </picture>
</div>

> ⚠️ Snake를 표시하려면 아래 GitHub Actions 워크플로우 세팅이 필요합니다.  
> `.github/workflows/snake.yml` 파일을 만들고 아래 내용을 붙여넣으세요.

<details>
<summary>📎 snake.yml 워크플로우 보기</summary>

```yaml
name: Generate Snake Animation

on:
  schedule:
    - cron: "0 0 * * *"   # 매일 자정 자동 실행
  workflow_dispatch:       # 수동 실행 가능

jobs:
  generate:
    runs-on: ubuntu-latest
    permissions:
      contents: write

    steps:
      - uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark

      - uses: crazy-max/ghaction-github-pages@v3
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

</details>

<br/>

---

## 📚 Currently Studying

```
📌 REST API 설계와 예외 처리 구조
📌 MySQL 기반 데이터 모델링
📌 협업을 고려한 Git / GitHub 활용
📌 유지보수하기 좋은 코드 구조 고민
```

<br/>

---

## 📬 Contact

<div align="center">
  <a href="mailto:wlehrja5753@gmail.com">
    <img src="https://img.shields.io/badge/Gmail-wlehrja5753@gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white"/>
  </a>
</div>

<!-- Footer Wave -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:1a3a5c,100:0d1117&height=120&section=footer" />
</div>
