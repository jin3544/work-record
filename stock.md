<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="삼성전자(005930) 주간 주가 동향 보고서 | 2026.03.30 - 04.03">
  <meta name="robots" content="noindex, nofollow">
  <meta property="og:title" content="삼성전자 주간 주가 동향 보고서 | 2026.03.30 - 04.03">
  <meta property="og:description" content="삼성전자 주간 주가 동향 · 종가 186,200원 · 주간 수익률 +5.62%">
  <meta property="og:type" content="article">
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
    .company-badge { display: flex; align-items: center; gap: 16px; }
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
    .company-info h1 { font-size: 24px; font-weight: 700; color: var(--text-primary); }
    .company-info .ticker { font-size: 13px; color: var(--text-secondary); margin-top: 2px; }
    .report-meta { text-align: right; }
    .report-meta .report-date { font-size: 13px; color: var(--text-secondary); }
    .report-meta .report-period { font-size: 16px; font-weight: 600; color: var(--blue); margin-top: 4px; }

    .price-hero {
      margin-top: 24px;
      display: flex;
      align-items: flex-end;
      gap: 20px;
      flex-wrap: wrap;
      position: relative;
    }
    .price-current { font-size: 48px; font-weight: 800; color: var(--text-primary); letter-spacing: -2px; }
    .price-unit { font-size: 20px; color: var(--text-secondary); margin-bottom: 6px; }
    .price-change { display: flex; align-items: center; gap: 8px; margin-bottom: 8px; }
    .change-badge {
      padding: 4px 12px; border-radius: 20px;
      font-size: 16px; font-weight: 700;
      background: rgba(63,185,80,0.15);
      color: var(--green);
      border: 1px solid rgba(63,185,80,0.3);
    }
    .weekly-change { font-size: 13px; color: var(--text-secondary); }

    .container { max-width: 1280px; margin: 0 auto; padding: 28px 40px 60px; }

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
    .metric-card:hover { background: var(--bg-card-hover); border-color: var(--blue); }
    .metric-label {
      font-size: 11px; font-weight: 600;
      color: var(--text-muted);
      text-transform: uppercase;
      letter-spacing: 0.8px;
      margin-bottom: 8px;
    }
    .metric-value { font-size: 20px; font-weight: 700; color: var(--text-primary); letter-spacing: -0.5px; }
    .metric-sub { font-size: 12px; color: var(--text-secondary); margin-top: 4px; }
    .metric-up { color: var(--green); }
    .metric-down { color: var(--red); }

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
    tbody tr { border-top: 1px solid var(--border); transition: background 0.15s; }
    tbody tr:hover { background: rgba(88,166,255,0.05); }
    tbody td { padding: 13px 16px; font-size: 14px; text-align: right; color: var(--text-primary); }
    tbody td:first-child { text-align: left; font-weight: 600; }
    .td-up { color: var(--green); font-weight: 600; }
    .td-down { color: var(--red); font-weight: 600; }
    .td-neutral { color: var(--text-secondary); }
    .day-badge { display: inline-block; padding: 2px 8px; border-radius: 4px; font-size: 11px; font-weight: 700; margin-left: 6px; }
    .day-up { background: rgba(63,185,80,0.15); color: var(--green); }
    .day-down { background: rgba(248,81,73,0.15); color: var(--red); }

    .news-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(380px, 1fr)); gap: 12px; }
    .news-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 18px;
      transition: border-color 0.2s, background 0.2s;
      cursor: pointer;
    }
    .news-card:hover { border-color: var(--blue); background: var(--bg-card-hover); }
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
    .news-title { font-size: 14px; font-weight: 600; color: var(--text-primary); margin-bottom: 8px; line-height: 1.5; }
    .news-summary {
      font-size: 12px; color: var(--text-secondary); line-height: 1.6;
      display: -webkit-box; -webkit-line-clamp: 3; -webkit-box-orient: vertical; overflow: hidden;
    }

    .analyst-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
    .analyst-card { background: var(--bg-card); border: 1px solid var(--border); border-radius: 12px; padding: 20px; }
    .analyst-row { display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px; }
    .analyst-label { font-size: 13px; color: var(--text-secondary); }
    .analyst-value { font-size: 16px; font-weight: 700; color: var(--text-primary); }
    .target-bar { width: 100%; height: 6px; background: var(--bg-secondary); border-radius: 3px; margin-top: 12px; position: relative; }
    .target-fill { height: 100%; border-radius: 3px; background: linear-gradient(90deg, var(--red), var(--yellow), var(--green)); }
    .target-pointer {
      position: absolute; top: -4px;
      width: 14px; height: 14px;
      border-radius: 50%;
      background: var(--blue);
      border: 2px solid var(--bg-primary);
      transform: translateX(-50%);
    }
    .price-range-labels { display: flex; justify-content: space-between; margin-top: 6px; font-size: 11px; color: var(--text-muted); }

    .footer {
      margin-top: 40px;
      padding-top: 20px;
      border-top: 1px solid var(--border);
      display: flex; justify-content: space-between; align-items: center;
      flex-wrap: wrap; gap: 12px;
    }
    .footer-text { font-size: 12px; color: var(--text-muted); }
    .data-source { font-size: 11px; color: var(--text-muted); display: flex; align-items: center; gap: 6px; }
    .source-dot { width: 6px; height: 6px; border-radius: 50%; background: var(--blue); }

    @media print {
      body { background: #fff; color: #000; }
      .header { background: #1428A0; -webkit-print-color-adjust: exact; print-color-adjust: exact; }
      .metric-card, .chart-card, .table-wrap, .news-card, .analyst-card {
        break-inside: avoid; -webkit-print-color-adjust: exact; print-color-adjust: exact;
      }
    }

    @media (max-width: 768px) {
      .header { padding: 24px 20px; }
      .container { padding: 20px; }
      .price-current { font-size: 36px; }
      .analyst-grid { grid-template-columns: 1fr; }
      .news-grid { grid-template-columns: 1fr; }
      .metrics-grid { grid-template-columns: repeat(2, 1fr); }
    }

    @media (max-width: 480px) {
      .metrics-grid { grid-template-columns: 1fr; }
      .price-current { font-size: 28px; }
    }
  </style>
</head>
<body>

<div class="header">
  <div class="header-top">
    <div class="company-badge">
      <div class="company-logo">SE</div>
      <div class="company-info">
        <h1>삼성전자</h1>
        <div class="ticker">005930.KS · KSE · 소비자 전자</div>
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

<div class="container">

  <div class="metrics-grid" style="margin-top:0;">
    <div class="metric-card"><div class="metric-label">주간 시작가</div><div class="metric-value">176,300</div><div class="metric-sub">2026.03.30 종가</div></div>
    <div class="metric-card"><div class="metric-label">주간 최고가</div><div class="metric-value metric-up">190,800</div><div class="metric-sub">2026.04.01 장중</div></div>
    <div class="metric-card"><div class="metric-label">주간 최저가</div><div class="metric-value metric-down">167,000</div><div class="metric-sub">2026.03.31 장중</div></div>
    <div class="metric-card"><div class="metric-label">주간 등락폭</div><div class="metric-value metric-up">+5.62%</div><div class="metric-sub">176,300 → 186,200</div></div>
    <div class="metric-card"><div class="metric-label">주간 총거래량</div><div class="metric-value">152.1M</div><div class="metric-sub">일평균 30.4M주</div></div>
    <div class="metric-card"><div class="m
