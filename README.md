<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>LeadSuite - Fully Managed Cold Email Engine</title>
  <meta name="description" content="LeadSuite builds and manages a data-fueled cold email engine for B2B agencies and service businesses.">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
  <style>
    :root {
      --navy: #061f46;
      --navy-2: #0c2b5a;
      --blue: #1f6bff;
      --blue-2: #2f8cff;
      --blue-soft: #eaf3ff;
      --green: #18bf78;
      --green-soft: #e8fbf3;
      --orange: #ff7a1a;
      --orange-soft: #fff1e7;
      --paper: #ffffff;
      --wash: #f5f8fc;
      --wash-2: #eef5ff;
      --line: #dbe4ef;
      --line-strong: #c7d5e6;
      --muted: #667895;
      --muted-2: #8a98aa;
      --shadow: 0 18px 42px rgba(6, 31, 70, 0.11);
      --shadow-soft: 0 10px 24px rgba(6, 31, 70, 0.08);
      --max: 1180px;
    }

    * {
      box-sizing: border-box;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      margin: 0;
      font-family: "Inter", Arial, sans-serif;
      color: var(--navy);
      background: var(--paper);
      -webkit-font-smoothing: antialiased;
      text-rendering: optimizeLegibility;
    }

    body.lock-scroll {
      overflow: hidden;
    }

    img {
      display: block;
      max-width: 100%;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    button {
      font: inherit;
    }

    .wrap {
      width: min(var(--max), calc(100% - 48px));
      margin: 0 auto;
    }

    .site-header {
      position: sticky;
      top: 0;
      z-index: 40;
      background: rgba(255, 255, 255, 0.92);
      border-bottom: 1px solid rgba(219, 228, 239, 0.78);
      backdrop-filter: blur(18px);
    }

    .nav {
      height: 78px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 24px;
    }

    .brand {
      display: inline-flex;
      align-items: center;
      min-width: 172px;
    }

    .brand img {
      width: 170px;
      height: auto;
    }

    .nav-links {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 34px;
      color: var(--muted);
      font-size: 15px;
      font-weight: 600;
    }

    .nav-links a {
      transition: color 160ms ease;
    }

    .nav-links a:hover {
      color: var(--blue);
    }

    .nav-actions {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      min-height: 52px;
      padding: 0 28px;
      border-radius: 999px;
      border: 1px solid transparent;
      background: var(--blue);
      color: #ffffff;
      font-weight: 800;
      line-height: 1;
      cursor: pointer;
      box-shadow: 0 12px 24px rgba(31, 107, 255, 0.24);
      transition: transform 160ms ease, box-shadow 160ms ease, background 160ms ease;
      white-space: nowrap;
    }

    .btn:hover {
      transform: translateY(-2px);
      background: #0e5dff;
      box-shadow: 0 16px 30px rgba(31, 107, 255, 0.31);
    }

    .btn.secondary {
      background: #f7f9fc;
      color: var(--navy);
      border-color: #e7edf5;
      box-shadow: none;
    }

    .btn.secondary:hover {
      color: var(--blue);
      border-color: #c9dcff;
      background: #ffffff;
    }

    .btn.compact {
      min-height: 46px;
      padding: 0 22px;
      font-size: 14px;
    }

    .mobile-menu {
      display: none;
      width: 44px;
      height: 44px;
      border: 1px solid var(--line);
      border-radius: 999px;
      background: var(--paper);
      color: var(--navy);
      align-items: center;
      justify-content: center;
      cursor: pointer;
    }

    .mobile-menu svg {
      width: 22px;
      height: 22px;
    }

    .mobile-panel {
      display: none;
      border-top: 1px solid var(--line);
      background: var(--paper);
    }

    .mobile-panel.open {
      display: block;
    }

    .mobile-panel .wrap {
      display: grid;
      gap: 10px;
      padding: 18px 0 24px;
    }

    .mobile-panel a {
      padding: 13px 0;
      color: var(--muted);
      font-weight: 700;
    }

    .mobile-panel a.btn {
      color: #ffffff;
    }

    .hero {
      position: relative;
      overflow: hidden;
      padding: 30px 0 24px;
      background:
        radial-gradient(circle at 12% 20%, rgba(47, 140, 255, 0.09), transparent 32%),
        linear-gradient(180deg, #ffffff 0%, #ffffff 70%, var(--wash) 100%);
      text-align: center;
    }

    .offer-pill {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      min-height: 44px;
      padding: 0 22px;
      border-radius: 999px;
      border: 1px solid #bcd4ff;
      background: #edf4ff;
      color: var(--blue);
      font-size: 15px;
      font-weight: 800;
    }

    .offer-pill svg {
      width: 18px;
      height: 18px;
      flex: 0 0 auto;
    }

    .hero h1 {
      max-width: 1030px;
      margin: 24px auto 0;
      font-size: 64px;
      line-height: 1.04;
      font-weight: 900;
      letter-spacing: 0;
      color: var(--navy);
    }

    .hero h1 .blue {
      color: var(--blue);
    }

    .hero .subhead {
      max-width: 820px;
      margin: 20px auto 0;
      color: var(--muted);
      font-size: 19px;
      line-height: 1.46;
      font-weight: 500;
    }

    .hero .subhead strong {
      color: var(--navy);
      font-weight: 800;
    }

    .hero-actions {
      margin-top: 22px;
      display: flex;
      justify-content: center;
      gap: 14px;
      flex-wrap: wrap;
    }

    .proof-row {
      margin: 18px auto 0;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 22px;
      flex-wrap: wrap;
      color: var(--muted);
      font-size: 14px;
      font-weight: 700;
    }

    .proof-row span {
      display: inline-flex;
      align-items: center;
      gap: 8px;
    }

    .proof-dot {
      width: 9px;
      height: 9px;
      border-radius: 999px;
      background: var(--green);
      box-shadow: 0 0 0 5px var(--green-soft);
    }

    .hero-media {
      width: min(1040px, 100%);
      margin: 32px auto 0;
      border: 1px solid #b9cdf1;
      border-radius: 18px;
      overflow: hidden;
      box-shadow: 0 24px 58px rgba(6, 31, 70, 0.18);
      background: var(--paper);
    }

    .hero-media img {
      width: 100%;
      height: 270px;
      object-fit: cover;
      object-position: center 45%;
    }

    .metric-band {
      background: var(--paper);
      border-top: 1px solid var(--line);
      border-bottom: 1px solid var(--line);
    }

    .metric-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      border-left: 1px solid var(--line);
      border-right: 1px solid var(--line);
    }

    .metric {
      min-height: 142px;
      display: grid;
      align-content: center;
      justify-items: center;
      text-align: center;
      padding: 22px 18px;
      border-right: 1px solid var(--line);
    }

    .metric:last-child {
      border-right: 0;
    }

    .metric strong {
      display: block;
      color: var(--navy);
      font-size: 42px;
      line-height: 1;
      font-weight: 900;
    }

    .metric span {
      margin-top: 12px;
      color: #4f5d70;
      font-size: 17px;
      line-height: 1.25;
      font-weight: 500;
    }

    .section {
      padding: 92px 0;
    }

    .section[id] {
      scroll-margin-top: 92px;
    }

    .section.wash {
      background: var(--wash);
    }

    .section.bluewash {
      background: linear-gradient(180deg, #ffffff 0%, var(--wash-2) 100%);
    }

    .section.dark {
      background: var(--navy);
      color: #ffffff;
    }

    .section-label {
      color: var(--blue);
      font-size: 13px;
      font-weight: 900;
      letter-spacing: 0.32em;
      text-transform: uppercase;
    }

    .section.dark .section-label {
      color: #8fc0ff;
    }

    .section-heading {
      display: grid;
      grid-template-columns: 1.1fr 0.9fr;
      gap: 48px;
      align-items: end;
      margin-bottom: 48px;
    }

    .section-heading.center {
      display: block;
      max-width: 850px;
      margin: 0 auto 48px;
      text-align: center;
    }

    .section-heading h2 {
      margin: 14px 0 0;
      font-size: 54px;
      line-height: 1.08;
      letter-spacing: 0;
      font-weight: 900;
    }

    .section-heading p {
      margin: 0;
      color: var(--muted);
      font-size: 20px;
      line-height: 1.48;
      font-weight: 500;
    }

    .section.dark .section-heading p,
    .section.dark .body-copy {
      color: #c8d6ea;
    }

    .split {
      display: grid;
      grid-template-columns: 0.86fr 1.14fr;
      gap: 52px;
      align-items: center;
    }

    .body-copy {
      color: #52637a;
      font-size: 18px;
      line-height: 1.72;
    }

    .body-copy p {
      margin: 0 0 20px;
    }

    .body-copy strong {
      color: var(--navy);
      font-weight: 800;
    }

    .quote-bar {
      margin: 30px 0;
      padding: 22px 0 22px 24px;
      border-left: 5px solid var(--blue);
      color: var(--navy);
      font-size: 26px;
      line-height: 1.24;
      font-weight: 900;
    }

    .media-frame {
      border: 1px solid var(--line);
      border-radius: 18px;
      overflow: hidden;
      background: #ffffff;
      box-shadow: var(--shadow);
    }

    .media-frame img {
      width: 100%;
      height: auto;
    }

    .media-frame.slim img {
      max-height: 520px;
      object-fit: cover;
      object-position: center;
    }

    .problem-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
    }

    .problem-item,
    .proof-item,
    .timeline-phase,
    .faq-item,
    .labor-column,
    .plan-card {
      border: 1px solid var(--line);
      border-radius: 8px;
      background: var(--paper);
      box-shadow: var(--shadow-soft);
    }

    .problem-item {
      padding: 24px;
    }

    .problem-item .mark {
      display: inline-grid;
      place-items: center;
      width: 30px;
      height: 30px;
      border-radius: 8px;
      background: #fff0ed;
      color: #d64d30;
      font-weight: 900;
      margin-bottom: 18px;
    }

    .problem-item h3 {
      margin: 0 0 8px;
      font-size: 20px;
      line-height: 1.24;
      letter-spacing: 0;
    }

    .problem-item p {
      margin: 0;
      color: var(--muted);
      font-size: 15px;
      line-height: 1.55;
    }

    .workflow {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 0;
      border: 1px solid var(--line);
      border-radius: 18px;
      overflow: hidden;
      background: #ffffff;
      box-shadow: var(--shadow);
    }

    .workflow-step {
      min-height: 260px;
      padding: 28px 22px;
      border-right: 1px solid var(--line);
      background: linear-gradient(180deg, #ffffff 0%, #f8fbff 100%);
    }

    .workflow-step:last-child {
      border-right: 0;
    }

    .step-no {
      color: var(--blue);
      font-size: 12px;
      font-weight: 900;
      letter-spacing: 0.18em;
      text-transform: uppercase;
    }

    .workflow-step h3 {
      margin: 14px 0 10px;
      font-size: 20px;
      line-height: 1.2;
      letter-spacing: 0;
    }

    .workflow-step p {
      margin: 0;
      color: var(--muted);
      font-size: 15px;
      line-height: 1.55;
    }

    .tag {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      min-height: 28px;
      margin-top: 18px;
      padding: 0 10px;
      border-radius: 999px;
      color: var(--blue);
      background: var(--blue-soft);
      font-size: 11px;
      font-weight: 900;
      letter-spacing: 0.12em;
      text-transform: uppercase;
    }

    .tag.green {
      color: #078154;
      background: var(--green-soft);
    }

    .wide-asset {
      margin-top: 38px;
      border: 1px solid #c6d7f1;
      border-radius: 18px;
      overflow: hidden;
      background: #ffffff;
      box-shadow: var(--shadow);
    }

    .wide-asset img {
      width: 100%;
      height: auto;
    }

    .report-card {
      border: 1px solid var(--line);
      border-radius: 18px;
      overflow: hidden;
      background: var(--paper);
      box-shadow: var(--shadow);
    }

    .report-title {
      padding: 28px 30px;
      border-bottom: 1px solid var(--line);
      display: flex;
      justify-content: space-between;
      gap: 24px;
      align-items: center;
    }

    .report-title h3 {
      margin: 0;
      color: var(--navy);
      font-size: 24px;
      letter-spacing: 0;
    }

    .report-title span {
      color: var(--blue);
      font-size: 12px;
      font-weight: 900;
      letter-spacing: 0.2em;
      text-transform: uppercase;
    }

    .table {
      width: 100%;
      border-collapse: collapse;
      table-layout: fixed;
    }

    .table th {
      background: var(--navy);
      color: #ffffff;
      font-size: 16px;
      line-height: 1.2;
      font-weight: 900;
      text-align: center;
      padding: 18px 16px;
      border-right: 1px solid rgba(255, 255, 255, 0.24);
    }

    .table td {
      color: #151f2c;
      font-size: 16px;
      text-align: center;
      padding: 17px 16px;
      border-right: 1px solid var(--line);
      border-bottom: 1px solid var(--line);
      background: #ffffff;
    }

    .table td:first-child {
      font-weight: 700;
      color: var(--navy);
    }

    .table th:last-child,
    .table td:last-child {
      border-right: 0;
    }

    .table tr:last-child td {
      border-bottom: 0;
    }

    .compare {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 22px;
    }

    .compare-column {
      border: 1px solid var(--line);
      border-radius: 18px;
      background: var(--paper);
      overflow: hidden;
      box-shadow: var(--shadow-soft);
    }

    .compare-column.featured {
      border-color: #b7d1ff;
      box-shadow: 0 22px 48px rgba(31, 107, 255, 0.12);
    }

    .compare-head {
      padding: 26px 28px 22px;
      background: #ffffff;
      border-bottom: 1px solid var(--line);
    }

    .compare-column.featured .compare-head {
      background: #ecf4ff;
    }

    .compare-label {
      color: var(--blue);
      font-size: 12px;
      font-weight: 900;
      letter-spacing: 0.2em;
      text-transform: uppercase;
    }

    .compare-head h3 {
      margin: 10px 0 0;
      font-size: 28px;
      letter-spacing: 0;
    }

    .compare-list {
      list-style: none;
      margin: 0;
      padding: 24px 28px 28px;
      display: grid;
      gap: 14px;
    }

    .compare-list li {
      display: grid;
      grid-template-columns: 26px 1fr;
      gap: 12px;
      color: #52637a;
      font-size: 16px;
      line-height: 1.45;
    }

    .compare-list .icon {
      display: inline-grid;
      place-items: center;
      width: 26px;
      height: 26px;
      border-radius: 8px;
      font-weight: 900;
    }

    .compare-list .bad {
      color: #d64d30;
      background: #fff0ed;
    }

    .compare-list .good {
      color: #098c5b;
      background: var(--green-soft);
    }

    .total-row {
      border-top: 1px solid var(--line);
      padding: 24px 28px 28px;
      background: #fbfdff;
    }

    .total-row span {
      display: block;
      color: var(--muted);
      font-size: 13px;
      font-weight: 700;
      margin-bottom: 6px;
    }

    .total-row strong {
      font-size: 30px;
      line-height: 1.1;
      font-weight: 900;
      color: var(--navy);
    }

    .timeline {
      display: grid;
      gap: 18px;
    }

    .timeline-phase {
      display: grid;
      grid-template-columns: 132px 1fr;
      gap: 28px;
      padding: 28px;
      box-shadow: none;
    }

    .phase-num strong {
      display: block;
      color: var(--blue);
      font-size: 52px;
      line-height: 0.95;
      font-weight: 900;
    }

    .phase-num span {
      display: block;
      margin-top: 10px;
      color: var(--muted);
      font-size: 12px;
      font-weight: 900;
      letter-spacing: 0.16em;
      text-transform: uppercase;
    }

    .timeline-phase h3 {
      margin: 0 0 16px;
      font-size: 24px;
      letter-spacing: 0;
    }

    .checks {
      list-style: none;
      margin: 0;
      padding: 0;
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 11px 18px;
    }

    .checks li {
      display: grid;
      grid-template-columns: 24px 1fr;
      gap: 9px;
      color: var(--muted);
      font-size: 15px;
      line-height: 1.45;
    }

    .checks .check {
      color: var(--green);
      font-weight: 900;
    }

    .labor {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 22px;
    }

    .labor-column {
      padding: 30px;
      box-shadow: none;
    }

    .labor-column h3 {
      display: flex;
      align-items: center;
      gap: 12px;
      margin: 0 0 22px;
      font-size: 24px;
      letter-spacing: 0;
    }

    .small-pill {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      min-height: 28px;
      padding: 0 10px;
      border-radius: 999px;
      background: var(--blue-soft);
      color: var(--blue);
      font-size: 11px;
      font-weight: 900;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      white-space: nowrap;
    }

    .labor-column.you .small-pill {
      background: var(--green-soft);
      color: #078154;
    }

    .pricing-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 22px;
      max-width: 940px;
      margin: 0 auto;
    }

    .plan-card {
      position: relative;
      overflow: hidden;
      padding: 32px;
    }

    .plan-card.featured {
      border-color: #a9c9ff;
      background: #eef5ff;
      box-shadow: 0 22px 48px rgba(31, 107, 255, 0.14);
    }

    .plan-badge {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      min-height: 34px;
      padding: 0 14px;
      border-radius: 999px;
      background: var(--blue);
      color: #ffffff;
      font-size: 13px;
      font-weight: 900;
    }

    .plan-card.featured .plan-badge {
      background: var(--orange);
    }

    .plan-card h3 {
      margin: 18px 0 0;
      font-size: 38px;
      letter-spacing: 0;
    }

    .price {
      margin: 18px 0 6px;
      display: flex;
      align-items: baseline;
      gap: 8px;
      color: var(--navy);
    }

    .price strong {
      font-size: 48px;
      line-height: 1;
      font-weight: 900;
    }

    .price span {
      color: var(--muted);
      font-size: 17px;
      font-weight: 700;
    }

    .quarter {
      color: var(--blue);
      font-size: 14px;
      font-weight: 900;
      margin-bottom: 24px;
    }

    .plan-card .checks {
      grid-template-columns: 1fr;
      margin-bottom: 28px;
    }

    .scarcity {
      max-width: 850px;
      margin: 28px auto 0;
      padding: 22px 26px;
      border: 1px solid #c8dcff;
      border-radius: 8px;
      background: #ffffff;
      color: #52637a;
      font-size: 16px;
      line-height: 1.5;
      text-align: center;
      box-shadow: var(--shadow-soft);
    }

    .scarcity strong {
      color: var(--navy);
    }

    .proof-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 18px;
    }

    .proof-item {
      padding: 26px;
      box-shadow: none;
    }

    .proof-item span {
      color: var(--blue);
      font-size: 12px;
      font-weight: 900;
      letter-spacing: 0.16em;
      text-transform: uppercase;
    }

    .proof-item h3 {
      margin: 14px 0 10px;
      font-size: 22px;
      line-height: 1.22;
      letter-spacing: 0;
    }

    .proof-item p {
      margin: 0;
      color: var(--muted);
      font-size: 15px;
      line-height: 1.55;
    }

    .guarantee {
      display: grid;
      grid-template-columns: 150px 1fr;
      gap: 34px;
      align-items: center;
      padding: 40px;
      border: 1px solid rgba(255, 255, 255, 0.18);
      border-radius: 18px;
      background: linear-gradient(135deg, rgba(47, 140, 255, 0.2), rgba(24, 191, 120, 0.12));
    }

    .seal {
      width: 130px;
      height: 130px;
      border-radius: 999px;
      border: 2px solid #8fc0ff;
      display: grid;
      place-items: center;
      text-align: center;
      color: #ffffff;
      font-size: 13px;
      font-weight: 900;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      line-height: 1.35;
    }

    .guarantee h2 {
      margin: 0 0 14px;
      color: #ffffff;
      font-size: 38px;
      line-height: 1.1;
      letter-spacing: 0;
    }

    .guarantee p {
      margin: 0;
      color: #d5e2f4;
      font-size: 17px;
      line-height: 1.62;
    }

    .faq {
      max-width: 900px;
      margin: 0 auto;
      display: grid;
      gap: 12px;
    }

    .faq-item {
      box-shadow: none;
      overflow: hidden;
    }

    .faq-item button {
      width: 100%;
      min-height: 72px;
      padding: 0 26px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 20px;
      border: 0;
      background: #ffffff;
      color: var(--navy);
      text-align: left;
      font-size: 18px;
      font-weight: 900;
      cursor: pointer;
    }

    .faq-item button svg {
      width: 20px;
      height: 20px;
      flex: 0 0 auto;
      color: var(--blue);
      transition: transform 180ms ease;
    }

    .faq-item.open button svg {
      transform: rotate(45deg);
    }

    .faq-answer {
      max-height: 0;
      overflow: hidden;
      transition: max-height 220ms ease;
    }

    .faq-answer p {
      margin: 0;
      padding: 0 26px 24px;
      color: var(--muted);
      font-size: 16px;
      line-height: 1.62;
    }

    .final-cta {
      text-align: center;
      background:
        radial-gradient(circle at 50% 0%, rgba(31, 107, 255, 0.14), transparent 34%),
        var(--navy);
      color: #ffffff;
    }

    .final-cta h2 {
      max-width: 850px;
      margin: 0 auto 20px;
      font-size: 64px;
      line-height: 1.08;
      letter-spacing: 0;
      font-weight: 900;
    }

    .final-cta h2 span {
      color: #8fc0ff;
    }

    .final-cta p {
      max-width: 760px;
      margin: 0 auto 30px;
      color: #d5e2f4;
      font-size: 20px;
      line-height: 1.5;
      font-weight: 500;
    }

    .site-footer {
      padding: 42px 0;
      background: #ffffff;
      border-top: 1px solid var(--line);
    }

    .footer-grid {
      display: grid;
      grid-template-columns: 220px 1fr;
      gap: 40px;
      align-items: start;
    }

    .footer-grid img {
      width: 170px;
    }

    .footer-grid p {
      margin: 0;
      color: var(--muted);
      font-size: 14px;
      line-height: 1.62;
    }

    .reveal {
      opacity: 1;
      transform: none;
    }

    .reveal.in {
      opacity: 1;
      transform: none;
    }

    @media (max-width: 1100px) {
      .hero h1 {
        font-size: 56px;
      }

      .section-heading h2,
      .final-cta h2 {
        font-size: 48px;
      }

      .workflow {
        grid-template-columns: repeat(2, 1fr);
      }

      .workflow-step {
        border-bottom: 1px solid var(--line);
      }

      .workflow-step:nth-child(2n) {
        border-right: 0;
      }

      .workflow-step:last-child {
        grid-column: 1 / -1;
        border-bottom: 0;
      }
    }

    @media (max-width: 920px) {
      .nav-links,
      .nav-actions {
        display: none;
      }

      .mobile-menu {
        display: inline-flex;
      }

      .brand img {
        width: 148px;
      }

      .hero {
        padding-top: 42px;
      }

      .hero h1 {
        font-size: 52px;
      }

      .hero .subhead {
        font-size: 18px;
      }

      .hero-media img {
        height: 220px;
      }

      .metric-grid,
      .problem-grid,
      .proof-grid,
      .pricing-grid,
      .labor,
      .compare,
      .split,
      .section-heading {
        grid-template-columns: 1fr;
      }

      .metric-grid {
        border-bottom: 1px solid var(--line);
      }

      .metric {
        border-right: 0;
        border-bottom: 1px solid var(--line);
      }

      .metric:last-child {
        border-bottom: 0;
      }

      .section {
        padding: 72px 0;
      }

      .section-heading {
        gap: 20px;
        margin-bottom: 34px;
      }

      .section-heading h2 {
        font-size: 42px;
      }

      .section-heading p {
        font-size: 18px;
      }

      .split {
        gap: 34px;
      }

      .workflow {
        grid-template-columns: 1fr;
      }

      .workflow-step {
        min-height: 0;
        border-right: 0;
      }

      .workflow-step:last-child {
        grid-column: auto;
      }

      .checks {
        grid-template-columns: 1fr;
      }

      .report-title {
        display: grid;
        gap: 10px;
      }

      .table-wrap {
        overflow-x: auto;
        -webkit-overflow-scrolling: touch;
      }

      .table {
        min-width: 680px;
      }

      .guarantee {
        grid-template-columns: 1fr;
        padding: 30px;
      }

      .footer-grid {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 620px) {
      .wrap {
        width: min(100% - 30px, var(--max));
      }

      .nav {
        height: 70px;
      }

      .offer-pill {
        width: 100%;
        padding: 0 14px;
        font-size: 13px;
      }

      .hero {
        padding: 32px 0 20px;
      }

      .hero h1 {
        margin-top: 26px;
        font-size: 38px;
      }

      .hero .subhead {
        margin-top: 20px;
        font-size: 16px;
      }

      .hero-actions {
        display: grid;
        gap: 12px;
      }

      .btn {
        width: 100%;
        min-height: 50px;
        padding: 0 20px;
      }

      .proof-row {
        align-items: flex-start;
        justify-content: flex-start;
        text-align: left;
        gap: 14px;
      }

      .hero-media {
        margin-top: 24px;
        border-radius: 12px;
      }

      .hero-media img {
        height: 170px;
      }

      .metric {
        min-height: 118px;
      }

      .metric strong {
        font-size: 34px;
      }

      .metric span {
        font-size: 15px;
      }

      .section {
        padding: 58px 0;
      }

      .section-heading h2,
      .final-cta h2 {
        font-size: 34px;
      }

      .section-heading p,
      .body-copy,
      .final-cta p {
        font-size: 16px;
      }

      .quote-bar {
        font-size: 21px;
      }

      .problem-item,
      .proof-item,
      .labor-column,
      .plan-card,
      .timeline-phase {
        padding: 22px;
      }

      .timeline-phase {
        grid-template-columns: 1fr;
        gap: 16px;
      }

      .price strong {
        font-size: 40px;
      }

      .guarantee h2 {
        font-size: 30px;
      }
    }

    @media (prefers-reduced-motion: reduce) {
      html {
        scroll-behavior: auto;
      }

      .reveal {
        opacity: 1;
        transform: none;
        transition: none;
      }

      .btn,
      .faq-answer,
      .faq-item button svg {
        transition: none;
      }
    }
  </style>
</head>
<body>
  <header class="site-header">
    <div class="wrap nav">
      <a class="brand" href="#top" aria-label="LeadSuite home">
        <img src="assets/leadsuite-logo.png" width="2508" height="627" alt="LeadSuite">
      </a>
      <nav class="nav-links" aria-label="Primary navigation">
        <a href="#system">How it works</a>
        <a href="#proof">Proof</a>
        <a href="#timeline">Timeline</a>
        <a href="#pricing">Pricing</a>
        <a href="#faq">FAQ</a>
      </nav>
      <div class="nav-actions">
        <a href="#pricing">Pricing</a>
        <a class="btn compact secondary" href="#final">Book a Demo</a>
        <a class="btn compact" href="#pricing">Get Started</a>
      </div>
      <button class="mobile-menu" type="button" aria-expanded="false" aria-controls="mobile-panel" aria-label="Open navigation">
        <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M4 7h16M4 12h16M4 17h16" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg>
      </button>
    </div>
    <div class="mobile-panel" id="mobile-panel">
      <div class="wrap">
        <a href="#system">How it works</a>
        <a href="#proof">Proof</a>
        <a href="#timeline">Timeline</a>
        <a href="#pricing">Pricing</a>
        <a href="#faq">FAQ</a>
        <a class="btn" href="#final">Book a Demo</a>
      </div>
    </div>
  </header>

  <main id="top">
    <section class="hero">
      <div class="wrap">
        <div class="reveal">
          <div class="offer-pill">
            <svg viewBox="0 0 24 24" aria-hidden="true"><path d="M13 2 4 14h7l-1 8 10-13h-7l0-7Z" fill="currentColor"/></svg>
            Now offering a fully managed cold email engine - done for you
          </div>
          <h1>Fully Managed <span class="blue">Cold Email</span><br>Outbound for B2B Agencies</h1>
          <p class="subhead">We build and manage a data-fueled outbound engine that sources <strong>30,000-45,000 fresh prospects every month</strong>, launches campaigns on private infrastructure, and routes qualified replies to your team.</p>
          <div class="hero-actions">
            <a class="btn" href="#pricing">See Pricing Plans</a>
            <a class="btn secondary" href="#system">How the Engine Works</a>
          </div>
          <div class="proof-row" aria-label="LeadSuite proof points">
            <span><i class="proof-dot"></i> Private sending domains</span>
            <span><i class="proof-dot"></i> Fresh monthly lead data</span>
            <span><i class="proof-dot"></i> 24/7 deliverability monitoring</span>
          </div>
        </div>
      </div>
    </section>

    <section class="metric-band" aria-label="Key service metrics">
      <div class="wrap metric-grid">
        <div class="metric reveal"><strong>30K-45K</strong><span>Fresh prospects contacted monthly</span></div>
        <div class="metric reveal"><strong>60-90</strong><span>Private inboxes built and monitored</span></div>
        <div class="metric reveal"><strong>5-8 wks</strong><span>From kickoff to live campaigns</span></div>
        <div class="metric reveal"><strong>24/7</strong><span>AI deliverability monitoring</span></div>
      </div>
    </section>

    <section class="section" id="why">
      <div class="wrap">
        <div class="section-heading">
          <div class="reveal">
            <div class="section-label">Why this works</div>
            <h2>Fresh inputs beat better automation.</h2>
          </div>
          <p class="reveal">Most cold email does not fail because the copy is bad. It fails because the lead source is stale, overused, and already exhausted by competitors.</p>
        </div>
        <div class="split">
          <div class="body-copy reveal">
            <p>Apollo exports, cheap list vendors, and recycled database pulls create the same problem: you are sending to the same people everyone else already hammered last quarter.</p>
            <p>LeadSuite starts with live public business signals from Instagram, then enriches, validates, cleans, and suppresses the data before a single campaign launches.</p>
            <div class="quote-bar">Outbound is not broken. The inputs are.</div>
            <p>The fresh data goes into private cold email infrastructure, gets activated through managed SmartLead campaigns, and turns positive replies into qualified sales conversations your team can pursue.</p>
          </div>
          <div class="media-frame reveal">
            <img src="assets/leadsuite-dashboard.png" width="1672" height="941" alt="LeadSuite dashboard with outreach composer, qualified leads, recent activity, and campaign performance">
          </div>
        </div>
      </div>
    </section>

    <section class="section wash" id="problems">
      <div class="wrap">
        <div class="section-heading">
          <div class="reveal">
            <div class="section-label">The usual fixes</div>
            <h2>Why the old outbound playbook keeps stalling.</h2>
          </div>
          <p class="reveal">You are not new to outbound. You are overexposed to the parts that make it fragile: stale data, deliverability work, tool sprawl, and channels no one wants to manage.</p>
        </div>
        <div class="problem-grid">
          <article class="problem-item reveal">
            <span class="mark">&times;</span>
            <h3>Recycled databases</h3>
            <p>Broad lists decay fast. By the time you export them, your competitors may already be in the same inboxes.</p>
          </article>
          <article class="problem-item reveal">
            <span class="mark">&times;</span>
            <h3>DIY deliverability</h3>
            <p>Domains, DNS, inbox warmup, rotation, and spam checks pull your team into work that never directly closes deals.</p>
          </article>
          <article class="problem-item reveal">
            <span class="mark">&times;</span>
            <h3>Generic agencies</h3>
            <p>Most agencies compete on "better copy" while quietly using the same commoditized inputs as everyone else.</p>
          </article>
        </div>
      </div>
    </section>

    <section class="section" id="system">
      <div class="wrap">
        <div class="section-heading center reveal">
          <div class="section-label">How the system works</div>
          <h2>The infrastructure behind your outbound engine.</h2>
          <p>Five managed components running as one system: fresh data, enrichment, private infrastructure, campaign execution, and monthly optimization.</p>
        </div>
        <div class="workflow">
          <article class="workflow-step reveal">
            <div class="step-no">Step 01</div>
            <h3>LeadSweeper sourcing</h3>
            <p>Fresh e-commerce and Instagram-active business data sourced from live public signals.</p>
            <span class="tag">Fresh input</span>
          </article>
          <article class="workflow-step reveal">
            <div class="step-no">Step 02</div>
            <h3>Enrichment</h3>
            <p>ListKit, ZoomInfo, Apollo, and other sources fill contact gaps, validate emails, and prepare clean records.</p>
            <span class="tag">Verified</span>
          </article>
          <article class="workflow-step reveal">
            <div class="step-no">Step 03</div>
            <h3>Private inboxes</h3>
            <p>60-90 inboxes across fresh domains, isolated from your main business domain and monitored for health.</p>
            <span class="tag">Protected</span>
          </article>
          <article class="workflow-step reveal">
            <div class="step-no">Step 04</div>
            <h3>SmartLead execution</h3>
            <p>Campaign copy, sending windows, inbox rotation, reply tracking, and campaign operations handled end to end.</p>
            <span class="tag">Managed</span>
          </article>
          <article class="workflow-step reveal">
            <div class="step-no">Step 05</div>
            <h3>Refresh and optimize</h3>
            <p>New lists, new angles, deliverability checks, and positive reply enrichment every month.</p>
            <span class="tag green">Output</span>
          </article>
        </div>
        <div class="wide-asset reveal">
          <img src="assets/leadsuite-automation-map.png" width="1672" height="941" alt="LeadSuite infrastructure map showing admin panel, domains, inboxes, sending platform, personalized messages, and paying clients">
        </div>
      </div>
    </section>

    <section class="section bluewash" id="proof">
      <div class="wrap">
        <div class="section-heading">
          <div class="reveal">
            <div class="section-label">Proof and reporting</div>
            <h2>Numbers you can actually inspect.</h2>
          </div>
          <p class="reveal">The reference deck uses clear metric bands and performance tables. This page follows that same pattern so the offer feels measurable, not vague.</p>
        </div>
        <div class="report-card reveal">
          <div class="report-title">
            <h3>Monthly outbound performance snapshot</h3>
            <span>LeadSuite report</span>
          </div>
          <div class="table-wrap">
            <table class="table">
              <thead>
                <tr>
                  <th>Metric</th>
                  <th>Minimum Plan</th>
                  <th>Pro Plan</th>
                  <th>What It Means</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td>Fresh prospects</td>
                  <td>Up to 30,000/mo</td>
                  <td>Up to 45,000/mo</td>
                  <td>Monthly sourced and prepared data</td>
                </tr>
                <tr>
                  <td>Domains</td>
                  <td>30</td>
                  <td>45</td>
                  <td>Private sending infrastructure</td>
                </tr>
                <tr>
                  <td>Inboxes</td>
                  <td>60</td>
                  <td>90</td>
                  <td>Warmed and monitored accounts</td>
                </tr>
                <tr>
                  <td>Campaign cycle</td>
                  <td>Monthly</td>
                  <td>Monthly</td>
                  <td>New lists, tests, and optimization</td>
                </tr>
              </tbody>
            </table>
          </div>
        </div>
        <div class="wide-asset reveal">
          <img src="assets/leadsuite-metrics.png" width="1672" height="941" alt="LeadSuite key metrics and call performance table">
        </div>
      </div>
    </section>

    <section class="section" id="cost">
      <div class="wrap">
        <div class="section-heading">
          <div class="reveal">
            <div class="section-label">The real cost comparison</div>
            <h2>Why building it yourself rarely pencils out.</h2>
          </div>
          <p class="reveal">Outbound at this volume is not just a sender account. It is data, infrastructure, writing, monitoring, reporting, and constant operational upkeep.</p>
        </div>
        <div class="compare">
          <article class="compare-column reveal">
            <div class="compare-head">
              <div class="compare-label">The DIY route</div>
              <h3>Building it in-house</h3>
            </div>
            <ul class="compare-list">
              <li><span class="icon bad">&times;</span><span>$11,000-$16,000/mo for one SDR once you add salary, manager, and benefits.</span></li>
              <li><span class="icon bad">&times;</span><span>60-90 days to hire, onboard, and ramp before the motion is stable.</span></li>
              <li><span class="icon bad">&times;</span><span>Scraping, enrichment, domains, inboxes, sending tools, and reporting still need owners.</span></li>
              <li><span class="icon bad">&times;</span><span>You are still responsible for data quality, copy, deliverability, and campaign upkeep.</span></li>
            </ul>
            <div class="total-row">
              <span>Realistic monthly cost</span>
              <strong>$12,000-$17,000/mo</strong>
            </div>
          </article>
          <article class="compare-column featured reveal">
            <div class="compare-head">
              <div class="compare-label">The LeadSuite way</div>
              <h3>The managed engine</h3>
            </div>
            <ul class="compare-list">
              <li><span class="icon good">&#10003;</span><span>Full cold email engine built and managed for you in weeks, not months.</span></li>
              <li><span class="icon good">&#10003;</span><span>Fresh Instagram-sourced lead lists rebuilt every single month.</span></li>
              <li><span class="icon good">&#10003;</span><span>30-45 domains, 60-90 inboxes, and deliverability protection included.</span></li>
              <li><span class="icon good">&#10003;</span><span>Copy, sequences, sending, reporting, and optimization handled end to end.</span></li>
            </ul>
            <div class="total-row">
              <span>Starting at, billed quarterly</span>
              <strong>$3,000/mo</strong>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section class="section wash" id="timeline">
      <div class="wrap">
        <div class="section-heading">
          <div class="reveal">
            <div class="section-label">Launch timeline</div>
            <h2>From kickoff to live campaigns in weeks.</h2>
          </div>
          <p class="reveal">A bounded buildout with visible milestones, approvals, and monthly optimization once the first campaign is live.</p>
        </div>
        <div class="timeline">
          <article class="timeline-phase reveal">
            <div class="phase-num"><strong>01</strong><span>Weeks 1-2</span></div>
            <div>
              <h3>Discovery and strategy</h3>
              <ul class="checks">
                <li><span class="check">&#10003;</span><span>Review offer, ICP, and sales motion</span></li>
                <li><span class="check">&#10003;</span><span>Define sourcing angles and lead criteria</span></li>
                <li><span class="check">&#10003;</span><span>Purchase and configure private domains</span></li>
                <li><span class="check">&#10003;</span><span>Draft the first campaign for approval</span></li>
              </ul>
            </div>
          </article>
          <article class="timeline-phase reveal">
            <div class="phase-num"><strong>02</strong><span>Weeks 3-4</span></div>
            <div>
              <h3>Build and configuration</h3>
              <ul class="checks">
                <li><span class="check">&#10003;</span><span>Scrape and prepare the first targeted lead list</span></li>
                <li><span class="check">&#10003;</span><span>Enrich missing data and validate records</span></li>
                <li><span class="check">&#10003;</span><span>Warm inboxes and run deliverability checks</span></li>
                <li><span class="check">&#10003;</span><span>Configure reporting and reply tracking</span></li>
              </ul>
            </div>
          </article>
          <article class="timeline-phase reveal">
            <div class="phase-num"><strong>03</strong><span>Weeks 5-8</span></div>
            <div>
              <h3>Launch, optimize, and scale</h3>
              <ul class="checks">
                <li><span class="check">&#10003;</span><span>First campaign goes live</span></li>
                <li><span class="check">&#10003;</span><span>Deliverability and reply behavior monitored</span></li>
                <li><span class="check">&#10003;</span><span>Positive replies routed and phone-enriched</span></li>
                <li><span class="check">&#10003;</span><span>New monthly lists and email angles tested</span></li>
              </ul>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section class="section" id="labor">
      <div class="wrap">
        <div class="section-heading center reveal">
          <div class="section-label">Division of labor</div>
          <h2>We run the machine. You close the opportunities.</h2>
          <p>A clean split keeps your team focused on strategy, sales conversations, and closing instead of backend outbound operations.</p>
        </div>
        <div class="labor">
          <article class="labor-column reveal">
            <h3><span class="small-pill">LeadSuite</span> We handle</h3>
            <ul class="checks">
              <li><span class="check">&#10003;</span><span>Custom inbox and domain setup</span></li>
              <li><span class="check">&#10003;</span><span>LeadSweeper scraping and monthly list building</span></li>
              <li><span class="check">&#10003;</span><span>Contact enrichment and validation</span></li>
              <li><span class="check">&#10003;</span><span>Cold email copy and 3-step sequences</span></li>
              <li><span class="check">&#10003;</span><span>SmartLead setup, launch, and management</span></li>
              <li><span class="check">&#10003;</span><span>Deliverability monitoring and reporting</span></li>
            </ul>
          </article>
          <article class="labor-column you reveal">
            <h3><span class="small-pill">Your team</span> You handle</h3>
            <ul class="checks">
              <li><span class="check">&#10003;</span><span>Approve strategy and messaging</span></li>
              <li><span class="check">&#10003;</span><span>Give ICP and positioning feedback</span></li>
              <li><span class="check">&#10003;</span><span>Respond to interested leads</span></li>
              <li><span class="check">&#10003;</span><span>Take sales calls</span></li>
              <li><span class="check">&#10003;</span><span>Follow up with qualified opportunities</span></li>
              <li><span class="check">&#10003;</span><span>Sign clients</span></li>
            </ul>
          </article>
        </div>
      </div>
    </section>

    <section class="section bluewash" id="pricing">
      <div class="wrap">
        <div class="section-heading center reveal">
          <div class="section-label">Pricing</div>
          <h2>Choose your outbound engine.</h2>
          <p>Billed quarterly. 90-day minimum commitment. No setup fees.</p>
        </div>
        <div class="pricing-grid">
          <article class="plan-card reveal">
            <span class="plan-badge">Starter</span>
            <h3>Minimum</h3>
            <div class="price"><strong>$3,000</strong><span>/mo</span></div>
            <div class="quarter">$9,000 / quarter</div>
            <ul class="checks">
              <li><span class="check">&#10003;</span><span>Up to 30,000 leads contacted per month</span></li>
              <li><span class="check">&#10003;</span><span>30 domains purchased via PorkBun</span></li>
              <li><span class="check">&#10003;</span><span>60 private email inboxes</span></li>
              <li><span class="check">&#10003;</span><span>LeadSweeper-powered sourcing</span></li>
              <li><span class="check">&#10003;</span><span>24/7 AI deliverability monitoring</span></li>
              <li><span class="check">&#10003;</span><span>Phone enrichment on positive replies</span></li>
            </ul>
            <a class="btn secondary" href="#final">Start with Minimum</a>
          </article>
          <article class="plan-card featured reveal">
            <span class="plan-badge">Most Popular</span>
            <h3>Pro</h3>
            <div class="price"><strong>$5,000</strong><span>/mo</span></div>
            <div class="quarter">$15,000 / quarter</div>
            <ul class="checks">
              <li><span class="check">&#10003;</span><span>Up to 45,000 leads contacted per month</span></li>
              <li><span class="check">&#10003;</span><span>45 domains purchased via PorkBun</span></li>
              <li><span class="check">&#10003;</span><span>90 private email inboxes</span></li>
              <li><span class="check">&#10003;</span><span>Expanded LeadSweeper sourcing</span></li>
              <li><span class="check">&#10003;</span><span>More campaign testing capacity</span></li>
              <li><span class="check">&#10003;</span><span>Priority campaign management</span></li>
            </ul>
            <a class="btn" href="#final">Start with Pro</a>
          </article>
        </div>
        <p class="scarcity reveal"><strong>Only 3-5 new partners onboarded per month.</strong> Every account requires dedicated domain setup, inbox configuration, LeadSweeper sourcing, and private infrastructure allocation.</p>
      </div>
    </section>

    <section class="section" id="believability">
      <div class="wrap">
        <div class="section-heading">
          <div class="reveal">
            <div class="section-label">Why you can believe it works</div>
            <h2>We show you the messy middle.</h2>
          </div>
          <p class="reveal">Before you commit, you see how the engine is sourced, built, and measured - not just a promise that meetings will appear.</p>
        </div>
        <div class="proof-grid">
          <article class="proof-item reveal">
            <span>Mechanism proof</span>
            <h3>A specific, bounded system</h3>
            <p>Fresh sourcing, enrichment, private infrastructure, campaign execution, and reporting are shown as one operating model.</p>
          </article>
          <article class="proof-item reveal">
            <span>Process proof</span>
            <h3>Sample leads and infra checklist</h3>
            <p>You can inspect how Instagram signals map to your ICP and what the deliverability checklist includes before launch.</p>
          </article>
          <article class="proof-item reveal">
            <span>Operational proof</span>
            <h3>Reporting you can read</h3>
            <p>Monthly reporting covers sends, replies, positive responses, and deliverability health so you know what is converting.</p>
          </article>
        </div>
      </div>
    </section>

    <section class="section dark" id="guarantee">
      <div class="wrap">
        <div class="guarantee reveal">
          <div class="seal">Build<br>and<br>launch<br>guarantee</div>
          <div>
            <h2>If it is not live, we keep working.</h2>
            <p>We guarantee your outreach engine will be built, configured, launched, monitored, and optimized to the agreed execution timeline. If the infrastructure setup, first list buildout, campaign sequence, and first campaign launch are not complete within the agreed onboarding window, we keep working at no additional management fee until the system is live.</p>
          </div>
        </div>
      </div>
    </section>

    <section class="section wash" id="faq">
      <div class="wrap">
        <div class="section-heading center reveal">
          <div class="section-label">Questions, answered</div>
          <h2>The things skeptical buyers ask.</h2>
        </div>
        <div class="faq">
          <article class="faq-item reveal">
            <button type="button">Are Instagram-sourced leads actually qualified for B2B?<svg viewBox="0 0 24 24" aria-hidden="true"><path d="M12 5v14M5 12h14" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg></button>
            <div class="faq-answer"><p>Instagram is a discovery layer, not the final qualification layer. We use public business signals to find active companies, then enrich, validate, clean, and suppress records against your ICP before outreach.</p></div>
          </article>
          <article class="faq-item reveal">
            <button type="button">Will these emails land in the inbox?<svg viewBox="0 0 24 24" aria-hidden="true"><path d="M12 5v14M5 12h14" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg></button>
            <div class="faq-answer"><p>You send from private domains and inboxes, never your main business domain. Inboxes are warmed, rotated, and monitored so health issues can be flagged before they become expensive.</p></div>
          </article>
          <article class="faq-item reveal">
            <button type="button">Why not use Apollo, ZoomInfo, or a VA?<svg viewBox="0 0 24 24" aria-hidden="true"><path d="M12 5v14M5 12h14" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg></button>
            <div class="faq-answer"><p>Apollo and ZoomInfo can be useful, but they are broad databases. A VA can run a tool, but they do not give you a managed system: fresh data, enrichment, infrastructure, deliverability, campaigns, and reporting together.</p></div>
          </article>
          <article class="faq-item reveal">
            <button type="button">How much work will my team still have to do?<svg viewBox="0 0 24 24" aria-hidden="true"><path d="M12 5v14M5 12h14" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg></button>
            <div class="faq-answer"><p>Approve strategy, respond to interested replies, take the calls, follow up, and close. We handle scraping, enrichment, inboxes, deliverability, SmartLead operations, and reporting.</p></div>
          </article>
          <article class="faq-item reveal">
            <button type="button">Why the 90-day commitment?<svg viewBox="0 0 24 24" aria-hidden="true"><path d="M12 5v14M5 12h14" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg></button>
            <div class="faq-answer"><p>Cold email needs setup, warmup, launch, reply analysis, and optimization time. Ninety days gives the engine room to stabilize and produce data worth acting on.</p></div>
          </article>
        </div>
      </div>
    </section>

    <section class="section final-cta" id="final">
      <div class="wrap reveal">
        <h2>Stop fighting over the <span>same stale leads.</span></h2>
        <p>We build and manage the data-fueled cold email engine that turns fresh business signals into qualified B2B sales conversations. You approve the strategy, take the calls, and close.</p>
        <div class="hero-actions">
          <a class="btn" href="#pricing">Book a Strategy Call</a>
          <a class="btn secondary" href="#system">Review the System</a>
        </div>
      </div>
    </section>
  </main>

  <footer class="site-footer">
    <div class="wrap footer-grid">
      <a href="#top" aria-label="LeadSuite home">
        <img src="assets/leadsuite-logo.png" width="2508" height="627" alt="LeadSuite">
      </a>
      <p>LeadSuite builds and manages a data-fueled cold email engine for B2B agencies, SaaS, and service businesses. We guarantee buildout and execution to the agreed timeline, not closed revenue, which depends on your offer, pricing, and close rate. Sourcing uses public business signals, enriched and validated before outreach.</p>
    </div>
  </footer>

  <script>
    const menuButton = document.querySelector(".mobile-menu");
    const mobilePanel = document.querySelector(".mobile-panel");

    menuButton.addEventListener("click", () => {
      const isOpen = mobilePanel.classList.toggle("open");
      menuButton.setAttribute("aria-expanded", String(isOpen));
    });

    mobilePanel.querySelectorAll("a").forEach((link) => {
      link.addEventListener("click", () => {
        mobilePanel.classList.remove("open");
        menuButton.setAttribute("aria-expanded", "false");
      });
    });

    document.querySelectorAll(".faq-item button").forEach((button) => {
      button.addEventListener("click", () => {
        const item = button.closest(".faq-item");
        const answer = item.querySelector(".faq-answer");
        const isOpen = item.classList.contains("open");

        document.querySelectorAll(".faq-item.open").forEach((openItem) => {
          openItem.classList.remove("open");
          openItem.querySelector(".faq-answer").style.maxHeight = null;
        });

        if (!isOpen) {
          item.classList.add("open");
          answer.style.maxHeight = `${answer.scrollHeight}px`;
        }
      });
    });

    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("in");
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.12, rootMargin: "0px 0px -48px 0px" });

    document.querySelectorAll(".reveal").forEach((el) => observer.observe(el));
  </script>
</body>
</html>
<img width="1672" height="941" alt="leadsuite-metrics" src="https://github.com/user-attachments/assets/1a2dab92-460a-4ba0-b994-b105682c17f3" />
<img width="2508" height="627" alt="leadsuite-logo" src="https://github.com/user-attachments/assets/03ffe9f8-a093-40df-9efd-29a030007959" />
<img width="1672" height="941" alt="leadsuite-dashboard" src="https://github.com/user-attachments/assets/3ca5f245-45be-47ca-9743-e17870a70ca5" />
<img width="1672" height="941" alt="leadsuite-automation-map" src="https://github.com/user-attachments/assets/b3f73d72-ff0f-49a7-8d61-3edb54aa5e78" />

