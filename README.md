<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>THE DEVIL'S PLAN : 미스터리 거래소</title>
  <style>
    :root {
      --bg-dark: #07080b;
      --bg-panel: #101218;
      --bg-card: #161922;
      --bg-hover: #1e222e;
      --border: #2a2f3e;
      --gold: #d4af37;
      --gold-light: #f3d56b;
      --gold-dim: rgba(212, 175, 55, 0.16);
      --text-main: #f1f3f8;
      --text-muted: #8b93a7;
      --up: #ff4d5e;
      --down: #3b82f6;
      --secret: #9d4edd;
      --success: #10b981;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Pretendard', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
    }

    body {
      background-color: var(--bg-dark);
      color: var(--text-main);
      min-height: 100vh;
      overflow-x: hidden;
    }

    button {
      cursor: pointer;
      border: none;
      outline: none;
      transition: all 0.18s ease;
    }

    button:disabled {
      opacity: 0.4;
      cursor: not-allowed;
    }

    input, textarea {
      background: #0b0d13;
      border: 1px solid var(--border);
      color: var(--text-main);
      border-radius: 6px;
      padding: 10px 12px;
      font-size: 14px;
      outline: none;
    }

    input:focus, textarea:focus {
      border-color: var(--gold);
    }

    /* 상단 헤더 */
    .topbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 12px 24px;
      background: linear-gradient(180deg, #12151e 0%, #0b0d12 100%);
      border-bottom: 1px solid var(--border);
      position: sticky;
      top: 0;
      z-index: 50;
      flex-wrap: wrap;
      gap: 12px;
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 14px;
    }

    .brand-title {
      font-size: 18px;
      font-weight: 800;
      letter-spacing: 1px;
      color: var(--gold);
    }

    .brand-sub {
      font-size: 11px;
      color: var(--text-muted);
      letter-spacing: 0.5px;
    }

    .logo-wave-box {
      display: flex;
      align-items: center;
      gap: 8px;
      background: rgba(212, 175, 55, 0.08);
      border: 1px solid rgba(212, 175, 55, 0.35);
      padding: 4px 10px;
      border-radius: 6px;
    }

    .logo-wave-label {
      font-size: 11px;
      color: var(--gold-light);
      font-weight: 600;
    }

    .top-actions {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .badge-status {
      font-size: 12px;
      padding: 5px 10px;
      border-radius: 20px;
      background: var(--bg-card);
      border: 1px solid var(--border);
      color: var(--text-muted);
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: var(--success);
    }

    .dot.local {
      background: var(--gold);
    }

    .btn-outline {
      background: transparent;
      border: 1px solid var(--border);
      color: var(--text-main);
      padding: 6px 12px;
      border-radius: 6px;
      font-size: 12px;
      font-weight: 600;
    }

    .btn-outline:hover {
      border-color: var(--gold);
      color: var(--gold);
    }

    .btn-gold {
      background: linear-gradient(135deg, var(--gold) 0%, #b58d1e 100%);
      color: #090a0d;
      font-weight: 800;
      padding: 10px 18px;
      border-radius: 6px;
      font-size: 14px;
    }

    .btn-gold:hover {
      filter: brightness(1.08);
      transform: translateY(-1px);
    }

    /* 로비 화면 */
    .container {
      max-width: 1280px;
      margin: 0 auto;
      padding: 24px;
    }

    .lobby-grid {
      display: grid;
      grid-template-columns: 1.15fr 0.85fr;
      gap: 24px;
      margin-top: 10px;
    }

    @media (max-width: 960px) {
      .lobby-grid {
        grid-template-columns: 1fr;
      }
    }

    .panel {
      background: var(--bg-panel);
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 22px;
    }

    .panel-title {
      font-size: 16px;
      font-weight: 700;
      color: var(--gold-light);
      margin-bottom: 14px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .hero-banner {
      background: radial-gradient(circle at top right, rgba(212, 175, 55, 0.14), transparent 65%), var(--bg-panel);
      border: 1px solid rgba(212, 175, 55, 0.35);
      border-radius: 12px;
      padding: 24px;
      margin-bottom: 20px;
    }

    .hero-banner h1 {
      font-size: 26px;
      font-weight: 800;
      color: var(--gold);
      margin-bottom: 8px;
    }

    .hero-banner p {
      color: var(--text-muted);
      font-size: 14px;
      line-height: 1.6;
    }

    .daily-seed-tag {
      display: inline-block;
      margin-top: 12px;
      font-size: 12px;
      padding: 4px 10px;
      background: var(--gold-dim);
      border: 1px solid rgba(212, 175, 55, 0.4);
      color: var(--gold-light);
      border-radius: 4px;
    }

    .auth-box {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-bottom: 20px;
      padding-bottom: 20px;
      border-bottom: 1px solid var(--border);
    }

    .auth-row {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
    }

    .mode-cards {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 14px;
    }

    @media (max-width: 600px) {
      .mode-cards {
        grid-template-columns: 1fr;
      }
    }

    .mode-card {
      background: var(--bg-card);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 18px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      gap: 14px;
    }

    .mode-card h3 {
      font-size: 16px;
      color: var(--text-main);
      margin-bottom: 6px;
    }

    .mode-card p {
      font-size: 12.5px;
      color: var(--text-muted);
      line-height: 1.5;
    }

    /* 대기실 모달/영역 */
    .waiting-room {
      background: var(--bg-card);
      border: 1px solid var(--gold);
      border-radius: 10px;
      padding: 18px;
      margin-top: 16px;
      display: none;
    }

    .room-code-display {
      font-size: 26px;
      font-weight: 900;
      letter-spacing: 4px;
      color: var(--gold);
      background: #090b10;
      padding: 8px 16px;
      border-radius: 8px;
      border: 1px dashed var(--gold);
      display: inline-block;
    }

    .slot-list {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 8px;
      margin: 14px 0;
    }

    .slot-item {
      background: var(--bg-panel);
      border: 1px solid var(--border);
      padding: 8px;
      border-radius: 6px;
      font-size: 12px;
      text-align: center;
    }

    .slot-item.human {
      border-color: var(--gold);
      color: var(--gold-light);
      font-weight: 700;
    }

    /* 랭킹 테이블 */
    .ranking-table {
      width: 100%;
      border-collapse: collapse;
      font-size: 13px;
    }

    .ranking-table th {
      text-align: left;
      padding: 10px 8px;
      color: var(--text-muted);
      border-bottom: 1px solid var(--border);
      font-weight: 600;
    }

    .ranking-table td {
      padding: 10px 8px;
      border-bottom: 1px solid rgba(42, 47, 62, 0.5);
    }

    .rank-1 { color: var(--gold); font-weight: 800; }
    .rank-2 { color: #e2e8f0; font-weight: 700; }
    .rank-3 { color: #cd7f32; font-weight: 700; }

    /* 게임 화면 */
    #gameScreen {
      display: none;
    }

    .game-status-bar {
      display: grid;
      grid-template-columns: repeat(5, 1fr);
      gap: 12px;
      margin-bottom: 18px;
    }

    @media (max-width: 900px) {
      .game-status-bar {
        grid-template-columns: repeat(2, 1fr);
      }
    }

    .stat-card {
      background: var(--bg-panel);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 14px 16px;
    }

    .stat-label {
      font-size: 11.5px;
      color: var(--text-muted);
      margin-bottom: 4px;
    }

    .stat-value {
      font-size: 19px;
      font-weight: 800;
      color: var(--text-main);
    }

    .stat-value.gold { color: var(--gold); }

    .game-main-grid {
      display: grid;
      grid-template-columns: 1.65fr 0.85fr;
      gap: 18px;
    }

    @media (max-width: 1080px) {
      .game-main-grid {
        grid-template-columns: 1fr;
      }
    }

    /* 종목 카드 그리드 */
    .stocks-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 14px;
    }

    .stock-card {
      background: var(--bg-panel);
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 15px;
      position: relative;
      transition: border-color 0.2s;
    }

    .stock-card:hover {
      border-color: rgba(212, 175, 55, 0.5);
    }

    .stock-card.secret-active {
      border-color: var(--secret);
      box-shadow: 0 0 15px rgba(157, 78, 221, 0.2);
    }

    .stock-header {
      display: flex;
      justify-content: space-between;
      align-items: flex-start;
      margin-bottom: 10px;
    }

    .stock-name {
      font-size: 16px;
      font-weight: 800;
      color: var(--text-main);
    }

    .stock-price {
      font-size: 18px;
      font-weight: 800;
      text-align: right;
    }

    .price-up { color: var(--up); }
    .price-down { color: var(--down); }
    .price-flat { color: var(--text-muted); }

    .stock-meta {
      display: flex;
      justify-content: space-between;
      font-size: 12px;
      color: var(--text-muted);
      background: var(--bg-card);
      padding: 7px 10px;
      border-radius: 6px;
      margin-bottom: 10px;
    }

    .rule-box {
      font-size: 12px;
      line-height: 1.45;
      padding: 9px 10px;
      border-radius: 6px;
      background: rgba(255, 255, 255, 0.03);
      border-left: 3px solid var(--border);
      margin-bottom: 12px;
      min-height: 54px;
      color: var(--text-muted);
    }

    .rule-box.unlocked {
      border-left-color: var(--gold);
      color: var(--text-main);
      background: rgba(212, 175, 55, 0.07);
    }

    .trade-controls {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 6px;
    }

    .qty-btn {
      background: var(--bg-card);
      border: 1px solid var(--border);
      color: var(--text-main);
      width: 30px;
      height: 30px;
      border-radius: 6px;
      font-weight: 700;
    }

    .qty-btn:hover:not(:disabled) {
      border-color: var(--gold);
      color: var(--gold);
    }

    .order-badge {
      font-size: 12px;
      font-weight: 700;
      padding: 4px 8px;
      border-radius: 4px;
      background: var(--bg-dark);
      min-width: 72px;
      text-align: center;
    }

    .btn-secret {
      background: rgba(157, 78, 221, 0.16);
      border: 1px solid var(--secret);
      color: #d8b4fe;
      font-size: 11px;
      font-weight: 700;
      padding: 6px 9px;
      border-radius: 6px;
    }

    .btn-secret:hover:not(:disabled) {
      background: var(--secret);
      color: #fff;
    }

    /* 우측 사이드바 */
    .side-stack {
      display: flex;
      flex-direction: column;
      gap: 16px;
    }

    .piece-actions {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 8px;
      margin-top: 10px;
    }

    .btn-piece {
      background: var(--bg-card);
      border: 1px solid rgba(212, 175, 55, 0.45);
      color: var(--gold-light);
      padding: 9px 10px;
      border-radius: 6px;
      font-size: 12px;
      font-weight: 700;
    }

    .btn-piece:hover:not(:disabled) {
      background: var(--gold-dim);
    }

    .log-box {
      height: 190px;
      overflow-y: auto;
      background: #090b10;
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 10px;
      font-size: 12px;
      line-height: 1.55;
      color: var(--text-muted);
    }

    .log-item {
      margin-bottom: 6px;
      padding-bottom: 6px;
      border-bottom: 1px dashed rgba(255,255,255,0.06);
    }

    .log-item strong {
      color: var(--gold-light);
    }

    /* 모달 */
    .modal-backdrop {
      position: fixed;
      inset: 0;
      background: rgba(0, 0, 0, 0.78);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 100;
      padding: 20px;
    }

    .modal {
      background: var(--bg-panel);
      border: 1px solid var(--gold);
      border-radius: 12px;
      max-width: 560px;
      width: 100%;
      padding: 24px;
      max-height: 90vh;
      overflow-y: auto;
    }

    .modal h2 {
      color: var(--gold);
      margin-bottom: 12px;
      font-size: 20px;
    }

    .classified {
      color: #c084fc;
      font-weight: 800;
      letter-spacing: 1px;
    }
  </style>
</head>
<body>

  <!-- 상단 네비게이션 -->
  <header class="topbar">
    <div class="brand">
      <div>
        <div class="brand-title">THE DEVIL'S PLAN : 미스터리 거래소</div>
        <div class="brand-sub">DAILY ROTATION EDITION · 24 ROUNDS SURVIVAL</div>
      </div>
      <!-- 공식 로고 파형 그래프 (8주기) -->
      <div class="logo-wave-box" title="미스터리 거래소 공식 로고 파형 (8주기 반복)">
        <span class="logo-wave-label">공식 로고 파형</span>
        <svg id="headerLogoWave" width="120" height="28" viewBox="0 0 120 28"></svg>
      </div>
    </div>

    <div class="top-actions">
      <div class="badge-status" id="dbStatusBadge">
        <span class="dot local" id="dbDot"></span>
        <span id="dbStatusText">로컬 실시간 동기화 모드</span>
      </div>
      <button class="btn-outline" onclick="openFirebaseModal()">Firebase 연결 설정</button>
      <button class="btn-outline" id="btnBackLobby" style="display:none;" onclick="confirmBackToLobby()">로비로 나가기</button>
    </div>
  </header>

  <!-- 1. 로비 (홈 화면) -->
  <main class="container" id="lobbyScreen">
    <div class="hero-banner">
      <h1>미스터리 거래소 (MYSTERY EXCHANGE)</h1>
      <p>
        7개 종목에 숨겨진 주가 변동 알고리즘을 추리하고, <strong>시크릿</strong>과 <strong>피스</strong>를 활용해 24라운드 종료 시 최고 자산을 달성하세요.<br/>
        <strong>매일 자정(00:00)</strong> 날짜 시드에 따라 7개 종목의 주가 공식 조합과 변동 수치가 새롭게 변경됩니다.
      </p>
      <div class="daily-seed-tag" id="dailySeedInfo">오늘의 규칙 시드 로딩 중...</div>
    </div>

    <div class="lobby-grid">
      <!-- 좌측: 프로필 & 게임 모드 선택 -->
      <div class="panel">
        <div class="panel-title">
          <span>플레이어 인증 및 참가 설정</span>
          <span style="font-size:12px; color:var(--text-muted);" id="userAuthLabel">게스트 상태</span>
        </div>

        <div class="auth-box">
          <div class="auth-row">
            <input type="text" id="nicknameInput" placeholder="사용할 닉네임 입력 (최대 10자)" maxlength="10" style="flex:1;" />
            <button class="btn-gold" onclick="saveGuestNickname()">닉네임 적용</button>
            <button class="btn-outline" onclick="googleSignIn()" id="btnGoogleLogin">Google 로그인</button>
          </div>
          <div style="font-size:12px; color:var(--text-muted);">
            * 로그인 및 닉네임 설정 시 최종 자산 기록이 글로벌 명예의 전당 랭킹에 반영됩니다.
          </div>
        </div>

        <div class="panel-title"><span>게임 모드 선택</span></div>
        <div class="mode-cards">
          <!-- 솔로 플레이 -->
          <div class="mode-card">
            <div>
              <h3>솔로 서바이벌 (1인 + AI 7인)</h3>
              <p>무작위 한국인 AI 플레이어 7명과 즉시 24라운드 두뇌 대결을 시작합니다.</p>
            </div>
            <button class="btn-gold" onclick="startSoloGame()">솔로 매치 즉시 시작</button>
          </div>

          <!-- 멀티플레이 방 만들기 / 입장 -->
          <div class="mode-card">
            <div>
              <h3>친구와 멀티플레이 (방 코드)</h3>
              <p>6자리 방 코드를 생성해 친구를 초대하거나 코드를 입력해 입장합니다. 빈자리는 AI가 채웁니다.</p>
            </div>
            <div style="display:flex; flex-direction:column; gap:8px;">
              <button class="btn-gold" onclick="createMultiRoom()">새 방 만들기 (코드 생성)</button>
              <div style="display:flex; gap:6px;">
                <input type="text" id="joinCodeInput" placeholder="방 코드 6자리" maxlength="6" style="width:100%; text-transform:uppercase;" />
                <button class="btn-outline" style="white-space:nowrap;" onclick="joinMultiRoom()">입장</button>
              </div>
            </div>
          </div>
        </div>

        <!-- 멀티플레이 대기실 -->
        <div class="waiting-room" id="waitingRoomBox">
          <div style="display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:10px;">
            <div>
              <div style="font-size:12px; color:var(--text-muted);">멀티플레이 대기실 코드 (친구에게 공유)</div>
              <div style="display:flex; align-items:center; gap:10px; margin-top:4px;">
                <span class="room-code-display" id="displayRoomCode">------</span>
                <button class="btn-outline" onclick="copyRoomCode()">코드 복사</button>
              </div>
            </div>
            <div style="display:flex; gap:8px;">
              <button class="btn-gold" id="btnStartMulti" onclick="hostStartMultiGame()">게임 시작 (빈자리 AI 채움)</button>
              <button class="btn-outline" onclick="leaveMultiRoom()">대기실 나가기</button>
            </div>
          </div>
          <div class="slot-list" id="waitingSlots"></div>
          <div style="font-size:12px; color:var(--text-muted);">
            * 같은 기기 다른 브라우저 탭 또는 Firebase 연동 시 다른 기기 친구와 실시간으로 동기화됩니다.
          </div>
        </div>
      </div>

      <!-- 우측: 글로벌 랭킹 보드 -->
      <div class="panel">
        <div class="panel-title">
          <span>역대 최고 자산 랭킹 (TOP 15)</span>
          <button class="btn-outline" onclick="refreshLeaderboard()">새로고침</button>
        </div>
        <div style="overflow-x:auto;">
          <table class="ranking-table">
            <thead>
              <tr>
                <th>순위</th>
                <th>플레이어</th>
                <th>최고 자산</th>
                <th>등급</th>
                <th>기록일</th>
              </tr>
            </thead>
            <tbody id="leaderboardBody">
              <tr><td colspan="5" style="text-align:center; color:var(--text-muted);">랭킹 불러오는 중...</td></tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </main>

  <!-- 2. 인게임 화면 -->
  <main class="container" id="gameScreen">
    <!-- 상단 요약 바 -->
    <div class="game-status-bar">
      <div class="stat-card">
        <div class="stat-label">진행 라운드 / 다음 힌트 공개</div>
        <div class="stat-value gold" id="statRound">1 / 24 R</div>
        <div style="font-size:11px; color:var(--text-muted);" id="statNextHint">다음 규칙 공개: 5R</div>
      </div>
      <div class="stat-card">
        <div class="stat-label">보유 현금 (주문 후 예상)</div>
        <div class="stat-value" id="statCash">100,000원</div>
        <div style="font-size:11px; color:var(--text-muted);" id="statPendingCash">주문 반영: 100,000원</div>
      </div>
      <div class="stat-card">
        <div class="stat-label">총 평가 자산 (현금+주식)</div>
        <div class="stat-value gold" id="statTotalAsset">100,000원</div>
        <div style="font-size:11px; color:var(--text-muted);" id="statRank">현재 순위: 1위 / 8명</div>
      </div>
      <div class="stat-card">
        <div class="stat-label">보유 피스 / 시크릿 권리</div>
        <div class="stat-value" id="statPieces">피스 2개 · 시크릿 가능</div>
        <div style="font-size:11px; color:var(--text-muted);" id="statSecretStatus">1회 한정 블라인드</div>
      </div>
      <div class="stat-card" style="display:flex; flex-direction:column; justify-content:center;">
        <button class="btn-gold" style="width:100%; height:100%; font-size:15px;" id="btnConfirmRound" onclick="submitPlayerTurn()">
          거래 확정 및 라운드 진행
        </button>
      </div>
    </div>

    <div class="game-main-grid">
      <!-- 좌측: 7개 종목 거래 보드 -->
      <div>
        <div class="panel-title">
          <span>상장 종목 현황 (초기가 10,000원 · 최저가 100원)</span>
          <span style="font-size:12px; color:var(--text-muted);" id="multiSyncNotice"></span>
        </div>
        <div class="stocks-grid" id="stocksGrid"></div>
      </div>

      <!-- 우측: 피스 활용 + 실시간 순위 + 거래소 로그 -->
      <div class="side-stack">
        <div class="panel">
          <div class="panel-title"><span>피스 (PIECE) 특수 권리</span></div>
          <p style="font-size:12px; color:var(--text-muted); line-height:1.5;">
            20라운드 종료 전까지 피스 1개를 소모해 미공개 종목 규칙 1개를 미리 해금하거나 가상 현금 10,000원으로 환전할 수 있습니다.
          </p>
          <div class="piece-actions">
            <button class="btn-piece" id="btnPieceHint" onclick="usePieceForHint()">피스 1개 → 규칙 선공개</button>
            <button class="btn-piece" id="btnPieceCash" onclick="usePieceForCash()">피스 1개 → +10,000원</button>
          </div>
        </div>

        <div class="panel">
          <div class="panel-title"><span>실시간 참가자 순위 (8인)</span></div>
          <table class="ranking-table">
            <thead>
              <tr>
                <th>순위</th>
                <th>플레이어</th>
                <th>총 자산</th>
              </tr>
            </thead>
            <tbody id="inGameRankBody"></tbody>
          </table>
        </div>

        <div class="panel">
          <div class="panel-title"><span>거래소 브리핑 로그</span></div>
          <div class="log-box" id="gameLogBox"></div>
        </div>
      </div>
    </div>
  </main>

  <!-- Firebase 설정 모달 -->
  <div class="modal-backdrop" id="firebaseModal">
    <div class="modal">
      <h2>Firebase 실시간 데이터베이스 연결</h2>
      <p style="font-size:13px; color:var(--text-muted); line-height:1.55; margin-bottom:12px;">
        서로 다른 기기(PC/모바일)의 친구와 방 코드로 실시간 멀티플레이를 하거나 공용 글로벌 랭킹을 공유하려면 Firebase 프로젝트의 <code>firebaseConfig</code> JSON을 붙여넣으세요.<br/>
        (미입력 시 브라우저 내장 실시간 동기화로 자동 작동합니다.)
      </p>
      <textarea id="firebaseConfigInput" rows="8" style="width:100%; font-family:monospace; font-size:12px;" placeholder='{
  "apiKey": "AIzaSy...",
  "authDomain": "your-app.firebaseapp.com",
  "databaseURL": "https://your-app-default-rtdb.firebaseio.com",
  "projectId": "your-app",
  "storageBucket": "your-app.appspot.com",
  "messagingSenderId": "123456789",
  "appId": "1:123456789:web:abcdef"
}'></textarea>
      <div style="display:flex; justify-content:flex-end; gap:8px; margin-top:14px;">
        <button class="btn-outline" onclick="clearFirebaseConfig()">설정 초기화</button>
        <button class="btn-outline" onclick="closeFirebaseModal()">닫기</button>
        <button class="btn-gold" onclick="saveFirebaseConfig()">저장 및 연결</button>
      </div>
    </div>
  </div>

  <!-- 최종 결과 모달 -->
  <div class="modal-backdrop" id="resultModal">
    <div class="modal" style="max-width:640px;">
      <h2>24라운드 종료 · 최종 정산 결과</h2>
      <div id="resultSummaryBox" style="margin-bottom:16px;"></div>
      <table class="ranking-table" style="margin-bottom:18px;">
        <thead>
          <tr>
            <th>최종 순위</th>
            <th>플레이어</th>
            <th>최종 자산</th>
            <th>생존 판정</th>
          </tr>
        </thead>
        <tbody id="finalRankBody"></tbody>
      </table>
      <div style="display:flex; justify-content:flex-end; gap:10px;">
        <button class="btn-gold" onclick="finishAndGoLobby()">로비로 돌아가기 (랭킹 반영)</button>
      </div>
    </div>
  </div>

  <!-- Firebase Compat SDK (동적 초기화 지원) -->
  <script src="https://www.gstatic.com/firebasejs/10.12.2/firebase-app-compat.js"></script>
  <script src="https://www.gstatic.com/firebasejs/10.12.2/firebase-auth-compat.js"></script>
  <script src="https://www.gstatic.com/firebasejs/10.12.2/firebase-database-compat.js"></script>

  <script>
    /*************************************************************************
     * 1. 일일 시드(YYYY-MM-DD) & 7개 공식 종목 일일 규칙 엔진
     *************************************************************************/
    const STOCK_NAMES = [
      '맛소금융',
      '무조건설',
      '방어제철',
      '알트엔터',
      '열림보안',
      '코요테크',
      '후자전자'
    ];

    // 공식 로고 파형 (8주기 사인/지그재그 형태)
    const LOGO_WAVE_PATTERN = [1.08, 1.14, 1.04, 0.90, 0.86, 0.95, 1.06, 1.12];

    // 일반 한국인 AI 이름 풀 (연예인/방송인 제외)
    const KOREAN_AI_NAMES = [
      '김도윤', '이서연', '박지훈', '최하은', '정우진', '강수빈', '조민재',
      '윤지아', '장현우', '임채원', '한시우', '오유진', '서준호', '신예린',
      '권태양', '황다인', '안준서', '송지민', '전민규', '홍서윤', '유승현',
      '문하린', '양지호', '손채은', '배준영', '백소율', '허건우', '남지우'
    ];

    function getTodayDateString() {
      const now = new Date();
      const y = now.getFullYear();
      const m = String(now.getMonth() + 1).padStart(2, '0');
      const d = String(now.getDate()).padStart(2, '0');
      return `${y}-${m}-${d}`;
    }

    // 결정론적 시드 난수 생성기 (Mulberry32)
    function createSeededRandom(seedStr) {
      let h = 2166136261 >>> 0;
      for (let i = 0; i < seedStr.length; i++) {
        h ^= seedStr.charCodeAt(i);
        h = Math.imul(h, 16777619);
      }
      return function() {
        h += 0x6D2B79F5;
        let t = Math.imul(h ^ (h >>> 15), 1 | h);
        t ^= t + Math.imul(t ^ (t >>> 7), 61 | t);
        return ((t ^ (t >>> 14)) >>> 0) / 4294967296;
      };
    }

    // 매일 날짜 시드 기반으로 7개 종목에 7가지 공식 메커니즘을 매칭 & 파라미터 변동
    function generateDailyRules(dateStr) {
      const rand = createSeededRandom('DEVILS_PLAN_EXCHANGE_' + dateStr);

      // 0~6 인덱스를 시드 기반으로 셔플하여 매일 종목별 규칙이 바뀌도록 구성
      const indices = [0, 1, 2, 3, 4, 5, 6];
      for (let i = indices.length - 1; i > 0; i--) {
        const j = Math.floor(rand() * (i + 1));
        [indices[i], indices[j]] = [indices[j], indices[i]];
      }

      // 7가지 핵심 메커니즘 템플릿 (업로드된 공식 규칙 기반 + 일일 파라미터 가변)
      const upThreshold = 4;
      const upPct = 15 + Math.floor(rand() * 3) * 5; // 15%, 20%, 25%
      const downPct = 10 + Math.floor(rand() * 2) * 5; // 10%, 15%
      const followPct = 10 + Math.floor(rand() * 2) * 5; // 10%, 15%
      const supplyUnit = 150 + Math.floor(rand() * 3) * 50; // 150, 200, 250원
      const secretUpPct = 12 + Math.floor(rand() * 5); // 12~16%
      const secretDownAmt = 800 + Math.floor(rand() * 3) * 200; // 800, 1000, 1200원
      const battleUpAmt = 1200 + Math.floor(rand() * 3) * 200; // 1200, 1400, 1600원
      const battleDownAmt = 600 + Math.floor(rand() * 3) * 100; // 600, 700, 800원
      const rangeMin = 8 + Math.floor(rand() * 5); // 8~12주
      const rangeMax = rangeMin + 18 + Math.floor(rand() * 5); // +18~22주
      const rangeAmt = 1200 + Math.floor(rand() * 4) * 200; // 1200~1800원

      // 각 종목의 인덱스 위치 파악 (연동 규칙용)
      const stockAt = (ruleTypeIdx) => STOCK_NAMES[indices[ruleTypeIdx]];

      const ruleTemplates = [
        // 0: 시장 상승 종목 수 연동 (맛소금융 원형)
        (selfIdx) => ({
          type: 'MARKET_UP_COUNT',
          desc: `직전 라운드에 ${upThreshold}개 이상의 주식이 상승했을 경우 +${upPct}%, 그렇지 않으면 -${downPct}%`,
          calc: (ctx, st) => {
            if (ctx.round === 1) return Math.round(st.price * 1.05);
            return ctx.prevUpCount >= upThreshold
              ? Math.round(st.price * (1 + upPct / 100))
              : Math.round(st.price * (1 - downPct / 100));
          }
        }),
        // 1: 특정 타겟 종목 상승 추종 (무조건설 원형)
        (selfIdx) => {
          const targetIdx = indices[2]; // 보유총량 반비례 종목 추종
          const targetName = STOCK_NAMES[targetIdx];
          return {
            type: 'FOLLOW_TARGET',
            desc: `${targetName}의 가격이 직전 라운드에 올랐으면 +${followPct}%, 그렇지 않으면 -${followPct}%`,
            calc: (ctx, st) => {
              const target = ctx.stocks[targetIdx];
              const rose = target.lastChange > 0;
              return rose
                ? Math.round(st.price * (1 + followPct / 100))
                : Math
