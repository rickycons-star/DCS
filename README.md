# DCS
Data Strategy
[Discovery_Assessment_Templates.html](https://github.com/user-attachments/files/29678347/Discovery_Assessment_Templates.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Discovery Assessment Templates — Data & Core Services</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif; background: #F4EFEA; color: #2C2C2C; font-size: 13px; }
  .page-header { background: #6B4226; color: #fff; padding: 20px 40px; display: flex; align-items: center; justify-content: space-between; }
  .page-header h1 { font-size: 20px; font-weight: 500; }
  .page-header .sub { font-size: 11px; color: #C4A882; margin-top: 4px; }
  .nav { background: #fff; border-bottom: 1px solid #E2D8CE; padding: 0 40px; display: flex; gap: 4px; overflow-x: auto; }
  .nav-btn { padding: 10px 14px; font-size: 12px; color: #6B6B6B; cursor: pointer; border: none; background: none; white-space: nowrap; border-bottom: 2px solid transparent; transition: all 0.15s; }
  .nav-btn:hover { color: #6B4226; }
  .nav-btn.active { color: #6B4226; border-bottom-color: #6B4226; font-weight: 500; }
  .content { max-width: 1100px; margin: 0 auto; padding: 24px 40px; }
  .panel { display: none; }
  .panel.active { display: block; }
  /* Cards */
  .card { background: #fff; border: 0.5px solid #E2D8CE; border-radius: 8px; padding: 20px; margin-bottom: 16px; }
  .card-title { font-size: 15px; font-weight: 500; color: #2C2C2C; margin-bottom: 4px; }
  .card-sub { font-size: 11px; color: #6B6B6B; font-style: italic; margin-bottom: 16px; }
  /* Heatmap */
  .heatmap-table { width: 100%; border-collapse: collapse; font-size: 12px; }
  .heatmap-table th { padding: 8px 10px; font-weight: 500; font-size: 11px; text-align: center; color: #fff; }
  .heatmap-table th.team-col { text-align: left; background: #2C2C2C; width: 200px; }
  .heatmap-table td { padding: 6px 8px; border-bottom: 0.5px solid #E2D8CE; text-align: center; }
  .heatmap-table td.team-name { text-align: left; font-weight: 500; color: #2C2C2C; }
  .heatmap-table tr:nth-child(even) td { background: #F7F4F1; }
  .heatmap-table tr:hover td { background: #F0EAE3; }
  .heatmap-table tfoot td { font-weight: 500; background: #F7F4F1 !important; }
  .rag { display: inline-block; border-radius: 4px; font-size: 10px; font-weight: 500; padding: 3px 10px; min-width: 60px; text-align: center; }
  .rag-green  { background: #E8F5EC; color: #1A4D2A; border: 0.5px solid #1A4D2A; }
  .rag-amber  { background: #FDF3E3; color: #7A4A0A; border: 0.5px solid #7A4A0A; }
  .rag-red    { background: #FAEAEA; color: #7B2A1A; border: 0.5px solid #7B2A1A; }
  .rag-pending{ background: #F7F4F1; color: #6B6B6B; border: 0.5px solid #D4C9B8; }
  /* Domain slides */
  .domain-hdr { display: flex; align-items: center; gap: 12px; margin-bottom: 16px; }
  .domain-dot { width: 12px; height: 12px; border-radius: 3px; flex-shrink: 0; }
  .domain-name { font-size: 16px; font-weight: 500; }
  .domain-desc { font-size: 11px; color: #6B6B6B; font-style: italic; }
  .q-table { width: 100%; border-collapse: collapse; font-size: 12px; }
  .q-table th { padding: 8px 12px; font-weight: 500; font-size: 11px; text-align: left; }
  .q-table th.curr-hdr { background: #5A3A1A; color: #fff; }
  .q-table th.tgt-hdr  { background: #1A4D58; color: #fff; }
  .q-table th.q-hdr    { background: #2C2C2C; color: #fff; width: 28%; }
  .q-table th.gap-hdr  { background: #2C2C2C; color: #fff; width: 80px; text-align: center; }
  .q-table td { padding: 10px 12px; border-bottom: 0.5px solid #E2D8CE; vertical-align: top; line-height: 1.5; }
  .q-table td.curr-cell { background: #FFF6EE; }
  .q-table td.tgt-cell  { background: #EDF5F7; color: #1A4D58; }
  .q-table td.gap-cell  { text-align: center; vertical-align: middle; }
  .q-table tr:nth-child(even) td.q-cell { background: #F7F4F1; }
  /* How to use */
  .step { display: flex; gap: 14px; margin-bottom: 12px; align-items: flex-start; }
  .step-num { width: 36px; height: 36px; border-radius: 6px; display: flex; align-items: center; justify-content: center; font-size: 18px; font-weight: 500; color: #fff; flex-shrink: 0; }
  .step-body { flex: 1; background: #F7F4F1; border: 0.5px solid #E2D8CE; border-radius: 6px; padding: 10px 14px; }
  .step-title { font-weight: 500; font-size: 13px; margin-bottom: 4px; }
  .step-desc { font-size: 12px; color: #6B6B6B; line-height: 1.5; }
  /* Legend */
  .legend { display: flex; gap: 20px; flex-wrap: wrap; margin-bottom: 16px; }
  .legend-item { display: flex; align-items: center; gap: 6px; font-size: 11px; color: #6B6B6B; }
  .legend-swatch { width: 20px; height: 14px; border-radius: 3px; }
  /* Print */
  @media print {
    .nav, .page-header { display: none; }
    .panel { display: block !important; page-break-after: always; }
    .card { break-inside: avoid; }
  }
  @media (max-width: 700px) {
    .content { padding: 16px; }
    .heatmap-table { font-size: 10px; }
    .q-table { font-size: 11px; }
  }
</style>
</head>
<body>

<div class="page-header">
  <div>
    <div class="sub">JPMorganChase  ·  Data & Core Services  ·  CONFIDENTIAL</div>
    <h1>Discovery Assessment Templates — Phase 2</h1>
  </div>
  <div style="font-size:11px; color:#C4A882; text-align:right;">10 product functions<br>5 assessment domains</div>
</div>

<div class="nav">
  <button class="nav-btn active" onclick="show('heatmap', this)">Portfolio heatmap</button>
  <button class="nav-btn" onclick="show('df', this)">Data Foundation</button>
  <button class="nav-btn" onclick="show('di', this)">Data Inventory</button>
  <button class="nav-btn" onclick="show('ap', this)">Auto Provisioning</button>
  <button class="nav-btn" onclick="show('cm', this)">Config Management</button>
  <button class="nav-btn" onclick="show('ins', this)">Insights & Reporting</button>
  <button class="nav-btn" onclick="show('howto', this)">How to use</button>
</div>

<div class="content">

<!-- ── HEATMAP ─────────────────────────────────────────── -->
<div id="heatmap" class="panel active">
  <div class="card">
    <div class="card-title">Portfolio Heatmap — Current State RAG by Domain</div>
    <div class="card-sub">One row per product function. RAG status agreed with Product Lead after each discovery session. Domain summary row shows weakest area across the portfolio.</div>
    <div class="legend">
      <div class="legend-item"><span class="legend-swatch" style="background:#E8F5EC;border:0.5px solid #1A4D2A;"></span>Green — meets target</div>
      <div class="legend-item"><span class="legend-swatch" style="background:#FDF3E3;border:0.5px solid #7A4A0A;"></span>Amber — partial / in progress</div>
      <div class="legend-item"><span class="legend-swatch" style="background:#FAEAEA;border:0.5px solid #7B2A1A;"></span>Red — significant gap</div>
      <div class="legend-item"><span class="legend-swatch" style="background:#F7F4F1;border:0.5px solid #D4C9B8;"></span>Pending — session not yet held</div>
    </div>
    <table class="heatmap-table">
      <thead>
        <tr>
          <th class="team-col">Product function</th>
          <th style="background:#1B5E8A;">Data<br>Foundation</th>
          <th style="background:#0D6B5A;">Data<br>Inventory</th>
          <th style="background:#7A4A00;">Auto<br>Provisioning</th>
          <th style="background:#4A2A7A;">Config<br>Management</th>
          <th style="background:#6B4226;">Insights &amp;<br>Reporting</th>
          <th style="background:#2C2C2C;">Overall</th>
        </tr>
      </thead>
      <tbody id="heatmap-body"></tbody>
      <tfoot id="heatmap-foot"></tfoot>
    </table>
  </div>
</div>

<!-- ── DOMAIN SLIDES ───────────────────────────────────── -->
<div id="df" class="panel"></div>
<div id="di" class="panel"></div>
<div id="ap" class="panel"></div>
<div id="cm" class="panel"></div>
<div id="ins" class="panel"></div>

<!-- ── HOW TO USE ──────────────────────────────────────── -->
<div id="howto" class="panel">
  <div class="card">
    <div class="card-title">How to use these templates</div>
    <div class="card-sub">A guide for discovery session facilitators and programme team members.</div>
    <div class="step"><div class="step-num" style="background:#6B4226;">1</div><div class="step-body"><div class="step-title">Before the session</div><div class="step-desc">Share the domain questions with the Product Lead 5 days in advance. Ask them to nominate a data lead and engineering lead to join. Confirm the session is 90 minutes.</div></div></div>
    <div class="step"><div class="step-num" style="background:#1A4D58;">2</div><div class="step-body"><div class="step-title">During the session</div><div class="step-desc">Work through each domain in order. Capture current state verbatim — do not interpret or adjust in the session. Mark questions Red / Amber / Green provisionally.</div></div></div>
    <div class="step"><div class="step-num" style="background:#7A4A00;">3</div><div class="step-body"><div class="step-title">After the session (within 5 days)</div><div class="step-desc">Write up current and target state for each question. Share the completed domain views with the Product Lead for RAG sign-off before updating the portfolio heatmap.</div></div></div>
    <div class="step"><div class="step-num" style="background:#1B5E8A;">4</div><div class="step-body"><div class="step-title">Update the heatmap</div><div class="step-desc">Once RAG is agreed per domain, update the heatmap for that team. The heatmap is the source of truth for programme leadership reporting.</div></div></div>
    <div class="step"><div class="step-num" style="background:#4A2A7A;">5</div><div class="step-body"><div class="step-title">Delta analysis</div><div class="step-desc">After all sessions complete, review each domain across all teams to identify the most common gaps. These become the priority workstreams for Phase 3 delivery.</div></div></div>
  </div>
</div>

</div><!-- /content -->

<script>
const teams = [
  { name:"Payments & Settlements",  df:"amber", di:"green",   ap:"red",     cm:"amber", ins:"amber",  overall:"amber" },
  { name:"Trade Finance",           df:"red",   di:"amber",   ap:"red",     cm:"red",   ins:"pending", overall:"red" },
  { name:"Risk & Compliance Data",  df:"green", di:"green",   ap:"amber",   cm:"green", ins:"amber",  overall:"green" },
  { name:"Client Reporting",        df:"amber", di:"red",     ap:"red",     cm:"amber", ins:"red",    overall:"red" },
  { name:"Markets Data",            df:"pending",di:"pending",ap:"pending", cm:"pending",ins:"pending",overall:"pending" },
  { name:"Corporate Treasury",      df:"green", di:"amber",   ap:"green",   cm:"amber", ins:"green",  overall:"green" },
  { name:"Securities Services",     df:"pending",di:"pending",ap:"pending", cm:"pending",ins:"pending",overall:"pending" },
  { name:"FX & Rates",              df:"amber", di:"green",   ap:"red",     cm:"amber", ins:"pending",overall:"amber" },
  { name:"Digital Banking",         df:"red",   di:"amber",   ap:"red",     cm:"red",   ins:"red",    overall:"red" },
  { name:"Operations & Controls",   df:"amber", di:"amber",   ap:"pending", cm:"amber", ins:"amber",  overall:"amber" },
];

const domains = [
  {
    id:"df", label:"Data Foundation", color:"#1B5E8A", rag:"amber",
    desc:"Governance, ownership, quality standards and data lineage",
    qs:[
      { q:"Are named data owners defined and accountable for each dataset?",
        curr:"Ownership is informal — engineering leads act as de facto owners but with no formal accountability or published responsibility.",
        tgt:"Named Data Owner per dataset, accountable for quality and access decisions, published in the data catalogue.", gap:"red" },
      { q:"Are data quality SLAs defined, measured and enforced?",
        curr:"No formal SLAs exist. Quality issues are raised reactively via Jira tickets after a problem has been identified in production.",
        tgt:"Documented SLAs per critical dataset. Automated monitoring with alerting, remediation workflows and monthly quality reporting.", gap:"red" },
      { q:"Is data lineage documented end-to-end (source to consumption)?",
        curr:"Partial — pipeline lineage exists in Databricks but business lineage from source systems to reporting is undocumented.",
        tgt:"Full lineage from source to consumption documented in the enterprise data catalogue, accessible to all stakeholders.", gap:"amber" },
      { q:"Is data classified by sensitivity and regulatory obligation?",
        curr:"Some datasets are classified but the taxonomy is inconsistent across teams and not enforced at ingestion.",
        tgt:"All datasets classified using the enterprise taxonomy. Classification enforced at ingestion, reviewed annually.", gap:"amber" },
    ]
  },
  {
    id:"di", label:"Data Inventory", color:"#0D6B5A", rag:"amber",
    desc:"Cataloguing, metadata management and discoverability",
    qs:[
      { q:"Are all datasets catalogued with accurate metadata?",
        curr:"Approximately 70% of core datasets are catalogued in Collibra. Descriptions and classifications are inconsistent across teams.",
        tgt:"100% of datasets catalogued. Automated metadata sync from source systems. Classification reviewed quarterly.", gap:"amber" },
      { q:"Is a data dictionary maintained and kept current?",
        curr:"A Confluence-based dictionary exists for some teams but is not consistently maintained or linked to the catalogue.",
        tgt:"Dictionary integrated into the enterprise catalogue. Terms linked to datasets, definitions versioned and approved by Data Owner.", gap:"amber" },
      { q:"Is data ownership clearly mapped in the catalogue?",
        curr:"Ownership fields exist in Collibra but are unpopulated for 40% of datasets. No process to keep them current.",
        tgt:"100% of catalogue entries have a named owner. Ownership reviewed and confirmed at each annual data governance cycle.", gap:"red" },
      { q:"Can data consumers easily discover and request access to data?",
        curr:"Discovery is largely by word of mouth. No self-service access request workflow — all requests go via email to the platform team.",
        tgt:"Self-service discovery portal with search, classification filter and automated access request workflow.", gap:"red" },
    ]
  },
  {
    id:"ap", label:"Auto Provisioning", color:"#7A4A00", rag:"red",
    desc:"Automated infrastructure, access and environment provisioning",
    qs:[
      { q:"Are new environments provisioned via a self-service, automated process?",
        curr:"Manual Terraform execution by senior engineers only. Takes 3–5 business days, high error rate, no approval workflow or audit trail.",
        tgt:"Self-service auto provisioning via a portal. Policy-governed, fully auditable, average provisioning time under 2 hours.", gap:"red" },
      { q:"Is access provisioning role-based and automated on role assignment?",
        curr:"Access is granted manually via Jira request to the platform team. No RBAC enforcement — access is often broader than required.",
        tgt:"RBAC enforced across all systems. Access provisioned automatically on role assignment, reviewed and certified quarterly.", gap:"red" },
      { q:"Are provisioning actions logged and auditable?",
        curr:"No centralised audit log. Individual engineers maintain ad hoc notes but these are not standardised or retained.",
        tgt:"Full audit trail for all provisioning actions, retained for regulatory period, accessible to compliance and internal audit.", gap:"red" },
      { q:"Is there a deprovisioning process when roles change or staff leave?",
        curr:"Deprovisioning is manual and often missed. Access reviews are conducted annually but rely on manager attestation only.",
        tgt:"Automated deprovisioning triggered by HR system events. Access revoked within 24 hours of role change or departure.", gap:"red" },
    ]
  },
  {
    id:"cm", label:"Config Management", color:"#4A2A7A", rag:"amber",
    desc:"Configuration baselines, drift detection and change control",
    qs:[
      { q:"Are configuration baselines defined for all environments?",
        curr:"Baselines exist for production only. Dev and UAT environments are not baselined, leading to frequent environment-specific defects.",
        tgt:"Baselines defined and documented for all environments. Stored in version control, reviewed on each platform upgrade.", gap:"amber" },
      { q:"Is config drift detection in place and monitored?",
        curr:"No automated drift detection. Drift is discovered manually or when an incident occurs — often weeks after the change.",
        tgt:"Automated drift detection running continuously. Alerts triggered within 15 minutes of deviation from baseline.", gap:"red" },
      { q:"Are all configuration changes tracked, approved and audited?",
        curr:"Changes tracked in Jira but the process is not consistently followed. Emergency changes bypass the process entirely.",
        tgt:"All changes tracked in the ITSM tool with mandatory approval workflow. Emergency changes documented within 24 hours.", gap:"amber" },
      { q:"Is there a process to remediate detected drift automatically?",
        curr:"No automated remediation. Drift is flagged to the team but remediation is manual and unscheduled.",
        tgt:"Automated remediation for known drift patterns. Complex remediation escalated to engineering with SLA.", gap:"red" },
    ]
  },
  {
    id:"ins", label:"Insights & Reporting", color:"#6B4226", rag:"amber",
    desc:"Dashboards, KPIs, self-service analytics and leadership reporting",
    qs:[
      { q:"Are self-service dashboards available to the product team?",
        curr:"Two dashboards exist in Tableau but they are not well known across the team and are rarely used outside of the data team.",
        tgt:"Comprehensive self-service dashboard suite covering all key operational and financial KPIs, promoted and accessible to all.", gap:"amber" },
      { q:"Are KPIs agreed, baselined and tracked against targets?",
        curr:"KPIs are defined informally in team OKRs but are not formally agreed with leadership or tracked in a centralised tool.",
        tgt:"KPIs formally agreed with product leadership. Targets set, baselined from current data and tracked monthly.", gap:"amber" },
      { q:"Is reporting consumed by leadership on a regular cadence?",
        curr:"Monthly reports are produced but distributed via email. No interactive access — leadership cannot drill down or interrogate data.",
        tgt:"Leadership dashboard with drill-down capability. Monthly automated report with exception highlighting and trend analysis.", gap:"amber" },
      { q:"Is there a data product available for downstream AI/ML consumption?",
        curr:"No formalised data products. AI/ML teams access raw datasets directly, with no quality guarantees or SLAs.",
        tgt:"Published data products with documented schemas, quality SLAs and versioning. Accessible via self-service API.", gap:"red" },
    ]
  }
];

function ragChip(status) {
  const map = { green:"rag-green", amber:"rag-amber", red:"rag-red", pending:"rag-pending" };
  const lbl = { green:"Green", amber:"Amber", red:"Red", pending:"Pending" };
  return `<span class="rag ${map[status]||'rag-pending'}">${lbl[status]||'—'}</span>`;
}

// Build heatmap
const tbody = document.getElementById('heatmap-body');
teams.forEach(t => {
  tbody.innerHTML += `<tr>
    <td class="team-name">${t.name}</td>
    <td>${ragChip(t.df)}</td><td>${ragChip(t.di)}</td>
    <td>${ragChip(t.ap)}</td><td>${ragChip(t.cm)}</td>
    <td>${ragChip(t.ins)}</td><td>${ragChip(t.overall)}</td>
  </tr>`;
});
document.getElementById('heatmap-foot').innerHTML = `<tr>
  <td class="team-name" style="font-size:11px;color:#6B6B6B;">Domain summary</td>
  <td>${ragChip('amber')}</td><td>${ragChip('amber')}</td>
  <td>${ragChip('red')}</td><td>${ragChip('amber')}</td>
  <td>${ragChip('amber')}</td><td></td>
</tr>`;

// Build domain panels
domains.forEach(d => {
  const qRows = d.qs.map(q => `
    <tr>
      <td class="q-cell">${q.q}</td>
      <td class="curr-cell">${q.curr}</td>
      <td class="tgt-cell">${q.tgt}</td>
      <td class="gap-cell">${ragChip(q.gap)}</td>
    </tr>`).join('');
  document.getElementById(d.id).innerHTML = `
    <div class="card">
      <div class="domain-hdr">
        <span class="domain-dot" style="background:${d.color};"></span>
        <div>
          <div class="domain-name">${d.label} &nbsp;${ragChip(d.rag)}</div>
          <div class="domain-desc">${d.desc}</div>
        </div>
      </div>
      <table class="q-table">
        <thead><tr>
          <th class="q-hdr">Discovery question</th>
          <th class="curr-hdr">Current state</th>
          <th class="tgt-hdr">Target state</th>
          <th class="gap-hdr">Gap</th>
        </tr></thead>
        <tbody>${qRows}</tbody>
      </table>
      <div style="margin-top:12px;font-size:11px;color:#6B6B6B;font-style:italic;">
        Update current state and gap status after each discovery session. Agree RAG with Product Lead before publishing.
      </div>
    </div>`;
});

function show(id, btn) {
  document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.nav-btn').forEach(b => b.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  btn.classList.add('active');
}
</script>
</body>
</html>
