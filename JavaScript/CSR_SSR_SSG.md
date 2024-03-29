# 클라이언트 사이드 렌더링 (Client Side Rendering, CSR)
![image](https://user-images.githubusercontent.com/79434205/219850916-77727987-524f-4d4b-afd1-7540803a7d7e.png)
- 서버는 자바스크립트 코드가 담긴 링크를 전달하고 **브라우저**에서 링크의 코드를 통해 페이지 렌더링
- 자바스크립트 코드의 다운로드가 끝나야 렌더링이 시작되므로 **초기 페이지 로딩 느림**
- 페이지의 일부가 바뀌면 바뀐 부분만 새로 렌더링 -> **후속 페이지 로딩 빠름**
- 페이지 렌더링이 끝났을 때 자바스크립트도 완전히 로드되어 있으므로 TTV와 TTI가 같음 -> **사용자의 입력을 바로 처리할 수 있음**
- API 요청 및 응답이 느림
- 브라우저에 페이지가 보이기 전에는 코드가 비어 있으므로 크롤링 어려움 -> **SEO에 불리**
- 요청 시에만 서버와 통신하므로 서버의 부담이 적음
- **SPA** (Single Page Application) 및 **동적**인 사이트에 적합
- `React` , `Vue.js` , `Angular` 등의 라이브러리 / 프레임워크 사용

# 서버 사이드 렌더링 (Server Side Rendering, SSR)
![image](https://user-images.githubusercontent.com/79434205/219850997-2dd9d189-2378-4e2f-b0fa-2de12b9664f2.png)
- 전통적인 렌더링 방법
- **서버**가 미리 페이지를 렌더링하여 HTML 파일로 브라우저에 전달하고 브라우저는 보여주기만 함
- **초기 페이지 로딩 빠름**
- 서버에서 페이지를 완전히 그려 전달하기 때문에 페이지의 일부만 바뀌어도 전체를 새로 렌더링 -> **후속 페이지 로딩 느림**
- 새로고침 시 **빈 페이지 깜빡임 현상**이 생길 수 있음
- 페이지는 미리 렌더링되어 있지만 자바스크립트가 로드가 덜 되어 있으므로 TTV와 TTI에 차이가 생김 -> **사용자의 입력을 바로 처리할 수 없음**
- API 요청 및 응답이 빠름
- 브라우저에 페이지가 보이기 전에도 서버에 데이터가 존재하므로 크롤링 가능 -> **SEO에 유리**
- 서버에 부담이 갈 수 있음
- `Next.js` (`React`) , `Nuxt.js` (`Vue.js`), `Angular Universal` (`Angular`) 등의 라이브러리 / 프레임워크 사용

# 정적 사이트 생성 (Static Site Generation, SSG)
![image](https://user-images.githubusercontent.com/79434205/219851010-33159bbd-dea9-435b-bc01-a6185a5a4a06.png)
- **빌드** 시 HTML 파일을 미리 생성 -> 서버에서는 브라우저에 파일을 전달하고 브라우저는 보여주기만 함
- 요청을 그때그때 서버에 보내는 것이 아니라 **요청에 대한 페이지를 미리 만들어 두고 그것을 제공**하기 때문에 로딩 속도가 빠르며 서버의 부담이 적음
- 컨텐츠가 오래되었을 수 있음
- 페이지의 내용을 변경할 때마다 새로 빌드하고 배포해야 함
- 모든 요청을 예측하여 그에 대한 페이지들을 미리 만들어 둬야 함
- 항상 같은 내용이거나 자주 변경되지 않는 컨텐츠를 가진 **정적**인 사이트에 적합
- `Jekyll`, `Gatsby` 등의 프레임워크 사용

## 증분 정적 재생성 (Incremental Static Regeneration, ISR)
![image](https://user-images.githubusercontent.com/79434205/219851038-82e18688-b511-4e68-a5f4-3a1086758cf3.png)
- SSG의 단점을 보완한 방식
- 이미 배포가 된 정적 사이트에 새로운 페이지를 추가하거나 기존 페이지의 컨텐츠를 업데이트할 수 있음
- 오래된 컨텐츠가 보이는 것을 방지하기 위해 **주기적**으로 페이지를 새로 빌드하고 배포
- 아직까진 `Next.js` 에서만 사용 가능

## 참고 사이트
- https://www.freecodecamp.org/news/web-page-rendering-on-the-browser-different-methods/
- https://www.clariontech.com/blog/server-side-rendering-vs.-client-side-rendering
- https://www.growth-rocket.com/blog/a-closer-look-at-client-side-server-side-rendering/
- https://dev.to/pahanperera/visual-explanation-and-comparison-of-csr-ssr-ssg-and-isr-34ea
- https://dev.to/anshuman_bhardwaj/what-the-heck-is-ssg-static-site-generation-explained-with-nextjs-5cja