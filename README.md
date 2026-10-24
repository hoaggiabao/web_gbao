# web_gbao <!doctype html>
<html lang="vi">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>chi congdz</title>
<style>
  :root{
    --bg:#070B14; --panel:rgba(13,21,38,0.82); --ink:#1263f8; --muted:#5A6A8A; --line:rgba(74,125,255,0.18);
    --accent:#4A7DFF; --ok:#1ACC7A; --warn:#E8A030; --bad:#E85060;
    --chip:rgba(15,25,40,0.75); --mono:ui-monospace,SFMono-Regular,"SF Mono",Menlo,Consolas,monospace;
  }
  *{box-sizing:border-box}
  
  /* ── Hiệu ứng Nền Vũ Trụ ── */
  body {
    margin: 0;
    background-color: #070B14;
    background: #070B14 url('https://www.image2url.com/r2/default/gifs/1790222811378-a9a85d25-8ee8-4ebb-ab27-dd829df0b1d4.gif') no-repeat center center fixed;
    background-size: cover;
    color: var(--ink);
    font: 15px/1.55 -apple-system, "Helvetica Neue", system-ui, sans-serif;
    padding: 14px 16px 80px;
    -webkit-text-size-adjust: 100%;
    position: relative;
    min-height: 100vh;
  }

  /* ── ONBOARDING OVERLAY ── */
  .onboarding-overlay {
    position: fixed;
    top: 0; left: 0; width: 100vw; height: 100vh;
    background: rgba(3, 7, 18, 0.85);
    backdrop-filter: blur(16px);
    -webkit-backdrop-filter: blur(16px);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 999999;
    padding: 20px;
    opacity: 1;
    transition: opacity 0.3s ease;
  }
  .onboarding-overlay.hidden {
    opacity: 0;
    pointer-events: none;
  }
  .onboarding-card {
    background: rgba(13, 21, 38, 0.95);
    border: 1px solid rgba(74, 125, 255, 0.35);
    border-radius: 20px;
    padding: 28px 24px;
    max-width: 400px;
    width: 100%;
    text-align: center;
    box-shadow: 0 10px 35px rgba(0, 0, 0, 0.6), 0 0 20px rgba(74, 125, 255, 0.2);
    animation: onboardingPop 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  }
  @keyframes onboardingPop {
    0% { transform: scale(0.9); opacity: 0; }
    100% { transform: scale(1); opacity: 1; }
  }
  .onboarding-icon {
    font-size: 42px;
    margin-bottom: 14px;
  }
  .onboarding-title {
    font-size: 22px;
    font-weight: 700;
    color: #fff;
    margin: 0 0 8px;
    letter-spacing: -0.01em;
  }
  .onboarding-title span {
    background: linear-gradient(135deg, #4A7DFF, #a855f7);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
  .onboarding-desc {
    color: var(--muted);
    font-size: 14px;
    margin: 0 0 24px;
    line-height: 1.5;
  }
  .onboarding-btn {
    width: 100%;
    padding: 13px;
    font-size: 15px;
    font-weight: 600;
    border-radius: 12px;
    background: linear-gradient(135deg, #2E63DB, #6040C8);
    color: #fff;
    border: 0;
    cursor: pointer;
    box-shadow: 0 4px 15px rgba(74, 125, 255, 0.4);
    transition: filter 0.15s;
  }
  .onboarding-btn:hover {
    filter: brightness(1.08);
  }

  /* ── hướng dẫn ── */
  .wrap{max-width:100%;margin:0 auto}

.guide{
  border-radius:18px;
  padding:17px;
  margin-bottom:15px;
  background:linear-gradient(145deg,rgba(14,24,43,.88),rgba(7,13,26,.78));
  border:1px solid var(--line);
  box-shadow:0 14px 36px rgba(0,0,0,.22),inset 0 1px 0 rgba(255,255,255,.035);
  backdrop-filter:blur(16px);
  -webkit-backdrop-filter:blur(16px);
  position:relative;
  overflow:hidden;
}

.guide::before{
  content:"";
  position:absolute;
  left:8%;right:8%;top:0;height:1px;
  background:linear-gradient(90deg,transparent,var(--accent),var(--accent2),transparent);
}

.guide-title{
  font-size:12px;
  font-weight:800;
  letter-spacing:.08em;
  text-transform:uppercase;
  color:#9db7ff;
  margin:0 0 13px;
  display:flex;
  align-items:center;
  gap:8px;
}

.guide-title::before{
  content:"ℹ";
  width:23px;height:23px;
  border-radius:8px;
  display:inline-flex;
  align-items:center;
  justify-content:center;
  color:#fff;
  background:linear-gradient(135deg,var(--accent),var(--accent2));
  box-shadow:0 5px 16px rgba(91,140,255,.25);
}

.steps{
  list-style:none;
  margin:0;
  padding:0;
  display:flex;
  flex-direction:column;
  gap:8px;
}

.steps li{
  display:flex;
  gap:10px;
  align-items:flex-start;
  font-size:13px;
  color:var(--ink);
  padding:7px 8px;
  border-radius:10px;
  transition:.18s ease;
}

.steps li:hover{
  background:rgba(91,140,255,.055);
  transform:translateX(2px);
}

.step-n{
  min-width:23px;
  height:23px;
  border-radius:8px;
  display:flex;
  align-items:center;
  justify-content:center;
  font-size:11px;
  font-weight:900;
  background:linear-gradient(135deg,#477cff,#784fe9);
  color:#fff;
  margin-top:1px;
  box-shadow:0 5px 14px rgba(91,140,255,.22);
}

.steps li b{color:#f1f5ff}
.steps li span{color:var(--muted);font-size:12px;display:block;margin-top:2px}

.panel{
  background:linear-gradient(145deg,rgba(14,23,41,.84),rgba(7,13,25,.78));
  border:1px solid var(--line);
  border-radius:15px;
  padding:16px;
  margin-bottom:14px;
  box-shadow:0 12px 32px rgba(0,0,0,.19),inset 0 1px 0 rgba(255,255,255,.025);
  backdrop-filter:blur(15px);
  -webkit-backdrop-filter:bl
