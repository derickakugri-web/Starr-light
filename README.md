# Starr-light
Trading site
<h2 onclick="checkAdmin()" style="cursor: pointer;">STΛR LIGHT</h2>

<div id="admin-panel" style="display: none; margin-top: 20px;">
    <div class="admin-card">
        <h3>CEO Vault</h3>
        <p class="profit-text">₵ <span id="total-profit">0.00</span></p>
        <button onclick="archiveProfit()" style="background: #ffd700; color: black; border: none; padding: 10px; border-radius: 5px; cursor: pointer;">Archive & Reset</button>
        <p style="font-size: 0.8rem; color: #888; margin-top: 10px;">Last Session: ₵ <span id="last-session">0.00</span></p>
    </div>
</div>

<script>
let totalProfitUSD = 0;
let archivedProfitUSD = 0;
const GHS_RATE = 15.50; // Set your current rate here
const SPREAD = 0.005;   // 0.5% fee

// 1. The Ghost Entrance
function checkAdmin() {
    let pin = prompt("Enter CEO PIN:");
    if (pin === "1997") {
        document.getElementById('admin-panel').style.display = 'block';
        updateAdminDisplay();
    } else {
        alert("Access Denied.");
    }
}

// 2. Logic to track profit during trades
// Call this whenever a trade is made in your app
function recordTrade(amountUSD) {
    let fee = amountUSD * SPREAD;
    totalProfitUSD += fee;
    updateAdminDisplay();
}

// 3. Update the Gold Card
function updateAdminDisplay() {
    document.getElementById('total-profit').innerText = (totalProfitUSD * GHS_RATE).toFixed(2);
    document.getElementById('last-session').innerText = (archivedProfitUSD * GHS_RATE).toFixed(2);
}

// 4. The Archive Move
function archiveProfit() {
    if(confirm("Archive today's earnings, Boss?")) {
        archivedProfitUSD = totalProfitUSD;
        totalProfitUSD = 0;
        updateAdminDisplay();
    }
}
</script>
