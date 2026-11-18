 
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Finova — Personal Finance & Wealth Tracker</title>
  <style>
    :root {
      --bg-app: #F8FAFC;
      --bg-surface: #FFFFFF;
      --bg-subtle: #F1F5F9;
      --bg-hover: #F8FAFC;
      --border-light: #E2E8F0;
      --border-focus: #0F172A;

      --text-primary: #0F172A;
      --text-secondary: #475569;
      --text-muted: #64748B;

      --emerald-50: #ECFDF5;
      --emerald-100: #D1FAE5;
      --emerald-500: #10B981;
      --emerald-600: #059669;
      --emerald-700: #047857;

      --red-50: #FEF2F2;
      --red-100: #FEE2E2;
      --red-500: #EF4444;
      --red-600: #DC2626;

      --amber-50: #FFFBEB;
      --amber-100: #FEF3C7;
      --amber-500: #F59E0B;
      --amber-600: #D97706;

      --blue-50: #EFF6FF;
      --blue-500: #3B82F6;
      --blue-600: #2563EB;

      --navy-800: #1E293B;
      --navy-900: #0F172A;

      --shadow-xs: 0 1px 2px rgba(15, 23, 42, 0.04);
      --shadow-card: 0 4px 20px -2px rgba(15, 23, 42, 0.05);
      --shadow-hover: 0 12px 24px -6px rgba(15, 23, 42, 0.09);
      --shadow-modal: 0 24px 48px -12px rgba(15, 23, 42, 0.22);

      --radius-sm: 8px;
      --radius-md: 12px;
      --radius-lg: 16px;
      --radius-full: 9999px;

      --sidebar-width: 260px;
      --font-sans: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
      --transition: 0.2s cubic-bezier(0.16, 1, 0.3, 1);
    }

    *, *::before, *::after {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html {
      font-size: 16px;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
    }

    body {
      font-family: var(--font-sans);
      background-color: var(--bg-app);
      color: var(--text-primary);
      line-height: 1.5;
      overflow-x: hidden;
    }

    button, input, select {
      font-family: inherit;
      font-size: inherit;
    }

    button {
      cursor: pointer;
      border: none;
      background: none;
    }
    .app-shell {
      display: flex;
      min-height: 100vh;
    }

    .sidebar {
      width: var(--sidebar-width);
      background: var(--bg-surface);
      border-right: 1px solid var(--border-light);
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      position: fixed;
      top: 0;
      left: 0;
      bottom: 0;
      z-index: 40;
      transition: transform 0.3s ease;
    }

    .sidebar-header {
      padding: 24px 20px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      border-bottom: 1px solid var(--border-light);
    }

    .brand {
      display: flex;
      align-items: center;
      gap: 12px;
      text-decoration: none;
      color: var(--text-primary);
    }

    .brand-logo {
      width: 38px;
      height: 38px;
      border-radius: 11px;
      background: linear-gradient(135deg, var(--navy-900) 0%, #1E3A8A 100%);
      color: var(--emerald-500);
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 4px 10px rgba(15, 23, 42, 0.18);
      flex-shrink: 0;
    }

    .brand-text {
      display: flex;
      flex-direction: column;
    }

    .brand-name {
      font-size: 1.25rem;
      font-weight: 700;
      letter-spacing: -0.025em;
      line-height: 1.1;
    }

    .brand-tag {
      font-size: 0.6875rem;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      color: var(--text-muted);
      margin-top: 2px;
    }

    .sidebar-close-btn {
      display: none;
      padding: 6px;
      border-radius: var(--radius-sm);
      color: var(--text-muted);
    }

    .sidebar-close-btn:hover {
      background: var(--bg-subtle);
      color: var(--text-primary);
    }

    .nav-list {
      padding: 16px 12px;
      display: flex;
      flex-direction: column;
      gap: 4px;
    }

    .nav-btn {
      display: flex;
      align-items: center;
      gap: 12px;
      width: 100%;
      padding: 12px 14px;
      border-radius: var(--radius-md);
      font-size: 0.875rem;
      font-weight: 500;
      color: var(--text-secondary);
      transition: all var(--transition);
      text-align: left;
    }

    .nav-btn svg {
      width: 19px;
      height: 19px;
      flex-shrink: 0;
      transition: color var(--transition);
    }

    .nav-btn:hover {
      background: var(--bg-subtle);
      color: var(--text-primary);
    }

    .nav-btn.active {
      background: var(--navy-900);
      color: #FFFFFF;
      font-weight: 600;
      box-shadow: 0 4px 12px rgba(15, 23, 42, 0.14);
    }

    .nav-btn.active svg {
      color: var(--emerald-500);
    }

    .sidebar-footer {
      padding: 16px;
      border-top: 1px solid var(--border-light);
    }

    .demo-box {
      background: var(--bg-app);
      border: 1px solid var(--border-light);
      border-radius: var(--radius-md);
      padding: 14px;
    }

    .demo-status {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 0.75rem;
      font-weight: 600;
      color: var(--text-primary);
      margin-bottom: 6px;
    }

    .pulse-dot {
      width: 8px;
      height: 8px;
      border-radius: 50%;
      background: var(--emerald-500);
      box-shadow: 0 0 0 3px var(--emerald-100);
    }

    .demo-desc {
      font-size: 0.725rem;
      color: var(--text-muted);
      margin-bottom: 12px;
      line-height: 1.4;
    }

    .btn-reset {
      width: 100%;
      padding: 8px 12px;
      background: var(--bg-surface);
      border: 1px solid var(--border-light);
      border-radius: var(--radius-sm);
      font-size: 0.75rem;
      font-weight: 600;
      color: var(--text-secondary);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
      transition: all var(--transition);
    }

    .btn-reset:hover {
      border-color: var(--text-muted);
      color: var(--text-primary);
      background: var(--bg-subtle);
    }

    /* Mobile Topbar & Overlay */
    .mobile-topbar {
      display: none;
      position: sticky;
      top: 0;
      z-index: 30;
      background: var(--bg-surface);
      border-bottom: 1px solid var(--border-light);
      padding: 12px 16px;
      align-items: center;
      justify-content: space-between;
    }

    .mobile-menu-btn {
      padding: 8px;
      border-radius: var(--radius-sm);
      color: var(--text-primary);
    }

    .mobile-menu-btn:hover {
      background: var(--bg-subtle);
    }

    .sidebar-overlay {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(15, 23, 42, 0.45);
      backdrop-filter: blur(2px);
      z-index: 35;
    }

    .sidebar-overlay.open {
      display: block;
    }

    /* Main Content Container */
    .main-content {
      flex: 1;
      margin-left: var(--sidebar-width);
      padding: 28px 32px;
      max-width: 1440px;
      width: 100%;
    }

    /* Page Header */
    .topbar {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      margin-bottom: 28px;
    }

    .page-title-group h1 {
      font-size: 1.625rem;
      font-weight: 700;
      letter-spacing: -0.025em;
      color: var(--text-primary);
    }

    .date-subtitle {
      display: flex;
      align-items: center;
      gap: 6px;
      font-size: 0.875rem;
      color: var(--text-muted);
      margin-top: 4px;
    }

    .topbar-actions {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    /* Buttons */
    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      padding: 10px 16px;
      border-radius: var(--radius-md);
      font-size: 0.875rem;
      font-weight: 600;
      transition: all var(--transition);
      white-space: nowrap;
    }

    .btn svg {
      width: 17px;
      height: 17px;
    }

    .btn-emerald {
      background: var(--emerald-600);
      color: #FFFFFF;
      box-shadow: 0 2px 8px rgba(5, 150, 105, 0.25);
    }

    .btn-emerald:hover {
      background: var(--emerald-700);
      transform: translateY(-1px);
    }

    .btn-navy {
      background: var(--navy-900);
      color: #FFFFFF;
      box-shadow: 0 2px 8px rgba(15, 23, 42, 0.18);
    }

    .btn-navy:hover {
      background: var(--navy-800);
      transform: translateY(-1px);
    }

    .btn-outline {
      background: var(--bg-surface);
      border: 1px solid var(--border-light);
      color: var(--text-secondary);
    }

    .btn-outline:hover {
      background: var(--bg-subtle);
      color: var(--text-primary);
    }

    .btn-danger {
      background: var(--red-600);
      color: #FFFFFF;
    }

    .btn-danger:hover {
      background: #B91C1C;
    }

    .btn-sm {
      padding: 7px 12px;
      font-size: 0.8125rem;
      border-radius: var(--radius-sm);
    }

    /* ==========================================================================
       3. CARDS, GRIDS & KPI METRICS
       ========================================================================== */
    .section-view {
      display: none;
      animation: fadeUp 0.28s ease-out forwards;
    }

    .section-view.active {
      display: block;
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(8px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .card {
      background: var(--bg-surface);
      border: 1px solid var(--border-light);
      border-radius: var(--radius-lg);
      padding: 22px;
      box-shadow: var(--shadow-card);
      transition: transform var(--transition), box-shadow var(--transition);
    }

    .card-hover:hover {
      transform: translateY(-2px);
      box-shadow: var(--shadow-hover);
    }

    .kpi-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 20px;
      margin-bottom: 24px;
    }

    .kpi-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 14px;
    }

    .kpi-label {
      font-size: 0.875rem;
      font-weight: 500;
      color: var(--text-muted);
    }

    .kpi-icon {
      width: 40px;
      height: 40px;
      border-radius: var(--radius-md);
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .kpi-icon svg {
      width: 20px;
      height: 20px;
    }

    .icon-navy { background: #F1F5F9; color: var(--navy-900); }
    .icon-emerald { background: var(--emerald-50); color: var(--emerald-600); }
    .icon-red { background: var(--red-50); color: var(--red-500); }
    .icon-blue { background: var(--blue-50); color: var(--blue-600); }

    .kpi-value {
      font-size: 1.75rem;
      font-weight: 700;
      letter-spacing: -0.025em;
      color: var(--text-primary);
      line-height: 1.2;
    }

    .text-emerald { color: var(--emerald-600); }
    .text-red { color: var(--red-500); }

    .kpi-foot {
      margin-top: 8px;
      font-size: 0.78rem;
      color: var(--text-muted);
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .badge-pill {
      display: inline-flex;
      align-items: center;
      padding: 2px 8px;
      border-radius: var(--radius-full);
      font-size: 0.72rem;
      font-weight: 600;
    }

    .badge-emerald { background: var(--emerald-50); color: var(--emerald-700); }
    .badge-red { background: var(--red-50); color: var(--red-600); }
    .badge-amber { background: var(--amber-50); color: var(--amber-600); }
    .badge-neutral { background: var(--bg-subtle); color: var(--text-secondary); }

    /* Charts Grid */
    .charts-row-main {
      display: grid;
      grid-template-columns: 2fr 1fr;
      gap: 20px;
      margin-bottom: 24px;
    }

    .charts-row-secondary {
      display: grid;
      grid-template-columns: 1fr 1.4fr;
      gap: 20px;
    }

    .card-header {
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      gap: 12px;
      margin-bottom: 18px;
    }

    .card-title {
      font-size: 1rem;
      font-weight: 700;
      color: var(--text-primary);
    }

    .card-subtitle {
      font-size: 0.8rem;
      color: var(--text-muted);
      margin-top: 2px;
    }

    .canvas-wrapper {
      position: relative;
      width: 100%;
      height: 270px;
    }

    .canvas-wrapper-sm {
      position: relative;
      width: 100%;
      height: 225px;
    }

    canvas {
      display: block;
      width: 100%;
      height: 100%;
    }

    /* Interactive Canvas Tooltip */
    .chart-tooltip {
      position: absolute;
      pointer-events: none;
      background: var(--navy-900);
      color: #FFFFFF;
      padding: 8px 12px;
      border-radius: var(--radius-sm);
      font-size: 0.75rem;
      font-weight: 500;
      box-shadow: 0 8px 20px rgba(15, 23, 42, 0.25);
      opacity: 0;
      transform: translate(-50%, -110%);
      transition: opacity 0.15s ease;
      z-index: 20;
      white-space: nowrap;
    }

    .chart-tooltip.visible {
      opacity: 1;
    }

    .doughnut-legend {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 8px 14px;
      margin-top: 14px;
      padding-top: 14px;
      border-top: 1px solid var(--border-light);
    }

    .legend-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      font-size: 0.78rem;
      color: var(--text-secondary);
      min-width: 0;
    }

    .legend-left {
      display: flex;
      align-items: center;
      gap: 7px;
      min-width: 0;
    }

    .legend-dot {
      width: 9px;
      height: 9px;
      border-radius: 50%;
      flex-shrink: 0;
    }

    .legend-name {
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }

    .legend-val {
      font-weight: 600;
      color: var(--text-primary);
      margin-left: 6px;
    }

    /* ==========================================================================
       4. LISTS, FORMS & TABLES
       ========================================================================== */
    .tx-list {
      display: flex;
      flex-direction: column;
    }

    .tx-item {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      padding: 13px 0;
      border-bottom: 1px solid var(--border-light);
    }

    .tx-item:last-child {
      border-bottom: none;
      padding-bottom: 0;
    }

    .tx-item:first-child {
      padding-top: 0;
    }

    .tx-left {
      display: flex;
      align-items: center;
      gap: 12px;
      min-width: 0;
    }

    .tx-badge-icon {
      width: 38px;
      height: 38px;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
    }

    .tx-info {
      min-width: 0;
    }

    .tx-title {
      font-size: 0.875rem;
      font-weight: 600;
      color: var(--text-primary);
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }

    .tx-meta {
      font-size: 0.75rem;
      color: var(--text-muted);
      margin-top: 2px;
    }

    .tx-right {
      display: flex;
      align-items: center;
      gap: 12px;
      flex-shrink: 0;
    }

    .tx-amount {
      font-size: 0.9rem;
      font-weight: 700;
    }

    /* Two-column layout for Income & Expenses Management */
    .manage-grid {
      display: grid;
      grid-template-columns: 400px 1fr;
      gap: 24px;
      align-items: start;
    }

    .form-group {
      margin-bottom: 16px;
    }

    .form-label {
      display: block;
      font-size: 0.8rem;
      font-weight: 600;
      color: var(--text-secondary);
      margin-bottom: 6px;
    }

    .form-control {
      width: 100%;
      padding: 10px 14px;
      background: var(--bg-app);
      border: 1px solid var(--border-light);
      border-radius: var(--radius-md);
      font-size: 0.875rem;
      color: var(--text-primary);
      transition: all var(--transition);
    }

    .form-control:focus {
      outline: none;
      background: var(--bg-surface);
      border-color: var(--emerald-500);
      box-shadow: 0 0 0 3px rgba(16, 185, 129, 0.14);
    }

    .form-error {
      font-size: 0.75rem;
      color: var(--red-600);
      margin-top: 5px;
      display: none;
    }

    .form-error.visible {
      display: block;
    }

    /* Type Segmented Control */
    .type-toggle {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 6px;
      background: var(--bg-subtle);
      padding: 4px;
      border-radius: var(--radius-md);
    }

    .type-option {
      position: relative;
    }

    .type-option input {
      position: absolute;
      opacity: 0;
      pointer-events: none;
    }

    .type-option span {
      display: block;
      text-align: center;
      padding: 8px 12px;
      border-radius: 9px;
      font-size: 0.85rem;
      font-weight: 600;
      color: var(--text-secondary);
      cursor: pointer;
      transition: all var(--transition);
    }

    .type-option input[value="expense"]:checked + span {
      background: var(--bg-surface);
      color: var(--red-600);
      box-shadow: var(--shadow-xs);
    }

    .type-option input[value="income"]:checked + span {
      background: var(--bg-surface);
      color: var(--emerald-600);
      box-shadow: var(--shadow-xs);
    }

    .summary-strip {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
      margin-bottom: 20px;
    }

    .strip-card {
      padding: 18px 20px;
      border-radius: var(--radius-lg);
      border: 1px solid;
    }

    .strip-income {
      background: var(--emerald-50);
      border-color: var(--emerald-100);
    }

    .strip-expense {
      background: var(--red-50);
      border-color: var(--red-100);
    }

    .strip-label {
      font-size: 0.75rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.05em;
    }

    .strip-value {
      font-size: 1.5rem;
      font-weight: 700;
      margin-top: 4px;
    }

    .icon-action-btn {
      padding: 6px;
      border-radius: var(--radius-sm);
      color: var(--text-muted);
      transition: all var(--transition);
      display: inline-flex;
      align-items: center;
      justify-content: center;
    }

    .icon-action-btn:hover {
      background: var(--bg-subtle);
      color: var(--text-primary);
    }

    .icon-action-btn.delete:hover {
      background: var(--red-50);
      color: var(--red-600);
    }

    /* ==========================================================================
       5. BUDGETS & PROGRESS BARS
       ========================================================================== */
    .budget-overview-header {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      padding-bottom: 20px;
      border-bottom: 1px solid var(--border-light);
    }

    .budget-inline-form {
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .budget-inline-form input {
      width: 150px;
    }

    .budget-stats-row {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 20px;
      padding: 20px 0;
    }

    .budget-stat-label {
      font-size: 0.8rem;
      color: var(--text-muted);
      font-weight: 500;
    }

    .budget-stat-val {
      font-size: 1.5rem;
      font-weight: 700;
      margin-top: 4px;
    }

    .progress-meta {
      display: flex;
      align-items: center;
      justify-content: space-between;
      font-size: 0.8125rem;
      font-weight: 600;
      margin-bottom: 8px;
    }

    .progress-track {
      width: 100%;
      height: 12px;
      background: var(--bg-subtle);
      border-radius: var(--radius-full);
      overflow: hidden;
    }

    .progress-track-sm {
      height: 8px;
    }

    .progress-fill {
      height: 100%;
      border-radius: var(--radius-full);
      background: var(--emerald-500);
      transition: width 0.45s cubic-bezier(0.16, 1, 0.3, 1), background-color 0.3s ease;
    }

    .progress-fill.warn { background: var(--amber-500); }
    .progress-fill.danger { background: var(--red-500); }

    .budget-alert-banner {
      margin-top: 16px;
      padding: 12px 16px;
      border-radius: var(--radius-md);
      font-size: 0.84rem;
      font-weight: 500;
      display: none;
      align-items: center;
      gap: 10px;
    }

    .budget-alert-banner.warn {
      display: flex;
      background: var(--amber-50);
      border: 1px solid var(--amber-100);
      color: #92400E;
    }

    .budget-alert-banner.danger {
      display: flex;
      background: var(--red-50);
      border: 1px solid var(--red-100);
      color: #991B1B;
    }

    .cat-budget-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 16px;
      margin-top: 16px;
    }

    .cat-budget-card {
      background: var(--bg-app);
      border: 1px solid var(--border-light);
      border-radius: var(--radius-md);
      padding: 16px;
    }

    .cat-budget-top {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 8px;
      margin-bottom: 10px;
    }

    .cat-budget-title {
      font-size: 0.9rem;
      font-weight: 700;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .cat-limit-input-wrap {
      display: flex;
      align-items: center;
      gap: 6px;
      font-size: 0.78rem;
      color: var(--text-muted);
    }

    .cat-limit-input {
      width: 84px;
      padding: 5px 8px;
      background: var(--bg-surface);
      border: 1px solid var(--border-light);
      border-radius: 6px;
      text-align: right;
      font-weight: 600;
      font-size: 0.8125rem;
      color: var(--text-primary);
    }

    .cat-limit-input:focus {
      outline: none;
      border-color: var(--emerald-500);
    }

    .cat-budget-nums {
      display: flex;
      justify-content: space-between;
      font-size: 0.78rem;
      color: var(--text-muted);
      margin-bottom: 8px;
    }

    /* ==========================================================================
       6. TRANSACTION HISTORY TABLE
       ========================================================================== */
    .filters-toolbar {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      gap: 12px;
      margin-bottom: 20px;
    }

    .search-box {
      position: relative;
      flex: 1;
      min-width: 240px;
      max-width: 380px;
    }

    .search-box svg {
      position: absolute;
      left: 13px;
      top: 50%;
      transform: translateY(-50%);
      width: 16px;
      height: 16px;
      color: var(--text-muted);
    }

    .search-box input {
      padding-left: 38px;
    }

    .filter-selects {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
    }

    .filter-selects select {
      width: auto;
      min-width: 145px;
    }

    .table-responsive {
      width: 100%;
      overflow-x: auto;
    }

    .data-table {
      width: 100%;
      border-collapse: collapse;
      text-align: left;
    }

    .data-table th {
      padding: 12px 16px;
      font-size: 0.74rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.05em;
      color: var(--text-muted);
      border-bottom: 1px solid var(--border-light);
      white-space: nowrap;
    }

    .data-table td {
      padding: 14px 16px;
      font-size: 0.875rem;
      border-bottom: 1px solid var(--border-light);
      vertical-align: middle;
    }

    .data-table tbody tr {
      transition: background-color var(--transition);
    }

    .data-table tbody tr:hover {
      background-color: var(--bg-app);
    }

    .text-right {
      text-align: right;
    }

    .empty-state {
      text-align: center;
      padding: 48px 20px;
    }

    .empty-icon {
      width: 48px;
      height: 48px;
      border-radius: 50%;
      background: var(--bg-subtle);
      color: var(--text-muted);
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 12px;
    }

    .empty-state h3 {
      font-size: 0.95rem;
      font-weight: 700;
      color: var(--text-primary);
    }

    .empty-state p {
      font-size: 0.82rem;
      color: var(--text-muted);
      margin-top: 4px;
    }

    /* ==========================================================================
       7. SAVINGS GOALS
       ========================================================================== */
    .goals-layout {
      display: grid;
      grid-template-columns: 360px 1fr;
      gap: 24px;
      align-items: start;
    }

    .goals-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 18px;
    }

    .goal-card {
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }

    .goal-top {
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
      gap: 10px;
    }

    .goal-title-wrap {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .goal-icon {
      width: 40px;
      height: 40px;
      border-radius: 11px;
      background: var(--bg-subtle);
      color: var(--navy-900);
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
    }

    .goal-icon.completed {
      background: var(--emerald-100);
      color: var(--emerald-700);
    }

    .goal-name {
      font-size: 0.98rem;
      font-weight: 700;
      color: var(--text-primary);
    }

    .goal-remaining {
      font-size: 0.78rem;
      color: var(--text-muted);
      margin-top: 2px;
    }

    .goal-numbers {
      display: flex;
      align-items: baseline;
      justify-content: space-between;
      margin: 18px 0 8px;
    }

    .goal-saved {
      font-size: 1.25rem;
      font-weight: 700;
      color: var(--text-primary);
    }

    .goal-target {
      font-size: 0.8rem;
      color: var(--text-muted);
      font-weight: 500;
    }

    .goal-footer {
      margin-top: 18px;
      padding-top: 14px;
      border-top: 1px solid var(--border-light);
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    /* ==========================================================================
       8. MODALS & TOAST NOTIFICATIONS
       ========================================================================== */
    .modal-backdrop {
      position: fixed;
      inset: 0;
      background: rgba(15, 23, 42, 0.5);
      backdrop-filter: blur(3px);
      display: none;
      align-items: center;
      justify-content: center;
      padding: 16px;
      z-index: 60;
    }

    .modal-backdrop.open {
      display: flex;
    }

    .modal-dialog {
      background: var(--bg-surface);
      border-radius: var(--radius-lg);
      max-width: 410px;
      width: 100%;
      padding: 24px;
      box-shadow: var(--shadow-modal);
      animation: fadeUp 0.2s ease-out;
    }

    .modal-icon {
      width: 44px;
      height: 44px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: 14px;
    }

    .modal-title {
      font-size: 1.1rem;
      font-weight: 700;
      color: var(--text-primary);
    }

    .modal-body-text {
      font-size: 0.875rem;
      color: var(--text-muted);
      margin-top: 6px;
      line-height: 1.5;
    }

    .modal-actions {
      display: flex;
      justify-content: flex-end;
      gap: 10px;
      margin-top: 22px;
    }

    .toast-container {
      position: fixed;
      bottom: 22px;
      right: 22px;
      z-index: 70;
      display: flex;
      flex-direction: column;
      gap: 10px;
      pointer-events: none;
    }

    .toast {
      background: var(--navy-900);
      color: #FFFFFF;
      padding: 12px 16px;
      border-radius: var(--radius-md);
      font-size: 0.85rem;
      font-weight: 500;
      box-shadow: 0 10px 25px rgba(15, 23, 42, 0.22);
      display: flex;
      align-items: center;
      gap: 10px;
      animation: fadeUp 0.22s ease-out;
    }

    /* ==========================================================================
       9. RESPONSIVE BREAKPOINTS
       ========================================================================== */
    @media (max-width: 1180px) {
      .kpi-grid {
        grid-template-columns: repeat(2, 1fr);
      }
      .charts-row-main,
      .charts-row-secondary,
      .manage-grid,
      .goals-layout {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 860px) {
      .sidebar {
        transform: translateX(-100%);
      }
      .sidebar.open {
        transform: translateX(0);
      }
      .sidebar-close-btn {
        display: inline-flex;
      }
      .mobile-topbar {
        display: flex;
      }
      .main-content {
        margin-left: 0;
        padding: 20px 16px;
      }
      .cat-budget-grid,
      .goals-grid {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 540px) {
      .kpi-grid,
      .budget-stats-row,
      .summary-strip {
        grid-template-columns: 1fr;
      }
      .topbar-actions {
        width: 100%;
      }
      .topbar-actions .btn {
        flex: 1;
      }
    }
  </style>
</head>
<body>

  <!-- Mobile Top Header -->
  <header class="mobile-topbar">
    <div class="brand">
      <div class="brand-logo">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"><polyline points="22 7 13.5 15.5 8.5 10.5 2 17"></polyline><polyline points="16 7 22 7 22 13"></polyline></svg>
      </div>
      <span class="brand-name">Finova</span>
    </div>
    <button id="mobile-menu-btn" class="mobile-menu-btn" aria-label="Open menu">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="3" y1="12" x2="21" y2="12"></line><line x1="3" y1="6" x2="21" y2="6"></line><line x1="3" y1="18" x2="21" y2="18"></line></svg>
    </button>
  </header>

  <div id="sidebar-overlay" class="sidebar-overlay"></div>

  <div class="app-shell">
    <!-- Sidebar Navigation -->
    <aside id="sidebar" class="sidebar">
      <div>
        <div class="sidebar-header">
          <div class="brand">
            <div class="brand-logo">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"><polyline points="22 7 13.5 15.5 8.5 10.5 2 17"></polyline><polyline points="16 7 22 7 22 13"></polyline></svg>
            </div>
            <div class="brand-text">
              <span class="brand-name">Finova</span>
              <span class="brand-tag">Wealth OS</span>
            </div>
          </div>
          <button id="sidebar-close-btn" class="sidebar-close-btn" aria-label="Close menu">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>
          </button>
        </div>

        <nav class="nav-list" aria-label="Primary Navigation">
          <button class="nav-btn active" data-tab="dashboard">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="7" height="7" rx="1"></rect><rect x="14" y="3" width="7" height="7" rx="1"></rect><rect x="14" y="14" width="7" height="7" rx="1"></rect><rect x="3" y="14" width="7" height="7" rx="1"></rect></svg>
            <span>Dashboard Overview</span>
          </button>
          <button class="nav-btn" data-tab="manage">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M17 3v18"></path><path d="m21 7-4-4-4 4"></path><path d="M7 21V3"></path><path d="m3 17 4 4 4-4"></path></svg>
            <span>Income &amp; Expenses</span>
          </button>
          <button class="nav-btn" data-tab="budgets">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21.21 15.89A10 10 0 1 1 8 2.83"></path><path d="M22 12A10 10 0 0 0 12 2v10z"></path></svg>
            <span>Monthly Budget</span>
          </button>
          <button class="nav-btn" data-tab="history">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"></path><polyline points="14 2 14 8 20 8"></polyline><line x1="16" y1="13" x2="8" y2="13"></line><line x1="16" y1="17" x2="8" y2="17"></line></svg>
            <span>Transaction History</span>
          </button>
          <button class="nav-btn" data-tab="goals">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle><circle cx="12" cy="12" r="6"></circle><circle cx="12" cy="12" r="2"></circle></svg>
            <span>Savings Goals</span>
          </button>
        </nav>
      </div>

      <div class="sidebar-footer">
        <div class="demo-box">
          <div class="demo-status">
            <span class="pulse-dot"></span>
            <span>Demo Data Active</span>
          </div>
          <p class="demo-desc">All entries are saved locally in your browser's storage.</p>
          <button id="reset-demo-btn" class="btn-reset">
            <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 12a9 9 0 1 0 9-9 9.75 9.75 0 0 0-6.74 2.74L3 8"></path><path d="M3 3v5h5"></path></svg>
            <span>Reset Demo Data</span>
          </button>
        </div>
      </div>
    </aside>

    <!-- Main Workspace -->
    <main class="main-content">
      <!-- Top Header -->
      <header class="topbar">
        <div class="page-title-group">
          <h1 id="header-title">Welcome back, Alex</h1>
          <p class="date-subtitle">
            <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect><line x1="16" y1="2" x2="16" y2="6"></line><line x1="8" y1="2" x2="8" y2="6"></line><line x1="3" y1="10" x2="21" y2="10"></line></svg>
            <span id="live-date-text"></span>
          </p>
        </div>
        <div class="topbar-actions">
          <button class="btn btn-emerald" onclick="quickAddTransaction('income')">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle><line x1="12" y1="8" x2="12" y2="16"></line><line x1="8" y1="12" x2="16" y2="12"></line></svg>
            <span>Add Income</span>
          </button>
          <button class="btn btn-navy" onclick="quickAddTransaction('expense')">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle><line x1="8" y1="12" x2="16" y2="12"></line></svg>
            <span>Add Expense</span>
          </button>
        </div>
      </header>

      <!-- ======================================================================
           SECTION A: DASHBOARD OVERVIEW
           ====================================================================== -->
      <section id="view-dashboard" class="section-view active">
        <!-- 4 KPI Summary Cards -->
        <div class="kpi-grid">
          <div class="card card-hover">
            <div class="kpi-header">
              <span class="kpi-label">Total Balance</span>
              <div class="kpi-icon icon-navy">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 12V7H5a2 2 0 0 1 0-4h14v4"></path><path d="M3 5v14a2 2 0 0 0 2 2h16v-5"></path><path d="M18 12a2 2 0 0 0 0 4h4v-4Z"></path></svg>
              </div>
            </div>
            <div id="kpi-balance" class="kpi-value">$0.00</div>
            <div class="kpi-foot">All-time net cash position</div>
          </div>

          <div class="card card-hover">
            <div class="kpi-header">
              <span class="kpi-label">Monthly Income</span>
              <div class="kpi-icon icon-emerald">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="17" y1="7" x2="7" y2="17"></line><polyline points="17 17 7 17 7 7"></polyline></svg>
              </div>
            </div>
            <div id="kpi-income" class="kpi-value text-emerald">$0.00</div>
            <div class="kpi-foot"><span class="badge-pill badge-emerald">Current Month</span></div>
          </div>

          <div class="card card-hover">
            <div class="kpi-header">
              <span class="kpi-label">Monthly Expenses</span>
              <div class="kpi-icon icon-red">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="7" y1="17" x2="17" y2="7"></line><polyline points="7 7 17 7 17 17"></polyline></svg>
              </div>
            </div>
            <div id="kpi-expenses" class="kpi-value text-red">$0.00</div>
            <div id="kpi-budget-note" class="kpi-foot">Current month outflows</div>
          </div>

          <div class="card card-hover">
            <div class="kpi-header">
              <span class="kpi-label">Monthly Savings</span>
              <div class="kpi-icon icon-blue">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M19 5c-1.5 0-2.8 1.4-3 2-3.5-1.5-11-.3-11 5 0 1.8 0 3 2 4.5V20h4v-2h3v2h4v-4c1-.5 1.7-1 2-2h2v-4h-2c0-1-.5-1.5-1-2V5z"></path><path d="M2 9v1c0 1.1.9 2 2 2h1"></path></svg>
              </div>
            </div>
            <div id="kpi-savings" class="kpi-value">$0.00</div>
            <div class="kpi-foot"><span id="kpi-savings-badge" class="badge-pill badge-neutral">0% savings rate</span></div>
          </div>
        </div>

        <!-- Primary Charts Row: 6-Month Line Chart + Category Doughnut Chart -->
        <div class="charts-row-main">
          <div class="card">
            <div class="card-header">
              <div>
                <h2 class="card-title">6-Month Financial Cash Flow Trends</h2>
                <p class="card-subtitle">Hover over points to inspect monthly income vs. expenses</p>
              </div>
              <span class="badge-pill badge-emerald">HTML5 Canvas</span>
            </div>
            <div class="canvas-wrapper">
              <canvas id="trendCanvas"></canvas>
              <div id="trendTooltip" class="chart-tooltip"></div>
            </div>
          </div>

          <div class="card">
            <div class="card-header">
              <div>
                <h2 class="card-title">Expense Categories</h2>
                <p class="card-subtitle">Current month spending breakdown</p>
              </div>
            </div>
            <div class="canvas-wrapper-sm">
              <canvas id="doughnutCanvas"></canvas>
              <div id="doughnutTooltip" class="chart-tooltip"></div>
            </div>
            <div id="doughnutLegend" class="doughnut-legend"></div>
          </div>
        </div>

        <!-- Secondary Row: Income vs Expense Bar Chart + Recent Transactions -->
        <div class="charts-row-secondary">
          <div class="card">
            <div class="card-header">
              <div>
                <h2 class="card-title">Income vs. Expenses</h2>
                <p class="card-subtitle">Current month comparative summary</p>
              </div>
            </div>
            <div class="canvas-wrapper-sm">
              <canvas id="barCanvas"></canvas>
              <div id="barTooltip" class="chart-tooltip"></div>
            </div>
          </div>

          <div class="card">
            <div class="card-header">
              <div>
                <h2 class="card-title">Recent Transactions</h2>
                <p class="card-subtitle">Latest 5 recorded account movements</p>
              </div>
              <button class="btn btn-outline btn-sm" onclick="switchTab('history')">View All</button>
            </div>
            <div id="dashboardRecentList" class="tx-list"></div>
          </div>
        </div>
      </section>

      <!-- ======================================================================
           SECTION B: INCOME & EXPENSES MANAGEMENT
           ====================================================================== -->
      <section id="view-manage" class="section-view">
        <div class="manage-grid">
          <!-- Add / Edit Form Card -->
          <div class="card">
            <div class="card-header">
              <div>
                <h2 id="txFormTitle" class="card-title">Add New Transaction</h2>
                <p class="card-subtitle">Record an income source or expense item</p>
              </div>
              <button id="cancelEditBtn" class="btn btn-outline btn-sm" style="display:none;" onclick="resetTxForm()">Cancel</button>
            </div>

            <form id="txForm" novalidate>
              <input type="hidden" id="txId" />

              <div class="form-group">
                <label class="form-label">Transaction Type</label>
                <div class="type-toggle">
                  <label class="type-option">
                    <input type="radio" name="txType" value="expense" checked />
                    <span>Expense</span>
                  </label>
                  <label class="type-option">
                    <input type="radio" name="txType" value="income" />
                    <span>Income</span>
                  </label>
                </div>
              </div>

              <div class="form-group">
                <label for="txAmount" class="form-label">Amount ($)</label>
                <input type="number" id="txAmount" class="form-control" step="0.01" min="0.01" placeholder="0.00" required />
                <div id="errAmount" class="form-error">Please enter a valid positive amount.</div>
              </div>

              <div class="form-group">
                <label for="txCategory" class="form-label">Category</label>
                <select id="txCategory" class="form-control" required></select>
              </div>

              <div class="form-group">
                <label for="txDate" class="form-label">Date</label>
                <input type="date" id="txDate" class="form-control" required />
                <div id="errDate" class="form-error">Please select a valid date.</div>
              </div>

              <div class="form-group">
                <label for="txDescription" class="form-label">Description</label>
                <input type="text" id="txDescription" class="form-control" placeholder="e.g., Client Retainer, Trader Joe's" required />
                <div id="errDesc" class="form-error">Please enter a brief description.</div>
              </div>

              <button type="submit" id="txSubmitBtn" class="btn btn-navy" style="width:100%;">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"></polyline></svg>
                <span>Save Transaction</span>
              </button>
            </form>
          </div>

          <!-- Summary & Editable Feed -->
          <div>
            <div class="summary-strip">
              <div class="strip-card strip-income">
                <div class="strip-label text-emerald">All-Time Total Income</div>
                <div id="manageTotalIncome" class="strip-value text-emerald">$0.00</div>
              </div>
              <div class="strip-card strip-expense">
                <div class="strip-label text-red">All-Time Total Expenses</div>
                <div id="manageTotalExpense" class="strip-value text-red">$0.00</div>
              </div>
            </div>

            <div class="card">
              <div class="card-header">
                <div>
                  <h3 class="card-title">All Recorded Entries</h3>
                  <p class="card-subtitle">Edit or remove any transaction below</p>
                </div>
                <span id="manageCountBadge" class="badge-pill badge-neutral">0 entries</span>
              </div>
              <div id="manageTxList" class="tx-list" style="max-height: 460px; overflow-y: auto; padding-right: 4px;"></div>
            </div>
          </div>
        </div>
      </section>

      <!-- ======================================================================
           SECTION C: MONTHLY BUDGET
           ====================================================================== -->
      <section id="view-budgets" class="section-view">
        <div class="card" style="margin-bottom: 24px;">
          <div class="budget-overview-header">
            <div>
              <h2 class="card-title">Overall Monthly Spending Budget</h2>
              <p class="card-subtitle">Monitor current month spending against your target cap</p>
            </div>
            <form id="overallBudgetForm" class="budget-inline-form">
              <input type="number" id="overallBudgetInput" class="form-control" min="1" step="1" required placeholder="Monthly limit ($)" />
              <button type="submit" class="btn btn-navy">Update Limit</button>
            </form>
          </div>

          <div class="budget-stats-row">
            <div>
              <div class="budget-stat-label">Total Monthly Budget</div>
              <div id="budgetTotalVal" class="budget-stat-val">$0.00</div>
            </div>
            <div>
              <div class="budget-stat-label">Amount Spent (This Month)</div>
              <div id="budgetSpentVal" class="budget-stat-val text-red">$0.00</div>
            </div>
            <div>
              <div class="budget-stat-label">Remaining Budget</div>
              <div id="budgetRemainingVal" class="budget-stat-val text-emerald">$0.00</div>
            </div>
          </div>

          <div class="progress-meta">
            <span id="budgetPctText">0% of monthly budget utilized</span>
            <span id="budgetStatusPill" class="badge-pill badge-emerald">On Track</span>
          </div>
          <div class="progress-track">
            <div id="budgetProgressBar" class="progress-fill" style="width: 0%;"></div>
          </div>

          <div id="budgetAlertBanner" class="budget-alert-banner">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><path d="m21.73 18-8-14a2 2 0 0 0-3.48 0l-8 14A2 2 0 0 0 4 21h16a2 2 0 0 0 1.73-3Z"></path><line x1="12" y1="9" x2="12" y2="13"></line><line x1="12" y1="17" x2="12.01" y2="17"></line></svg>
            <span id="budgetAlertText"></span>
          </div>
        </div>

        <div class="card">
          <div class="card-header">
            <div>
              <h3 class="card-title">Category-Wise Budget Tracking</h3>
              <p class="card-subtitle">Customize monthly caps for individual expense categories</p>
            </div>
          </div>
          <div id="catBudgetGrid" class="cat-budget-grid"></div>
        </div>
      </section>

      <!-- ======================================================================
           SECTION D: TRANSACTION HISTORY
           ====================================================================== -->
      <section id="view-history" class="section-view">
        <div class="card">
          <div class="filters-toolbar">
            <div class="search-box">
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line></svg>
              <input type="text" id="historySearch" class="form-control" placeholder="Search by transaction name or category..." />
            </div>

            <div class="filter-selects">
              <select id="historyTypeFilter" class="form-control">
                <option value="all">All Types</option>
                <option value="income">Income Only</option>
                <option value="expense">Expenses Only</option>
              </select>

              <select id="historyCatFilter" class="form-control">
                <option value="all">All Categories</option>
              </select>

              <select id="historySort" class="form-control">
                <option value="date-desc">Date: Newest First</option>
                <option value="date-asc">Date: Oldest First</option>
                <option value="amount-desc">Amount: Highest First</option>
                <option value="amount-asc">Amount: Lowest First</option>
              </select>
            </div>
          </div>

          <div class="table-responsive">
            <table class="data-table">
              <thead>
                <tr>
                  <th>Transaction Name</th>
                  <th>Category</th>
                  <th>Date</th>
                  <th>Type</th>
                  <th class="text-right">Amount</th>
                  <th class="text-right">Actions</th>
                </tr>
              </thead>
              <tbody id="historyTableBody"></tbody>
            </table>
          </div>

          <div id="historyEmptyState" class="empty-state" style="display:none;">
            <div class="empty-icon">
              <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"></circle><line x1="21" y1="21" x2="16.65" y2="16.65"></line></svg>
            </div>
            <h3>No transactions found</h3>
            <p>Adjust your search filters or add a new transaction to get started.</p>
          </div>
        </div>
      </section>

      <!-- ======================================================================
           SECTION E: SAVINGS GOALS
           ====================================================================== -->
      <section id="view-goals" class="section-view">
        <div class="goals-layout">
          <!-- Create Goal Form -->
          <div class="card">
            <div class="card-header">
              <div>
                <h2 class="card-title">Create Savings Goal</h2>
                <p class="card-subtitle">Set a target milestone and track progress</p>
              </div>
            </div>

            <form id="goalForm" novalidate>
              <div class="form-group">
                <label for="goalName" class="form-label">Goal Name</label>
                <input type="text" id="goalName" class="form-control" placeholder="e.g., Emergency Fund, Japan Trip" required />
                <div id="errGoalName" class="form-error">Please enter a goal name.</div>
              </div>

              <div class="form-group">
                <label for="goalTarget" class="form-label">Target Amount ($)</label>
                <input type="number" id="goalTarget" class="form-control" min="1" step="0.01" placeholder="5000.00" required />
                <div id="errGoalTarget" class="form-error">Target amount must be greater than $0.</div>
              </div>

              <div class="form-group">
                <label for="goalSaved" class="form-label">Initial Saved Amount ($)</label>
                <input type="number" id="goalSaved" class="form-control" min="0" step="0.01" placeholder="0.00" value="0" required />
                <div id="errGoalSaved" class="form-error">Saved amount cannot be negative.</div>
              </div>

              <button type="submit" class="btn btn-emerald" style="width:100%;">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="5" x2="12" y2="19"></line><line x1="5" y1="12" x2="19" y2="12"></line></svg>
                <span>Create Goal</span>
              </button>
            </form>
          </div>

          <!-- Goals Cards Container -->
          <div>
            <div id="goalsGrid" class="goals-grid"></div>
            <div id="goalsEmptyState" class="card empty-state" style="display:none;">
              <div class="empty-icon" style="background: var(--emerald-50); color: var(--emerald-600);">
                <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"></circle><circle cx="12" cy="12" r="6"></circle><circle cx="12" cy="12" r="2"></circle></svg>
              </div>
              <h3>No savings goals yet</h3>
              <p>Create your first savings target on the left to start building wealth.</p>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>

  <!-- Confirmation Modal -->
  <div id="confirmModal" class="modal-backdrop" role="dialog" aria-modal="true">
    <div class="modal-dialog">
      <div class="modal-icon" style="background: var(--red-50); color: var(--red-600);">
        <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><path d="m21.73 18-8-14a2 2 0 0 0-3.48 0l-8 14A2 2 0 0 0 4 21h16a2 2 0 0 0 1.73-3Z"></path><line x1="12" y1="9" x2="12" y2="13"></line><line x1="12" y1="17" x2="12.01" y2="17"></line></svg>
      </div>
      <h3 id="confirmModalTitle" class="modal-title">Confirm Action</h3>
      <p id="confirmModalDesc" class="modal-body-text">Are you sure you want to proceed?</p>
      <div class="modal-actions">
        <button id="confirmCancelBtn" class="btn btn-outline">Cancel</button>
        <button id="confirmProceedBtn" class="btn btn-danger">Confirm</button>
      </div>
    </div>
  </div>

  <!-- Add Funds Modal -->
  <div id="depositModal" class="modal-backdrop" role="dialog" aria-modal="true">
    <div class="modal-dialog">
      <div class="modal-icon" style="background: var(--emerald-50); color: var(--emerald-600);">
        <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="1" x2="12" y2="23"></line><path d="M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6"></path></svg>
      </div>
      <h3 class="modal-title">Add Funds to Goal</h3>
      <p id="depositGoalInfo" class="modal-body-text">Contribute toward your savings milestone.</p>
      <form id="depositForm" style="margin-top: 16px;">
        <input type="hidden" id="depositGoalId" />
        <div class="form-group">
          <label for="depositAmount" class="form-label">Deposit Amount ($)</label>
          <input type="number" id="depositAmount" class="form-control" min="0.01" step="0.01" placeholder="100.00" required />
        </div>
        <div class="modal-actions">
          <button type="button" class="btn btn-outline" onclick="closeDepositModal()">Cancel</button>
          <button type="submit" class="btn btn-emerald">Add Funds</button>
        </div>
      </form>
    </div>
  </div>

  <!-- Toast Container -->
  <div id="toastContainer" class="toast-container"></div>

  <!-- ==========================================================================
       VANILLA JAVASCRIPT APPLICATION LOGIC & CUSTOM HTML5 CANVAS CHARTS
       ========================================================================== -->
  <script>
    (function () {
      "use strict";

      /* ------------------------------------------------------------------------
         1. CONSTANTS & CATEGORY DEFINITIONS
         ------------------------------------------------------------------------ */
      const STORAGE_KEYS = {
        TRANSACTIONS: "finova_transactions_v1",
        BUDGETS: "finova_budgets_v1",
        GOALS: "finova_goals_v1"
      };

      const CATEGORIES = {
        income: ["Salary", "Freelance", "Investments", "Bonus", "Other Income"],
        expense: [
          "Housing",
          "Food & Dining",
          "Transportation",
          "Utilities",
          "Entertainment",
          "Shopping",
          "Healthcare",
          "Subscriptions"
        ]
      };

      const CATEGORY_COLORS = {
        "Housing": "#0F172A",
        "Food & Dining": "#10B981",
        "Transportation": "#3B82F6",
        "Utilities": "#F59E0B",
        "Entertainment": "#8B5CF6",
        "Shopping": "#EC4899",
        "Healthcare": "#EF4444",
        "Subscriptions": "#06B6D4"
      };

      /* ------------------------------------------------------------------------
         2. SAMPLE DEMO DATA GENERATOR
         ------------------------------------------------------------------------ */
      function buildDemoData() {
        const now = new Date();
        const year = now.getFullYear();
        const month = String(now.getMonth() + 1).padStart(2, "0");

        const pastMonthDate = (monthsBack, day) => {
          const d = new Date(year, now.getMonth() - monthsBack, day);
          const y = d.getFullYear();
          const m = String(d.getMonth() + 1).padStart(2, "0");
          const dd = String(day).padStart(2, "0");
          return `${y}-${m}-${dd}`;
        };

        const transactions = [
          // Current Month Transactions
          { id: "demo-1", type: "income", amount: 5600.00, category: "Salary", date: `${year}-${month}-01`, description: "Primary Tech Salary (Demo)" },
          { id: "demo-2", type: "income", amount: 950.00, category: "Freelance", date: `${year}-${month}-08`, description: "Product Strategy Consulting (Demo)" },
          { id: "demo-3", type: "expense", amount: 1750.00, category: "Housing", date: `${year}-${month}-02`, description: "Monthly Apartment Lease (Demo)" },
          { id: "demo-4", type: "expense", amount: 435.50, category: "Food & Dining", date: `${year}-${month}-05`, description: "Whole Foods & Bistro Dinner (Demo)" },
          { id: "demo-5", type: "expense", amount: 190.00, category: "Utilities", date: `${year}-${month}-06`, description: "Electricity, Water & Fiber Internet (Demo)" },
          { id: "demo-6", type: "expense", amount: 145.00, category: "Transportation", date: `${year}-${month}-09`, description: "City Metro Pass & Fuel (Demo)" },
          { id: "demo-7", type: "expense", amount: 240.00, category: "Shopping", date: `${year}-${month}-11`, description: "Everyday Apparel & Home Goods (Demo)" },
          { id: "demo-8", type: "expense", amount: 88.00, category: "Entertainment", date: `${year}-${month}-13`, description: "Cinema & Weekend Tickets (Demo)" },
          { id: "demo-9", type: "expense", amount: 54.00, category: "Subscriptions", date: `${year}-${month}-14`, description: "Cloud Storage & Music Plan (Demo)" },

          // Historical 5 Months (For 6-Month Financial Trend Line Chart)
          { id: "demo-h1", type: "income", amount: 5600.00, category: "Salary", date: pastMonthDate(1, 1), description: "Primary Tech Salary (Demo)" },
          { id: "demo-h2", type: "expense", amount: 3180.00, category: "Housing", date: pastMonthDate(1, 5), description: "Monthly Living & Rent (Demo)" },
          { id: "demo-h3", type: "income", amount: 6100.00, category: "Bonus", date: pastMonthDate(2, 1), description: "Salary + Quarterly Bonus (Demo)" },
          { id: "demo-h4", type: "expense", amount: 3490.00, category: "Shopping", date: pastMonthDate(2, 12), description: "Living Expenses & Travel (Demo)" },
          { id: "demo-h5", type: "income", amount: 5400.00, category: "Salary", date: pastMonthDate(3, 1), description: "Primary Tech Salary (Demo)" },
          { id: "demo-h6", type: "expense", amount: 2980.00, category: "Housing", date: pastMonthDate(3, 10), description: "Monthly Living & Rent (Demo)" },
          { id: "demo-h7", type: "income", amount: 5400.00, category: "Salary", date: pastMonthDate(4, 1), description: "Primary Tech Salary (Demo)" },
          { id: "demo-h8", type: "expense", amount: 3260.00, category: "Food & Dining", date: pastMonthDate(4, 15), description: "Monthly Living & Dining (Demo)" },
          { id: "demo-h9", type: "income", amount: 5200.00, category: "Salary", date: pastMonthDate(5, 1), description: "Primary Tech Salary (Demo)" },
          { id: "demo-h10", type: "expense", amount: 2890.00, category: "Housing", date: pastMonthDate(5, 8), description: "Monthly Living & Rent (Demo)" }
        ];

        const budgets = {
          overall: 3600,
          categories: {
            "Housing": 1800,
            "Food & Dining": 600,
            "Transportation": 250,
            "Utilities": 250,
            "Entertainment": 150,
            "Shopping": 300,
            "Healthcare": 150,
            "Subscriptions": 100
          }
        };

        const goals = [
          { id: "goal-1", name: "Emergency Fund", target: 15000, saved: 11400 },
          { id: "goal-2", name: "Japan Vacation", target: 4500, saved: 2950 },
          { id: "goal-3", name: "New MacBook Pro", target: 2600, saved: 1300 }
        ];

        return { transactions, budgets, goals };
      }

      /* ------------------------------------------------------------------------
         3. STATE MANAGEMENT & LOCALSTORAGE PERSISTENCE
         ------------------------------------------------------------------------ */
      const appState = {
        transactions: [],
        budgets: { overall: 3600, categories: {} },
        goals: [],
        chartHitRegions: {
          trend: [],
          doughnut: [],
          bar: []
        },
        hoveredSlice: -1
      };

      function loadFromStorage() {
        try {
          const rawTx = localStorage.getItem(STORAGE_KEYS.TRANSACTIONS);
          const rawBudgets = localStorage.getItem(STORAGE_KEYS.BUDGETS);
          const rawGoals = localStorage.getItem(STORAGE_KEYS.GOALS);

          if (rawTx && rawBudgets && rawGoals) {
            appState.transactions = JSON.parse(rawTx);
            appState.budgets = JSON.parse(rawBudgets);
            appState.goals = JSON.parse(rawGoals);
            return;
          }
        } catch (err) {
          console.warn("Storage unavailable, falling back to demo data.", err);
        }
        const demo = buildDemoData();
        appState.transactions = demo.transactions;
        appState.budgets = demo.budgets;
        appState.goals = demo.goals;
        saveToStorage();
      }

      function saveToStorage() {
        try {
          localStorage.setItem(STORAGE_KEYS.TRANSACTIONS, JSON.stringify(appState.transactions));
          localStorage.setItem(STORAGE_KEYS.BUDGETS, JSON.stringify(appState.budgets));
          localStorage.setItem(STORAGE_KEYS.GOALS, JSON.stringify(appState.goals));
        } catch (err) {
          console.warn("Could not persist to localStorage.", err);
        }
      }

      /* ------------------------------------------------------------------------
         4. CORE CALCULATIONS & FORMATTING HELPERS
         ------------------------------------------------------------------------ */
      function formatCurrency(val) {
        return new Intl.NumberFormat("en-US", {
          style: "currency",
          currency: "USD",
          minimumFractionDigits: 2
        }).format(val || 0);
      }

      function formatShortCurrency(val) {
        if (Math.abs(val) >= 1000) {
          return "$" + (val / 1000).toFixed(1).replace(/\.0$/, "") + "k";
        }
        return "$" + Math.round(val);
      }

      function formatDisplayDate(isoDate) {
        const d = new Date(isoDate + "T00:00:00");
        return d.toLocaleDateString("en-US", { month: "short", day: "numeric", year: "numeric" });
      }

      function escapeHtml(str) {
        const div = document.createElement("div");
        div.textContent = str;
        return div.innerHTML;
      }

      /**
       * Computes all dashboard metrics:
       * Total Balance = Total Income - Total Expenses
       * Monthly Savings = Monthly Income - Monthly Expenses
       * Remaining Budget = Monthly Budget - Monthly Expenses
       */
      function computeMetrics() {
        const now = new Date();
        const currentYM = `${now.getFullYear()}-${String(now.getMonth() + 1).padStart(2, "0")}`;

        let totalIncome = 0;
        let totalExpenses = 0;
        let monthlyIncome = 0;
        let monthlyExpenses = 0;
        const monthlyByCategory = {};

        CATEGORIES.expense.forEach((cat) => {
          monthlyByCategory[cat] = 0;
        });

        appState.transactions.forEach((tx) => {
          const amt = Number(tx.amount) || 0;
          const isThisMonth = tx.date.startsWith(currentYM);

          if (tx.type === "income") {
            totalIncome += amt;
            if (isThisMonth) monthlyIncome += amt;
          } else {
            totalExpenses += amt;
            if (isThisMonth) {
              monthlyExpenses += amt;
              monthlyByCategory[tx.category] = (monthlyByCategory[tx.category] || 0) + amt;
            }
          }
        });

        const totalBalance = totalIncome - totalExpenses;
        const monthlySavings = monthlyIncome - monthlyExpenses;
        const savingsRate = monthlyIncome > 0 ? Math.round((monthlySavings / monthlyIncome) * 100) : 0;
        const remainingBudget = (appState.budgets.overall || 0) - monthlyExpenses;

        return {
          totalIncome,
          totalExpenses,
          totalBalance,
          monthlyIncome,
          monthlyExpenses,
          monthlySavings,
          savingsRate,
          remainingBudget,
          monthlyByCategory
        };
      }

      /* ------------------------------------------------------------------------
         5. CUSTOM HTML5 CANVAS CHARTS (ZERO EXTERNAL LIBRARIES)
         ------------------------------------------------------------------------ */
      function setupHiDPICanvas(canvas) {
        const rect = canvas.parentElement.getBoundingClientRect();
        const dpr = window.devicePixelRatio || 1;
        canvas.width = Math.max(rect.width * dpr, 10);
        canvas.height = Math.max(rect.height * dpr, 10);
        const ctx = canvas.getContext("2d");
        ctx.setTransform(dpr, 0, 0, dpr, 0, 0);
        return { ctx, width: rect.width, height: rect.height };
      }

      /**
       * Chart 1: 6-Month Financial Trends (Smooth Dual Line + Area Gradient)
       */
      function drawTrendLineChart() {
        const canvas = document.getElementById("trendCanvas");
        if (!canvas) return;
        const { ctx, width, height } = setupHiDPICanvas(canvas);
        ctx.clearRect(0, 0, width, height);

        const now = new Date();
        const points = [];
        for (let i = 5; i >= 0; i--) {
          const d = new Date(now.getFullYear(), now.getMonth() - i, 1);
          const ym = `${d.getFullYear()}-${String(d.getMonth() + 1).padStart(2, "0")}`;
          const label = d.toLocaleDateString("en-US", { month: "short" });
          let income = 0;
          let expense = 0;
          appState.transactions.forEach((tx) => {
            if (tx.date.startsWith(ym)) {
              if (tx.type === "income") income += Number(tx.amount);
              else expense += Number(tx.amount);
            }
          });
          points.push({ label, income, expense });
        }

        const pad = { top: 28, right: 20, bottom: 32, left: 52 };
        const plotW = width - pad.left - pad.right;
        const plotH = height - pad.top - pad.bottom;

        const maxVal = Math.max(
          1000,
          ...points.map((p) => Math.max(p.income, p.expense))
        );
        const niceMax = Math.ceil(maxVal / 1000) * 1000;

        // Top Legend
        ctx.font = "600 11px -apple-system, BlinkMacSystemFont, sans-serif";
        ctx.fillStyle = "#10B981";
        ctx.beginPath();
        ctx.arc(width - 145, 11, 4, 0, Math.PI * 2);
        ctx.fill();
        ctx.fillStyle = "#475569";
        ctx.fillText("Income", width - 136, 15);

        ctx.fillStyle = "#EF4444";
        ctx.beginPath();
        ctx.arc(width - 75, 11, 4, 0, Math.PI * 2);
        ctx.fill();
        ctx.fillStyle = "#475569";
        ctx.fillText("Expenses", width - 66, 15);

        // Horizontal Gridlines & Y Labels
        const gridSteps = 4;
        ctx.strokeStyle = "#F1F5F9";
        ctx.lineWidth = 1;
        ctx.font = "500 11px -apple-system, BlinkMacSystemFont, sans-serif";
        ctx.textAlign = "right";
        ctx.textBaseline = "middle";

        for (let i = 0; i <= gridSteps; i++) {
          const val = (niceMax / gridSteps) * i;
          const y = pad.top + plotH - (i / gridSteps) * plotH;
          ctx.beginPath();
          ctx.moveTo(pad.left, y);
          ctx.lineTo(pad.left + plotW, y);
          ctx.stroke();

          ctx.fillStyle = "#64748B";
          ctx.fillText(formatShortCurrency(val), pad.left - 8, y);
        }

        // Compute coordinates
        const coords = points.map((p, idx) => {
          const x = pad.left + (idx / (points.length - 1)) * plotW;
          const yInc = pad.top + plotH - (p.income / niceMax) * plotH;
          const yExp = pad.top + plotH - (p.expense / niceMax) * plotH;
          return { ...p, x, yInc, yExp };
        });

        // X Axis Labels
        ctx.textAlign = "center";
        ctx.textBaseline = "top";
        coords.forEach((c) => {
          ctx.fillStyle = "#64748B";
          ctx.fillText(c.label, c.x, pad.top + plotH + 10);
        });

        // Helper for smooth bezier curve
        const drawSmoothSeries = (key, strokeColor, fillTop, fillBottom) => {
          if (coords.length < 2) return;
          ctx.save();
          ctx.beginPath();
          ctx.moveTo(coords[0].x, coords[0][key]);
          for (let i = 0; i < coords.length - 1; i++) {
            const curr = coords[i];
            const next = coords[i + 1];
            const cpX = (curr.x + next.x) / 2;
            ctx.bezierCurveTo(cpX, curr[key], cpX, next[key], next.x, next[key]);
          }
          ctx.strokeStyle = strokeColor;
          ctx.lineWidth = 2.6;
          ctx.stroke();

          // Gradient Area Fill
          ctx.lineTo(coords[coords.length - 1].x, pad.top + plotH);
          ctx.lineTo(coords[0].x, pad.top + plotH);
          ctx.closePath();
          const grad = ctx.createLinearGradient(0, pad.top, 0, pad.top + plotH);
          grad.addColorStop(0, fillTop);
          grad.addColorStop(1, fillBottom);
          ctx.fillStyle = grad;
          ctx.fill();
          ctx.restore();
        };

        drawSmoothSeries("yInc", "#10B981", "rgba(16, 185, 129, 0.16)", "rgba(16, 185, 129, 0.0)");
        drawSmoothSeries("yExp", "#EF4444", "rgba(239, 68, 68, 0.10)", "rgba(239, 68, 68, 0.0)");

        // Data Points & Hit Regions
        appState.chartHitRegions.trend = [];
        coords.forEach((c) => {
          // Income Dot
          ctx.beginPath();
          ctx.arc(c.x, c.yInc, 4, 0, Math.PI * 2);
          ctx.fillStyle = "#FFFFFF";
          ctx.fill();
          ctx.lineWidth = 2.4;
          ctx.strokeStyle = "#10B981";
          ctx.stroke();

          // Expense Dot
          ctx.beginPath();
          ctx.arc(c.x, c.yExp, 4, 0, Math.PI * 2);
          ctx.fillStyle = "#FFFFFF";
          ctx.fill();
          ctx.lineWidth = 2.4;
          ctx.strokeStyle = "#EF4444";
          ctx.stroke();

          appState.chartHitRegions.trend.push({
            x: c.x,
            y: Math.min(c.yInc, c.yExp),
            radius: 26,
            label: `${c.label}: In ${formatCurrency(c.income)} | Out ${formatCurrency(c.expense)}`
          });
        });
      }

      /**
       * Chart 2: Expense Categories Doughnut Chart
       */
      function drawDoughnutChart(metrics) {
        const canvas = document.getElementById("doughnutCanvas");
        const legendEl = document.getElementById("doughnutLegend");
        if (!canvas || !legendEl) return;

        const { ctx, width, height } = setupHiDPICanvas(canvas);
        ctx.clearRect(0, 0, width, height);

        const entries = Object.entries(metrics.monthlyByCategory)
          .filter(([, amt]) => amt > 0)
          .sort((a, b) => b[1] - a[1]);

        const totalSpent = entries.reduce((sum, [, amt]) => sum + amt, 0);
        const cx = width / 2;
        const cy = height / 2;
        const outerR = Math.min(width, height) * 0.43;
        const innerR = outerR * 0.65;

        appState.chartHitRegions.doughnut = [];

        if (entries.length === 0 || totalSpent <= 0) {
          ctx.beginPath();
          ctx.arc(cx, cy, outerR, 0, Math.PI * 2);
          ctx.arc(cx, cy, innerR, 0, Math.PI * 2, true);
          ctx.fillStyle = "#F1F5F9";
          ctx.fill();

          ctx.fillStyle = "#64748B";
          ctx.font = "600 12px -apple-system, BlinkMacSystemFont, sans-serif";
          ctx.textAlign = "center";
          ctx.textBaseline = "middle";
          ctx.fillText("No expenses yet", cx, cy);
          legendEl.innerHTML = "";
          return;
        }

        let startAngle = -Math.PI / 2;
        entries.forEach(([cat, amt], idx) => {
          const sliceAngle = (amt / totalSpent) * Math.PI * 2;
          const endAngle = startAngle + sliceAngle;
          const isHovered = appState.hoveredSlice === idx;
          const rOut = isHovered ? outerR + 5 : outerR;

          ctx.beginPath();
          ctx.arc(cx, cy, rOut, startAngle, endAngle);
          ctx.arc(cx, cy, innerR, endAngle, startAngle, true);
          ctx.closePath();
          ctx.fillStyle = CATEGORY_COLORS[cat] || "#64748B";
          ctx.fill();

          // White slice separator
          ctx.lineWidth = 2;
          ctx.strokeStyle = "#FFFFFF";
          ctx.stroke();

          const pct = Math.round((amt / totalSpent) * 100);
          appState.chartHitRegions.doughnut.push({
            idx,
            cx,
            cy,
            innerR,
            outerR: outerR + 6,
            startAngle,
            endAngle,
            label: `${cat}: ${formatCurrency(amt)} (${pct}%)`
          });

          startAngle = endAngle;
        });

        // Center Total Readout
        ctx.textAlign = "center";
        ctx.textBaseline = "middle";
        ctx.fillStyle = "#64748B";
        ctx.font = "500 11px -apple-system, BlinkMacSystemFont, sans-serif";
        ctx.fillText("Total Spent", cx, cy - 10);

        ctx.fillStyle = "#0F172A";
        ctx.font = "700 15px -apple-system, BlinkMacSystemFont, sans-serif";
        ctx.fillText(formatShortCurrency(totalSpent), cx, cy + 9);

        // Render top 4 legend items
        legendEl.innerHTML = entries
          .slice(0, 4)
          .map(([cat, amt]) => {
            const color = CATEGORY_COLORS[cat] || "#64748B";
            return `
              <div class="legend-item">
                <div class="legend-left">
                  <span class="legend-dot" style="background:${color};"></span>
                  <span class="legend-name">${escapeHtml(cat)}</span>
                </div>
                <span class="legend-val">${formatShortCurrency(amt)}</span>
              </div>
            `;
          })
          .join("");
      }

      /**
       * Chart 3: Monthly Income vs. Expenses Grouped Bar Chart
       */
      function drawBarChart(metrics) {
        const canvas = document.getElementById("barCanvas");
        if (!canvas) return;
        const { ctx, width, height } = setupHiDPICanvas(canvas);
        ctx.clearRect(0, 0, width, height);

        const bars = [
          { label: "Income", value: metrics.monthlyIncome, color: "#10B981" },
          { label: "Expenses", value: metrics.monthlyExpenses, color: "#EF4444" },
          { label: "Net Savings", value: Math.max(metrics.monthlySavings, 0), color: "#0F172A" }
        ];

        const pad = { top: 20, right: 16, bottom: 32, left: 50 };
        const plotW = width - pad.left - pad.right;
        const plotH = height - pad.top - pad.bottom;

        const maxVal = Math.max(1000, ...bars.map((b) => b.value));
        const niceMax = Math.ceil(maxVal / 1000) * 1000;

        // Horizontal Grid
        ctx.strokeStyle = "#F1F5F9";
        ctx.lineWidth = 1;
        ctx.font = "500 11px -apple-system, BlinkMacSystemFont, sans-serif";
        ctx.textAlign = "right";
        ctx.textBaseline = "middle";

        for (let i = 0; i <= 4; i++) {
          const val = (niceMax / 4) * i;
          const y = pad.top + plotH - (i / 4) * plotH;
          ctx.beginPath();
          ctx.moveTo(pad.left, y);
          ctx.lineTo(pad.left + plotW, y);
          ctx.stroke();

          ctx.fillStyle = "#64748B";
          ctx.fillText(formatShortCurrency(val), pad.left - 8, y);
        }

        const slotW = plotW / bars.length;
        const barW = Math.min(44, slotW * 0.48);
        appState.chartHitRegions.bar = [];

        bars.forEach((b, idx) => {
          const barH = (b.value / niceMax) * plotH;
          const x = pad.left + slotW * idx + (slotW - barW) / 2;
          const y = pad.top + plotH - barH;
          const radius = Math.min(8, barH / 2);

          // Rounded top rectangle
          ctx.fillStyle = b.color;
          ctx.beginPath();
          if (barH > 0) {
            ctx.moveTo(x, y + barH);
            ctx.lineTo(x, y + radius);
            ctx.quadraticCurveTo(x, y, x + radius, y);
            ctx.lineTo(x + barW - radius, y);
            ctx.quadraticCurveTo(x + barW, y, x + barW, y + radius);
            ctx.lineTo(x + barW, y + barH);
          }
          ctx.closePath();
          ctx.fill();

          // X-axis label
          ctx.fillStyle = "#475569";
          ctx.font = "600 11px -apple-system, BlinkMacSystemFont, sans-serif";
          ctx.textAlign = "center";
          ctx.textBaseline = "top";
          ctx.fillText(b.label, x + barW / 2, pad.top + plotH + 10);

          appState.chartHitRegions.bar.push({
            x,
            y: pad.top,
            w: barW,
            h: plotH,
            centerX: x + barW / 2,
            topY: Math.max(y, pad.top + 10),
            label: `${b.label}: ${formatCurrency(b.value)}`
          });
        });
      }

      function attachCanvasInteractions() {
        // Trend Line Hover
        const trendCanvas = document.getElementById("trendCanvas");
        const trendTip = document.getElementById("trendTooltip");
        trendCanvas.addEventListener("mousemove", (e) => {
          const rect = trendCanvas.getBoundingClientRect();
          const mx = e.clientX - rect.left;
          const hit = appState.chartHitRegions.trend.find((pt) => Math.abs(mx - pt.x) <= pt.radius);
          if (hit) {
            trendTip.textContent = hit.label;
            trendTip.style.left = `${hit.x}px`;
            trendTip.style.top = `${hit.y}px`;
            trendTip.classList.add("visible");
          } else {
            trendTip.classList.remove("visible");
          }
        });
        trendCanvas.addEventListener("mouseleave", () => trendTip.classList.remove("visible"));

        // Doughnut Slice Hover
        const doughCanvas = document.getElementById("doughnutCanvas");
        const doughTip = document.getElementById("doughnutTooltip");
        doughCanvas.addEventListener("mousemove", (e) => {
          const rect = doughCanvas.getBoundingClientRect();
          const mx = e.clientX - rect.left;
          const my = e.clientY - rect.top;

          let matched = null;
          for (const seg of appState.chartHitRegions.doughnut) {
            const dx = mx - seg.cx;
            const dy = my - seg.cy;
            const dist = Math.sqrt(dx * dx + dy * dy);
            if (dist >= seg.innerR && dist <= seg.outerR) {
              let angle = Math.atan2(dy, dx);
              if (angle < -Math.PI / 2) angle += Math.PI * 2;
              if (angle >= seg.startAngle && angle <= seg.endAngle) {
                matched = seg;
                break;
              }
            }
          }

          if (matched) {
            if (appState.hoveredSlice !== matched.idx) {
              appState.hoveredSlice = matched.idx;
              drawDoughnutChart(computeMetrics());
            }
            doughTip.textContent = matched.label;
            doughTip.style.left = `${mx}px`;
            doughTip.style.top = `${my - 8}px`;
            doughTip.classList.add("visible");
          } else {
            if (appState.hoveredSlice !== -1) {
              appState.hoveredSlice = -1;
              drawDoughnutChart(computeMetrics());
            }
            doughTip.classList.remove("visible");
          }
        });
        doughCanvas.addEventListener("mouseleave", () => {
          doughTip.classList.remove("visible");
          if (appState.hoveredSlice !== -1) {
            appState.hoveredSlice = -1;
            drawDoughnutChart(computeMetrics());
          }
        });

        // Bar Hover
        const barCanvas = document.getElementById("barCanvas");
        const barTip = document.getElementById("barTooltip");
        barCanvas.addEventListener("mousemove", (e) => {
          const rect = barCanvas.getBoundingClientRect();
          const mx = e.clientX - rect.left;
          const hit = appState.chartHitRegions.bar.find((b) => mx >= b.x - 8 && mx <= b.x + b.w + 8);
          if (hit) {
            barTip.textContent = hit.label;
            barTip.style.left = `${hit.centerX}px`;
            barTip.style.top = `${hit.topY}px`;
            barTip.classList.add("visible");
          } else {
            barTip.classList.remove("visible");
          }
        });
        barCanvas.addEventListener("mouseleave", () => barTip.classList.remove("visible"));
      }

      /* ------------------------------------------------------------------------
         6. UI RENDERING FUNCTIONS
         ------------------------------------------------------------------------ */
      function renderAll() {
        const metrics = computeMetrics();
        renderKPIs(metrics);
        renderDashboardRecent();
        renderManageList(metrics);
        renderBudgets(metrics);
        renderHistoryTable();
        renderGoals();
        drawTrendLineChart();
        drawDoughnutChart(metrics);
        drawBarChart(metrics);
      }

      function renderKPIs(m) {
        const balEl = document.getElementById("kpi-balance");
        balEl.textContent = formatCurrency(m.totalBalance);
        balEl.className = `kpi-value ${m.totalBalance >= 0 ? "" : "text-red"}`;

        document.getElementById("kpi-income").textContent = formatCurrency(m.monthlyIncome);
        document.getElementById("kpi-expenses").textContent = formatCurrency(m.monthlyExpenses);

        const savEl = document.getElementById("kpi-savings");
        savEl.textContent = formatCurrency(m.monthlySavings);
        savEl.className = `kpi-value ${m.monthlySavings >= 0 ? "text-emerald" : "text-red"}`;

        const rateBadge = document.getElementById("kpi-savings-badge");
        rateBadge.textContent = `${m.savingsRate}% savings rate`;
        rateBadge.className = `badge-pill ${m.savingsRate >= 20 ? "badge-emerald" : "badge-neutral"}`;
      }

      function renderDashboardRecent() {
        const container = document.getElementById("dashboardRecentList");
        const recent = [...appState.transactions]
          .sort((a, b) => new Date(b.date) - new Date(a.date))
          .slice(0, 5);

        if (recent.length === 0) {
          container.innerHTML = `<div class="empty-state" style="padding:28px 12px;"><p>No transactions recorded yet.</p></div>`;
          return;
        }

        container.innerHTML = recent
          .map((tx) => {
            const isInc = tx.type === "income";
            return `
              <div class="tx-item">
                <div class="tx-left">
                  <div class="tx-badge-icon ${isInc ? "icon-emerald" : "icon-red"}">
                    ${isInc
                      ? `<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><line x1="17" y1="7" x2="7" y2="17"></line><polyline points="17 17 7 17 7 7"></polyline></svg>`
                      : `<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><line x1="7" y1="17" x2="17" y2="7"></line><polyline points="7 7 17 7 17 17"></polyline></svg>`
                    }
                  </div>
                  <div class="tx-info">
                    <div class="tx-title">${escapeHtml(tx.description)}</div>
                    <div class="tx-meta">${escapeHtml(tx.category)} &bull; ${formatDisplayDate(tx.date)}</div>
                  </div>
                </div>
                <div class="tx-amount ${isInc ? "text-emerald" : ""}">
                  ${isInc ? "+" : "-"}${formatCurrency(tx.amount)}
                </div>
              </div>
            `;
          })
          .join("");
      }

      function renderManageList(metrics) {
        document.getElementById("manageTotalIncome").textContent = formatCurrency(metrics.totalIncome);
        document.getElementById("manageTotalExpense").textContent = formatCurrency(metrics.totalExpenses);
        document.getElementById("manageCountBadge").textContent = `${appState.transactions.length} entries`;

        const container = document.getElementById("manageTxList");
        const sorted = [...appState.transactions].sort((a, b) => new Date(b.date) - new Date(a.date));

        if (sorted.length === 0) {
          container.innerHTML = `<div class="empty-state"><p>No transactions yet. Use the form to add one.</p></div>`;
          return;
        }

        container.innerHTML = sorted
          .map((tx) => {
            const isInc = tx.type === "income";
            return `
              <div class="tx-item">
                <div class="tx-left">
                  <span class="legend-dot" style="background:${isInc ? "#10B981" : "#EF4444"};"></span>
                  <div class="tx-info">
                    <div class="tx-title">${escapeHtml(tx.description)}</div>
                    <div class="tx-meta">${escapeHtml(tx.category)} &bull; ${formatDisplayDate(tx.date)}</div>
                  </div>
                </div>
                <div class="tx-right">
                  <span class="tx-amount ${isInc ? "text-emerald" : "text-red"}">
                    ${isInc ? "+" : "-"}${formatCurrency(tx.amount)}
                  </span>
                  <div>
                    <button class="icon-action-btn" title="Edit transaction" onclick="window.finovaEditTx('${tx.id}')">
                      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"></path><path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"></path></svg>
                    </button>
                    <button class="icon-action-btn delete" title="Delete transaction" onclick="window.finovaDeleteTx('${tx.id}')">
                      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="3 6 5 6 21 6"></polyline><path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"></path></svg>
                    </button>
                  </div>
                </div>
              </div>
            `;
          })
          .join("");
      }

      function renderBudgets(metrics) {
        const totalCap = Number(appState.budgets.overall) || 0;
        const spent = metrics.monthlyExpenses;
        const remaining = totalCap - spent;
        const rawPct = totalCap > 0 ? Math.round((spent / totalCap) * 100) : 0;
        const clampedPct = Math.min(rawPct, 100);

        document.getElementById("overallBudgetInput").value = totalCap;
        document.getElementById("budgetTotalVal").textContent = formatCurrency(totalCap);
        document.getElementById("budgetSpentVal").textContent = formatCurrency(spent);

        const remEl = document.getElementById("budgetRemainingVal");
        remEl.textContent = formatCurrency(remaining);
        remEl.className = `budget-stat-val ${remaining >= 0 ? "text-emerald" : "text-red"}`;

        document.getElementById("budgetPctText").textContent = `${rawPct}% of monthly budget utilized`;

        const bar = document.getElementById("budgetProgressBar");
        const pill = document.getElementById("budgetStatusPill");
        const banner = document.getElementById("budgetAlertBanner");
        const bannerText = document.getElementById("budgetAlertText");

        bar.style.width = `${clampedPct}%`;
        bar.className = "progress-fill";
        banner.className = "budget-alert-banner";

        if (rawPct >= 100) {
          bar.classList.add("danger");
          pill.className = "badge-pill badge-red";
          pill.textContent = "Limit Exceeded";
          banner.classList.add("danger");
          bannerText.textContent = `Warning: You have exceeded your monthly budget by ${formatCurrency(Math.abs(remaining))}.`;
        } else if (rawPct >= 80) {
          bar.classList.add("warn");
          pill.className = "badge-pill badge-amber";
          pill.textContent = "Approaching Limit";
          banner.classList.add("warn");
          bannerText.textContent = `Heads up: You've used ${rawPct}% of your monthly budget with ${formatCurrency(remaining)} remaining.`;
        } else {
          pill.className = "badge-pill badge-emerald";
          pill.textContent = "On Track";
        }

        // Category-wise budgets
        const catGrid = document.getElementById("catBudgetGrid");
        catGrid.innerHTML = CATEGORIES.expense
          .map((cat) => {
            const limit = Number(appState.budgets.categories[cat]) || 0;
            const catSpent = metrics.monthlyByCategory[cat] || 0;
            const pct = limit > 0 ? Math.min(Math.round((catSpent / limit) * 100), 100) : (catSpent > 0 ? 100 : 0);
            const rawCatPct = limit > 0 ? Math.round((catSpent / limit) * 100) : 0;

            let fillClass = "progress-fill";
            if (limit > 0 && rawCatPct >= 100) fillClass += " danger";
            else if (limit > 0 && rawCatPct >= 75) fillClass += " warn";

            const dotColor = CATEGORY_COLORS[cat] || "#64748B";

            return `
              <div class="cat-budget-card">
                <div class="cat-budget-top">
                  <div class="cat-budget-title">
                    <span class="legend-dot" style="background:${dotColor};"></span>
                    <span>${escapeHtml(cat)}</span>
                  </div>
                  <div class="cat-limit-input-wrap">
                    <span>Limit $</span>
                    <input type="number" class="cat-limit-input" min="0" step="10" value="${limit}"
                      onchange="window.finovaUpdateCatBudget('${cat}', this.value)" />
                  </div>
                </div>
                <div class="cat-budget-nums">
                  <span>Spent: <strong>${formatCurrency(catSpent)}</strong></span>
                  <span>${limit > 0 ? `Left: ${formatCurrency(Math.max(limit - catSpent, 0))}` : "No cap set"}</span>
                </div>
                <div class="progress-track progress-track-sm">
                  <div class="${fillClass}" style="width:${pct}%;"></div>
                </div>
              </div>
            `;
          })
          .join("");
      }

      function renderHistoryTable() {
        const query = document.getElementById("historySearch").value.toLowerCase().trim();
        const typeFilter = document.getElementById("historyTypeFilter").value;
        const catFilter = document.getElementById("historyCatFilter").value;
        const sortBy = document.getElementById("historySort").value;

        let list = appState.transactions.filter((tx) => {
          const matchText =
            tx.description.toLowerCase().includes(query) ||
            tx.category.toLowerCase().includes(query);
          const matchType = typeFilter === "all" || tx.type === typeFilter;
          const matchCat = catFilter === "all" || tx.category === catFilter;
          return matchText && matchType && matchCat;
        });

        list.sort((a, b) => {
          if (sortBy === "date-desc") return new Date(b.date) - new Date(a.date);
          if (sortBy === "date-asc") return new Date(a.date) - new Date(b.date);
          if (sortBy === "amount-desc") return b.amount - a.amount;
          if (sortBy === "amount-asc") return a.amount - b.amount;
          return 0;
        });

        const tbody = document.getElementById("historyTableBody");
        const emptyState = document.getElementById("historyEmptyState");

        if (list.length === 0) {
          tbody.innerHTML = "";
          emptyState.style.display = "block";
          return;
        }

        emptyState.style.display = "none";
        tbody.innerHTML = list
          .map((tx) => {
            const isInc = tx.type === "income";
            return `
              <tr>
                <td style="font-weight:600;">${escapeHtml(tx.description)}</td>
                <td><span class="badge-pill badge-neutral">${escapeHtml(tx.category)}</span></td>
                <td style="color:var(--text-muted); font-size:0.82rem;">${formatDisplayDate(tx.date)}</td>
                <td>
                  <span class="badge-pill ${isInc ? "badge-emerald" : "badge-red"}">
                    ${isInc ? "Income" : "Expense"}
                  </span>
                </td>
                <td class="text-right" style="font-weight:700; color:${isInc ? "var(--emerald-600)" : "var(--text-primary)"};">
                  ${isInc ? "+" : "-"}${formatCurrency(tx.amount)}
                </td>
                <td class="text-right">
                  <button class="icon-action-btn" title="Edit" onclick="window.finovaEditTx('${tx.id}')">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"></path><path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"></path></svg>
                  </button>
                  <button class="icon-action-btn delete" title="Delete" onclick="window.finovaDeleteTx('${tx.id}')">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="3 6 5 6 21 6"></polyline><path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"></path></svg>
                  </button>
                </td>
              </tr>
            `;
          })
          .join("");
      }

      function renderGoals() {
        const grid = document.getElementById("goalsGrid");
        const empty = document.getElementById("goalsEmptyState");

        if (appState.goals.length === 0) {
          grid.innerHTML = "";
          empty.style.display = "block";
          return;
        }

        empty.style.display = "none";
        grid.innerHTML = appState.goals
          .map((g) => {
            // Savings Progress = (Saved Amount / Target Amount) * 100
            const rawPct = g.target > 0 ? Math.round((g.saved / g.target) * 100) : 0;
            const pct = Math.min(rawPct, 100);
            const remaining = Math.max(g.target - g.saved, 0);
            const isDone = g.saved >= g.target;

            return `
              <div class="card card-hover goal-card">
                <div>
                  <div class="goal-top">
                    <div class="goal-title-wrap">
                      <div class="goal-icon ${isDone ? "completed" : ""}">
                        ${isDone
                          ? `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><path d="M22 11.08V12a10 10 0 1 1-5.93-9.14"></path><polyline points="22 4 12 14.01 9 11.01"></polyline></svg>`
                          : `<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2"><circle cx="12" cy="12" r="10"></circle><circle cx="12" cy="12" r="6"></circle><circle cx="12" cy="12" r="2"></circle></svg>`
                        }
                      </div>
                      <div>
                        <div class="goal-name">${escapeHtml(g.name)}</div>
                        <div class="goal-remaining">
                          ${isDone ? "Target Achieved!" : `${formatCurrency(remaining)} remaining to target`}
                        </div>
                      </div>
                    </div>
                    <button class="icon-action-btn delete" title="Delete goal" onclick="window.finovaDeleteGoal('${g.id}')">
                      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><polyline points="3 6 5 6 21 6"></polyline><path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"></path></svg>
                    </button>
                  </div>

                  <div class="goal-numbers">
                    <span class="goal-saved">${formatCurrency(g.saved)}</span>
                    <span class="goal-target">of ${formatCurrency(g.target)} (${rawPct}%)</span>
                  </div>

                  <div class="progress-track progress-track-sm">
                    <div class="progress-fill" style="width:${pct}%;"></div>
                  </div>
                </div>

                <div class="goal-footer">
                  <span class="badge-pill ${isDone ? "badge-emerald" : "badge-neutral"}">${rawPct}% Funded</span>
                  <button class="btn btn-outline btn-sm" onclick="window.finovaOpenDeposit('${g.id}')">
                    + Add Funds
                  </button>
                </div>
              </div>
            `;
          })
          .join("");
      }

      /* ------------------------------------------------------------------------
         7. NAVIGATION, MODALS & FORM CONTROLLERS
         ------------------------------------------------------------------------ */
      function populateCategorySelects(txType = "expense") {
        const txSelect = document.getElementById("txCategory");
        txSelect.innerHTML = CATEGORIES[txType]
          .map((c) => `<option value="${escapeHtml(c)}">${escapeHtml(c)}</option>`)
          .join("");

        const filterSelect = document.getElementById("historyCatFilter");
        const currentFilterVal = filterSelect.value || "all";
        const allCats = [...CATEGORIES.income, ...CATEGORIES.expense];
        filterSelect.innerHTML =
          `<option value="all">All Categories</option>` +
          allCats.map((c) => `<option value="${escapeHtml(c)}">${escapeHtml(c)}</option>`).join("");
        filterSelect.value = currentFilterVal;
      }

      window.switchTab = function (tabKey) {
        document.querySelectorAll(".section-view").forEach((el) => el.classList.remove("active"));
        const activeView = document.getElementById(`view-${tabKey}`);
        if (activeView) activeView.classList.add("active");

        document.querySelectorAll(".nav-btn").forEach((btn) => {
          btn.classList.toggle("active", btn.dataset.tab === tabKey);
        });

        const titles = {
          dashboard: "Welcome back, Alex",
          manage: "Income & Expenses",
          budgets: "Monthly Budget",
          history: "Transaction History",
          goals: "Savings Goals"
        };
        document.getElementById("header-title").textContent = titles[tabKey] || "Finova";

        // Close mobile drawer if open
        document.getElementById("sidebar").classList.remove("open");
        document.getElementById("sidebar-overlay").classList.remove("open");

        if (tabKey === "dashboard") {
          const metrics = computeMetrics();
          drawTrendLineChart();
          drawDoughnutChart(metrics);
          drawBarChart(metrics);
        }
      };

      window.quickAddTransaction = function (type) {
        window.switchTab("manage");
        window.resetTxForm();
        const radio = document.querySelector(`input[name="txType"][value="${type}"]`);
        if (radio) {
          radio.checked = true;
          populateCategorySelects(type);
        }
        document.getElementById("txAmount").focus();
      };

      window.resetTxForm = function () {
        document.getElementById("txForm").reset();
        document.getElementById("txId").value = "";
        document.getElementById("txDate").value = new Date().toISOString().split("T")[0];
        document.getElementById("txFormTitle").textContent = "Add New Transaction";
        document.getElementById("txSubmitBtn").querySelector("span").textContent = "Save Transaction";
        document.getElementById("cancelEditBtn").style.display = "none";
        document.querySelectorAll("#txForm .form-error").forEach((el) => el.classList.remove("visible"));
        populateCategorySelects("expense");
      };

      window.finovaEditTx = function (id) {
        const tx = appState.transactions.find((t) => t.id === id);
        if (!tx) return;
        window.switchTab("manage");
        document.getElementById("txId").value = tx.id;
        const radio = document.querySelector(`input[name="txType"][value="${tx.type}"]`);
        if (radio) radio.checked = true;
        populateCategorySelects(tx.type);
        document.getElementById("txAmount").value = tx.amount;
        document.getElementById("txCategory").value = tx.category;
        document.getElementById("txDate").value = tx.date;
        document.getElementById("txDescription").value = tx.description;

        document.getElementById("txFormTitle").textContent = "Edit Transaction";
        document.getElementById("txSubmitBtn").querySelector("span").textContent = "Update Transaction";
        document.getElementById("cancelEditBtn").style.display = "inline-flex";
      };

      let confirmCallback = null;
      function openConfirmDialog(title, desc, onConfirm) {
        document.getElementById("confirmModalTitle").textContent = title;
        document.getElementById("confirmModalDesc").textContent = desc;
        confirmCallback = onConfirm;
        document.getElementById("confirmModal").classList.add("open");
      }

      function closeConfirmDialog() {
        document.getElementById("confirmModal").classList.remove("open");
        confirmCallback = null;
      }

      window.finovaDeleteTx = function (id) {
        openConfirmDialog(
          "Delete Transaction",
          "Are you sure you want to delete this transaction? All dashboard metrics will recalculate immediately.",
          () => {
            appState.transactions = appState.transactions.filter((t) => t.id !== id);
            saveToStorage();
            renderAll();
            showToast("Transaction deleted.");
          }
        );
      };

      window.finovaUpdateCatBudget = function (cat, val) {
        const num = Math.max(0, parseFloat(val) || 0);
        appState.budgets.categories[cat] = num;
        saveToStorage();
        renderAll();
        showToast(`Updated ${cat} budget limit.`);
      };

      window.finovaOpenDeposit = function (goalId) {
        const goal = appState.goals.find((g) => g.id === goalId);
        if (!goal) return;
        document.getElementById("depositGoalId").value = goal.id;
        document.getElementById("depositGoalInfo").textContent =
          `${goal.name}: ${formatCurrency(goal.saved)} saved of ${formatCurrency(goal.target)} target.`;
        document.getElementById("depositAmount").value = "";
        document.getElementById("depositModal").classList.add("open");
        document.getElementById("depositAmount").focus();
      };

      window.closeDepositModal = function () {
        document.getElementById("depositModal").classList.remove("open");
      };

      window.finovaDeleteGoal = function (goalId) {
        openConfirmDialog(
          "Delete Savings Goal",
          "Are you sure you want to remove this savings goal?",
          () => {
            appState.goals = appState.goals.filter((g) => g.id !== goalId);
            saveToStorage();
            renderAll();
            showToast("Savings goal removed.");
          }
        );
      };

      function showToast(msg) {
        const container = document.getElementById("toastContainer");
        const el = document.createElement("div");
        el.className = "toast";
        el.innerHTML = `
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#10B981" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="20 6 9 17 4 12"></polyline></svg>
          <span>${escapeHtml(msg)}</span>
        `;
        container.appendChild(el);
        setTimeout(() => {
          el.style.opacity = "0";
          el.style.transition = "opacity 0.25s ease";
          setTimeout(() => el.remove(), 250);
        }, 2800);
      }

      /* ------------------------------------------------------------------------
         8. BOOTSTRAP & EVENT LISTENERS
         ------------------------------------------------------------------------ */
      document.addEventListener("DOMContentLoaded", () => {
        // Set Live Current Date
        const now = new Date();
        document.getElementById("live-date-text").textContent = now.toLocaleDateString("en-US", {
          weekday: "long",
          month: "long",
          day: "numeric",
          year: "numeric"
        });
        document.getElementById("txDate").value = now.toISOString().split("T")[0];

        loadFromStorage();
        populateCategorySelects("expense");
        attachCanvasInteractions();
        renderAll();

        // Sidebar Navigation
        document.querySelectorAll(".nav-btn").forEach((btn) => {
          btn.addEventListener("click", () => window.switchTab(btn.dataset.tab));
        });

        // Mobile Drawer Toggles
        document.getElementById("mobile-menu-btn").addEventListener("click", () => {
          document.getElementById("sidebar").classList.add("open");
          document.getElementById("sidebar-overlay").classList.add("open");
        });
        const closeSidebar = () => {
          document.getElementById("sidebar").classList.remove("open");
          document.getElementById("sidebar-overlay").classList.remove("open");
        };
        document.getElementById("sidebar-close-btn").addEventListener("click", closeSidebar);
        document.getElementById("sidebar-overlay").addEventListener("click", closeSidebar);

        // Transaction Type Switch
        document.querySelectorAll('input[name="txType"]').forEach((radio) => {
          radio.addEventListener("change", (e) => populateCategorySelects(e.target.value));
        });

        // Add / Edit Transaction Submit
        document.getElementById("txForm").addEventListener("submit", (e) => {
          e.preventDefault();
          const id = document.getElementById("txId").value;
          const type = document.querySelector('input[name="txType"]:checked').value;
          const amount = parseFloat(document.getElementById("txAmount").value);
          const category = document.getElementById("txCategory").value;
          const date = document.getElementById("txDate").value;
          const description = document.getElementById("txDescription").value.trim();

          let valid = true;
          document.getElementById("errAmount").classList.toggle("visible", isNaN(amount) || amount <= 0);
          if (isNaN(amount) || amount <= 0) valid = false;

          document.getElementById("errDate").classList.toggle("visible", !date);
          if (!date) valid = false;

          document.getElementById("errDesc").classList.toggle("visible", !description);
          if (!description) valid = false;

          if (!valid) return;

          if (id) {
            const idx = appState.transactions.findIndex((t) => t.id === id);
            if (idx !== -1) {
              appState.transactions[idx] = { id, type, amount, category, date, description };
              showToast("Transaction updated!");
            }
          } else {
            appState.transactions.unshift({
              id: "tx-" + Date.now(),
              type,
              amount,
              category,
              date,
              description
            });
            showToast(`${type === "income" ? "Income" : "Expense"} recorded!`);
          }

          saveToStorage();
          window.resetTxForm();
          renderAll();
        });

        // Overall Budget Submit
        document.getElementById("overallBudgetForm").addEventListener("submit", (e) => {
          e.preventDefault();
          const val = parseFloat(document.getElementById("overallBudgetInput").value);
          if (!isNaN(val) && val > 0) {
            appState.budgets.overall = val;
            saveToStorage();
            renderAll();
            showToast("Monthly budget limit updated.");
          }
        });

        // History Filters & Search
        ["historySearch", "historyTypeFilter", "historyCatFilter", "historySort"].forEach((id) => {
          document.getElementById(id).addEventListener("input", renderHistoryTable);
          document.getElementById(id).addEventListener("change", renderHistoryTable);
        });

        // Create Savings Goal Submit
        document.getElementById("goalForm").addEventListener("submit", (e) => {
          e.preventDefault();
          const name = document.getElementById("goalName").value.trim();
          const target = parseFloat(document.getElementById("goalTarget").value);
          const saved = parseFloat(document.getElementById("goalSaved").value);

          let valid = true;
          document.getElementById("errGoalName").classList.toggle("visible", !name);
          if (!name) valid = false;

          document.getElementById("errGoalTarget").classList.toggle("visible", isNaN(target) || target <= 0);
          if (isNaN(target) || target <= 0) valid = false;

          document.getElementById("errGoalSaved").classList.toggle("visible", isNaN(saved) || saved < 0);
          if (isNaN(saved) || saved < 0) valid = false;

          if (!valid) return;

          appState.goals.push({
            id: "goal-" + Date.now(),
            name,
            target,
            saved
          });

          saveToStorage();
          e.target.reset();
          document.getElementById("goalSaved").value = "0";
          renderAll();
          showToast("Savings goal created!");
        });

        // Add Funds to Goal Submit
        document.getElementById("depositForm").addEventListener("submit", (e) => {
          e.preventDefault();
          const goalId = document.getElementById("depositGoalId").value;
          const amount = parseFloat(document.getElementById("depositAmount").value);
          const goal = appState.goals.find((g) => g.id === goalId);

          if (goal && !isNaN(amount) && amount > 0) {
            goal.saved += amount;
            saveToStorage();
            window.closeDepositModal();
            renderAll();
            showToast(`Added ${formatCurrency(amount)} to ${goal.name}!`);
          }
        });

        // Confirmation Modal Actions
        document.getElementById("confirmCancelBtn").addEventListener("click", closeConfirmDialog);
        document.getElementById("confirmProceedBtn").addEventListener("click", () => {
          if (confirmCallback) confirmCallback();
          closeConfirmDialog();
        });

        // Reset Demo Data
        document.getElementById("reset-demo-btn").addEventListener("click", () => {
          openConfirmDialog(
            "Reset Demo Data",
            "This will restore Finova's default sample transactions, budgets, and savings goals. Continue?",
            () => {
              const demo = buildDemoData();
              appState.transactions = demo.transactions;
              appState.budgets = demo.budgets;
              appState.goals = demo.goals;
              saveToStorage();
              renderAll();
              showToast("Sample demo data restored.");
            }
          );
        });

        // Responsive Chart Redraw on Window Resize
        let resizeTimer;
        window.addEventListener("resize", () => {
          clearTimeout(resizeTimer);
          resizeTimer = setTimeout(() => {
            const metrics = computeMetrics();
            drawTrendLineChart();
            drawDoughnutChart(metrics);
            drawBarChart(metrics);
          }, 120);
        });
      });
    })();
  </script>
</body>
</html>
