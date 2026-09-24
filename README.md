# midnight--trading-
a trading binary bot
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Nova — realistic UI/UX dashboard</title>
  <!-- Font & icons (clean, modern) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: #f6f8fc;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      padding: 16px;
      transition: background 0.3s;
    }

    /* dark mode adaptation (optional but we keep light) */
    .app {
      width: 100%;
      max-width: 1320px;
      background: #ffffff;
      border-radius: 32px;
      box-shadow: 0 20px 40px -12px rgba(0, 20, 45, 0.15), 0 8px 24px -6px rgba(0, 0, 0, 0.05);
      display: flex;
      overflow: hidden;
      transition: all 0.2s;
    }

    /* ---------- SIDEBAR ---------- */
    .sidebar {
      width: 260px;
      background: #ffffff;
      padding: 28px 16px;
      display: flex;
      flex-direction: column;
      border-right: 1px solid #eef1f7;
      flex-shrink: 0;
    }

    .logo-area {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 0 12px 28px 12px;
    }

    .logo-icon {
      background: #1e2b4f;
      color: white;
      width: 36px;
      height: 36px;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 20px;
      font-weight: 700;
      box-shadow: 0 6px 12px -6px rgba(0, 20, 45, 0.25);
    }

    .logo-text {
      font-weight: 700;
      font-size: 20px;
      letter-spacing: -0.3px;
      color: #121826;
    }

    .logo-text span {
      color: #4f6af5;
    }

    .nav {
      display: flex;
      flex-direction: column;
      gap: 6px;
      flex: 1;
    }

    .nav-item {
      display: flex;
      align-items: center;
      gap: 14px;
      padding: 12px 16px;
      border-radius: 14px;
      color: #5c6a7e;
      font-weight: 500;
      font-size: 15px;
      transition: all 0.15s;
      cursor: pointer;
      border: none;
      background: transparent;
      width: 100%;
      text-align: left;
    }

    .nav-item i {
      width: 20px;
      font-size: 18px;
      color: #7c8799;
      transition: color 0.15s;
    }

    .nav-item:hover {
      background: #f2f5fb;
      color: #1e2b4f;
    }

    .nav-item:hover i {
      color: #1e2b4f;
    }

    .nav-item.active {
      background: #eef2ff;
      color: #1e2b4f;
      font-weight: 600;
    }

    .nav-item.active i {
      color: #4f6af5;
    }

    .sidebar-footer {
      padding-top: 24px;
      border-top: 1px solid #eef1f7;
      margin-top: 24px;
    }

    .user-card {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 12px;
      border-radius: 16px;
      background: #fafbff;
      transition: background 0.2s;
      cursor: pointer;
    }

    .user-card:hover {
      background: #f2f5fb;
    }

    .avatar {
      width: 40px;
      height: 40px;
      background: linear-gradient(135deg, #4f6af5, #8e5cf7);
      border-radius: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-weight: 600;
      font-size: 16px;
      box-shadow: 0 4px 8px -4px rgba(79, 106, 245, 0.4);
    }

    .user-info h4 {
      font-size: 14px;
      font-weight: 600;
      color: #121826;
    }

    .user-info p {
      font-size: 12px;
      color: #7c8799;
      margin-top: 2px;
    }

    /* ---------- MAIN CONTENT ---------- */
    .main {
      flex: 1;
      padding: 32px 36px;
      background: #ffffff;
      overflow-y: auto;
    }

    .top-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 32px;
      flex-wrap: wrap;
      gap: 16px;
    }

    .greeting h1 {
      font-size: 26px;
      font-weight: 700;
      color: #121826;
      letter-spacing: -0.5px;
    }

    .greeting p {
      font-size: 15px;
      color: #6f7d93;
      margin-top: 4px;
    }

    .actions {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .search-box {
      display: flex;
      align-items: center;
      gap: 8px;
      background: #f5f7fd;
      padding: 10px 18px;
      border-radius: 40px;
      border: 1px solid #e6eaf2;
      transition: all 0.2s;
    }

    .search-box i {
      color: #8f9bb0;
      font-size: 16px;
    }

    .search-box input {
      border: none;
      background: transparent;
      outline: none;
      font-size: 14px;
      font-family: 'Inter', sans-serif;
      color: #121826;
      width: 160px;
    }

    .search-box input::placeholder {
      color: #9aa6bc;
    }

    .search-box:focus-within {
      border-color: #4f6af5;
      background: #ffffff;
      box-shadow: 0 0 0 4px rgba(79, 106, 245, 0.1);
    }

    .btn-icon {
      background: #ffffff;
      border: 1px solid #e6eaf2;
      width: 42px;
      height: 42px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #4f6af5;
      font-size: 18px;
      cursor: pointer;
      transition: all 0.15s;
    }

    .btn-icon:hover {
      background: #f2f5fb;
      border-color: #d0d8e8;
    }

    /* stats grid */
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 20px;
      margin-bottom: 32px;
    }

    .stat-card {
      background: #ffffff;
      border: 1px solid #edf0f7;
      border-radius: 24px;
      padding: 20px 20px 22px;
      transition: all 0.2s;
      box-shadow: 0 4px 12px -6px rgba(0, 0, 0, 0.02);
    }

    .stat-card:hover {
      border-color: #d9e0ee;
      box-shadow: 0 12px 24px -12px rgba(0, 20, 45, 0.08);
    }

    .stat-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 14px;
    }

    .stat-header span {
      font-size: 14px;
      font-weight: 500;
      color: #6b7a91;
      letter-spacing: 0.2px;
    }

    .stat-icon {
      width: 36px;
      height: 36px;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #f2f5fb;
      color: #4f6af5;
    }

    .stat-value {
      font-size: 28px;
      font-weight: 700;
      color: #121826;
      letter-spacing: -0.5px;
      line-height: 1.2;
    }

    .stat-trend {
      display: flex;
      align-items: center;
      gap: 6px;
      margin-top: 10px;
      font-size: 13px;
      font-weight: 500;
    }

    .trend-up {
      color: #12b76a;
    }

    .trend-down {
      color: #f04438;
    }

    .stat-trend i {
      font-size: 12px;
    }

    /* chart + activity row */
    .chart-section {
      display: flex;
      gap: 24px;
      margin-bottom: 32px;
      flex-wrap: wrap;
    }

    .chart-container {
      flex: 2;
      background: #ffffff;
      border: 1px solid #edf0f7;
      border-radius: 28px;
      padding: 24px 24px 18px;
      min-width: 320px;
      box-shadow: 0 4px 12px -6px rgba(0, 0, 0, 0.02);
    }

    .chart-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }

    .chart-header h3 {
      font-size: 18px;
      font-weight: 600;
      color: #121826;
      letter-spacing: -0.3px;
    }

    .chart-header a {
      font-size: 14px;
      color: #4f6af5;
      text-decoration: none;
      font-weight: 500;
      transition: color 0.15s;
    }

    .chart-header a:hover {
      color: #2c45d0;
    }

    .chart-bars {
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      height: 180px;
      gap: 8px;
      padding: 0 4px;
    }

    .bar-item {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 8px;
      flex: 1;
      height: 100%;
    }

    .bar-wrapper {
      display: flex;
      align-items: flex-end;
      height: 140px;
      width: 100%;
      justify-content: center;
    }

    .bar {
      width: 100%;
      max-width: 38px;
      background: linear-gradient(180deg, #4f6af5, #6d8aff);
      border-radius: 12px 12px 8px 8px;
      transition: all 0.2s;
      height: 0%; /* will be set via js */
      box-shadow: 0 4px 8px -4px rgba(79, 106, 245, 0.3);
      cursor: pointer;
      position: relative;
      min-height: 6px;
    }

    .bar:hover {
      opacity: 0.85;
      transform: scaleY(1.02);
    }

    .bar-label {
      font-size: 13px;
      color: #7c8799;
      font-weight: 500;
    }

    .activity-panel {
      flex: 1.2;
      background: #ffffff;
      border: 1px solid #edf0f7;
      border-radius: 28px;
      padding: 24px 20px;
      min-width: 240px;
      box-shadow: 0 4px 12px -6px rgba(0, 0, 0, 0.02);
    }

    .activity-panel h3 {
      font-size: 18px;
      font-weight: 600;
      color: #121826;
      margin-bottom: 20px;
      letter-spacing: -0.3px;
    }

    .activity-list {
      display: flex;
      flex-direction: column;
      gap: 16px;
    }

    .activity-item {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .activity-avatar {
      width: 38px;
      height: 38px;
      border-radius: 10px;
      background: #eef2ff;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #4f6af5;
      font-size: 16px;
      flex-shrink: 0;
    }

    .activity-detail {
      flex: 1;
    }

    .activity-detail p {
      font-size: 14px;
      font-weight: 500;
      color: #121826;
      line-height: 1.3;
    }

    .activity-detail span {
      font-size: 12px;
      color: #8896ab;
      display: block;
      margin-top: 3px;
    }

    /* ---------- TABLE / RECENT ---------- */
    .recent-section {
      background: #ffffff;
      border: 1px solid #edf0f7;
      border-radius: 28px;
      padding: 24px 24px 16px;
      box-shadow: 0 4px 12px -6px rgba(0, 0, 0, 0.02);
    }

    .recent-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 18px;
    }

    .recent-header h3 {
      font-size: 18px;
      font-weight: 600;
      color: #121826;
      letter-spacing: -0.3px;
    }

    .recent-header a {
      font-size: 14px;
      color: #4f6af5;
      text-decoration: none;
      font-weight: 500;
    }

    .table-wrapper {
      overflow-x: auto;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      font-size: 14px;
    }

    th {
      text-align: left;
      padding: 10px 0 12px;
      font-weight: 500;
      color: #7c8799;
      font-size: 13px;
      letter-spacing: 0.3px;
      border-bottom: 1px solid #edf0f7;
    }

    td {
      padding: 14px 0;
      border-bottom: 1px solid #f0f3fa;
      color: #1e2b4f;
      font-weight: 500;
    }

    tr:last-child td {
      border-bottom: none;
    }

    .status-badge {
      display: inline-block;
      padding: 4px 12px;
      border-radius: 30px;
      font-size: 12px;
      font-weight: 600;
    }

    .status-badge.paid {
      background: #e6f7ed;
      color: #0e7b4c;
    }

    .status-badge.pending {
      background: #fff6e5;
      color: #b25e00;
    }

    .status-badge.canceled {
      background: #ffe9e9;
      color: #c4320a;
    }

    /* responsive */
    @media (max-width: 1024px) {
      .stats-grid {
        grid-template-columns: repeat(2, 1fr);
      }
      .sidebar {
        width: 84px;
        padding: 24px 12px;
      }
      .logo-text, .nav-item span, .user-info {
        display: none;
      }
      .nav-item {
        justify-content: center;
        padding: 12px;
      }
      .nav-item i {
        margin: 0;
      }
      .logo-area {
        justify-content: center;
        padding: 0 0 24px 0;
      }
      .user-card {
        justify-content: center;
      }
      .avatar {
        margin: 0;
      }
      .main {
        padding: 24px;
      }
    }

    @media (max-width: 640px) {
      .stats-grid {
        grid-template-columns: 1fr;
      }
      .app {
        border-radius: 24px;
      }
      .search-box input {
        width: 100px;
      }
      .top-bar {
        flex-direction: column;
        align-items: flex-start;
      }
      .chart-bars {
        height: 140px;
      }
      .bar-wrapper {
        height: 100px;
      }
    }

    /* micro-interaction */
    .ripple {
      position: relative;
      overflow: hidden;
    }
  </style>
</head>
<body>
  <div class="app">
    <!-- SIDEBAR -->
    <aside class="sidebar">
      <div class="logo-area">
        <div class="logo-icon">N</div>
        <div class="logo-text">Nova<span>.</span></div>
      </div>
      <nav class="nav">
        <button class="nav-item active"><i class="fas fa-grid-2"></i><span>Overview</span></button>
        <button class="nav-item"><i class="fas fa-chart-pie"></i><span>Analytics</span></button>
        <button class="nav-item"><i class="fas fa-wallet"></i><span>Payments</span></button>
        <button class="nav-item"><i class="fas fa-users"></i><span>Customers</span></button>
        <button class="nav-item"><i class="fas fa-cog"></i><span>Settings</span></button>
      </nav>
      <div class="sidebar-footer">
        <div class="user-card">
          <div class="avatar">JD</div>
          <div class="user-info">
            <h4>Jordan Davis</h4>
            <p>Product Lead</p>
          </div>
        </div>
      </div>
    </aside>

    <!-- MAIN CONTENT -->
    <main class="main">
      <!-- top bar -->
      <div class="top-bar">
        <div class="greeting">
          <h1>Good morning, Jordan</h1>
          <p>Here's what's happening with your product today.</p>
        </div>
        <div class="actions">
          <div class="search-box">
            <i class="fas fa-search"></i>
            <input type="text" placeholder="Search..." id="searchInput">
          </div>
          <button class="btn-icon" id="notificationBtn"><i class="far fa-bell"></i></button>
        </div>
      </div>

      <!-- stats cards -->
      <div class="stats-grid">
        <div class="stat-card">
          <div class="stat-header">
            <span>Total revenue</span>
            <div class="stat-icon"><i class="fas fa-dollar-sign"></i></div>
          </div>
          <div class="stat-value">$48,290</div>
          <div class="stat-trend trend-up"><i class="fas fa-arrow-up"></i> 12.4% vs last month</div>
        </div>
        <div class="stat-card">
          <div class="stat-header">
            <span>Active users</span>
            <div class="stat-icon"><i class="fas fa-user-group"></i></div>
          </div>
          <div class="stat-value">8,642</div>
          <div class="stat-trend trend-up"><i class="fas fa-arrow-up"></i> 8.1% vs last month</div>
        </div>
        <div class="stat-card">
          <div class="stat-header">
            <span>Conversion</span>
            <div class="stat-icon"><i class="fas fa-percent"></i></div>
          </div>
          <div class="stat-value">5.28%</div>
          <div class="stat-trend trend-down"><i class="fas fa-arrow-down"></i> 0.6% vs last month</div>
        </div>
        <div class="stat-card">
          <div class="stat-header">
            <span>Avg. order</span>
            <div class="stat-icon"><i class="fas fa-cart-shopping"></i></div>
          </div>
          <div class="stat-value">$156.40</div>
          <div class="stat-trend trend-up"><i class="fas fa-arrow-up"></i> 3.2% vs last month</div>
        </div>
      </div>

      <!-- chart + activity -->
      <div class="chart-section">
        <div class="chart-container">
          <div class="chart-header">
            <h3>Weekly performance</h3>
            <a href="#">View report →</a>
          </div>
          <div class="chart-bars" id="chartBars">
            <!-- bars will be injected via js -->
          </div>
        </div>
        <div class="activity-panel">
          <h3>Recent activity</h3>
          <div class="activity-list">
            <div class="activity-item">
              <div class="activity-avatar"><i class="fas fa-file-invoice"></i></div>
              <div class="activity-detail">
                <p>New invoice #INV-2049</p>
                <span>2 min ago · $1,280</span>
              </div>
            </div>
            <div class="activity-item">
              <div class="activity-avatar"><i class="fas fa-user-plus"></i></div>
              <div class="activity-detail">
                <p>Sarah Chen joined</p>
                <span>25 min ago · Team</span>
              </div>
            </div>
            <div class="activity-item">
              <div class="activity-avatar"><i class="fas fa-rotate"></i></div>
              <div class="activity-detail">
                <p>Subscription renewed</p>
                <span>1 hr ago · Pro plan</span>
              </div>
            </div>
            <div class="activity-item">
              <div class="activity-avatar"><i class="fas fa-credit-card"></i></div>
              <div class="activity-detail">
                <p>Payment received</p>
                <span>3 hrs ago · $845</span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- recent transactions table -->
      <div class="recent-section">
        <div class="recent-header">
          <h3>Recent transactions</h3>
          <a href="#">View all →</a>
        </div>
        <div class="table-wrapper">
          <table>
            <thead>
              <tr>
                <th>Customer</th>
                <th>Date</th>
                <th>Amount</th>
                <th>Status</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Olivia Rhye</td>
                <td>Feb 20, 2025</td>
                <td>$420.00</td>
                <td><span class="status-badge paid">Paid</span></td>
              </tr>
              <tr>
                <td>Phoenix Baker</td>
                <td>Feb 19, 2025</td>
                <td>$1,050.00</td>
                <td><span class="status-badge pending">Pending</span></td>
              </tr>
              <tr>
                <td>Lana Steiner</td>
                <td>Feb 18, 2025</td>
                <td>$280.50</td>
                <td><span class="status-badge paid">Paid</span></td>
              </tr>
              <tr>
                <td>Demi Wilkinson</td>
                <td>Feb 17, 2025</td>
                <td>$670.00</td>
                <td><span class="status-badge canceled">Canceled</span></td>
              </tr>
              <tr>
                <td>Candice Wu</td>
                <td>Feb 16, 2025</td>
                <td>$1,200.00</td>
                <td><span class="status-badge paid">Paid</span></td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </main>
  </div>

  <script>
    (function() {
      // ----- DYNAMIC BAR CHART (realistic weekly data) -----
      const chartBars = document.getElementById('chartBars');
      const weeklyData = [
        { day: 'Mon', value: 48 },
        { day: 'Tue', value: 72 },
        { day: 'Wed', value: 58 },
        { day: 'Thu', value: 94 },
        { day: 'Fri', value: 82 },
        { day: 'Sat', value: 66 },
        { day: 'Sun', value: 39 }
      ];

      // find max for scaling (max 100 for clean)
      const maxValue = 100;

      // clear and build bars
      chartBars.innerHTML = '';
      weeklyData.forEach(item => {
        const barItem = document.createElement('div');
        barItem.className = 'bar-item';

        const wrapper = document.createElement('div');
        wrapper.className = 'bar-wrapper';

        const bar = document.createElement('div');
        bar.className = 'bar';
        // height as percentage relative to 100
        const heightPercent = (item.value / maxValue) * 100;
        bar.style.height = heightPercent + '%';
        // tooltip
        bar.setAttribute('title', `${item.day}: ${item.value} orders`);
        // extra data for realism
        bar.dataset.value = item.value;

        wrapper.appendChild(bar);
        barItem.appendChild(wrapper);

        const label = document.createElement('div');
        label.className = 'bar-label';
        label.textContent = item.day;
        barItem.appendChild(label);

        chartBars.appendChild(barItem);
      });

      // ----- INTERACTIVE: CLICK BAR TO SHOW SMALL PULSE (micro-interaction) -----
      document.querySelectorAll('.bar').forEach(bar => {
        bar.addEventListener('click', function(e) {
          // realistic "data point selection" effect
          this.style.transition = 'all 0.1s';
          this.style.opacity = '0.7';
          this.style.transform = 'scaleY(0.98)';
          setTimeout(() => {
            this.style.opacity = '1';
            this.style.transform = 'scaleY(1)';
          }, 120);
          // optional: show value in console (realistic feedback)
          const val = this.dataset.value;
          const label = this.closest('.bar-item').querySelector('.bar-label').textContent;
          console.log(`📊 ${label}: ${val} orders`);
        });
      });

      // ----- NAVIGATION ACTIVE STATE (UI/UX) -----
      const navItems = document.querySelectorAll('.nav-item');
      navItems.forEach(item => {
        item.addEventListener('click', function(e) {
          e.preventDefault();
          navItems.forEach(n => n.classList.remove('active'));
          this.classList.add('active');
        });
      });

      // ----- NOTIFICATION BUTTON micro-interaction -----
      const notifBtn = document.getElementById('notificationBtn');
      notifBtn.addEventListener('click', function() {
        this.style.transform = 'scale(0.92)';
        setTimeout(() => this.style.transform = 'scale(1)', 150);
        // realistic: show a toast-like message (simple)
        const originalColor = this.style.color;
        this.style.color = '#4f6af5';
        this.style.backgroundColor = '#eef2ff';
        setTimeout(() => {
          this.style.color = '';
          this.style.backgroundColor = '';
        }, 300);
      });

      // ----- SEARCH FOCUS (nice UX) -----
      const searchInput = document.getElementById('searchInput');
      searchInput.addEventListener('keydown', (e) => {
        if (e.key === 'Enter' && searchInput.value.trim() !== '') {
          alert(`🔍 Searching for: "${searchInput.value}" (demo)`);
          searchInput.value = '';
        }
      });

      // ----- HOVER micro-interaction for stat cards (already via CSS, but we add a little JS for fun) -----
      document.querySelectorAll('.stat-card').forEach(card => {
        card.addEventListener('mouseenter', function() {
          this.style.transform = 'translateY(-3px)';
          this.style.transition = 'all 0.2s ease';
        });
        card.addEventListener('mouseleave', function() {
          this.style.transform = 'translateY(0)';
        });
      });

      // ----- user card / avatar click -----
      document.querySelector('.user-card')?.addEventListener('click', () => {
        alert('👤 Profile settings (demo)');
      });

      // ----- make table rows interactive (UI realism) -----
      document.querySelectorAll('tbody tr').forEach(row => {
        row.style.transition = 'background 0.15s';
        row.addEventListener('mouseenter', function() {
          this.style.backgroundColor = '#fafbff';
        });
        row.addEventListener('mouseleave', function() {
          this.style.backgroundColor = 'transparent';
        });
        row.addEventListener('click', function() {
          const customer = this.cells[0].innerText;
          const amount = this.cells[2].innerText;
          alert(`📋 Transaction: ${customer} · ${amount} (demo)`);
        });
      });

      // ----- set random height variation for bar chart after load? already set with data. but we can animate initial load -----
      // animate bars from 0 to target on load
      window.addEventListener('load', () => {
        const bars = document.querySelectorAll('.bar');
        bars.forEach((bar, index) => {
          const targetHeight = bar.style.height;
          bar.style.height = '0%';
          setTimeout(() => {
            bar.style.transition = 'height 0.6s cubic-bezier(0.2, 0.9, 0.3, 1)';
            bar.style.height = targetHeight;
          }, index * 70);
        });
      });

      // also add a tiny "live" data update simulation? not needed, but keeping it realistic.
      // But we can update one stat card value slightly for demo effect? no, avoid distraction.
    })();
  </script>
</body>
</html>
