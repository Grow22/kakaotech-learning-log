## 🗓 이번 주 개요
- 주차: Week 04 (6/8~6/12)
- 키워드: #Next.js #ServerComponent #DataFetching #풀스택

## 📚 이번 주 학습한 것

### 1. <Next.js 라우팅과 렌더링> — 파일 만들면 페이지가 된다

- 핵심 개념:
  - `app/` 폴더 안에 디렉토리 만들고 `page.tsx` 넣으면 그게 곧 URL이 된다.
  - `layout.tsx`는 공통 뼈대, `loading.tsx`는 로딩 UI, `not-found.tsx`는 404 페이지 등 파일 이름이 정해져 있다.
  - 동적 라우팅은 `[변수명]` 디렉토리로 만들면 params로 값을 받아온다.

- 라우팅 구조 예시:
```
app/
├── page.tsx              → /
├── about/page.tsx        → /about
└── products/[productId]/page.tsx  → /products/123
```

- Next.js 15부터 params가 Promise로 바뀜:
```tsx
// 15 이전: 그냥 params.productId로 바로 접근
// 15 이후: await으로 꺼내야 함
const { productId } = await params;
```

### 2. <Data Fetching>

- 핵심 개념:
  - Server Component에서 바로 `await fetch()`로 처리 -> 브라우저 Network 탭에 안 잡힘
  - fetch 여러 개를 순차적으로 하면 시간이 다 합쳐지는데, `Promise.all`로 병렬 처리한다.
  - `Suspense`로 감싸면 각각 완료되는 대로 화면에 먼저 보여줄 수 있음 (Streaming)
  - POST/PUT/DELETE는 `"use server"` 붙인 Server Actions로 처리하는 게 권장 방식
  - Client Component에서 직접 외부 API를 호출하면 CORS 설정이 필요.. Server Component는 서버끼리 통신이라 불필요

- Suspense 패턴:
```tsx
<Suspense fallback={<h2>Loading Posts...</h2>}>
  <PostsList />    {/* 3초 걸려도 다른 데이터 먼저 보여줌 */}
</Suspense>
```

- Next.js를 사용하게 되면 최대한 서버에서 처리하는 게 좋은 거 같다. 클라이언트로 내려갈수록 CORS 같은 귀찮은(?) 부분이 생기는 거 같다.

## 🧱 막혔던 지점 & 해결 과정
- 문제 상황: 솔직히 이번 주 강의를 제대로 못 들었다.. Server Component, Client Component, Server Actions 이런 개념들이 한번에 확 와닿지가 않음
- 시도한 방법: 기말고사가 끝나고 복습할 때 따라갈 수 있도록 강의 자료를 훑으면서 큰 흐름 위주로 정리
- 최종 해결 / 참고 자료: "유저 인터랙션 부분에 대해 Client, 아니면 Server" 이 기준 하나만 잡고 갔다. 세부적인 건 나중에 실습하면서 다시 봐야 할 거 같다.

## 🔁 이번 주 회고 (KPT)
- Keep 유지하고 싶은 습관:
- Problem 아쉬웠던 점:
- Try 다음 주에 시도할 것:

## 🎯 다음 주 목표
- [ ] 기말고사가 수요일 저녁에 끝난다. 이번 주는 강의 일정이 없기 때문에 시험을 마친 후 지금까지 배운 것 중 3, 4주차 강의를 깊이 있게 학습하지 못했는데, 마지막 주차에 도입하기 전 다시 한번 학습을 진행할 예정이다.
