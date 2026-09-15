
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Revolut | Incoming Transfer</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Roboto, sans-serif; }
  body { background: #0f1620; color: #e6ecf3; min-height: 100vh; display: flex; align-items: center; justify-content: center; padding: 20px; }
  .card { background: #1a2332; border-radius: 18px; padding: 40px; max-width: 460px; width: 100%; box-shadow: 0 20px 60px rgba(0,0,0,0.5); }
  .logo { font-size: 26px; font-weight: 800; letter-spacing: -1px; margin-bottom: 30px; color: #fff; }
  .logo span { color: #0075eb; }
  .row { display: flex; justify-content: space-between; padding: 14px 0; border-bottom: 1px solid #2a3648; font-size: 15px; }
  .row:last-child { border: none; }
  .label { color: #8a97a8; }
  .value { color: #fff; font-weight: 500; text-align: right; }
  .amount { font-size: 34px; font-weight: 700; text-align: center; margin: 20px 0 30px; color: #00d4a4; }
  button { width: 100%; padding: 16px; background: #0075eb; color: #fff; border: none; border-radius: 12px; font-size: 16px; font-weight: 600; cursor: pointer; }
  button:hover:not(:disabled) { background: #0060c4; }
  button:disabled { background: #2a3648; cursor: not-allowed; }
  .hidden { display: none !important; }
  .spinner { margin: 30px auto; width: 42px; height: 42px; border: 4px solid #2a3648; border-top-color: #0075eb; border-radius: 50%; animation: spin 0.8s linear infinite; }
  @keyframes spin { to { transform: rotate(360deg); } }
  .status { margin-top: 25px; padding: 18px; border-radius: 12px; background: #3a1620; border-left: 4px solid #ff5566; color: #ff8a9a; font-size: 14px; line-height: 1.5; }
  .status h3 { color: #ff5566; margin-bottom: 8px; font-size: 16px; }
  .status .code { font-family: monospace; background: #0f1620; padding: 6px 10px; border-radius: 6px; margin-top: 10px; display: inline-block; font-size: 12px; color: #ffb3b3; }
  .footer { text-align: center; margin-top: 20px; font-size: 12px; color: #5a6778; }
</style>
</head>
<body>
  <div class="card">
    <div class="logo">Revolut<span>.</span></div>
    <div class="row"><span class="label">From</span><span class="value">Guarda Wallet</span></div>
    <div class="row"><span class="label">To</span><span class="value">Leila Westskytte</span></div>
    <div class="row"><span class="label">Reference</span><span class="value">TXN-GRD-88291-BTC</span></div>
    <div class="row"><span class="label">Network</span><span class="value">Bitcoin (BTC)</span></div>
    <div class="amount">2,700,000.00 KR</div>

    <button id="btn" type="button">Receive Transaction</button>

    <div id="spin" class="spinner hidden"></div>

    <div id="err" class="status hidden">
      <h3>⚠ Transaction Failed — Security Breach Detected</h3>
      Our system flagged unusual activity on the originating wallet. The incoming transfer has been placed on hold pending manual verification.
      <br><br>
      <strong>Contact your assigned agent for more information.</strong>
      <div class="code">ERR_SEC_KYC_BREACH_0x4F71</div>
    </div>

    <div class="footer">Revolut Bank UAB · Secured by 256-bit encryption</div>
  </div>

<script>
  document.addEventListener('DOMContentLoaded', function() {
    var btn = document.getElementById('btn');
    var spin = document.getElementById('spin');
    var err = document.getElementById('err');

    btn.addEventListener('click', function() {
      btn.disabled = true;
      btn.textContent = 'Processing...';
      err.classList.add('hidden');
      spin.classList.remove('hidden');

      setTimeout(function() {
        spin.classList.add('hidden');
        err.classList.remove('hidden');
        btn.textContent = 'Transaction Blocked';
      }, 3000);
    });
  });
</script>
</body>
</html>
