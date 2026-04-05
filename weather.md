
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>삼성전자 주간 주가 동향 보고서 | 2026.03.30 - 04.03</title>
  <script src="https://cdn.jsdelivr.net/npm/apexcharts@3.45.2/dist/apexcharts.min.js"></script>
  <style>
    :root {
      --bg-primary: #0d1117;
      --bg-secondary: #161b22;
      --bg-card: #1c2128;
      --bg-card-hover: #22272e;
      --border: #30363d;
      --text-primary: #e6edf3;
      --text-secondary: #8b949e;
      --text-muted: #484f58;
      --blue: #58a6ff;
      --green: #3fb950;
      --red: #f85149;
      --yellow: #e3b341;
      --purple: #bc8cff;
      --orange: #ffa657;
      --samsung-blue: #1428A0;
      --samsung-blue-light: #1f3fc4;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      font-family: 'Segoe UI', -apple-system, BlinkMacSystemFont, sans-serif;
      background: var(--bg-primary);
      color: var(--text-primary);
      min-height: 100vh;
      line-height: 1.6;
    }

    /* ─── Header ─── */
    .header {
      background: linear-gradient(135deg, #0d1117 0%, #1428A0 50%, #0d1117 100%);
      border-bottom: 1px solid var(--border);
      padding: 32px 40px 28px;
      position: relative;
      overflow: hidden;
    }
    .header::before {
      content: '';
      position: absolute;
      top: -50%; left: -50%;
      width: 200%; height: 200%;
      background: radial-gradient(ellipse at 60% 50%, rgba(20,40,160,0.3) 0%, transparent 60%);
      pointer-events: none;
    }
    .header-top {
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 16px;
      position: relative;
    }
    .company-badge {
      display: flex;
      align-items: center;
      gap: 16px;
    }
    .company-logo {
      width: 52px; height: 52px;
      background: linear-gradient(135deg, #1428A0, #2947d6);
      border-radius: 12px;
      display: flex; align-items: center; justify-content: center;
      font-size: 22px; font-weight: 900;
      color: #fff;
      letter-spacing: -1px;
      box-shadow: 0 4px 20px rgba(20,40,160,0.5);
    }
    .company-info h1 {
      font-size: 24px; font-weight: 700;
      color: var(--text-primary);
    }
    .company-info .ticker {
      font-size: 13px; color: var(--text-secondary);
      margin-top: 2px;
    }
    .report-meta {
      text-align: right;
    }
    .report-meta .report-date {
      font-size: 13px; color: var(--text-secondary);
    }
    .report-meta .report-period {
      font-size: 16px; font-weight: 600; color: var(--blue);
      margin-top: 4px;
    }

    .price-hero {
      margin-top: 24px;
      display: flex;
      align-items: flex-end;
      gap: 20px;
      flex-wrap: wrap;
      position: relative;
    }
    .price-current {
      font-size: 48px; font-weight: 800;
      color: var(--text-primary);
      letter-spacing: -2px;
    }
    .price-unit { font-size: 20px; color: var(--text-secondary); margin-bottom: 6px; }
    .price-change {
      display: flex; align-items: center; gap: 8px;
      margin-bottom: 8px;
    }
    .change-badge {
      padding: 4px 12px; border-radius: 20px;
      font-size: 16px; font-weight: 700;
      background: rgba(63,185,80,0.15);
      color: var(--green);
      border: 1px solid rgba(63,185,80,0.3);
    }
    .change-badge.negative {
      background: rgba(248,81,73,0.15);
      color: var(--red);
      border-color: rgba(248,81,73,0.3);
    }
    .weekly-change {
      font-size: 13px; color: var(--text-secondary);
    }

    /* ─── Layout ─── */
    .container { max-width: 1280px; margin: 0 auto; padding: 28px 40px 60px; }

    /* ─── Metric Cards ─── */
    .metrics-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(190px, 1fr));
      gap: 12px;
      margin-bottom: 28px;
    }
    .metric-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 18px;
      transition: background 0.2s, border-color 0.2s;
    }
    .metric-card:hover {
      background: var(--bg-card-hover);
      border-color: var(--blue);
    }
    .metric-label {
      font-size: 11px; font-weight: 600;
      color: var(--text-muted);
      text-transform: uppercase;
      letter-spacing: 0.8px;
      margin-bottom: 8px;
    }
    .metric-value {
      font-size: 20px; font-weight: 700;
      color: var(--text-primary);
      letter-spacing: -0.5px;
    }
    .metric-sub {
      font-size: 12px; color: var(--text-secondary);
      margin-top: 4px;
    }
    .metric-up { color: var(--green); }
    .metric-down { color: var(--red); }

    /* ─── Section ─── */
    .section { margin-bottom: 28px; }
    .section-title {
      font-size: 16px; font-weight: 700;
      color: var(--text-primary);
      margin-bottom: 14px;
      padding-bottom: 10px;
      border-bottom: 1px solid var(--border);
      display: flex; align-items: center; gap: 8px;
    }
    .section-title .icon {
      width: 24px; height: 24px;
      background: rgba(88,166,255,0.15);
      border-radius: 6px;
      display: inline-flex; align-items: center; justify-content: center;
      font-size: 13px;
    }

    /* ─── Chart Grid ─── */
    .chart-grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 16px;
    }
    .chart-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 20px 20px 12px;
    }
    .chart-title {
      font-size: 13px; font-weight: 600;
      color: var(--text-secondary);
      margin-bottom: 14px;
      text-transform: uppercase;
      letter-spacing: 0.6px;
    }
    #candlestick-chart { height: 320px; }
    #volume-chart { height: 160px; }
    #performance-chart { height: 200px; }

    /* ─── Table ─── */
    .table-wrap {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 12px;
      overflow: hidden;
    }
    table { width: 100%; border-collapse: collapse; }
    thead th {
      background: var(--bg-secondary);
      padding: 12px 16px;
      font-size: 11px; font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 0.8px;
      color: var(--text-muted);
      text-align: right;
    }
    thead th:first-child { text-align: left; }
    tbody tr {
      border-top: 1px solid var(--border);
      transition: background 0.15s;
    }
    tbody tr:hover { background: rgba(88,166,255,0.05); }
    tbody td {
      padding: 13px 16px;
      font-size: 14px;
      text-align: right;
      color: var(--text-primary);
    }
    tbody td:first-child { text-align: left; font-weight: 600; }
    .td-up { color: var(--green); font-weight: 600; }
    .td-down { color: var(--red); font-weight: 600; }
    .td-neutral { color: var(--text-secondary); }
    .day-badge {
      display: inline-block;
      padding: 2px 8px; border-radius: 4px;
      font-size: 11px; font-weight: 700;
      margin-left: 6px;
    }
    .day-up { background: rgba(63,185,80,0.15); color: var(--green); }
    .day-down { background: rgba(248,81,73,0.15); color: var(--red); }

    /* ─── News ─── */
    .news-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(380px, 1fr));
      gap: 12px;
    }
    .news-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 18px;
      transition: border-color 0.2s, background 0.2s;
      cursor: pointer;
    }
    .news-card:hover {
      border-color: var(--blue);
      background: var(--bg-card-hover);
    }
    .news-tag {
      display: inline-block;
      padding: 2px 8px; border-radius: 4px;
      font-size: 10px; font-weight: 700;
      text-transform: uppercase; letter-spacing: 0.5px;
      margin-bottom: 10px;
    }
    .tag-ai { background: rgba(188,140,255,0.15); color: var(--purple); }
    .tag-earnings { background: rgba(227,179,65,0.15); color: var(--yellow); }
    .tag-chip { background: rgba(88,166,255,0.15); color: var(--blue); }
    .tag-product { background: rgba(63,185,80,0.15); color: var(--green); }
    .tag-market { background: rgba(255,166,87,0.15); color: var(--orange); }
    .news-title {
      font-size: 14px; font-weight: 600;
      color: var(--text-primary);
      margin-bottom: 8px;
      line-height: 1.5;
    }
    .news-summary {
      font-size: 12px; color: var(--text-secondary);
      line-height: 1.6;
      display: -webkit-box;
      -webkit-line-clamp: 3;
      -webkit-box-orient: vertical;
      overflow: hidden;
    }

    /* ─── Analyst ─── */
    .analyst-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
    }
    .analyst-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 20px;
    }
    .analyst-row {
      display: flex; justify-content: space-between; align-items: center;
      margin-bottom: 12px;
    }
    .analyst-label { font-size: 13px; color: var(--text-secondary); }
    .analyst-value { font-size: 16px; font-weight: 700; color: var(--text-primary); }
    .target-bar {
      width: 100%; height: 6px;
      background: var(--bg-secondary);
      border-radius: 3px;
      margin-top: 12px;
      position: relative;
    }
    .target-fill {
      height: 100%; border-radius: 3px;
      background: linear-gradient(90deg, var(--red), var(--yellow), var(--green));
    }
    .target-pointer {
      position: absolute; top: -4px;
      width: 14px; height: 14px;
      border-radius: 50%;
      background: var(--blue);
      border: 2px solid var(--bg-primary);
      transform: translateX(-50%);
    }
    .price-range-labels {
      display: flex; justify-content: space-between;
      margin-top: 6px;
      font-size: 11px; color: var(--text-muted);
    }
    .consensus-ring { position: relative; width: 120px; height: 120px; margin: 0 auto; }
    .consensus-text {
      position: absolute; top: 50%; left: 50%;
      transform: translate(-50%, -50%);
      text-align: center;
    }
    .consensus-text .score { font-size: 28px; font-weight: 800; color: var(--green); }
    .consensus-text .label { font-size: 11px; color: var(--text-secondary); }

    /* ─── Footer ─── */
    .footer {
      margin-top: 40px;
      padding-top: 20px;
      border-top: 1px solid var(--border);
      display: flex; justify-content: space-between; align-items: center;
      flex-wrap: wrap; gap: 12px;
    }
    .footer-text { font-size: 12px; color: var(--text-muted); }
    .data-source {
      font-size: 11px; color: var(--text-muted);
      display: flex; align-items: center; gap: 6px;
    }
    .source-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--blue); }

    /* ─── Divider ─── */
    .divider { height: 1px; background: var(--border); margin: 28px 0; }

    @media (max-width: 768px) {
      .header { padding: 24px 20px; }
      .container { padding: 20px; }
      .price-current { font-size: 36px; }
      .analyst-grid { grid-template-columns: 1fr; }
      .news-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>

<!-- ═══════════════════════════════ HEADER ═══════════════════════════════ -->
<div class="header">
  <div class="header-top">
    <div class="company-badge">
      <div class="company-logo">SE</div>
      <div class="company-info">
        <h1>삼성전자</h1>
        <div class="ticker">005930.KS &nbsp;·&nbsp; KSE &nbsp;·&nbsp; 소비자 전자</div>
      </div>
    </div>
    <div class="report-meta">
      <div class="report-date">보고서 생성일: 2026.04.05 (일)</div>
      <div class="report-period">주간 주가 동향 · 2026.03.30 ~ 04.03</div>
    </div>
  </div>

  <div class="price-hero">
    <div>
      <div style="font-size:12px;color:var(--text-muted);margin-bottom:4px;">최근 종가 (2026.04.03)</div>
      <div style="display:flex;align-items:baseline;gap:6px;">
        <div class="price-current">186,200</div>
        <div class="price-unit">KRW</div>
      </div>
    </div>
    <div class="price-change">
      <span class="change-badge">▲ +7,800 (+4.37%)</span>
      <span class="weekly-change">전일 대비 · 주간 수익률 +5.62%</span>
    </div>
  </div>
</div>

<!-- ═══════════════════════════════ BODY ═══════════════════════════════ -->
<div class="container">

  <!-- 핵심 지표 -->
  <div class="metrics-grid" style="margin-top:0;">
    <div class="metric-card">
      <div class="metric-label">주간 시작가</div>
      <div class="metric-value">176,300</div>
      <div class="metric-sub">2026.03.30 종가</div>
    </div>
    <div class="metric-card">
      <div class="metric-label">주간 최고가</div>
      <div class="metric-value metric-up">190,800</div>
      <div class="metric-sub">2026.04.01 장중</div>
    </div>
    <div class="metric-card">
      <div class="metric-label">주간 최저가</div>
      <div class="metric-value metric-down">167,000</div>
      <div class="metric-sub">2026.03.31 장중</div>
    </div>
    <div class="metric-card">
      <div class="metric-label">주간 등락폭</div>
      <div class="metric-value metric-up">+5.62%</div>
      <div class="metric-sub">176,300 → 186,200</div>
    </div>
    <div class="metric-card">
      <div class="metric-label">주간 총거래량</div>
      <div class="metric-value">152.1M</div>
      <div class="metric-sub">일평균 30.4M주</div>
    </div>
    <div class="metric-card">
      <div class="metric-label">시가총액</div>
      <div class="metric-value">1,244.9조</div>
      <div class="metric-sub">KRW</div>
    </div>
    <div class="metric-card">
      <div class="metric-label">52주 최저 대비</div>
      <div class="metric-value metric-up">+251.8%</div>
      <div class="metric-sub">52주 최저 52,900</div>
    </div>
    <div class="metric-card">
      <div class="metric-label">Forward P/E</div>
      <div class="metric-value">6.48x</div>
      <div class="metric-sub">배당수익률 1.27%</div>
    </div>
  </div>

  <!-- 차트 섹션 -->
  <div class="section">
    <div class="section-title">
      <span class="icon">📊</span> 캔들스틱 차트 · 일별 가격 동향
    </div>
    <div class="chart-card">
      <div class="chart-title">Open / High / Low / Close (KRW)</div>
      <div id="candlestick-chart"></div>
    </div>
  </div>

  <div class="section">
    <div class="section-title">
      <span class="icon">📈</span> 거래량 분석
    </div>
    <div class="chart-card">
      <div class="chart-title">일별 거래량 (단위: 만주)</div>
      <div id="volume-chart"></div>
    </div>
  </div>

  <div class="section">
    <div class="section-title">
      <span class="icon">📉</span> 일별 등락률 추이
    </div>
    <div class="chart-card">
      <div class="chart-title">전일 대비 등락률 (%)</div>
      <div id="performance-chart"></div>
    </div>
  </div>

  <!-- 일별 데이터 테이블 -->
  <div class="section">
    <div class="section-title">
      <span class="icon">📋</span> 일별 OHLCV 상세 데이터
    </div>
    <div class="table-wrap">
      <table>
        <thead>
          <tr>
            <th>날짜</th>
            <th>시가</th>
            <th>고가</th>
            <th>저가</th>
            <th>종가</th>
            <th>등락</th>
            <th>등락률</th>
            <th>거래량</th>
            <th>거래대금 (억)</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>2026.03.30 (월)
              <span class="day-badge day-up">▲ 상승</span>
            </td>
            <td>171,000</td>
            <td class="metric-up">176,650</td>
            <td class="metric-down">170,600</td>
            <td class="td-up">176,300</td>
            <td class="td-neutral">— </td>
            <td class="td-neutral">기준일</td>
            <td>22,269,147</td>
            <td>39,244</td>
          </tr>
          <tr>
            <td>2026.03.31 (화)
              <span class="day-badge day-down">▼ 하락</span>
            </td>
            <td>170,000</td>
            <td class="metric-up">174,700</td>
            <td class="metric-down">167,000</td>
            <td class="td-down">167,200</td>
            <td class="td-down">▼ 9,100</td>
            <td class="td-down">-5.16%</td>
            <td>38,659,593</td>
            <td>64,638</td>
          </tr>
          <tr>
            <td>2026.04.01 (수)
              <span class="day-badge day-up">▲ 상승</span>
            </td>
            <td>179,000</td>
            <td class="metric-up">190,800</td>
            <td class="metric-down">178,000</td>
            <td class="td-up">189,650</td>
            <td class="td-up">▲ 22,450</td>
            <td class="td-up">+13.43%</td>
            <td>32,390,251</td>
            <td>61,382</td>
          </tr>
          <tr>
            <td>2026.04.02 (목)
              <span class="day-badge day-down">▼ 하락</span>
            </td>
            <td>192,600</td>
            <td class="metric-up">193,600</td>
            <td class="metric-down">175,000</td>
            <td class="td-down">178,400</td>
            <td class="td-down">▼ 11,250</td>
            <td class="td-down">-5.93%</td>
            <td>38,615,231</td>
            <td>68,904</td>
          </tr>
          <tr>
            <td>2026.04.03 (금)
              <span class="day-badge day-up">▲ 상승</span>
            </td>
            <td>184,200</td>
            <td class="metric-up">187,200</td>
            <td class="metric-down">182,700</td>
            <td class="td-up">186,200</td>
            <td class="td-up">▲ 7,800</td>
            <td class="td-up">+4.37%</td>
            <td>20,194,447</td>
            <td>37,601</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>

  <!-- 애널리스트 분석 -->
  <div class="section">
    <div class="section-title">
      <span class="icon">🔍</span> 애널리스트 분석 · 목표주가
    </div>
    <div class="analyst-grid">
      <div class="analyst-card">
        <div class="analyst-row">
          <span class="analyst-label">현재 주가</span>
          <span class="analyst-value">186,200</span>
        </div>
        <div class="analyst-row">
          <span class="analyst-label">목표주가 (평균)</span>
          <span class="analyst-value" style="color:var(--blue)">239,873</span>
        </div>
        <div class="analyst-row">
          <span class="analyst-label">목표주가 (중앙값)</span>
          <span class="analyst-value" style="color:var(--blue)">250,000</span>
        </div>
        <div class="analyst-row">
          <span class="analyst-label">상승 여력 (평균 기준)</span>
          <span class="analyst-value metric-up">+28.8%</span>
        </div>
        <div class="target-bar">
          <div class="target-fill" style="width:100%;"></div>
          <div class="target-pointer" style="left: calc((186200 - 110000) / (340000 - 110000) * 100%);"></div>
        </div>
        <div class="price-range-labels">
          <span>최저 110,000</span>
          <span>목표 239,873</span>
          <span>최고 340,000</span>
        </div>
      </div>
      <div class="analyst-card">
        <div style="margin-bottom:16px;">
          <div class="analyst-row">
            <span class="analyst-label">분석 대상 애널리스트 수</span>
            <span class="analyst-value">37명</span>
          </div>
          <div class="analyst-row">
            <span class="analyst-label">Forward P/E</span>
            <span class="analyst-value">6.48x</span>
          </div>
          <div class="analyst-row">
            <span class="analyst-label">EV/EBITDA</span>
            <span class="analyst-value">12.26x</span>
          </div>
          <div class="analyst-row">
            <span class="analyst-label">매출 성장률 (YoY)</span>
            <span class="analyst-value metric-up">+23.8%</span>
          </div>
          <div class="analyst-row">
            <span class="analyst-label">순이익 성장률 (YoY)</span>
            <span class="analyst-value metric-up">+155.4%</span>
          </div>
          <div class="analyst-row">
            <span class="analyst-label">베타 (Beta)</span>
            <span class="analyst-value">1.211</span>
          </div>
        </div>
        <div id="analyst-donut-chart" style="height:120px;"></div>
      </div>
    </div>
  </div>

  <!-- 뉴스 -->
  <div class="section">
    <div class="section-title">
      <span class="icon">📰</span> 주요 관련 뉴스
    </div>
    <div class="news-grid">
      <div class="news-card">
        <span class="news-tag tag-ai">AI 반도체</span>
        <div class="news-title">AMD, 삼성전자와 HBM4 공급 협력 확대</div>
        <div class="news-summary">AMD와 삼성전자가 차세대 AI 가속기(Instinct)용 HBM4 메모리 공급 및 EPYC CPU용 고급 DRAM 협력을 확대. 삼성이 AMD 칩 파운드리 파트너 가능성도 탐색 중으로, AI 인프라 공급망 강화에 기여.</div>
      </div>
      <div class="news-card">
        <span class="news-tag tag-earnings">실적 전망</span>
        <div class="news-title">1분기 영업이익 6배 급증 전망 · 사상 최대 실적 기대</div>
        <div class="news-summary">AI 붐에 따른 메모리 칩 가격 급등으로 삼성전자 1Q26 영업이익 40.5조원(+6배 YoY) 예상. 매출은 50% 증가 전망. 29개 증권사 LSEG SmartEstimate 기반.</div>
      </div>
      <div class="news-card">
        <span class="news-tag tag-chip">반도체 시장</span>
        <div class="news-title">한국 반도체주, 지정학적 불안에 최대 24% 급락 후 매수 기회</div>
        <div class="news-summary">삼성전자·SK하이닉스 밸류에이션이 지정학적 리스크 기반 매도세로 저평가 국면 진입. 상위 펀드들은 현재 구간을 적극 매수 기회로 평가.</div>
      </div>
      <div class="news-card">
        <span class="news-tag tag-product">신제품</span>
        <div class="news-title">Galaxy S26 Ultra, 하드웨어 기반 프라이버시 디스플레이 탑재</div>
        <div class="news-summary">삼성전자, Galaxy S26 Ultra에 화면 자체에 시야각 제한 기술 내장한 Privacy Display 하드웨어 도입. 플래그십 라인업의 프리미엄 차별화 강화.</div>
      </div>
      <div class="news-card">
        <span class="news-tag tag-market">시장 분석</span>
        <div class="news-title">삼성전자, 내재 가치 대비 저평가 종목으로 분석</div>
        <div class="news-summary">글로벌 지정학적 긴장 및 에너지 시장 변동성 속에서도 삼성전자는 내재 가치 이하에서 거래 중인 유망 종목으로 지목됨.</div>
      </div>
      <div class="news-card">
        <span class="news-tag tag-ai">글로벌 AI</span>
        <div class="news-title">AMD, NAVER Cloud와 한국 소버린 AI 인프라 구축 협력</div>
        <div class="news-summary">AMD와 NAVER Cloud가 한국 소버린 AI 인프라 프로젝트 협력 합의. 삼성의 HBM4 기술이 해당 프로젝트의 핵심 공급망으로 연결되며 반도체 수요 확대 기대.</div>
      </div>
    </div>
  </div>

  <!-- 주간 요약 -->
  <div class="section">
    <div class="section-title">
      <span class="icon">📝</span> 주간 동향 종합 요약
    </div>
    <div style="background:var(--bg-card);border:1px solid var(--border);border-radius:12px;padding:24px;">
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:20px;">
        <div>
          <div style="font-size:13px;font-weight:700;color:var(--blue);margin-bottom:12px;text-transform:uppercase;letter-spacing:0.8px;">강세 요인</div>
          <ul style="list-style:none;display:flex;flex-direction:column;gap:8px;">
            <li style="font-size:13px;color:var(--text-secondary);padding-left:16px;position:relative;">
              <span style="position:absolute;left:0;color:var(--green);">▲</span>
              AMD와 HBM4 공급 협력 확대 · AI 반도체 수요 수혜 확인
            </li>
            <li style="font-size:13px;color:var(--text-secondary);padding-left:16px;position:relative;">
              <span style="position:absolute;left:0;color:var(--green);">▲</span>
              1Q26 사상 최대 실적 달성 기대 (영업이익 +6배 YoY)
            </li>
            <li style="font-size:13px;color:var(--text-secondary);padding-left:16px;position:relative;">
              <span style="position:absolute;left:0;color:var(--green);">▲</span>
              4/3 기준 주간 +5.62% 상승 마감
            </li>
            <li style="font-size:13px;color:var(--text-secondary);padding-left:16px;position:relative;">
              <span style="position:absolute;left:0;color:var(--green);">▲</span>
              애널리스트 평균 목표주가 239,873원 · 상승여력 28.8%
            </li>
            <li style="font-size:13px;color:var(--text-secondary);padding-left:16px;position:relative;">
              <span style="position:absolute;left:0;color:var(--green);">▲</span>
              글로벌 메모리 반도체 슈퍼사이클 지속
            </li>
          </ul>
        </div>
        <div>
          <div style="font-size:13px;font-weight:700;color:var(--orange);margin-bottom:12px;text-transform:uppercase;letter-spacing:0.8px;">위험 요인</div>
          <ul style="list-style:none;display:flex;flex-direction:column;gap:8px;">
            <li style="font-size:13px;color:var(--text-secondary);padding-left:16px;position:relative;">
              <span style="position:absolute;left:0;color:var(--red);">▼</span>
              3/31 -5.16%, 4/2 -5.93% 급락 · 변동성 확대
            </li>
            <li style="font-size:13px;color:var(--text-secondary);padding-left:16px;position:relative;">
              <span style="position:absolute;left:0;color:var(--red);">▼</span>
              지정학적 리스크로 인한 외국인 투자 심리 위축
            </li>
            <li style="font-size:13px;color:var(--text-secondary);padding-left:16px;position:relative;">
              <span style="position:absolute;left:0;color:var(--red);">▼</span>
              52주 최고 223,000 대비 여전히 -16.5% 할인
            </li>
            <li style="font-size:13px;color:var(--text-secondary);padding-left:16px;position:relative;">
              <span style="position:absolute;left:0;color:var(--red);">▼</span>
              글로벌 소비자 전자 수요 회복 속도 불확실
            </li>
            <li style="font-size:13px;color:var(--text-secondary);padding-left:16px;position:relative;">
              <span style="position:absolute;left:0;color:var(--red);">▼</span>
              Beta 1.21 · 시장 대비 높은 민감도
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>

  <!-- Footer -->
  <div class="footer">
    <div class="footer-text">본 보고서는 투자 권유가 아니며, 투자의 최종 책임은 투자자 본인에게 있습니다.</div>
    <div class="data-source">
      <span class="source-dot"></span>
      데이터 출처: Yahoo Finance &nbsp;·&nbsp; 생성: 2026.04.05
    </div>
  </div>

</div>

<!-- ═══════════════════════════════ SCRIPTS ═══════════════════════════════ -->
<script>
  // ─── 캔들스틱 차트 ───
  const candleOptions = {
    series: [{
      name: '삼성전자',
      data: [
        { x: '03/30', y: [171000, 176650, 170600, 176300] },
        { x: '03/31', y: [170000, 174700, 167000, 167200] },
        { x: '04/01', y: [179000, 190800, 178000, 189650] },
        { x: '04/02', y: [192600, 193600, 175000, 178400] },
        { x: '04/03', y: [184200, 187200, 182700, 186200] },
      ]
    }],
    chart: {
      type: 'candlestick',
      height: 320,
      background: 'transparent',
      toolbar: { show: false },
      animations: { enabled: true, speed: 600 }
    },
    theme: { mode: 'dark' },
    plotOptions: {
      candlestick: {
        colors: {
          upward: '#3fb950',
          downward: '#f85149'
        },
        wick: { useFillColor: true }
      }
    },
    xaxis: {
      type: 'category',
      labels: { style: { colors: '#8b949e', fontSize: '12px' } },
      axisBorder: { show: false },
      axisTicks: { show: false }
    },
    yaxis: {
      labels: {
        formatter: v => v.toLocaleString() + '원',
        style: { colors: '#8b949e', fontSize: '11px' }
      },
      min: 160000,
      max: 200000
    },
    grid: {
      borderColor: '#30363d',
      strokeDashArray: 4
    },
    tooltip: {
      theme: 'dark',
      custom: function({ seriesIndex, dataPointIndex, w }) {
        const o = w.globals.seriesCandleO[seriesIndex][dataPointIndex];
        const h = w.globals.seriesCandleH[seriesIndex][dataPointIndex];
        const l = w.globals.seriesCandleL[seriesIndex][dataPointIndex];
        const c = w.globals.seriesCandleC[seriesIndex][dataPointIndex];
        const isUp = c >= o;
        const color = isUp ? '#3fb950' : '#f85149';
        const arrow = isUp ? '▲' : '▼';
        return `<div style="background:#1c2128;border:1px solid #30363d;border-radius:8px;padding:12px 16px;font-family:sans-serif;">
          <div style="font-weight:700;color:${color};margin-bottom:8px;">${arrow} ${c.toLocaleString()}원</div>
          <div style="font-size:12px;color:#8b949e;display:grid;grid-template-columns:auto auto;gap:4px 16px;">
            <span>시가</span><span style="color:#e6edf3;">${o.toLocaleString()}</span>
            <span>고가</span><span style="color:#3fb950;">${h.toLocaleString()}</span>
            <span>저가</span><span style="color:#f85149;">${l.toLocaleString()}</span>
            <span>종가</span><span style="color:${color};">${c.toLocaleString()}</span>
          </div>
        </div>`;
      }
    }
  };
  new ApexCharts(document.querySelector('#candlestick-chart'), candleOptions).render();

  // ─── 거래량 차트 ───
  const volumes = [2226.9, 3865.9, 3239.0, 3861.5, 2019.4]; // 만주
  const volColors = ['#3fb950', '#f85149', '#3fb950', '#f85149', '#3fb950'];
  const volumeOptions = {
    series: [{ name: '거래량(만주)', data: volumes }],
    chart: {
      type: 'bar',
      height: 160,
      background: 'transparent',
      toolbar: { show: false },
      animations: { enabled: true, speed: 600 }
    },
    theme: { mode: 'dark' },
    plotOptions: {
      bar: {
        borderRadius: 4,
        columnWidth: '55%',
        distributed: true
      }
    },
    colors: volColors,
    dataLabels: {
      enabled: true,
      formatter: v => v.toFixed(1) + 'M',
      style: { fontSize: '11px', colors: ['#e6edf3'] }
    },
    xaxis: {
      categories: ['03/30', '03/31', '04/01', '04/02', '04/03'],
      labels: { style: { colors: '#8b949e', fontSize: '12px' } },
      axisBorder: { show: false },
      axisTicks: { show: false }
    },
    yaxis: {
      labels: {
        formatter: v => v.toFixed(0) + 'M',
        style: { colors: '#8b949e', fontSize: '11px' }
      }
    },
    grid: { borderColor: '#30363d', strokeDashArray: 4 },
    legend: { show: false },
    tooltip: {
      theme: 'dark',
      y: { formatter: v => v.toFixed(2) + '만주' }
    }
  };
  new ApexCharts(document.querySelector('#volume-chart'), volumeOptions).render();

  // ─── 등락률 차트 ───
  const perfData = [-5.16, 13.43, -5.93, 4.37]; // 3/31~4/3 (3/30 기준일 제외)
  const perfColors = perfData.map(v => v >= 0 ? '#3fb950' : '#f85149');
  const perfOptions = {
    series: [{ name: '등락률', data: perfData }],
    chart: {
      type: 'bar',
      height: 200,
      background: 'transparent',
      toolbar: { show: false },
      animations: { enabled: true, speed: 600 }
    },
    theme: { mode: 'dark' },
    plotOptions: {
      bar: {
        borderRadius: 4,
        columnWidth: '50%',
        distributed: true
      }
    },
    colors: perfColors,
    dataLabels: {
      enabled: true,
      formatter: v => (v >= 0 ? '+' : '') + v.toFixed(2) + '%',
      style: { fontSize: '12px', fontWeight: 700, colors: ['#e6edf3'] }
    },
    xaxis: {
      categories: ['03/31', '04/01', '04/02', '04/03'],
      labels: { style: { colors: '#8b949e', fontSize: '12px' } },
      axisBorder: { show: false },
      axisTicks: { show: false }
    },
    yaxis: {
      labels: {
        formatter: v => v.toFixed(1) + '%',
        style: { colors: '#8b949e', fontSize: '11px' }
      }
    },
    grid: {
      borderColor: '#30363d',
      strokeDashArray: 4,
      yaxis: { lines: { show: true } }
    },
    annotations: {
      yaxis: [{
        y: 0,
        borderColor: '#484f58',
        strokeDashArray: 0
      }]
    },
    legend: { show: false },
    tooltip: {
      theme: 'dark',
      y: { formatter: v => (v >= 0 ? '+' : '') + v.toFixed(2) + '%' }
    }
  };
  new ApexCharts(document.querySelector('#performance-chart'), perfOptions).render();

  // ─── 애널리스트 도넛 ───
  const donutOptions = {
    series: [75, 20, 5],
    chart: {
      type: 'donut',
      height: 120,
      background: 'transparent',
    },
    theme: { mode: 'dark' },
    labels: ['매수', '중립', '매도'],
    colors: ['#3fb950', '#e3b341', '#f85149'],
    legend: {
      position: 'right',
      labels: { colors: '#8b949e' },
      fontSize: '11px'
    },
    dataLabels: {
      enabled: false
    },
    plotOptions: {
      pie: {
        donut: {
          size: '65%',
          labels: {
            show: true,
            total: {
              show: true,
              label: '매수 우세',
              color: '#3fb950',
              fontSize: '11px',
              formatter: () => '37명'
            }
          }
        }
      }
    },
    tooltip: {
      theme: 'dark',
      y: { formatter: v => v + '%' }
    }
  };
  new ApexCharts(document.querySelector('#analyst-donut-chart'), donutOptions).render();
</script>
</body>
</html>
