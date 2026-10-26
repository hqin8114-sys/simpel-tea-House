<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Tea Business ERP Suite | FI CO MM SD PP HCM</title>
<style>
:root{
    --primary:#0d9488;
    --bg:#f3f4f6;
    --card:#ffffff;
    --text:#111827;
    --muted:#6b7280;
    --border:#e5e7eb;
    --success:#dcfce7;
    --success-text:#166534;
    --warn:#fffbeb;
    --warn-text:#92400e;
    --danger:#b91c1c;
}
*{box-sizing:border-box;margin:0;padding:0}
body{
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
    background:var(--bg);
    color:var(--text);
    padding:24px
}
.header{
    display:flex;
    align-items:center;
    gap:8px;
    font-size:18px;
    font-weight:600;
    margin-bottom:24px
}
.tabs{
    display:flex;
    gap:8px;
    margin-bottom:24px;
    flex-wrap:wrap
}
.tab{
    padding:10px 18px;
    border-radius:8px;
    border:none;
    font-size:14px;
    cursor:pointer;
    background:#e5e7eb;
    color:#374151;
    font-weight:500
}
.tab.active{
    background:var(--primary);
    color:white
}
.tab-panel{display:none}
.tab-panel.active{display:block}
.stat-row{
    display:grid;
    grid-template-columns:repeat(3,1fr);
    gap:16px;
    margin-bottom:20px
}
.stat-card{
    background:var(--card);
    padding:24px;
    border-radius:12px;
    border:1px solid var(--border);
    box-shadow:0 1px 3px #00000008
}
.stat-label{
    font-size:14px;
    color:var(--muted);
    margin-bottom:6px
}
.stat-value{
    font-size:32px;
    font-weight:700
}
.table-card{
    background:var(--card);
    border-radius:12px;
    border:1px solid var(--border);
    box-shadow:0 1px 3px #00000008;
    padding:24px
}
.table-head{
    display:flex;
    justify-content:space-between;
    align-items:center;
    margin-bottom:16px
}
.table-head h2{
    font-size:20px;
    font-weight:600
}
.btn-add{
    background:var(--primary);
    color:white;
    border:none;
    padding:10px 16px;
    border-radius:8px;
    font-weight:600;
    cursor:pointer
}
table{
    width:100%;
    border-collapse:collapse
}
th,td{
    text-align:left;
    padding:14px 10px;
    font-size:14px;
    border-bottom:1px solid var(--border)
}
th{
    color:var(--muted);
    font-weight:500;
    text-transform:uppercase;
    font-size:13px
}
.badge{
    display:inline-block;
    padding:4px 10px;
    border-radius:999px;
    font-size:13px;
    font-weight:500
}
.badge.paid{
    background:var(--success);
    color:var(--success-text)
}
.badge.unpaid{
    background:var(--warn);
    color:var(--warn-text)
}
.btn-del{
    background:var(--danger);
    color:white;
    border:none;
    padding:6px 12px;
    border-radius:6px;
    cursor:pointer;
    font-weight:500
}
.note{
    margin-top:16px;
    font-size:13px;
    color:var(--muted)
}
.modal-bg{
    display:none;
    position:fixed;
    inset:0;
    background:#00000040;
    align-items:center;
    justify-content:center;
    padding:20px;
    z-index:99
}
.modal-bg.show{display:flex}
.modal{
    background:white;
    width:min(500px,100%);
    border-radius:12px;
    padding:24px
}
.modal h2{margin-bottom:20px;font-size:18px}
.field{
    display:block;
    margin-bottom:14px;
    font-size:14px;
    font-weight:500
}
.field input,.field select{
    width:100%;
    margin-top:6px;
    padding:10px;
    border:1px solid var(--border);
    border-radius:6px;
    font:inherit
}
.modal-actions{
    display:flex;
    justify-content:flex-end;
    gap:10px;
    margin-top:20px
}
.btn-cancel{
    background:#e5e7eb;
    border:none;
    padding:10px 16px;
    border-radius:8px;
    cursor:pointer
}
.btn-save{
    background:var(--primary);
    color:white;
    border:none;
    padding:10px 16px;
    border-radius:8px;
    cursor:pointer
}
@media(max-width:720px){
    .stat-row{grid-template-columns:1fr}
}
</style>
</head>
<body>
<div class="header">
    <span>🍃 Tea Business ERP Suite | FI CO MM SD PP HCM</span>
</div>
<div class="tabs">
    <button class="tab active" data-tab="fi">FI Financial Accounting</button>
    <button class="tab" data-tab="co">CO Controlling</button>
    <button class="tab" data-tab="mm">MM Material Management</button>
    <button class="tab" data-tab="sd">SD Sales & Distribution</button>
    <button class="tab" data-tab="pp">PP Production Planning</button>
    <button class="tab" data-tab="hcm">HCM Human Resources</button>
</div>

<!-- FI -->
<div class="tab-panel active" id="fi">
    <div class="stat-row">
        <div class="stat-card">
            <div class="stat-label">Total Vouchers</div>
            <div class="stat-value" id="fi-total">6</div>
        </div>
        <div class="stat-card">
            <div class="stat-label">Unpaid Bills</div>
            <div class="stat-value" id="fi-unpaid">2</div>
        </div>
        <div class="stat-card">
            <div class="stat-label">Account Types</div>
            <div class="stat-value" id="fi-cat">4</div>
        </div>
    </div>
    <div class="table-card">
        <div class="table-head">
            <h2>Account Record List</h2>
            <button class="btn-add" onclick="openModal('fi')">Add Record</button>
        </div>
        <table>
            <thead>
                <tr>
                    <th>Voucher No.</th>
                    <th>Account Type</th>
                    <th>Amount</th>
                    <th>Date</th>
                    <th>Status</th>
                    <th>Action</th>
                </tr>
            </thead>
            <tbody id="fi-body">
                <tr>
                    <td>V001</td>
                    <td>Income</td>
                    <td>12000</td>
                    <td>2026-10-01</td>
                    <td><span class="badge paid">Paid</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'fi')">Delete</button></td>
                </tr>
                <tr>
                    <td>V002</td>
                    <td>Expense</td>
                    <td>3500</td>
                    <td>2026-10-03</td>
                    <td><span class="badge unpaid">Unpaid</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'fi')">Delete</button></td>
                </tr>
                <tr>
                    <td>V003</td>
                    <td>Income</td>
                    <td>8600</td>
                    <td>2026-10-05</td>
                    <td><span class="badge paid">Paid</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'fi')">Delete</button></td>
                </tr>
                <tr>
                    <td>V004</td>
                    <td>Expense</td>
                    <td>2200</td>
                    <td>2026-10-08</td>
                    <td><span class="badge unpaid">Unpaid</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'fi')">Delete</button></td>
                </tr>
                <tr>
                    <td>V005</td>
                    <td>Transfer</td>
                    <td>5000</td>
                    <td>2026-10-10</td>
                    <td><span class="badge paid">Paid</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'fi')">Delete</button></td>
                </tr>
                <tr>
                    <td>V006</td>
                    <td>Tax</td>
                    <td>1800</td>
                    <td>2026-10-12</td>
                    <td><span class="badge paid">Paid</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'fi')">Delete</button></td>
                </tr>
            </tbody>
        </table>
        <div class="note">Voucher entry, payment, general ledger & financial report</div>
    </div>
</div>

<!-- CO -->
<div class="tab-panel" id="co">
    <div class="stat-row">
        <div class="stat-card">
            <div class="stat-label">Total Items</div>
            <div class="stat-value" id="co-total">5</div>
        </div>
        <div class="stat-card">
            <div class="stat-label">High Cost Items</div>
            <div class="stat-value" id="co-high">2</div>
        </div>
        <div class="stat-card">
            <div class="stat-label">Store Count</div>
            <div class="stat-value" id="co-cat">3</div>
        </div>
    </div>
    <div class="table-card">
        <div class="table-head">
            <h2>Cost & Profit List</h2>
            <button class="btn-add" onclick="openModal('co')">Add Record</button>
        </div>
        <table>
            <thead>
                <tr>
                    <th>Drink Name</th>
                    <th>Store</th>
                    <th>Cost</th>
                    <th>Sale Price</th>
                    <th>Status</th>
                    <th>Action</th>
                </tr>
            </thead>
            <tbody id="co-body">
                <tr>
                    <td>Brown Sugar Boba Milk Tea</td>
                    <td>Store A</td>
                    <td>4.2</td>
                    <td>18</td>
                    <td><span class="badge paid">Normal</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'co')">Delete</button></td>
                </tr>
                <tr>
                    <td>Fresh Lemon Green Tea</td>
                    <td>Store A</td>
                    <td>2.1</td>
                    <td>12</td>
                    <td><span class="badge paid">Normal</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'co')">Delete</button></td>
                </tr>
                <tr>
                    <td>Mango Smoothie</td>
                    <td>Store B</td>
                    <td>5.8</td>
                    <td>22</td>
                    <td><span class="badge unpaid">High Cost</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'co')">Delete</button></td>
                </tr>
                <tr>
                    <td>Oolong Milk Tea</td>
                    <td>Store B</td>
                    <td>3.5</td>
                    <td>16</td>
                    <td><span class="badge paid">Normal</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'co')">Delete</button></td>
                </tr>
                <tr>
                    <td>Strawberry Latte</td>
                    <td>Store C</td>
                    <td>6.3</td>
                    <td>24</td>
                    <td><span class="badge unpaid">High Cost</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'co')">Delete</button></td>
                </tr>
            </tbody>
        </table>
        <div class="note">Product costing, store cost & profit analysis</div>
    </div>
</div>

<!-- MM -->
<div class="tab-panel" id="mm">
    <div class="stat-row">
        <div class="stat-card">
            <div class="stat-label">Total Materials</div>
            <div class="stat-value" id="mm-total">6</div>
        </div>
        <div class="stat-card">
            <div class="stat-label">Low Stock Items</div>
            <div class="stat-value" id="mm-low">2</div>
        </div>
        <div class="stat-card">
            <div class="stat-label">Categories</div>
            <div class="stat-value" id="mm-cat">4</div>
        </div>
    </div>
    <div class="table-card">
        <div class="table-head">
            <h2>Material Inventory List</h2>
            <button class="btn-add" onclick="openModal('mm')">Add Record</button>
        </div>
        <table>
            <thead>
                <tr>
                    <th>Material Name</th>
                    <th>Category</th>
                    <th>Stock</th>
                    <th>Unit</th>
                    <th>Status</th>
                    <th>Action</th>
                </tr>
            </thead>
            <tbody id="mm-body">
                <tr>
                    <td>Black Tea</td>
                    <td>Tea</td>
                    <td>120</td>
                    <td>kg</td>
                    <td><span class="badge paid">Normal</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'mm')">Delete</button></td>
                </tr>
                <tr>
                    <td>Fresh Milk</td>
                    <td>Dairy</td>
                    <td>25</td>
                    <td>L</td>
                    <td><span class="badge unpaid">Low Stock</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'mm')">Delete</button></td>
                </tr>
                <tr>
                    <td>Tapioca Boba</td>
                    <td>Topping</td>
                    <td>80</td>
                    <td>kg</td>
                    <td><span class="badge paid">Normal</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'mm')">Delete</button></td>
                </tr>
                <tr>
                    <td>Mango</td>
                    <td>Fruit</td>
                    <td>18</td>
                    <td>kg</td>
                    <td><span class="badge unpaid">Low Stock</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'mm')">Delete</button></td>
                </tr>
                <tr>
                    <td>Paper Cup</td>
                    <td>Package</td>
                    <td>500</td>
                    <td>pcs</td>
                    <td><span class="badge paid">Normal</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'mm')">Delete</button></td>
                </tr>
                <tr>
                    <td>Coconut Jelly</td>
                    <td>Topping</td>
                    <td>95</td>
                    <td>kg</td>
                    <td><span class="badge paid">Normal</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'mm')">Delete</button></td>
                </tr>
            </tbody>
        </table>
        <div class="note">Tea, milk, toppings, fruits & packaging stock control</div>
    </div>
</div>

<!-- SD -->
<div class="tab-panel" id="sd">
    <div class="stat-row">
        <div class="stat-card">
            <div class="stat-label">Total Orders</div>
            <div class="stat-value" id="sd-total">6</div>
        </div>
        <div class="stat-card">
            <div class="stat-label">Pending Delivery</div>
            <div class="stat-value" id="sd-pending">2</div>
        </div>
        <div class="stat-card">
            <div class="stat-label">Sales Channels</div>
            <div class="stat-value" id="sd-cat">3</div>
        </div>
    </div>
    <div class="table-card">
        <div class="table-head">
            <h2>Order List</h2>
            <button class="btn-add" onclick="openModal('sd')">Add Record</button>
        </div>
        <table>
            <thead>
                <tr>
                    <th>Order No.</th>
                    <th>Channel</th>
                    <th>Amount</th>
                    <th>Date</th>
                    <th>Status</th>
                    <th>Action</th>
                </tr>
            </thead>
            <tbody id="sd-body">
                <tr>
                    <td>ORD001</td>
                    <td>Dine-in</td>
                    <td>36</td>
                    <td>2026-10-20</td>
                    <td><span class="badge paid">Finished</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'sd')">Delete</button></td>
                </tr>
                <tr>
                    <td>ORD002</td>
                    <td>Takeaway</td>
                    <td>24</td>
                    <td>2026-10-20</td>
                    <td><span class="badge paid">Finished</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'sd')">Delete</button></td>
                </tr>
                <tr>
                    <td>ORD003</td>
                    <td>Delivery</td>
                    <td>48</td>
                    <td>2026-10-20</td>
                    <td><span class="badge unpaid">Pending</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'sd')">Delete</button></td>
                </tr>
                <tr>
                    <td>ORD004</td>
                    <td>Dine-in</td>
                    <td>52</td>
                    <td>2026-10-21</td>
                    <td><span class="badge paid">Finished</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'sd')">Delete</button></td>
                </tr>
                <tr>
                    <td>ORD005</td>
                    <td>Delivery</td>
                    <td>32</td>
                    <td>2026-10-21</td>
                    <td><span class="badge unpaid">Pending</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'sd')">Delete</button></td>
                </tr>
                <tr>
                    <td>ORD006</td>
                    <td>Takeaway</td>
                    <td>18</td>
                    <td>2026-10-21</td>
                    <td><span class="badge paid">Finished</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'sd')">Delete</button></td>
                </tr>
            </tbody>
        </table>
        <div class="note">Dine-in, takeaway, delivery order & billing management</div>
    </div>
</div>

<!-- PP -->
<div class="tab-panel" id="pp">
    <div class="stat-row">
        <div class="stat-card">
            <div class="stat-label">Total BOM</div>
            <div class="stat-value" id="pp-total">4</div>
        </div>
        <div class="stat-card">
            <div class="stat-label">In Production</div>
            <div class="stat-value" id="pp-prod">1</div>
        </div>
        <div class="stat-card">
            <div class="stat-label">Formula Types</div>
            <div class="stat-value" id="pp-cat">3</div>
        </div>
    </div>
    <div class="table-card">
        <div class="table-head">
            <h2>BOM & Production List</h2>
            <button class="btn-add" onclick="openModal('pp')">Add Record</button>
        </div>
        <table>
            <thead>
                <tr>
                    <th>BOM No.</th>
                    <th>Drink</th>
                    <th>Main Material</th>
                    <th>Qty</th>
                    <th>Status</th>
                    <th>Action</th>
                </tr>
            </thead>
            <tbody id="pp-body">
                <tr>
                    <td>BOM01</td>
                    <td>Boba Milk Tea</td>
                    <td>Black Tea</td>
                    <td>0.15kg</td>
                    <td><span class="badge paid">Ready</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'pp')">Delete</button></td>
                </tr>
                <tr>
                    <td>BOM02</td>
                    <td>Lemon Green Tea</td>
                    <td>Green Tea</td>
                    <td>0.1kg</td>
                    <td><span class="badge paid">Ready</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'pp')">Delete</button></td>
                </tr>
                <tr>
                    <td>BOM03</td>
                    <td>Mango Smoothie</td>
                    <td>Mango</td>
                    <td>0.2kg</td>
                    <td><span class="badge unpaid">Producing</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'pp')">Delete</button></td>
                </tr>
                <tr>
                    <td>BOM04</td>
                    <td>Oolong Milk Tea</td>
                    <td>Oolong</td>
                    <td>0.12kg</td>
                    <td><span class="badge paid">Ready</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'pp')">Delete</button></td>
                </tr>
            </tbody>
        </table>
        <div class="note">Drink formula BOM, scheduling & production order</div>
    </div>
</div>

<!-- HCM -->
<div class="tab-panel" id="hcm">
    <div class="stat-row">
        <div class="stat-card">
            <div class="stat-label">Total Staff</div>
            <div class="stat-value" id="hcm-total">5</div>
        </div>
        <div class="stat-card">
            <div class="stat-label">On Leave</div>
            <div class="stat-value" id="hcm-leave">1</div>
        </div>
        <div class="stat-card">
            <div class="stat-label">Departments</div>
            <div class="stat-value" id="hcm-cat">3</div>
        </div>
    </div>
    <div class="table-card">
        <div class="table-head">
            <h2>Employee List</h2>
            <button class="btn-add" onclick="openModal('hcm')">Add Record</button>
        </div>
        <table>
            <thead>
                <tr>
                    <th>Emp ID</th>
                    <th>Name</th>
                    <th>Dept</th>
                    <th>Position</th>
                    <th>Status</th>
                    <th>Action</th>
                </tr>
            </thead>
            <tbody id="hcm-body">
                <tr>
                    <td>E001</td>
                    <td>Alice</td>
                    <td>Store A</td>
                    <td>Barista</td>
                    <td><span class="badge paid">On Duty</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'hcm')">Delete</button></td>
                </tr>
                <tr>
                    <td>E002</td>
                    <td>Bob</td>
                    <td>Store A</td>
                    <td>Cashier</td>
                    <td><span class="badge paid">On Duty</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'hcm')">Delete</button></td>
                </tr>
                <tr>
                    <td>E003</td>
                    <td>Cindy</td>
                    <td>Store B</td>
                    <td>Barista</td>
                    <td><span class="badge unpaid">Leave</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'hcm')">Delete</button></td>
                </tr>
                <tr>
                    <td>E004</td>
                    <td>David</td>
                    <td>HQ</td>
                    <td>Manager</td>
                    <td><span class="badge paid">On Duty</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'hcm')">Delete</button></td>
                </tr>
                <tr>
                    <td>E005</td>
                    <td>Ella</td>
                    <td>Store C</td>
                    <td>Barista</td>
                    <td><span class="badge paid">On Duty</span></td>
                    <td><button class="btn-del" onclick="delRow(this,'hcm')">Delete</button></td>
                </tr>
            </tbody>
        </table>
        <div class="note">Employee profile, shift schedule & payroll</div>
    </div>
</div>

<!-- Modal -->
<div class="modal-bg" id="modalBg">
    <div class="modal">
        <h2 id="modalTitle">Add Record</h2>
        <form id="form">
            <div id="modalFields"></div>
            <div class="modal-actions">
                <button type="button" class="btn-cancel" onclick="closeModal()">Cancel</button>
                <button type="submit" class="btn-save">Save</button>
            </div>
        </form>
    </div>
</div>

<script>
let currentTab = "fi";
const config = {
    fi:{
        title:"Add Financial Record",
        fields:`
            <label class="field">Voucher No.<input name="f1" required></label>
            <label class="field">Account Type
                <select name="f2" required>
                    <option>Income</option><option>Expense</option><option>Transfer</option><option>Tax</option>
                </select>
            </label>
            <label class="field">Amount<input name="f3" type="number" step="0.01" min="0" required></label>
            <label class="field">Date<input name="f4" type="date" required></label>
            <label class="field">Status
                <select name="f5" required>
                    <option>Paid</option><option>Unpaid</option>
                </select>
            </label>
        `,
        render:(d)=>`<td>${d.f1}</td><td>${d.f2}</td><td>${d.f3}</td><td>${d.f4}</td><td><span class="badge ${d.f5==='Unpaid'?'unpaid':'paid'}">${d.f5}</span></td><td><button class="btn-del" onclick="delRow(this,'fi')">Delete</button></td>`,
        refresh:()=>{
            const rows = document.querySelectorAll("#fi-body tr");
            let unpaid=0;
            let cat=new Set();
            rows.forEach(tr=>{
                cat.add(tr.children[1].innerText.trim());
                if(tr.children[4].innerText.trim()==='Unpaid') unpaid++;
            })
            document.getElementById("fi-total").innerText=rows.length;
            document.getElementById("fi-unpaid").innerText=unpaid;
            document.getElementById("fi-cat").innerText=cat.size;
        }
    },
    co:{
        title:"Add Cost Record",
        fields:`
            <label class="field">Drink Name<input name="f1" required></label>
            <label class="field">Store
                <select name="f2" required>
                    <option>Store A</option><option>Store B</option><option>Store C</option>
                </select>
            </label>
            <label class="field">Cost<input name="f3" type="number" step="0.01" min="0" required></label>
            <label class="field">Sale Price<input name="f4" type="number" step="0.01" min="0" required></label>
            <label class="field">Status
                <select name="f5" required>
                    <option>Normal</option><option>High Cost</option>
                </select>
            </label>
        `,
        render:(d)=>`<td>${d.f1}</td><td>${d.f2}</td><td>${d.f3}</td><td>${d.f4}</td><td><span class="badge ${d.f5==='High Cost'?'unpaid':'paid'}">${d.f5}</span></td><td><button class="btn-del" onclick="delRow(this,'co')">Delete</button></td>`,
        refresh:()=>{
            const rows = document.querySelectorAll("#co-body tr");
            let high=0;
            let cat=new Set();
            rows.forEach(tr=>{
                cat.add(tr.children[1].innerText.trim());
                if(tr.children[4].innerText.trim()==='High Cost') high++;
            })
            document.getElementById("co-total").innerText=rows.length;
            document.getElementById("co-high").innerText=high;
            document.getElementById("co-cat").innerText=cat.size;
        }
    },
    mm:{
        title:"Add Material Record",
        fields:`
            <label class="field">Material Name<input name="f1" required></label>
            <label class="field">Category
                <select name="f2" required>
                    <option>Tea</option><option>Dairy</option><option>Topping</option><option>Fruit</option><option>Package</option>
                </select>
            </label>
            <label class="field">Stock<input name="f3" type="number" step="0.1" min="0" required></label>
            <label class="field">Unit<input name="f4" required></label>
            <label class="field">Status
                <select name="f5" required>
                    <option>Normal</option><option>Low Stock</option>
                </select>
            </label>
        `,
        render:(d)=>`<td>${d.f1}</td><td>${d.f2}</td><td>${d.f3}</td><td>${d.f4}</td><td><span class="badge ${d.f5==='Low Stock'?'unpaid':'paid'}">${d.f5}</span></td><td><button class="btn-del" onclick="delRow(this,'mm')">Delete</button></td>`,
        refresh:()=>{
            const rows = document.querySelectorAll("#mm-body tr");
            let low=0;
            let cat=new Set();
            rows.forEach(tr=>{
                cat.add(tr.children[1].innerText.trim());
                if(tr.children[4].innerText.trim()==='Low Stock') low++;
            })
            document.getElementById("mm-total").innerText=rows.length;
            document.getElementById("mm-low").innerText=low;
            document.getElementById("mm-cat").innerText=cat.size;
        }
    },
    sd:{
        title:"Add Sales Order",
        fields:`
            <label class="field">Order No.<input name="f1" required></label>
            <label class="field">Channel
                <select name="f2" required>
                    <option>Dine-in</option><option>Takeaway</option><option>Delivery</option>
                </select>
            </label>
            <label class="field">Amount<input name="f3" type="number" step="0.01" min="0" required></label>
            <label class="field">Date<input name="f4" type="date" required></label>
            <label class="field">Status
                <select name="f5" required>
                    <option>Finished</option><option>Pending</option>
                </select>
            </label>
        `,
        render:(d)=>`<td>${d.f1}</td><td>${d.f2}</td><td>${d.f3}</td><td>${d.f4}</td><td><span class="badge ${d.f5==='Pending'?'unpaid':'paid'}">${d.f5}</span></td><td><button class="btn-del" onclick="delRow(this,'sd')">Delete</button></td>`,
        refresh:()=>{
            const rows = document.querySelectorAll("#sd-body tr");
            let pending=0;
            let cat=new Set();
            rows.forEach(tr=>{
                cat.add(tr.children[1].innerText.trim());
                if(tr.children[4].innerText.trim()==='Pending') pending++;
            })
            document.getElementById("sd-total").innerText=rows.length;
            document.getElementById("sd-pending").innerText=pending;
            document.getElementById("sd-cat").innerText=cat.size;
        }
    },
    pp:{
        title:"Add BOM Record",
        fields:`
            <label class="field">BOM No.<input name="f1" required></label>
            <label class="field">Drink<input name="f2" required></label>
            <label class="field">Main Material<input name="f3" required></label>
            <label class="field">Qty<input name="f4" required></label>
            <label class="field">Status
                <select name="f5" required>
                    <option>Ready</option><option>Producing</option>
                </select>
            </label>
        `,
        render:(d)=>`<td>${d.f1}</td><td>${d.f2}</td><td>${d.f3}</td><td>${d.f4}</td><td><span class="badge ${d.f5==='Producing'?'unpaid':'paid'}">${d.f5}</span></td><td><button class="btn-del" onclick="delRow(this,'pp')">Delete</button></td>`,
        refresh:()=>{
            const rows = document.querySelectorAll("#pp-body tr");
            let prod=0;
            let cat=new Set();
            rows.forEach(tr=>{
                cat.add(tr.children[2].innerText.trim());
                if(tr.children[4].innerText.trim()==='Producing') prod++;
            })
            document.getElementById("pp-total").innerText=rows.length;
            document.getElementById("pp-prod").innerText=prod;
            document.getElementById("pp-cat").innerText=cat.size;
        }
    },
    hcm:{
        title:"Add Employee",
        fields:`
            <label class="field">Emp ID<input name="f1" required></label>
            <label class="field">Name<input name="f2" required></label>
            <label class="field">Department
                <select name="f3" required>
                    <option>Store A</option><option>Store B</option><option>Store C</option><option>HQ</option>
                </select>
            </label>
            <label class="field">Position<input name="f4" required></label>
            <label class="field">Status
                <select name="f5" required>
                    <option>On Duty</option><option>Leave</option>
                </select>
            </label>
        `,
        render:(d)=>`<td>${d.f1}</td><td>${d.f2}</td><td>${d.f3}</td><td>${d.f4}</td><td><span class="badge ${d.f5==='Leave'?'unpaid':'paid'}">${d.f5}</span></td><td><button class="btn-del" onclick="delRow(this,'hcm')">Delete</button></td>`,
        refresh:()=>{
            const rows = document.querySelectorAll("#hcm-body tr");
            let leave=0;
            let cat=new Set();
            rows.forEach(tr=>{
                cat.add(tr.children[2].innerText.trim());
                if(tr.children[4].innerText.trim()==='Leave') leave++;
            })
            document.getElementById("hcm-total").innerText=rows.length;
            document.getElementById("hcm-leave").innerText=leave;
            document.getElementById("hcm-cat").innerText=cat.size;
        }
    }
};

document.querySelectorAll(".tab").forEach(tab=>{
    tab.onclick=()=>{
        const t = tab.dataset.tab;
        currentTab = t;
        document.querySelectorAll(".tab").forEach(x=>x.classList.remove("active"));
        tab.classList.add("active");
        document.querySelectorAll(".tab-panel").forEach(p=>p.classList.remove("active"));
        document.getElementById(t).classList.add("active");
    }
})

function openModal(tabKey){
    currentTab = tabKey;
    const c = config[tabKey];
    document.getElementById("modalTitle").innerText = c.title;
    document.getElementById("modalFields").innerHTML = c.fields;
    document.getElementById("modalBg").classList.add("show");
}
function closeModal(){
    document.getElementById("modalBg").classList.remove("show");
    document.getElementById("form").reset();
}
document.getElementById("modalBg").onclick = (e)=>{
    if(e.target === document.getElementById("modalBg")) closeModal();
}

document.getElementById("form").onsubmit = function(e){
    e.preventDefault();
    const fd = new FormData(this);
    const data = {
        f1:fd.get("f1"),f2:fd.get("f2"),f3:fd.get("f3"),
        f4:fd.get("f4"),f5:fd.get("f5")
    };
    const tbody = document.getElementById(currentTab+"-body");
    const tr = document.createElement("tr");
    tr.innerHTML = config[currentTab].render(data);
    tbody.prepend(tr);
    config[currentTab].refresh();
    closeModal();
}

function delRow(btn,tabKey){
    if(!confirm("Delete this record?")) return;
    btn.closest("tr").remove();
    config[tabKey].refresh();
}

Object.keys(config).forEach(k=>config[k].refresh());
</script>
</body>
</html>
