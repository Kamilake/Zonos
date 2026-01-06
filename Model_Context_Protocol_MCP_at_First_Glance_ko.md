# 모델 컨텍스트 프로토콜(MCP) 첫인상: MCP 서버의 보안성과 유지보수성 연구

**저자:** Mohammed Mehedi Hasan; Hao Li; Emad Fallahzadeh; Gopi Krishnan Rajbahadur; Bram Adams; Ahmed E. Hassan

**출처:** arXiv:2506.13538v4 (2025년 6월 20일)

GPT-4와 같은 파운데이션 모델(FM)은 점점 ... 전통적인 분석 및 리팩터링 관행의 가치를 재확인하게 만들고 있다.

## CCS 개념

• 소프트웨어 및 소프트웨어 공학 → 경험적 소프트웨어 검증.

## 추가 핵심어 및 구문

모델 컨텍스트 프로토콜, MCP, 보안, 코드 스멜, 소프트웨어 버그, 유지보수성

## ACM 참고 형식

Mohammed Mehedi Hasan, Hao Li, Emad Fallahzadeh, Gopi Krishnan Rajbahadur, Bram Adams, and Ahmed E. Hassan. TBD. Model Context Protocol (MCP) at First Glance: Studying the Security and Maintainability of MCP Servers. ACM Trans. Softw. Eng. Methodol., ( TBD), 38 pages. https://doi.org/10.1145/nnnnnnn.nnnnnnn Authors’ Contact Information: Mohammed Mehedi Hasan, mohammedmehedi.hasan@queensu.ca, Queen’s University, Kingston, ON, Canada; Hao Li, Queen’s University, Kingston, ON, Canada, hao.li@queensu.ca; Emad Fallahzadeh, Queen’s University, Kingston, ON, Canada, emad.fallahzadeh@queensu.ca; Gopi Krishnan Rajbahadur, Queen’s University, School of Computing, Kingston, Ontario, Canada, grajbahadur@acm.org; Bram Adams, Queen’s University, Kingston, ON, Canada, bram.adams@queensu.ca; Ahmed E. Hassan, Queen’s University, Kingston, ON, Canada, ahmed@cs.queensu.ca. Permission to make digital or hard copies of all or part of this work for personal or classroom use is granted without fee provided that copies are not made or distributed for profit or commercial advantage and that copies bear this notice and the full citation on the first page. Copyrights for components of this work owned by others than ACM must be honored. Abstracting with credit is permitted. To copy otherwise, or republish, to post on servers or to redistribute to lists, requires prior specific permission and/or a fee. Request permissions from permissions@acm.org. © TBD ACM. ACM 1557-7392/TBD/0-ART https://doi.org/10.1145/nnnnnnn.nnnnnnn

서론 파운데이션 모델(FM)(예: GPT-4 [99], ...)이 ... 중요한 소프트웨어 차원(예: 건강성, 지속가능성,

1https://github.com/Azure/azure-mcp

보안과 유지보수성. 특히, ... 주당 평균 5.5회 커밋(전통 소프트웨어 2.5회/주 대비) ... 강력한 MCP 특화 취약점 탐지 기법과 도구가 필요함을 시사한다.
RQ-2: MCP 서버에는 어느 정도의 유지보수성 이슈가 존재하는가... 코드 수준 버그. 본 논문의 주요 기여는 다음과 같다:

(1) 데이터셋: 우리는 오픈소스 MCP 서버의 첫 큐레이션 데이터셋[57]을 제시한다. 수집은
공식 목록과 GitHub 마이닝 저장소 모두에서 이루어졌으며, MCP 후속 연구를 위한 기반 자산이 될 수 있다.

(2) 분석 프레임워크 및 베이스라인: 우리는 하이브리드 분석 프레임워크를 개발·적용한다.
이는 일반 목적 정적 분석 도구(예: SonarQ...)를 결합하여 ... 새로운 오픈소스 소프트웨어 도메인의 경험적 연구에 활용 가능한 베이스라인을 제공한다.

(3) 시사점:
• 우리는 MCP 생태계를 대상으로 한 첫 대규모 경험적 연구를 수행하며, 건강성,
지속가능성, 보안, 유지보수성을 살핀다. ... 예: MCP 서버의 66%에 코드 스멜, 14.4%에 버그가 있다.

• MCP 특화 취약점은 전통적 취약점보다 더 흔할 수 있지만,
전통적 도구와 새로 등장한 MCP 특화 도구 모두에서 탐지가 어렵다 ... MCP 특화 취약점 탐지·완화 기법이 필요하다.

• MCP 서버의 유지보수성 문제(예: 코드 스멜, 버그)는 ...와 밀접히 관련되어
기존 소프트웨어 공학 지식이 ... FM을 현실에서 통합하는 애플리케이션 개발자에게 도움이 됨을 시사한다.

Search Tool  AI 애플리케이션  Framework-A  Stripe Tool  Foundation...(d) MCP: 프레임워크로부터 도구·프롬프트·리소스를 분리

**그림 1.** FM 기반 AI 애플리케이션 개발을 동기부여하는 예. (a)에서 Alex는 AI 애플리케이션을 개발했고

![Fig. 1 (page 5)](assets/pages/page_05.png)

framework A를 사용해 별도의 커스텀 도구가 필요 없었다. (b)에서는 ...—제품 탐색부터 결제까지—를 만들고 싶지만 곧 다음을 깨닫는다:

(1) 제품 검색에는 전용 검색 메커니즘(예: 웹 검색 API)이 필요하다.
(2) 제품 추천에는 발견된 제품을 종합·순위화할 LLM이 필요하다.
(3) 결제 수집에는 결제 게이트웨이(예: Stripe 연동)가 필요하다.
Alex는 도구가 필요하다는 것을 배웠고, 도구는 자체 포함된 구현체이다... 다양한 커뮤니티에서 MCP 서버가 급증하면서, 이제 다음을 어떻게 결정해야 할지 혼란스러워졌다:

(1) 핵심 AI 애플리케이션에 쓰기에 가장 건강하고 지속가능한 MCP 서버는 무엇인가?
(RQ-0)

(2) 민감한 고객 데이터(예: 자격 증명, 신용카드 정보)를 보호하기 위해 MCP 서버의 보안을 어떻게 검증할 수 있는가? (RQ-1)

(3) 버그나 스멜이 있을 가능성 등 MCP 서버의 유지보수 품질을 어떻게 평가할 수 있는가?

버그 또는 스멜? (RQ-2) 본 연구에서는 정량·정성 분석을 통해 이러한 과제를 탐구한다.
배경 3.1 FM 기반 AI 애플리케이션을 위한 도구 환경 3.... 개발 오버헤드를 크게 낮추고 도입을 가속한다.

FM 기반 AI 애플리케이션 생태계 전반에서 새로운 도구의 채택을 ... REFLECTION transport: stdio  transport: stdio  외부 서비스

**그림 2.** MCP 클라이언트-서버 아키텍처의 고수준 개요

![Fig. 2 (page 8)](assets/pages/page_08.png)

3.2.1 MCP 워크플로. 전형적인 MCP 워크플로에서 AI 애플리케이션은 ... 데스크톱 애플리케이션부터 클라우드 기반 서버 배포까지 사용된다.

3.2.5 MCP 클라이언트. MCP 클라이언트는 ... 인기 있는 전이(간접) 의존성 체인에 포함될 때 특히 중요하다 [117].

2https://glama.ai/mcp/servers/@stripe/agent-toolkit

3https://glama.ai/mcp/servers/@atharvagupta2003/mcp-stripe
신흥 도메인으로서, 우리는 MCP 서버를 ... 연구가 증가하는 것도 관찰했다. 연구 설계 개요는 그림 3에 제시한다.

GitHub에서 MCP SDK import 마이닝  마이닝 수: 1,556  전체 수: 1,899  저장소 메트릭 필터링/저장 수: 583

### 5.1 데이터 수집

GitHub에서 클론  SonarQube로 정적 분석  ...  고유 이슈  LLM Jury  GPT-4o  Claude 3.7 Sonnet  Gemini 2.5 Pro

### 5.2 소스 코드 정적 분석

### 5.3 이슈 클러스터링

LLM-Jury가 식별한 이슈 패턴 검증

### 5.4 비교 가능한 베이스라인 찾기

검색 문자열 준비  검색 건수: 135  Google Scholar 검색  베이스라인 추출

**그림 3.** 연구 설계 개요.

![Fig. 3 (page 11)](assets/pages/page_11.png)

5.1 데이터 수집 5.1.1 Anthropic 공식 ... Anthropic은 MCP 서버를 두 가지 주요 범주로 분류한다:

• 공식 통합: 조직이 유지·관리하는 MCP 서버... 예를 들어, AWS MCP 서버5는
Amazon의 AWS Labs에서 유지·관리한다.

• 커뮤니티 서버: 독립적인 커뮤니티 구성원 또는 기여자가 다양한 사용 사례를 위해 개발·유지하는 MCP 서버.
그중 한 예... 저장소 이름과 GitHub URL을 Elasticsearch 데이터베이스에 저장했다.

4https://github.com/modelcontextprotocol/servers?tab=readme-ov-file

5https://github.com/awslabs/mcp

6https://github.com/66julienmartin/MCP-server-Deepseek_R1

**표 1.** 프로그래밍 언어별 통합 유형 분포

```text
Language
Official
Community
Mined
Total Count
Python
JavaScript
TypeScript
Others
Total
```

5.1.2 SDK import를 위한 GitHub 마이닝. 우리는 ... SonarQube [29] (널리 사용되는 오픈소스 도구)로 정적 분석을 수행했다.

7https://docs.github.com/en/rest/search/search?apiVersion=2022-11-28#search-code

FindBugs [43], PMD [102]에 비해 SonarQube는 더 폭넓은 ... MITRE CWE Top

## 25 [91], OWASP Top 10 [7], PCI DSS [96]. 취약점 외에도 SonarQube는 널리 사용되며

코드 스멜 등 유지보수성 우려를 식별하는 데도 쓰인다 ... SonarQube는 다섯 가지 주요 심각도 유형 [127]을 사용한다:

(1) Blocker: 크래시, 보안 침해 등 심각한 의도치 않은 결과를 유발할 수 있어 즉시 해결이 필요한 문제.
보안 침해를 포함하며, 즉각적인 해결이 필요하다.
(2) Critical: 애플리케이션에 치명적 영향을 주는 이슈로, 가능한 한 빨리 수정해야 한다.
가능한 한 빨리.

(3) Major: 애플리케이션에 큰 영향을 주는 이슈.
(4) Minor: 애플리케이션에 비교적 작은 영향을 주는 이슈.
(5) Info: 애플리케이션에 예상되는 영향이 없다. 정보 제공 목적만 해당.
우리는 이슈 ... 기존 연구 [79]에 따라 메타데이터(예: 이슈 ... )를 포함해 이슈 인스턴스를 추출한다. 또한 LLM-Jury를 사용하는데, 이러한 유형의 시스템은 ...

8https://docs.sonarsource.com/sonarqube-server/10.4/extension-guide/web-api/

9https://rules.sonarsource.com/

**표 2.** 네 가지 검토 항목에 대해 비교 가능한 베이스라인을 찾기 위한 문헌조사 검색 전략:

```text
health and sustainability metrics, security vulnerabilities, code smells, and bugs. For each item, we crafted
```

핵심 변수를 활용해 구조화된 검색 문자열을 만들고, 체계적 ... Google Scholar에서 문헌 검색을 수행했으며, 표 2에 요약했다.

각 검색에서는 주요 변수를(예: 메트릭 이름, 버그 패턴, 도메인) 변형하여 다양한 조합을 만들었고, 그 결과

## 메트릭은 96회, 취약점은 5회, 코드 스멜은 4회, 버그는 30회 검색을 수행했다. 우리는 체계적으로

각 검색에서 상위 50개 결과를 검토하고, ... OSS 및 ML 베이스라인과 비교한 커뮤니티 메트릭/유사 연구를 포함했다는 점을 시사한다.

**표 3.** 세 가지 연구 질문에 대해 비교 가능한 베이스라인을 도출하기 위해 검토한 40편의 연구 요약

```text
questions, ordered by publication year.
RQ
Study
Purpose
RQ-0
Herraiz et al., 2009 [60]
An empirical study on OSS analyzing their evolution
Kerzazi et al., 2014 [69]
A study to measure the impact of build breakage
Borges et al., 2016 [25]
A study on the popularity of software systems hosted at GitHub
Hilton et al., 2016 [61]
Understanding the usage of CI systems
Coelho et al., 2017 [39]
Reasons Behind the Failure of Modern Open Source Projects
Baltes et al., 2018 [19]
A study on the Influence of CI on Commit Activity
Zou et al., 2019 [155]
An empirical study on branch usage in GitHub projects
Bao et al., 2019 [20]
Predicting newcomers’ transition to long-term contributors
Chen et al., 2020 [33]
A study on characterizing real-world build times
Goggins et al., 2021 [53]
Exploring the metrics related to health and sustainability
Moid et al., 2021 [90]
A study to predict repository stars using smart models
Ait et al., 2022 [4]
Assessing survival rate of GitHub projects
Xiao et al., 2023 [146]
Exploring the long-term project sustainability on GitHub
He et al., 2023 [59]
A study to evaluate the effectiveness of Dependabot
Idowu et al., 2024 [64]
A study on OSS ML projects, focusing on evolution
Lai et al., 2024 [72]
Comparison between ML and non-ML issues in OSS AI projects
Bernardo et al., 2024 [22]
Exploring CI adoption practices in ML projects
RQ-1
Rahman et al., 2019 [107]
An empirical study of security smells in IaC scripts
Wist et al., 2021 [143]
An empirical study on vulnerabilities in Docker Hub images
Ruihonen et al., 2021 [113]
A security-oriented static analysis of Python packages in PyPI
Latendresse et al., 2022 [74]
Analyzing security risks of JavaScript dependencies in NPM
Zerouali et al., 2022 [153]
A study on vulnerabilities affecting NPM and RubyGems packages
Alfadel et al., 2023 [6]
An analysis of security vulnerabilities in Python packages
RQ-2
Ayewah et al., 2007 [18]
A study of warnings found by FindBugs in Java programs
Yamashita et al., 2012 [150]
How well code smells reflect factors affecting maintainability
Park et al., 2015 [101]
An analysis of HTML and CSS syntax errors
Tufano et al., 2015 [134]
Understanding when and why bad smells are introduced
Saboury et al., 2017 [116]
An empirical study of code smells in JavaScript projects
Rice et al., 2017 [110]
An algorithm to detect method argument selection bugs
Castagna et al., 2017 [30]
A type system for functional languages to support gradual typing
Chen et al., 2018 [34]
An empirical study on how defects impact maintainability
Palomba et al., 2018 [100]
Relationship between code smells and fault/change proneness
Wang et al., 2019 [140]
An approach to automatically repair buggy loops
Munoz et al., 2020 [94]
Validating cognitive complexity’s impact on code understandability
Amit et al., 2021 [9]
Measuring the effort invested in bug fixing
Van Oort et al., 2021 [136]
Studying the prevalence of code smells in ML projects
Siddiq et al., 2022 [121]
A study of code smells in transformer-based code generation
Gupta et al., 2023 [55]
A severity assessment of Python code smells
Arteca et al., 2023 [15]
A study on detecting incorrect property accesses in JavaScript
Souza et al., 2024 [129]
Detecting exception-handling anti-patterns in Java, TS, and Python```

지속가능성 측면에서도 고무적이다. 예를 들어, 표 4에 보이듯 ... MCP 서버의 CI 도입률은 42.2%로, 일반 OSS 및 ML 도메인보다 약간 높다.

**표 4.** MCP 서버의 개발/커뮤니티 메트릭을 일반 OSS 및 ML 도메인과 비교

```text
domains. The bold ones are the age-normalized values of time-dependent metrics, e.g., which grow over time.
Metric Name
MCP Server
General OSS
Domain
ML Domain
Median Total Commit Count
```

36.3

### 608.0 [25]

### 110.0 [64]

Median Commits/Week 5.5

### 2.5 [19]

- Median Github Contributor Count 2.0

### 41.0 [25]

### 2.0 [64]

Norm. Median Github Contributor Count/year 4.0

### 61.2 [25]

- Median Follower Count Of Contributors 129.6

### 37.3 [90]

- Norm. Med. Follower Count Of Contributors/year 259.2

### 17.0 [90]

- Median Star Count 39.3

### 66.0 [59]

- Norm. Median Star Count/year 79.0

### 34.7 [59]

- Median Forks Count 9.0

### 51.0 [155]

- Norm. Median Forks Count/year 18.0

### 7.5 [155]

- Median Lines Of Code 925.2 21,168.0 [60] 2,849.0 [136] Median File Count 9.0

### 142.0 [60]

### 26.0 [64]

Median Total Github Issue Count 2.0

### 673.0 [20]

- Median Issue Lifetime in Days 5.6

### 4.0 [32]

### 25.0 [72]

CI Adoption Rate (%) 42.2

### 40.3 [61]

### 37.2 [115]

Build Success Rate(%) 90.0

### 70.0 [33]

- Median Build Duration in Mins 1.9

### 9.3 [33]

### 21.4 [22]

Median Time To Fix a Broken Build in Mins 13.9

### 46.0 [69]

- General OSS domain (40.3%) and the ML domain (37.2%). While the difference compared to general OSS is not substantial, this adoption rate is notable because prior work reports that open-source projects typically adopt CI only after one year [61], whereas our findings indicate that MCP servers often adopt CI within six months of their initial release. MCP servers also exhibit a higher median build success rate, shorter median build times, and faster resolution of broken builds compared to the baselines as shown in Table 4. According to prior research, better build-related metrics indicate that MCP servers are capable of doing more frequent releases [61], and release frequency can positively impact the development and sustainability of projects in their early stage [52]. MCP servers exhibit higher age-normalized growth in some metrics, e.g., stars and forks, despite appearing to lag behind OSS baselines in raw counts. As shown in Table 4, the median star count and fork count of MCP Servers are lower than the baselines. However, the MCP protocol was introduced only six months ago, whereas the baseline projects are much older, e.g., the median age of the projects for fork count and star count are 6.8 and 1.9 years, respectively. Hence, normalizing these metrics by project age, MCP servers demonstrate an exceptionally fast growth trajectory. Specifically, MCP servers average approximately 79 stars and 18 forks per year, surpassing the normalized rates of 34.7 stars and 7.5 per year observed in the OSS baselines. Additionally, we observe higher community reach of MCP contributors in both raw and age-normalized count of their followers. These accelerated early-stage trends suggest a promising early trajectory for sustainability within the MCP ecosystem. We find that mined MCP servers receive 101.4% more commits than community MCP servers. The median total commit count in mined, official, and community MCP servers is 44.3, 42.0, and 22.0, respectively. We use a Kruskal–Wallis H-test to confirm that the differences in total

commit count among the three integration types are statistically significant (𝐻= 22, 𝑝= 0.000), and a post-hoc Mann-Whitney U test with Cliff’s Delta reveals that the difference is only significant for community vs mined (𝑃𝑐𝑜𝑟𝑟= 0.000 and 𝑑= −0.243, small effect). The difference between the other two combinations is not significant indicating that mined MCP servers have more development activities than only community servers. We also find that mined MCP servers are 56% larger than the official MCP server in terms of LoC. We observe median LoC in mined, official, and community MCP servers are 1,445.5, 929, and 548, respectively. A Kruskal–Wallis H-test confirms that the differences in lines of code across the three integration types are statistically significant (𝐻= 44.4976, 𝑝< 0.0001). Post-hoc Mann–Whitney U tests with Cliff’s Delta reveal that mined MCP servers contain more lines of code than official MCP servers (𝑝corr = 0.008, 𝑑= −0.244, small effect) and community MCP servers (𝑝corr = 0.000, 𝑑= −0.345, medium effect). There is no significant difference between official and community MCP servers. Similar to the previous finding, a larger project size in mined MCP servers again demonstrates more development activities.

### Summary of RQ-0

(1) MCP servers demonstrate healthy development behaviors in terms of early-stage
health and sustainability indicators.

(2) Mined MCP servers are more active and larger in size, suggesting early adopter
momentum. 6.2 RQ-1: To what extent do MCP servers contain security vulnerabilities? Motivation. Vulnerabilities are widespread in open-source ecosystems. For example, 46% of Python packages and 40% of JavaScript packages contain at least one known security issue [74, 113]. We observe widespread adoption of these languages to build MCP servers. e.g., millions of weekly downloads of the MCP packages [11, 12], raising immediate concerns about their security posture. Moreover, the vulnerability landscape is evolving with the rise of FM-based AI tools. For instance, a recent attack targeting the FM-based code editor and MCP client “Cursor” 10 leveraged three malicious NPM packages to exfiltrate credentials from over 4,200 users.11 This example highlights the broader risks of MCP servers as they mediate access between FMs and external systems, a dimension that has not existed before. In particular, MCP servers, deployed locally or remotely, act as intermediaries connecting FMs with sensitive resources, e.g., file systems, databases, and API endpoints. As a result, MCP servers often handle confidential data, including credentials, API keys, and user information. This tight coupling with critical infrastructure makes MCP servers attractive targets for exploitation. Despite this, the extent to which MCP servers are vulnerable remains unknown. Motivated by these emerging threat landscapes, we investigate the extent and nature of vulnerabilities present in MCP servers. Specifically, this research question aims to characterize the prevalence and patterns of security vulnerabilities in MCP servers, comparing those with the reported vulnerabilities from other domains in previous literature and assessing whether current tools and techniques are sufficient to detect the unique vulnerability landscape of MCP servers. Approach. To extract vulnerability issues from MCP servers, we perform static analysis on their codebases using SonarQube, as detailed in Section 5.2.1. Out of five major severity categories of SonarQube, in this RQ, we focus on the first four severity levels: Blocker, Critical, Major, and Minor.

10https://www.cursor.com/en

11https://thehackernews.com/2025/05/malicious-npm-packages-infect-3200.html

우리는 이러한 범주에 속하는 모든 취약점을 ... 42개의 고유한 MCP 서버에서 추출했으며, 이는

## 13개의 CWE와 밀접하게 관련된다. 이들 CWE 중 다수는 다른 도메인에서 보고된 CVE의 근본 원인이기도 하며,

표 6에 보고된 바와 같이, 취약점 ... MCP 서버 설치뿐 아니라 그에 대한 ...도 필요함을 시사한다.

12https://next.sonarqube.com/sonarqube/coding_rules?open=secrets:S7219&rule_key=secrets:S7219

**표 5.** MCP 서버, PyPI 패키지, NPM 패키지, IaC 스크립트 전반의 취약점 패턴(유병률 내림차순 정렬)

```text
descending order of prevalence. Highlighted patterns indicate cross-domain similarities, with superscript
```
숫자와 색은 가장 가까운 의미적 매칭을 나타낸다. 예를 들어 ... Code Execution  Authentication Bypass2  Arbitrary Code Injection

**표 6.** MCP 서버에서의 취약점 패턴 유병률과, 가장 관련이 깊은 CWE 및

```text
example CVEs caused by those CWEs.
MCP Vulnerabilities
```

% of MCP Servers Related CWEs Example CVEs Caused by CWEs Credential Exposure 3.6% CWE-259, CWE-798 CVE-2022-29964 Lack of Access Control 1.4% CWE-306, CWE-284 CVE-2022-24985 CORS Issues 1.2% CWE-345 – Improper Resource Management 1.0% CWE-770 CVE-2022-23471 Transport Security Issues 0.7% CWE-295, CWE-297, CWE-327 CVE-2021-22909 Authentication Issues 0.5% CWE-347 CVE-2002-1796 Insecure File Creation 0.2% CWE-377 CVE-2022-41954 Input Validation Issues 0.2% CWE-611 CVE-2022-42745 complete runtime configuration, including API credentials and auxiliary services. Despite following these steps, in our initial attempt to scan a representative sample of 83 MCP servers, only 60 scans were successful, with the remainder failing due to an issue within the tool. After we reported this to the maintainers, they released a fixed version that enabled us to successfully scan an additional
MCP 서버 비율  관련 CWE  해당 CWE로 인해 발생한 예시 CVE ... 추가로 13개 서버를 성공적으로 스캔할 수 있었던 수정 버전 덕분에,
## 13 servers, bringing our total to 73. These events highlight that such MCP-specific tools are still
## 총 13개 서버를 더해 전체 73개가 되었다. 이러한 사건은 MCP 특화 도구가 아직
evolving in their early lifecycle. Despite the operational challenges and early stage of the tool, we still detect potential tool poisoning in 5.5% of MCP servers, which is more prevalent than credential exposure. The ability of an early-stage tool, deployed with considerable effort on a limited sample, to uncover
초기 라이프사이클에서 진화 중임을 보여준다. 운영상의 어려움에도 불구하고 ...
this rate of a critical MCP-specific vulnerability strongly underscores the likelihood of more hidden issues that existing tools are currently unable to detect. While mcp-scan is able to detect tool poisoning, it misses other security concerns, such as excessive permission requirements and insecure default behaviors. During the setup process, we manually uncovered several concerning patterns that were not flagged by the scanner. For instance, the apple-notes-mcp server13 requires full disk access on macOS to interact with the native Apple Notes SQLite database highlighting an overly privileged configuration that which can introduce a significant attack surface. Similarly, godot-mcp14 was configured with autoapproval enabled for sensitive operations such as stopping projects or modifying project identifiers, potentially allowing unvetted commands to be executed. These issues are missed by mcp-scan because it relies on tool descriptions obtained through reflection rather than analyzing the source code, limiting its ability to catch deeper or context-specific security flaws. Pure MCP servers are more prone to credential exposure and transport security issues than the MCP servers derived from other applications, in which 85% of the identified vulnerabilities are found in deployment files. To better understand MCP server vulnerabilities, we analyze five random MCP servers that are “pure” MCP implementations without inherited legacy code or multifunctional roles. The most common vulnerabilities in these projects are credential exposure and transport security issues. For instance, we identify transport security issues, e.g., SSL/TLS verification bypasses in sooperset/mcp-atlassian and tuanle96/mcp-odoo, while credential exposure was prevalent in amornpan/py-mcp-mssql, kiliczsh/mcp-mongo-server, and Matmax-Worldwide/payloadcmsmcp. Then, we analyze the projects with more than five identified vulnerabilities. We found that only five MCP servers—SciPhi-AI/R2R, alibaba/higress, devflowinc/trieve, get-convex/convex-backend, and anaversity/learn-agentic-ai—fit this criterion and in these servers 85% vulnerabilities are found in “.yaml” files. At the same time, all the MCP servers with more than five vulnerabilities have implemented MCP as an additional feature in addition to their current functionalities. This highlights that the vulnerabilities in pure MCP repositories and other repositories where MCP is a derived feature need to be studied differently. The traditional vulnerability scanner SonarQube cannot detect any vulnerabilities in official MCP servers. Figure 4 illustrates the distribution of vulnerability counts per server, grouped by integration type (official, community, and mined) where both community and mined MCP servers have a median vulnerability count of 2, while no vulnerability is found in official MCP servers. Interestingly, this mirrors findings from the Docker ecosystem, where official images have been shown to exhibit fewer vulnerabilities compared to community-maintained ones [143]. We detect exposed OpenAI and Gemini API keys, Google Cloud service account certificates, and GitHub tokens in community and mined MCP server repositories, posing significant risks of financial loss and unauthorized access. Figure 5 presents three representative examples of such credential exposures across JSON, Python, and certificate files from real-world repositories. Leaked API keys for platforms like OpenAI and Google Cloud can be exploited by malicious actors to initiate high-volume API calls, potentially resulting in substantial financial charges for the affected account owners. Likewise, exposed GitHub tokens may allow unauthorized access to private repositories or CI/CD pipelines. As shown in Table 6, these are indicative of CWE-798 (Use of Hardcoded Credentials), which has been associated with several previous high-impact security incidents, including CVE-2022-29964.
운영상의 어려움에도 ... 제한된 표본에서 상당한 노력으로 도구를 배포해,
13https://github.com/sirmews/apple-notes-mcp
이러한 치명적인 MCP 특화 취약점의 비율은 ... CVE-2022-29964를 포함한 여러 고영향 보안 사고와 연결됨을 강하게 시사한다.
14https://github.com/Coding-Solo/godot-mcp

official community mined Integration Type Vulnerability Count per MCP Server Integration Type Official Community Mined
공식  커뮤니티  마이닝  통합 유형  MCP 서버당 취약점 수  통합 유형  공식  커뮤니티  마이닝
**그림. 4.** Vulnerability count distribution per MCP server grouped by Integration Type.
**그림 4.** 통합 유형별로 그룹화한 MCP 서버당 취약점 수 분포.
![Fig. 4 (page 22)](assets/pages/page_22.png)

OPENAI_API_KEY ": "sk-Wo ******** g5" (a) Hardcoded OpenAI API key in a JSON configuration file. # Configure Gemini genai.configure(api_key='AIza **** -****1 zn4') model = genai.GenerativeModel('gemini -2.0-flash -001') (b) Gemini API key exposed directly in Python source code. "type": "service_account", "project_id ": "***", "private_key_id ": "d4d ****4a4", "private_key ": "-----BEGIN PRIVATE KEY -----\***\n-----END PRIVATE KEY -----\n", "universe_domain ": "googleapis.com" (c) Google Cloud service account private key exposed in a certificate file.
OPENAI_API_KEY ": "sk-Wo ******** g5" (a) 하드코딩된 OpenAI API 키 ... 클라우드 서비스 계정 개인 키가 인증서 파일에서 노출된 사례.
**그림. 5.** Examples of credential exposure across different code and configuration formats. As these are sensitive
**그림 5.** 다양한 코드/설정 형식에서의 자격 증명 노출 예시. (민감 정보이므로 ...)
![Fig. 5 (page 22)](assets/pages/page_22.png)

credentials and keys we have obfuscated those.

### Summary of RQ-1

(1) MCP servers exhibit distinct vulnerability patterns compared to other domains of
software engineering. Out of eight vulnerability patterns detected in MCP servers, three are common with other domains.

(2) MCP-specific vulnerabilities can be highly prevalent as even an early stage tool could
already detect 5.5% MCP-specific issues.

(3) Credential exposure, e.g., API Keys from FM service providers, GitHub tokens, can
cause significant financial loss and major data breaches. RQ-2: To what extent do MCP servers contain maintainability issues? Motivation. Maintainability remains a pressing concern in modern software systems, especially in the era of FM-based AI applications. According to the State of Software-2025 report [54], 73% of AI and big data systems fall below the industry benchmark for maintainability. In mature organizations,
유지보수성 이슈를 해결하기 위한 오버헤드는 최대 £25... 표 8. 특히 MCP에서 임계(critical) 코드 스멜의 중앙값은 ...

**표 7.** MCP 서버, ML 프로젝트, FM 생성 코드 전반의 코드 스멜 패턴(유병률 내림차순)

```text
in descending order. The first column (MCP server) includes prevalence percentages. Highlighted patterns
```

도메인 간 유사성을 나타내며, 위첨자 번호와 색으로 ... Issues (1.2%) missing-module-docstring1 Consider-usingenumerate4

**표 8.** 프로그래밍 언어별 Critical/Blocker 코드 스멜 분포. Critical smell %

```text
and Blocker smell % indicate the percentage of projects where at least one critical or blocker-level code
```

smell is present. Median Critical and Median Blocker represent the median number of critical and blocker code smells per project, respectively. Language Critical smell % Median Critical Blocker smell % Median Blocker Python 68.1 1.0 5.6 JavaScript 39.8 2.0 1.3 TypeScript 61.1 4.0 5.8 Others 47.3 12.0 4.4 servers ranges between 2 and 4 in the most commonly used programming languages, e.g., Python, JavaScript, and TypeScript, while the median number of blocker-level code smells is zero across all these languages. In contrast, traditional software engineering studies have reported that certain code smells can be present in nearly 100% of the studied Python ML projects and traditional Python projects [35, 136] and up-to 97% FM generated code can contain code smells [121]. 59.7% of MCP servers suffer from high cognitive complexity, which is also considered as the one of the most severe code smells in Python ecosystem. As summarized in Table 7, we observe that high cognitive complexity is almost three times more prevalent than the second most common code smell, e.g., code duplication-redundancy, in MCP servers. Cognitive complexity is a widely used metric for modeling and estimating the functional complexity, size, and effort required for software development [141]. While prior studies suggest a threshold of 15 for cognitive complexity [94], violation of this threshold is considered the one of the most severe code smells in the Python ecosystem [55]. Similarly, this threshold is violated in a substantial portion (59.7%) of MCP servers, which can lead to increased comprehension time, reduced understandability, and higher debugging time and error rates [94]. Mined MCP servers contain 66% more code smells than both official and community servers. Figure 6a presents the distribution of code smell counts per MCP server across different

integration types on a logarithmic scale. We observe a median code smell count of 5 in mined MCP servers, compared to 3 in official and community MCP servers. A Kruskal-Wallis H-test reveals a significant difference in code smell counts among the three integration types (𝐻= 23.2936, 𝑝< 0.001). Post-hoc Mann-Whitney U tests indicate that mined servers have more code smells than both official (𝑃−𝑣𝑎𝑙𝑢𝑒= 0.004 and 𝑑= −0.322, small effect) and community (𝑃−𝑣𝑎𝑙𝑢𝑒= 0.000 and 𝑑= −0.280, small effect) servers. However, the difference between official and community MCP servers is not statistically significant. We can partially explain by the larger size of mined MCP servers found in Section 6.1, as prior work [149] has shown a positive correlation between code size and code smells. official community mined Integration Type Codesmell Count per MCP Server (log) (a) Code smell count distribution by integration type in logarithmic scale. Python JavaScript TypeScript Programming Language Codesmell Count per MCP Server (log) (b) Code smell count distribution by programming language in logarithmic scale.

**Fig. 6.** Comparison of code smells by integration type and programming language.

![Fig. 6 (page 25)](assets/pages/page_25.png)

JavaScript MCP 서버는 ... 코드 스멜이 50% 적은 경향이 있다... 구조(Architecture) 이슈는 Java 생태계에서 보고된 버그에는 나타나지 않는다.

**표 9.** MCP 서버와 Java 프로젝트에서의 상위 버그 유형 및 분포. MCP 서버 비율은

```text
are shown in parentheses. The table is sorted in descending order of prevalence. Highlighted patterns indicate
```

도메인 간 유사성을 나타내며, 위첨자 번호와 색으로 ... (1.7%) Field only ever set to null  Suspicious reference comparison

**표 10.** 프로그래밍 언어별 Critical/Blocker 버그 분포. Critical bug % 및

```text
Blocker bug % indicate the percentage of projects where at least one critical or blocker-level bug is present.
Median Critical and Median Blocker represent the median number of critical and blocker bugs per project,```

각각. 언어별 Critical bug % 및 중앙값(Critical/Blocker) ... 그림 7a의 해당 바이올린 플롯 분포를 참고하라. 다만

15https://v8.dev/blog/array-sort

Python  JavaScript  TypeScript  프로그래밍 언어  버그 수 ... (b) 통합 유형별 MCP 서버당 버그 분포.

**그림 7.** MCP 서버 전반에서 통합 유형 및 프로그래밍 언어에 따른 버그 비교.

![Fig. 7 (page 27)](assets/pages/page_27.png)

표를 보면 TypeScript가 더 취약할 수 ... 이는 버그 도입 가능성 증가와 연관될 수 있다 [50].

### RQ-2 요약

(1) 66% of MCP servers contain at least one critical or blocker-level code smell, and 14.4%
정적 분석으로 탐지된 버그가 최소 1개 이상 ... 광범위한 유지보수성 우려를 보여준다.

(2) 가장 흔한 코드 스멜은 높은 인지 복잡도이며, MCP 서버의 59.7%에 영향을 준다.
이는 두 번째로 흔한 스멜보다 3배 ... 가독성/이해도 저하 및 오류 위험 증가와 강하게 연관된다.

(3) 마이닝된 MCP 서버는 공식/커뮤니티 서버보다 코드 스멜과 버그가 더 많다.
이는 개발 활동이 더 활발하거나, 유지보수 관행이 덜 구조화되어 있기 때문일 수 있다.

(4) 식별된 모든 MCP 버그 유형은 Java, Python, JavaScript 생태계에서 알려진 버그와 겹친다.
따라서 기존 디버깅 및 ... MCP 서버에도 적용될 수 있음을 시사한다. 특히 MCP 생태계에는 세 가지 주요 대상이 있다:

MCP 생태계의 대상: (i) 연구자, (ii) 실무자, (...) 전통 소프트웨어 도메인(6.2절)과의 유사성. 이러한 유사성은

16https://genai.owasp.org/llm-top-10/
이는 실무자가 전통적으로 잘 확립된 기법을 ... MCP 인프라 채택이 늘어남에 따라 진화할 것이다.

17https://www.reddit.com/r/mcp/comments/1hm3g2s/glama_mcp_server_directory/

타당성 위협 8.1 외적 타당성 본 연구에서는 ... 취약점뿐 아니라 코드 스멜과 버그까지도 포함한다.

8.3 내적 타당성 본 연구에서는 오픈소스 ... MCP 서버를 조사했으며, 그중 공통 이슈와 겹치는 것은 3개뿐이었다 ...
Python이나 Infrastructure-as-Code 같은 생태계 ... 추가적으로 ...

## 참고문헌(원문)

[20] Lingfeng Bao, Xin Xia, David Lo, and Gail C Murphy. 2019. A large scale study of long-time contributor prediction for github projects. IEEE Transactions on Software Engineering 47, 6 (2019), 1277–1298. [21] Setu Kumar Basak, Lorenzo Neil, Bradley Reaves, and Laurie Williams. 2022. What are the practices for secret management in software artifacts?. In 2022 IEEE Secure Development Conference (SecDev). IEEE, 69–76. [22] João Helis Bernardo, Daniel Alencar Da Costa, Sérgio Queiroz de Medeiros, and Uirá Kulesza. 2024. How do machine learning projects use continuous integration practices? an empirical study on GitHub actions. In Proceedings of the 21st International Conference on Mining Software Repositories. 665–676. [23] Ethan Bommarito and Michael Bommarito. 2019. An empirical analysis of the python package index (pypi). arXiv preprint arXiv:1907.11073 (2019). [24] Rishi Bommasani, Drew A Hudson, Ehsan Adeli, Russ Altman, Simran Arora, Sydney von Arx, Michael S Bernstein, Jeannette Bohg, Antoine Bosselut, Emma Brunskill, et al. 2021. On the opportunities and risks of foundation models. arXiv preprint arXiv:2108.07258 (2021). [25] Hudson Borges, Andre Hora, and Marco Tulio Valente. 2016. Understanding the factors that impact the popularity of GitHub repositories. In 2016 IEEE international conference on software maintenance and evolution (ICSME). IEEE, 334–344. [26] Tom Brown, Benjamin Mann, Nick Ryder, Melanie Subbiah, Jared D Kaplan, Prafulla Dhariwal, Arvind Neelakantan, Pranav Shyam, Girish Sastry, Amanda Askell, et al. 2020. Language models are few-shot learners. Advances in neural information processing systems 33 (2020), 1877–1901. [27] Simon Butler, Jonas Gamalielsson, Björn Lundell, Christoffer Brax, Anders Mattsson, Tomas Gustavsson, Jonas Feist, Bengt Kvarnström, and Erik Lönroth. 2022. Considerations and challenges for the adoption of open source components in software-intensive businesses. Journal of Systems and Software 186 (2022), 111152. [28] Paolo Calciati and Alessandra Gorla. 2017. How do apps evolve in their permission requests? a preliminary study. In

## 2017 IEEE/ACM 14th International Conference on Mining Software Repositories (MSR). IEEE, 37–41.

[29] G Ann Campbell and Patroklos P Papapetrou. 2013. SonarQube in action. Manning Publications Co. [30] Giuseppe Castagna and Victor Lanvin. 2017. Gradual typing with union and intersection types. Proceedings of the ACM on Programming Languages 1, ICFP (2017), 1–28. [31] CHAOSS Project. 2025. Community Health Analytics in Open Source Software: Topic - All Metrics. https://chaoss. community/kbtopic/all-metrics/. Accessed: Jun 10, 2025. [32] CHAOSS Project. 2025. Practitioner Guide: Responsiveness. https://chaoss.community/practitioner-guideresponsiveness/. Accessed: May 15, 2025. [33] Bihuan Chen, Linlin Chen, Chen Zhang, and Xin Peng. 2020. Buildfast: History-aware build outcome prediction for fast feedback and reduced cost in continuous integration. In Proceedings of the 35th IEEE/ACM International Conference on Automated Software Engineering. 42–53. [34] Celia Chen, Shi Lin, Michael Shoga, Qing Wang, and Barry Boehm. 2018. How do defects hurt qualities? an empirical study on characterizing a software maintainability ontology in open source software. In 2018 IEEE International Conference on Software Quality, Reliability and Security (QRS). IEEE, 226–237. [35] Zhifei Chen, Lin Chen, Wanwangying Ma, and Baowen Xu. 2016. Detecting code smells in python programs. In 2016 international conference on Software Analysis, Testing and Evolution (SATE). IEEE, 18–23. [36] Henry Chesbrough. 2023. Measuring the economic value of open source. San Francisco: Linux Foundation (2023). [37] Steve Christey and Robert A Martin. 2007. Vulnerability type distributions in CVE. Mitre report, May (2007). [38] Cloudflare. 2025. Cloudflare Agents Docs: Model Context Protocol (MCP). https://developers.cloudflare.com/agents/ model-context-protocol, last visited: Apr 23. [39] Jailton Coelho and Marco Tulio Valente. 2017. Why modern open source projects fail. In Proceedings of the 2017 11th Joint meeting on foundations of software engineering. 186–196. [40] CrewAI. 2025. CrewAI: The leading multi-agent platform. https://www.crewai.com/, last visited: May 27. [41] Dinis Barroqueiro Cruz, João Rafael Almeida, and José Luís Oliveira. 2023. Open source solutions for vulnerability assessment: A comparative analysis. IEEE Access 11 (2023), 100234–100255. [42] Ozren Dabic, Emad Aghajani, and Gabriele Bavota. 2021. Sampling projects in github for MSR studies. In 2021 IEEE/ACM 18th International Conference on Mining Software Repositories (MSR). IEEE, 560–564. [43] Andrey Loskutov Keith Lea David Hovemeyer, Bill Pugh. 2025. An extensible multilanguage static code analyzer. https://findbugs.sourceforge.net/, last visited: May 18. [44] DI De Silva, RD New Kandy, BLO Sachethana, SMDTH Dias, PYC Perera, ME Katipearachchi, and TDDH Jayasuriya. 2023. The Relationship between Code Complexity and Software Quality: An Empirical Study. Journal of Software Engineering Research and Development 11, 1 (2023), 1. [45] Alexandre Decan, Tom Mens, and Eleni Constantinou. 2018. On the impact of security vulnerabilities in the npm package dependency network. In Proceedings of the 15th international conference on mining software repositories. 181–191.

[46] Kerstin Denecke, Richard May, LLMHealthGroup, and Octavio Rivera Romero. 2024. Potential of large language models in health care: Delphi study. Journal of Medical Internet Research 26 (2024), e52399. [47] Dify. 2025. Dify: Build Production Ready Agentic Solution. https://dify.ai/, last visited: May 27. [48] Inc Docker et al. 2020. Docker. lınea].[Junio de 2017]. Disponible en: https://www. docker. com/what-docker (2020). [49] Tore Dybå, Vigdis By Kampenes, and Dag IK Sjøberg. 2006. A systematic review of statistical power in software engineering experiments. Information and Software Technology 48, 8 (2006), 745–755. [50] Filipe Falcão, Caio Barbosa, Baldoino Fonseca, Alessandro Garcia, Márcio Ribeiro, and Rohit Gheyi. 2020. On relating technical, social factors, and the introduction of bugs. In 2020 IEEE 27th International Conference on Software Analysis, Evolution and Reengineering (SANER). IEEE, 378–388. [51] Rosa Falotico and Piero Quatto. 2015. Fleiss’ kappa statistic without paradoxes. Quality & Quantity 49 (2015), 463–470. [52] Amir Hossein Ghapanchi. 2015. Predicting software future sustainability: A longitudinal perspective. Information Systems 49 (2015), 40–51. [53] Sean Goggins, Kevin Lumbard, and Matt Germonprez. 2021. Open source community health: Analytical metrics and their corresponding narratives. In 2021 IEEE/ACM 4th International Workshop on Software Health in Projects, Ecosystems and Communities (SoHeal). IEEE, 25–33. [54] Software Improvement Group. 2025. State of Software 2025: A Global Report on the Hidden Costs and Risks of Software. https://www.softwareimprovementgroup.com/wp-content/uploads/State-of-software-2025.pdf, last visited: May 08. [55] Aakanshi Gupta, Rashmi Gandhi, Nishtha Jatana, Divya Jatain, Sandeep Kumar Panda, and Janjhyam Venkata Naga Ramesh. 2023. A severity assessment of python code smells. IEEE Access 11 (2023), 119146–119160. [56] Md Shariful Haque, Jeff Carver, and Travis Atkison. 2018. Causes, impacts, and detection approaches of code smell: a survey. In Proceedings of the 2018 ACM Southeast Conference. 1–8. [57] Mohammed Mehedi Hasan, Hao Li, Emad Fallahzadeh, Gopi Krishnan Rajbahadur, Bram Adams, and A. E Hassan. 2025. The replication package of our study on MCP Servers. https://github.com/SAILResearch/replication-25-mcpserver-empirical-study, last visited: Jun 11. [58] Ahmed E Hassan, Gustavo A Oliva, Dayi Lin, Boyuan Chen, Zhen Ming, et al. 2024. Rethinking software engineering in the foundation model era: From task-driven ai copilots to goal-driven ai pair programmers. arXiv preprint arXiv:2404.10225 (2024). [59] Runzhi He, Hao He, Yuxia Zhang, and Minghui Zhou. 2023. Automating dependency updates in practice: An exploratory study on github dependabot. IEEE Transactions on Software Engineering 49, 8 (2023), 4004–4022. [60] Israel Herraiz, Jesus M Gonzalez-Barahona, and Gregorio Robles. 2008. Determinism and evolution. In Proceedings of the 2008 international working conference on Mining software repositories. 1–10. [61] Michael Hilton, Timothy Tunnell, Kai Huang, Darko Marinov, and Danny Dig. 2016. Usage, costs, and benefits of continuous integration in open-source projects. In Proceedings of the 31st IEEE/ACM international conference on automated software engineering. 426–437. [62] Xinyi Hou, Yanjie Zhao, Shenao Wang, and Haoyu Wang. 2025. Model Context Protocol (MCP): Landscape, Security Threats, and Future Research Directions. arXiv preprint arXiv:2503.23278 (2025). [63] IBM. 2025. Cost of a Data Breach Report 2024. https://www.ibm.com/reports/data-breach, last visited: May 27. [64] Samuel Idowu, Yorick Sens, Thorsten Berger, Jacob Krüger, and Michael Vierhauser. 2024. A large-scale study of ml-related python projects. In Proceedings of the 39th ACM/SIGAPP Symposium on Applied Computing. 1272–1281. [65] Alphabet Inc. 2025. Security checklist. https://developer.android.com/privacy-and-security/security-tips, last visited: June 03. [66] Nenad Jovanovic, Christopher Kruegel, and Engin Kirda. 2006. Pixy: A static analysis tool for detecting web application vulnerabilities. In 2006 IEEE Symposium on Security and Privacy (S&P’06). IEEE, 6–pp. [67] Jaehun Jung, Faeze Brahman, and Yejin Choi. 2024. Trust or Escalate: LLM Judges with Provable Guarantees for Human Agreement. arXiv preprint arXiv:2407.18370 (2024). [68] Arvinder Kaur and Ruchikaa Nayyar. 2020. A comparative study of static code analysis tools for vulnerability detection in c/c++ and java source code. Procedia Computer Science 171 (2020), 2023–2029. [69] Noureddine Kerzazi, Foutse Khomh, and Bram Adams. 2014. Why do automated builds break? an empirical study. In

## 2014 IEEE international conference on software maintenance and evolution. IEEE, 41–50.

[70] Sonu Kumar, Anubhav Girdhar, Ritesh Patil, and Divyansh Tripathi. 2025. MCP Guardian: A Security-First Layer for Safeguarding MCP-Based AI System. arXiv preprint arXiv:2504.12757 (2025). [71] Invariant Lab. 2025. Introducing MCP-Scan: Protecting MCP with Invariant. https://invariantlabs.ai/blog/introducingmcp-scan, last visited: May 29. [72] Tuan Dung Lai, Anj Simmons, Scott Barnett, Jean-Guy Schneider, and Rajesh Vasa. 2024. Comparative analysis of real issues in open-source machine learning projects. Empirical Software Engineering 29, 3 (2024), 60.

[73] LangChain. 2025. LangChain: composable framework to build with LLMs. https://www.langchain.com/, last visited: Apr 23. [74] Jasmine Latendresse, Suhaib Mujahid, Diego Elias Costa, and Emad Shihab. 2022. Not all dependencies are equal: An empirical study on production dependencies in npm. In Proceedings of the 37th IEEE/ACM International Conference on Automated Software Engineering. 1–12. [75] Luigi Lavazza, Sandro Morasca, and Davide Tosi. 2021. Comparing static analysis and code smells as defect predictors: an empirical study. In IFIP international conference on open source systems. Springer, 1–15. [76] Valentina Lenarduzzi, Francesco Lomio, Heikki Huttunen, and Davide Taibi. 2020. Are sonarqube rules inducing bugs?. In 2020 IEEE 27th international conference on software analysis, evolution and reengineering (SANER). IEEE, 501–511. [77] Patrick Lewis, Ethan Perez, Aleksandra Piktus, Fabio Petroni, Vladimir Karpukhin, Naman Goyal, Heinrich Küttler, Mike Lewis, Wen-tau Yih, Tim Rocktäschel, et al. 2020. Retrieval-augmented generation for knowledge-intensive nlp tasks. Advances in neural information processing systems 33 (2020), 9459–9474. [78] Hao Li and Cor-Paul Bezemer. 2025. Bridging the language gap: an empirical study of bindings for open source machine learning libraries across software package ecosystems. Empirical Software Engineering 30, 1 (2025), 6. [79] Hao Li, Cor-Paul Bezemer, and Ahmed E Hassan. 2024. Software Engineering and Foundation Models: Insights from Industry Blogs Using a Jury of Foundation Models. arXiv preprint arXiv:2410.09012 (2024). [80] Jiahuei Lin, Dayi Lin, Sky Zhang, and Ahmed E Hassan. 2024. Engineering AI Judge Systems. arXiv preprint arXiv:2411.17793 (2024). [81] LlamaIndex. 2025. LlamaIndex: LlamaIndex is the leading framework for building LLM-powered agents over your data with LLMs and workflows. https://docs.llamaindex.ai/en/stable/, last visited: Apr 23. [82] Google LLC. 2025. GenAI Toolbox: An introduction to MCP Toolbox. https://googleapis.github.io/genai-toolbox/ getting-started/introduction/, last visited: May 27. [83] Guillermo Macbeth, Eugenia Razumiejczyk, and Rubén Daniel Ledesma. 2011. Cliff’s Delta Calculator: A nonparametric effect size program for two groups of observations. Universitas Psychologica 10, 2 (2011), 545–555. [84] Thomas W MacFarland, Jan M Yates, Thomas W MacFarland, and Jan M Yates. 2016. Kruskal–Wallis H-test for oneway analysis of variance (ANOVA) by ranks. Introduction to nonparametric statistics for the biological sciences using R (2016), 177–211. [85] Meta. 2025. Function Calling: Llama 3.1 models now officially supports function calling. https://github.com/abetlen/ llama-cpp-python/issues/1618, last visited: May 15. [86] Microsoft. 2025. Introducing Model Context Protocol (MCP) in Copilot Studio: Simplified Integration with AI Apps and Agents. https://www.microsoft.com/en-us/microsoft-copilot/blog/copilot-studio/introducing-model-contextprotocol-mcp-in-copilot-studio-simplified-integration-with-ai-apps-and-agents, last visited: Apr 23. [87] Microsoft. 2025. Plug, Play, and Prey: The security risks of the Model Context Protocol. https: //techcommunity.microsoft.com/blog/microsoftdefendercloudblog/plug-play-and-prey-the-security-risks-ofthe-model-context-protocol/4410829, last visited: May 18. [88] Vishal Midha and Prashant Palvia. 2012. Factors affecting the success of Open Source Software. Journal of Systems and Software 85, 4 (2012), 895–905. [89] Mitre. 2025. Common Weakness Enumeration:: A community developed list of SW & HW weakness that can become vulnerabilities. https://cwe.mitre.org/index.html, last visited: May 15. [90] Mohammed Abdul Moid, Abdullah Siraj, Mohd Farhaan Ali, and Ahmed Osman Amoodi. 2021. Predicting Stars on Open-Source GitHub Projects. In 2021 Smart Technologies, Communication and Robotics (STCR). IEEE, 1–9. [91] Dietmar PF Möller. 2023. NIST cybersecurity framework and MITRE cybersecurity criteria. In Guide to Cybersecurity in Digital Transformation: Trends, Methods, Technologies, Applications and Best Practices. Springer, 231–271. [92] Suhaib Mujahid, Rabe Abdalkareem, and Emad Shihab. 2023. What are the characteristics of highly-selected packages? A case study on the npm ecosystem. Journal of Systems and Software 198 (2023), 111588. [93] Nuthan Munaiah, Steven Kroh, Craig Cabrey, and Meiyappan Nagappan. 2017. Curating github for engineered software projects. Empirical Software Engineering 22 (2017), 3219–3253. [94] Marvin Muñoz Barón, Marvin Wyrich, and Stefan Wagner. 2020. An empirical validation of cognitive complexity as a measure of source code understandability. In Proceedings of the 14th ACM/IEEE international symposium on empirical software engineering and measurement (ESEM). 1–12. [95] Vineeth Sai Narajala and Idan Habler. 2025. Enterprise-Grade Security for the Model Context Protocol (MCP): Frameworks and Mitigation Strategies. arXiv preprint arXiv:2504.08623 (2025). [96] Mathew Nicho, Hussein Fakhry, and Charles Haiber. 2011. An integrated security governance framework for effective PCI DSS implementation. International Journal of Information Security and Privacy (IJISP) 5, 3 (2011), 50–67. [97] OpenAI. 2025. Function Calling: Enable models to fetch data and take actions. https://platform.openai.com/docs/ guides/function-calling, last visited: May 15.

[98] OpenAI. 2025. OpenAI Agents SDK: Model context protocol (MCP). https://openai.github.io/openai-agents-python/ mcp, last visited: Apr 23. [99] OpenAI, Josh Achiam, Steven Adler, Sandhini Agarwal, Lama Ahmad, Ilge Akkaya, Florencia Leoni Aleman, Diogo Almeida, Janko Altenschmidt, et al. 2024. GPT-4 Technical Report. arXiv preprint arXiv:2303.08774 (2024). [100] Fabio Palomba, Gabriele Bavota, Massimiliano Di Penta, Fausto Fasano, Rocco Oliveto, and Andrea De Lucia. 2018. On the diffuseness and the impact on maintainability of code smells: a large scale empirical investigation. In Proceedings of the 40th International Conference on Software Engineering. 482–482. [101] Thomas H Park, Brian Dorn, and Andrea Forte. 2015. An analysis of HTML and CSS syntax errors in a web development course. ACM Transactions on Computing Education (TOCE) 15, 1 (2015), 1–21. [102] PMD. 2025. An extensible multilanguage static code analyzer. https://pmd.github.io/, last visited: May 18. [103] Luís Prates and Rúben Pereira. 2025. DevSecOps practices and tools. International Journal of Information Security 24,

## 1 (2025), 1–25.

[104] G Priyalakshmi and R Latha. 2018. Evaluation of software reusability based on coupling and cohesion. International Journal of Software Engineering and Knowledge Engineering 28, 10 (2018), 1455–1485. [105] Model Context Protocol. 2025. Model Context Protocol servers. https://github.com/modelcontextprotocol/servers, last visited: Apr 23. [106] Brandon Radosevich and John Halloran. 2025. MCP Safety Audit: LLMs with the Model Context Protocol Allow Major Security Exploits. arXiv preprint arXiv:2504.03767 (2025). [107] Akond Rahman, Chris Parnin, and Laurie Williams. 2019. The seven sins: Security smells in infrastructure as code scripts. In 2019 IEEE/ACM 41st International Conference on Software Engineering (ICSE). IEEE, 164–175. [108] Baishakhi Ray, Daryl Posnett, Vladimir Filkov, and Premkumar Devanbu. 2014. A large scale study of programming languages and code quality in github. In Proceedings of the 22nd ACM SIGSOFT international symposium on foundations of software engineering. 155–165. [109] Eric Raymond. 1999. The cathedral and the bazaar. Knowledge, Technology & Policy 12, 3 (1999), 23–49. [110] Andrew Rice, Edward Aftandilian, Ciera Jaspan, Emily Johnston, Michael Pradel, and Yulissa Arroyo-Paredes. 2017. Detecting argument selection defects. Proceedings of the ACM on Programming Languages 1, OOPSLA (2017), 1–22. [111] Chanchal K Roy, Minhaz F Zibran, and Rainer Koschke. 2014. The vision of software clone management: Past, present, and future (keynote paper). In 2014 Software Evolution Week-IEEE Conference on Software Maintenance, Reengineering, and Reverse Engineering (CSMR-WCRE). IEEE, 18–33. [112] Jukka Ruohonen. 2018. An empirical analysis of vulnerabilities in python packages for web applications. In 2018 9th International Workshop on Empirical Software Engineering in Practice (IWESEP). IEEE, 25–30. [113] Jukka Ruohonen, Kalle Hjerppe, and Kalle Rindell. 2021. A large-scale security-oriented static analysis of python packages in pypi. In 2021 18th International Conference on Privacy, Security and Trust (PST). IEEE, 1–10. [114] Graeme D Ruxton and Guy Beauchamp. 2008. Time for some a priori thinking about post hoc testing. Behavioral ecology 19, 3 (2008), 690–693. [115] Dhia Elhaq Rzig, Foyzul Hassan, Chetan Bansal, and Nachiappan Nagappan. 2022. Characterizing the usage of ci tools in ml projects. In Proceedings of the 16th ACM/IEEE International Symposium on Empirical Software Engineering and Measurement. 69–79. [116] Amir Saboury, Pooya Musavi, Foutse Khomh, and Giulio Antoniol. 2017. An empirical study of code smells in javascript projects. In 2017 IEEE 24th international conference on software analysis, evolution and reengineering (SANER). IEEE, 294–305. [117] Haya Samaana, Diego Elias Costa, Ahmad Abdellatif, and Emad Shihab. 2025. Opportunities and security risks of technical leverage: A replication study on the NPM ecosystem. Empirical Software Engineering 30, 3 (2025), 96. [118] Víctor Rea Sánchez, Pablo Neira Ayuso, José A Galindo, and David Benavides. 2020. Open source adoption factors—a systematic literature review. IEEE Access 8 (2020), 94594–94609. [119] Aleksei Shestov, Rodion Levichev, Ravil Mussabayev, Evgeny Maslov, Pavel Zadorozhny, Anton Cheshkov, Rustam Mussabayev, Alymzhan Toleu, Gulmira Tolegen, and Alexander Krassovitskiy. 2025. Finetuning large language models for vulnerability detection. IEEE Access (2025). [120] Nima Shiri Harzevili, Alvine Boaye Belle, Junjie Wang, Song Wang, Zhen Ming Jiang, and Nachiappan Nagappan. 2024. A systematic literature review on automated software vulnerability detection using machine learning. Comput. Surveys 57, 3 (2024), 1–36. [121] Mohammed Latif Siddiq, Shafayat H Majumder, Maisha R Mim, Sourov Jajodia, and Joanna CS Santos. 2022. An empirical study of code smells in transformer-based code generation techniques. In 2022 IEEE 22nd International Working Conference on Source Code Analysis and Manipulation (SCAM). IEEE, 71–82. [122] Randeep Singh and Ashok Kumar. 2018. Identifying various code-smells and refactoring opportunities in objectoriented software system: a systematic literature review. International Journal on Future Revolution in Computer Science & Communication Engineering 8, March (2018), 62–74.

[123] Satwinder Singh and Sharanpreet Kaur. 2018. A systematic literature review: Refactoring for disclosing code smells in object oriented software. Ain Shams Engineering Journal 9, 4 (2018), 2129–2151. [124] sixsentix. 2025. Ten most expensive bugs in history (part 2). https://www.sixsentix.com/insights/ten-most-expensivebugs-in-history-part-2, last visited: May 27. [125] Justin Smith, Brittany Johnson, Emerson Murphy-Hill, Bill Chu, and Heather Richter Lipford. 2018. How developers diagnose potential security vulnerabilities with a static analysis tool. IEEE Transactions on Software Engineering 45, 9 (2018), 877–897. [126] smithery. 2025. Smithery: Your Agent’s Gateway to the World. https://smithery.ai/, last visited: May 15. [127] SonarQube. 2025. SonarQube: Static Code Analysis. https://docs.sonarsource.com/sonarqube-server/latest/userguide/code-metrics/metrics-definition/#se-severity-types, last visited: May 14. [128] SonarQube. 2025. SonarQube: Static Code Analysis. https://docs.sonarsource.com/sonarqube-server/10.8/userguide/rules/security-related-rules, last visited: May 14. [129] Jairo Souza, Tales Alves, Robson Oliveira, Leopoldo Teixeira, and Baldoino Fonseca. 2024. Exception Miner: Multilanguage Static Analysis Tool to Identify Exception Handling Anti-Patterns. In Simpósio Brasileiro de Engenharia de Software (SBES). SBC, 741–747. [130] S, tefan Stănciulescu, Likang Yin, and Vladimir Filkov. 2022. Code, quality, and process metrics in graduated and retired asfi projects. In Proceedings of the 30th ACM Joint European Software Engineering Conference and Symposium on the Foundations of Software Engineering. 495–506. [131] Stripe. 2025. The Stripe Model Context Protocol server allows you to integrate with Stripe APIs through function calling. https://github.com/stripe/agent-toolkit/tree/main/modelcontextprotocol, last visited: May 27. [132] Sebastian Sztwiertnia, Maximilian Grübel, Amine Chouchane, Daniel Sokolowski, Krishna Narasimhan, and Mira Mezini. 2021. Impact of programming languages on machine learning bugs. In Proceedings of the 1st ACM International Workshop on AI and Software Testing/Analysis. 9–12. [133] Hugo Touvron, Thibaut Lavril, Gautier Izacard, Xavier Martinet, Marie-Anne Lachaux, Timothée Lacroix, Baptiste Rozière, Naman Goyal, Eric Hambro, Faisal Azhar, Aurelien Rodriguez, Armand Joulin, Edouard Grave, and Guillaume Lample. 2023. LLaMA: Open and Efficient Foundation Language Models. arXiv preprint arXiv:2302.13971 (2023). [134] Michele Tufano, Fabio Palomba, Gabriele Bavota, Rocco Oliveto, Massimiliano Di Penta, Andrea De Lucia, and Denys Poshyvanyk. 2015. When and why your code starts to smell bad. In 2015 IEEE/ACM 37th IEEE International Conference on Software Engineering, Vol. 1. IEEE, 403–414. [135] Marat Valiev, Bogdan Vasilescu, and James Herbsleb. 2018. Ecosystem-level determinants of sustained activity in open-source projects: A case study of the PyPI ecosystem. In Proceedings of the 2018 26th ACM Joint Meeting on European Software Engineering Conference and Symposium on the Foundations of Software Engineering. 644–655. [136] Bart Van Oort, Luís Cruz, Maurício Aniche, and Arie Van Deursen. 2021. The prevalence of code smells in machine learning projects. In 2021 IEEE/ACM 1st workshop on AI engineering-software engineering for AI (WAIN). IEEE, 1–8. [137] Morteza Verdi, Ashkan Sami, Jafar Akhondali, Foutse Khomh, Gias Uddin, and Alireza Karami Motlagh. 2020. An empirical study of c++ vulnerabilities in crowd-sourced code examples. IEEE Transactions on Software Engineering 48,

## 5 (2020), 1497–1514.

[138] James Walden. 2020. The impact of a major security event on an open source project: The case of OpenSSL. In Proceedings of the 17th international conference on mining software repositories. 409–419. [139] Haoyu Wang, Hao Li, Li Li, Yao Guo, and Guoai Xu. 2018. Why are android apps removed from google play? a large-scale empirical study. In Proceedings of the 15th International Conference on Mining Software Repositories. 231–242. [140] Weichao Wang, Zhaopeng Meng, Zan Wang, Shuang Liu, and Jianye Hao. 2019. LoopFix: An approach to automatic repair of buggy loops. Journal of Systems and Software 156 (2019), 100–112. [141] Yingxu Wang and Vincent Chiew. 2013. Empirical studies on the functional complexity of software in large-scale software systems. In Advances in Abstract Intelligence and Soft Computing. IGI Global Scientific Publishing, 174–192. [142] Thomas Weber, Maximilian Brandmaier, Albrecht Schmidt, and Sven Mayer. 2024. Significant productivity gains through programming with large language models. Proceedings of the ACM on Human-Computer Interaction 8, EICS (2024), 1–29. [143] Katrine Wist, Malene Helsem, and Danilo Gligoroski. 2021. Vulnerability analysis of 2500 docker hub images. In Advances in Security, Networks, and Internet of Things: Proceedings from SAM’20, ICWN’20, ICOMP’20, and ESCS’20. Springer, 307–327. [144] Di Wu, Fangwen Mu, Lin Shi, Zhaoqiang Guo, Kui Liu, Weiguang Zhuang, Yuqi Zhong, and Li Zhang. 2024. iSMELL: Assembling LLMs with Expert Toolsets for Code Smell Detection and Refactoring. In Proceedings of the 39th IEEE/ACM International Conference on Automated Software Engineering. 1345–1357. [145] Shijie Wu, Ozan Irsoy, Steven Lu, Vadim Dabravolski, Mark Dredze, Sebastian Gehrmann, Prabhanjan Kambadur, David Rosenberg, and Gideon Mann. 2023. Bloomberggpt: A large language model for finance. arXiv preprint

arXiv:2303.17564 (2023). [146] Wenxin Xiao, Hao He, Weiwei Xu, Yuxia Zhang, and Minghui Zhou. 2023. How early participation determines long-term sustained activity in github projects?. In Proceedings of the 31st ACM Joint European Software Engineering Conference and Symposium on the Foundations of Software Engineering. 29–41. [147] Pravin Singh Yadav, Rajwant Singh Rao, Alok Mishra, and Manjari Gupta. 2024. Machine learning-based methods for code smell detection: a survey. Applied Sciences 14, 14 (2024), 6149. [148] Mehmet Ali Yalçinkaya and Ecir Uğur Küçüksille. 2024. Artificial Intelligence and Dynamic Analysis-Based Web Application Vulnerability Scanner. ISeCure 16, 1 (2024). [149] Aiko Yamashita and Steve Counsell. 2013. Code smells as system-level indicators of maintainability: An empirical study. Journal of Systems and Software 86, 10 (2013), 2639–2653. [150] Aiko Yamashita and Leon Moonen. 2012. Do code smells reflect important maintainability aspects?. In 2012 28th IEEE international conference on software maintenance (ICSM). IEEE, 306–315. [151] Ping Yu, Yijian Wu, Jiahan Peng, Jian Zhang, and Peicheng Xie. 2023. Towards understanding fixes of sonarqube static analysis violations: A large-scale empirical study. In 2023 IEEE International Conference on Software Analysis, Evolution and Reengineering (SANER). IEEE, 569–580. [152] Ahmed Zerouali, Eleni Constantinou, Tom Mens, Gregorio Robles, and Jesús González-Barahona. 2018. An empirical analysis of technical lag in npm package dependencies. In International conference on software reuse. Springer, 95–110. [153] Ahmed Zerouali, Tom Mens, Alexandre Decan, and Coen De Roover. 2022. On the impact of security vulnerabilities in the npm and RubyGems dependency networks. Empirical Software Engineering 27, 5 (2022), 107. [154] Markus Zimmermann, Cristian-Alexandru Staicu, Cam Tenny, and Michael Pradel. 2019. Small world with high risks: A study of security threats in the npm ecosystem. In 28th USENIX security symposium (USENIX Security 19). 995–1010. [155] Weiqin Zou, Weiqiang Zhang, Xin Xia, Reid Holmes, and Zhenyu Chen. 2019. Branch use in practice: A large-scale empirical study of 2,923 projects on github. In 2019 IEEE 19th International Conference on Software Quality, Reliability and Security (QRS). IEEE, 306–317.