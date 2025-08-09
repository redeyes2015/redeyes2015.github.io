Basic Info
==========

I am Yu-Jen Chang, or you can just call me Ryan.

Mail: redeyes2015@gmail.com

Technical Skills
--------

* JavaScript, Typescript, Next.js, React (decent)
* Java, Spring Boot, Go (familiar)
* Python (slightly touched)

Experience
==========

LINE Taiwan - Technical Project Manager
----------
Sep 2022 - Present (3 years)

1. Maintain various services and campaign events for TW Sticker OA
    * Coordinate between different groups to realize each service, including
        teams in KR and JP
    * For each service, give man-month estimation, schedule plan, test plan,
      and loading test plan if neccessary
    * Design the architecture and coordinate the integration project with CHT,
      which allows users to subscribe LINE sticker premium plan from CHT
    * Design the architecture and coordinate the "Sticker Review" events every
      year since 2022
        * Backend: Go, Kotlin with Spring Boot; Front-end: Next.js
        * In 2023, gained 2M UU, 7.2M PV
        * In 2024, using Kafka and Playwright to generate snapshots for each
          user, without blocking the web service
    * Coordinate "Chinese New Year" event in 2023, which rewarded users for
      sending stickers from a specific list to his/her friends.
        * Reusing existing code base, and migrate from legacy deploy pipeline
          to Kubernetes
        * Test for heavy traffic (at max: ~1M messages / second)
        * In 2023, gained 3.3M UU, 18M PV
        * In 2024, we extract the core parts and integrate with another
          internal service, so that Biz side could create similar event easily

2. Maintain LINE Fact Checker service, which allow the user to search related
   rumor articles and see verified results from our partners.
    * Backend: Java with Spring Boot; Front-end: Vue 2
    * The web has ~1K Daily PV, ~13K MAU
    * Release search-by-image (OCR) in 2023, search-by-voice (STT) in 2024


3. Making campaign events for TW VOOM since 2023
    * Use code base and infra taken over from the other team, do migration
      due to internal service updates, and update for spec change
    * Backend: Java with Spring Boot; Front-end: Next.js, Nuxt, Gatsby
    * For 2025 CPBL all-start voting event, gained 540K UU, ~4.3M PV

LINE Taiwan - UIT Engineer
----------
Aug 2020 - Aug 2022 (2 years 1 month)

* Be the main front-end maintainer of LINE SPOT where users can find and
  comment on POIs
    * Use Next.js and a self-hosted SSR server
    * Communicate with backend using GraphQL
* The team worked in a Scrum manner


Vivotek
----------

Software Engineer (2011-2016) / Supervisor (2017-2020) (~9years)

- Guide a team of 4 front-end engineers
- Organize biannual in-company conferences to stimulate knowledge
    sharing among web developing colleague company-wide
- Maintain the web portal of VIVOCloud, which lets users access
    network video recorder (NVR) directly from the browser using WebRTC
  * Setup CI infrastructure
  * Migrate the building process to use Webpack and reduce the building time for 40%
  * Guide the team to migrate to VueJS gradually in order to bring in cleaner
      code architecture and developing environment of modern ECMAScript
- Maintain single-page-application style web interface of NVR
- Mentor other engineers to join in web development
- Reduced 30% of the firmware building time by revising Makefiles
    and raising the level of concurrency
- Help hosting several services for the team, such as Jenkins CI and Gitlab

Education
=========

- Master degree from Network Engineering of National Chiao Tung University (2007 ~ 2011)
- Bachelor degree from Computer Science and Information Engineering of National
    Taiwan University (2003 ~ 2007)

Additional Note
===============

- Decent English reading ability
  * TOEIC score: 950 (2013)
  * GEPT High-Intermediate Level Certificated (2017)

Reference
=========

- VIVOCloud: https://www.vivotek.com/zh-TW/products/cloud_service/vivocloud
- LINE Fact Checker: https://fact-checker.line.me/

