<!-- Header -->
<div align="center">

![header](https://capsule-render.vercel.app/api?type=waving&color=0:0f172a,50:1e3a5f,100:0f172a&height=200&section=header&text=Yongseong%20Kim&fontSize=48&fontColor=f8fafc&animation=fadeIn&fontAlignY=40&desc=Backend%20Developer&descAlignY=62&descColor=94a3b8)

</div>

<!-- Typing animation -->
<div align="center">

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&size=16&duration=3000&pause=1000&color=60A5FA&center=true&vCenter=true&multiline=true&width=500&height=70&lines=🌱+Java+%26+Spring+Boot+Backend+Developer;기본에+충실하고%2C+함께+만드는+개발을+좋아합니다)](https://git.io/typing-svg)

</div>

---

## 🙋‍♂️ About Me

```java
@Component
public class YongseongKim {

    private final String name     = "김용성 (Yongseong Kim)";
    private final String role     = "Backend Developer (신입)";
    private final String school   = "성결대학교";
    private final String[] stack  = {"Java", "Spring Boot", "MySQL", "JPA"};
    private final String motto    = "기본에 충실하게, 안정적으로 동작하는 구조를 고민합니다.";

    public String getContact() {
        return "wlehrja5753@gmail.com";
    }
}
```

---

## 🛠 Tech Stack

**Backend**

![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Spring](https://img.shields.io/badge/Spring-6DB33F?style=flat-square&logo=spring&logoColor=white)
![JPA](https://img.shields.io/badge/JPA-59666C?style=flat-square&logo=hibernate&logoColor=white)

**Database**

![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)

**Frontend** *(협업용)*

![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)

**Tools**

![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)
![IntelliJ IDEA](https://img.shields.io/badge/IntelliJ-000000?style=flat-square&logo=intellijidea&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?style=flat-square&logo=firebase&logoColor=black)

---

## 📂 Projects

### 🏛 우리동네 국회의원 (OurAssembly)
> 위치 기반으로 지역구 국회의원 정보를 확인하고, 관심 의원을 팔로우하면 관련 뉴스를 푸시 알림으로 받을 수 있는 시민 참여 서비스

| 항목 | 내용 |
|------|------|
| **기간** | 2024 |
| **역할** | 백엔드 개발 (FCM, 팔로우, 스케줄러) |
| **스택** | Spring Boot · MySQL · Firebase FCM · JWT · React/Vite |

**주요 구현**
- 🔔 **FCM 푸시 알림**: `MulticastMessage` 배치 발송(500건 단위), 실패 토큰 자동 정리
- 📡 **Spring Scheduler**: 매일 오전 9시 공공데이터 API 크롤링 → 팔로워에게 뉴스 알림 자동 발송
- 👥 **팔로우 시스템**: JWT 기반 팔로우/언팔로우, `FollowRepository` JPQL 쿼리 설계
- 🔐 **JWT 인증**: 로그인 시 FCM 토큰 저장, 인증 필터 구성

<details>
<summary>FCM 핵심 로직 보기</summary>

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

        BatchResponse response = FirebaseMessaging.getInstance().sendEachForMulticast(message);
        cleanUpInvalidTokens(batch, response); // 실패 토큰 정리
    }
}
```

</details>

<br/>

### 🌿 PlantCare
> 식물 등록, 성장 기록, 센서 데이터 확인 기능을 제공하는 식물 관리 팀 프로젝트

| 항목 | 내용 |
|------|------|
| **역할** | 백엔드 API 개발, DB 설계 |
| **스택** | Spring Boot · MySQL |

**주요 구현**
- 식물 등록 및 성장 기록 REST API 설계
- 센서 데이터 연동 구조 구현
- DB 모델링 및 데이터 처리

---

## 📈 GitHub Stats

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=ys06o&show_icons=true&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=60a5fa&icon_color=60a5fa&text_color=94a3b8)
&nbsp;
![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=ys06o&layout=compact&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=60a5fa&text_color=94a3b8)

</div>

<div align="center">

![Streak](https://streak-stats.demolab.com?user=ys06o&theme=github-dark-blue&hide_border=true&background=0d1117&ring=60a5fa&fire=60a5fa&currStreakLabel=94a3b8&sideLabels=94a3b8&dates=4b5563)

</div>

---

## 📚 현재 공부 중

- `REST API` 설계와 예외 처리 구조
- `MySQL` 기반 데이터 모델링
- 협업을 고려한 `Git` / `GitHub` 사용
- 유지보수하기 좋은 코드 구조 고민

---

## 📬 Contact

<div align="center">

[![Gmail](https://img.shields.io/badge/wlehrja5753@gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:wlehrja5753@gmail.com)

</div>

<!-- Footer -->
<div align="center">

![footer](https://capsule-render.vercel.app/api?type=waving&color=0:0f172a,50:1e3a5f,100:0f172a&height=120&section=footer)

</div>
