보내주신 시안의 글씨 배치, 디자인, 그리고 각 버튼(업적 보기, 상담 신청)과 메뉴들을 원하는 페이지나 링크로 이동할 수 있도록 수정한 전체 코드를 작성해 드립니다.

각 항목마다 링크(href="...")를 넣어두었으니, 원하시는 주소나 페이지 이동 경로(예: #portfolio, tel:010-1234-5678, 외부 링크 등)로 수정해서 사용하시면 됩니다.

HTML
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>더나은생활연구소 - 모바일 회사소개서</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Apple SD Gothic Neo', 'Noto Sans KR', sans-serif; -webkit-font-smoothing: antialiased; }
        body { background-color: #f4f6f9; color: #333; line-height: 1.5; display: flex; justify-content: center; overflow-x: hidden; }
        
        .mobile-container { 
            width: 100%; 
            max-width: 480px; 
            background: #ffffff; 
            min-height: 100vh; 
            box-shadow: 0 0 20px rgba(0,0,0,0.05); 
            position: relative; 
        }

        /* --- 메인 시안 스타일 구현 --- */
        .main-hero {
            padding: 40px 24px 50px 24px;
            background: #ffffff;
            position: relative;
            overflow: hidden;
            border-bottom: 8px solid #f8f9fa;
        }

        /* 상단 로고 영역 */
        .hero-top {
            display: flex;
            justify-content: flex-end;
            align-items: center;
            margin-bottom: 30px;
        }
        .logo-box {
            display: flex;
            align-items: center;
            gap: 8px;
            text-decoration: none;
        }
        .logo-box img {
            width: 36px;
            height: 36px;
            object-fit: contain;
        }
        .logo-box span {
            font-size: 0.95rem;
            font-weight: 700;
            color: #111;
            letter-spacing: -0.5px;
        }

        /* 텍스트 영역 */
        .hero-subtitle-top {
            font-size: 0.95rem;
            color: #555;
            font-weight: 400;
            margin-bottom: 8px;
        }

        .hero-title {
            font-size: 2.1rem;
            font-weight: 800;
            color: #111;
            letter-spacing: -1px;
            margin-bottom: 16px;
            line-height: 1.2;
        }

        .hero-subtitle-bottom {
            font-size: 1.15rem;
            font-weight: 600;
            color: #222;
            margin-bottom: 24px;
            line-height: 1.4;
        }
        .hero-subtitle-bottom .highlight {
            color: #003366; /* ONE-STOP 컨설팅 포인트 컬러 */
            font-weight: 800;
        }

        /* 카테고리 구분선 태그 (링크 이동 가능하도록 스타일 적용) */
        .categories {
            display: flex;
            align-items: center;
            flex-wrap: wrap;
            gap: 8px 0;
            font-size: 0.95rem;
            margin-bottom: 45px;
        }
        .categories a {
            padding: 0 10px;
            color: #333;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.2s;
        }
        .categories a:hover {
            color: #003366;
        }
        .categories a:first-child {
            padding-left: 0;
        }
        .categories a:not(:last-child) {
            border-right: 1px solid #ccc;
        }

        /* 하단 일러스트 및 버튼 영역 레이아웃 */
        .hero-bottom-content {
            display: flex;
            align-items: flex-end;
            justify-content: space-between;
            gap: 15px;
            position: relative;
        }

        /* 파란 원형 배경 일러스트 */
        .illustration-wrapper {
            width: 62%;
            position: relative;
        }
        .blue-circle-bg {
            width: 100%;
            aspect-ratio: 1;
            background-color: #0000a0; /* 진한 파란색 원 */
            border-radius: 50%;
            position: absolute;
            bottom: -10px;
            left: -15px;
            z-index: 1;
        }
        .illustration-img {
            width: 115%;
            max-width: none;
            position: relative;
            z-index: 2;
            display: block;
            object-fit: contain;
        }

        /* 노란색 버튼 그룹 */
        .action-buttons {
            width: 38%;
            display: flex;
            flex-direction: column;
            gap: 12px;
            z-index: 3;
            padding-bottom: 10px;
        }

        .cta-btn {
            display: block;
            width: 100%;
            padding: 14px 10px;
            background-color: #ffcc00; /* 산뜻한 노란색 */
            color: #111;
            text-align: center;
            font-size: 1rem;
            font-weight: 700;
            text-decoration: none;
            border-radius: 24px;
            box-shadow: 0 4px 10px rgba(255, 204, 0, 0.3);
            transition: transform 0.1s, background-color 0.2s;
        }
        .cta-btn:active {
            transform: scale(0.96);
            background-color: #e6b800;
        }

        /* 컨텐츠 섹션 예시 스타일 */
        .section-block {
            padding: 50px 24px;
            border-bottom: 1px solid #eee;
        }
        .section-block h2 {
            font-size: 1.4rem;
            margin-bottom: 15px;
            color: #111;
        }

        /* 푸터 */
        footer { padding: 30px 24px; text-align: center; font-size: 0.85rem; color: #888; background: #fafafa; }
    </style>
</head>
<body>

    <div class="mobile-container">
        
        <!-- 메인 오프닝 화면 -->
        <header class="main-hero">
            <!-- 우측 상단 로고 (클릭 시 맨 위로 이동 또는 특정 링크 연결 가능) -->
            <div class="hero-top">
                <a href="#" class="logo-box">
                    <img src="https://i.imgur.com/8Q8Q8Q8.png" alt="로고" onerror="this.style.display='none'">
                    <span>더나은생활연구소</span>
                </a>
            </div>

            <!-- 메인 카피 텍스트 -->
            <div class="hero-subtitle-top">식품의 안전과 기업의 성장을 함께하는</div>
            <h1 class="hero-title">더나은생활연구소</h1>
            <div class="hero-subtitle-bottom">
                식약처 인허가부터 사후관리까지<br>
                <span class="highlight">ONE-STOP 컨설팅</span>
            </div>

            <!-- 카테고리 태그 (각각 다른 페이지나 섹션으로 링크 연결) -->
            <div class="categories">
                <a href="#licensing">식약처 인허가</a>
                <a href="#cosmetics">화장품</a>
                <a href="#haccp">HACCP</a>
                <a href="#quasi-drug">의약외품</a>
            </div>

            <!-- 일러스트 및 노란색 링크 버튼 영역 -->
            <div class="hero-bottom-content">
                <div class="illustration-wrapper">
                    <div class="blue-circle-bg"></div>
                    <img src="https://i.imgur.com/qM7i52C.png" alt="전문가 팀 일러스트" class="illustration-img">
                </div>
                
                <div class="action-buttons">
                    <!-- 업적 보기 버튼 (클릭 시 아래 업적 섹션 또는 외부 포트폴리오로 이동) -->
                    <a href="#portfolio" class="cta-btn">업적 보기</a>
                    <!-- 상담 신청 버튼 (클릭 시 상담 폼이나 전화/카카오톡 채널로 연결) -->
                    <a href="#contact" class="cta-btn">상담 신청</a>
                </div>
            </div>
        </header>

        <!-- 링크 이동 테스트용 하단 섹션들 -->
        <section id="portfolio" class="section-block">
            <h2>🏆 업적 및 포트폴리오</h2>
            <p>여기에 회사의 주요 실적과 성공 사례가 들어갑니다.</p>
        </section>

        <section id="licensing" class="section-block">
            <h2>📝 식약처 인허가 안내</h2>
            <p>식약처 인허가 관련 상세 설명 내용입니다.</p>
        </section>

        <section id="contact" class="section-block">
            <h2>📞 상담 신청</h2>
            <p>문의하실 내용을 남겨주시면 빠르게 연락드리겠습니다.</p>
        </section>

        <!-- 푸터 -->
        <footer>
            &copy; 2026 더나은생활연구소. All rights reserved.
        </footer>

    </div>

</body>
</html>
