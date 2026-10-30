# shadowy-spooky-hex
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>تطبيق منصة بَرَكَة - النموذج التفاعلي</title>
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary: #1b4d3e;
            --primary-light: #2e6b56;
            --accent: #d97706;
            --bg: #f4f7f5;
            --card-bg: #ffffff;
            --text: #1f2937;
            --border: #e5e7eb;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Tajawal', sans-serif; }
        body { background-color: var(--bg); color: var(--text); padding-bottom: 50px; }

        /* Navigation Header */
        header {
            background: linear-gradient(135deg, var(--primary), var(--primary-light));
            color: white; padding: 20px 40px;
            display: flex; justify-content: space-between; align-items: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
        }

        .logo { font-size: 1.8rem; font-weight: 800; }
        .user-info { font-size: 0.95rem; opacity: 0.9; }

        /* Main Layout */
        .container { max-width: 1200px; margin: 30px auto; padding: 0 20px; }
        
        .nav-tabs {
            display: flex; gap: 10px; margin-bottom: 25px; border-bottom: 2px solid var(--border); padding-bottom: 10px;
        }

        .tab-btn {
            background: transparent; border: none; padding: 12px 24px;
            font-size: 1.1rem; font-weight: 700; color: #6b7280;
            cursor: pointer; border-radius: 8px; transition: all 0.3s;
        }

        .tab-btn.active, .tab-btn:hover {
            background-color: var(--primary); color: white;
        }

        .tab-content { display: none; }
        .tab-content.active { display: block; }

        /* Interactive Card */
        .card {
            background: var(--card-bg); border-radius: 16px; padding: 30px;
            border: 1px solid var(--border); box-shadow: 0 4px 15px rgba(0,0,0,0.03); margin-bottom: 25px;
        }

        .card h2 { color: var(--primary); margin-bottom: 20px; font-size: 1.5rem; display: flex; align-items: center; gap: 10px; }

        /* Form Controls */
        .form-group { margin-bottom: 20px; }
        label { display: block; font-weight: 700; margin-bottom: 8px; font-size: 1.05rem; }
        input, select {
            width: 100%; padding: 12px 16px; border: 1px solid var(--border);
            border-radius: 8px; font-size: 1rem; background-color: #f9fafb;
        }
        input:focus, select:focus { outline: none; border-color: var(--primary); background: #fff; }

        .btn-submit {
            background-color: var(--primary); color: white; border: none;
            padding: 14px 28px; font-size: 1.1rem; font-weight: 700;
            border-radius: 8px; cursor: pointer; width: 100%; transition: background 0.2s;
        }

        .btn-submit:hover { background-color: var(--primary-light); }

        /* Dashboard & Metric Boxes */
        .metrics-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 20px; margin-top: 20px;
        }

        .metric-card {
            background-color: #f0fdf4; border: 1px solid #bbf7d0; border-radius: 12px; padding: 20px; text-align: center;
        }

        .metric-card.warning { background-color: #fffbeb; border-color: #fde68a; }

        .metric-title { font-size: 0.95rem; color: #4b5563; font-weight: 700; }
        .metric-value { font-size: 1.8rem; font-weight: 800; color: var(--primary); margin-top: 5px; }

        /* Data Tables */
        table { width: 100%; border-collapse: collapse; margin-top: 15px; }
        th, td { padding: 12px 15px; border: 1px solid var(--border); text-align: right; }
        th { background-color: #f3f4f6; color: var(--primary); font-weight: 700; }

        @media (max-width: 768px) {
            header { flex-direction: column; text-align: center; gap: 10px; }
            .nav-tabs { flex-wrap: wrap; }
        }
    </style>
</head>
<body>

    <header>
        <div class="logo">🌾 منصة بَرَكَة (نموذج تفاعلي)</div>
        <div class="user-info">المستخدم: مالك أرض / مستثمر | المشروع: القمح والزيتون</div>
    </header>

    <div class="container">

        <!-- Navigation Tabs -->
        <div class="nav-tabs">
            <button class="tab-btn active" onclick="switchTab('estimation')">🧮 محرك التقدير الذكي</button>
            <button class="tab-btn" onclick="switchTab('expenses')">📝 سجل المصاريف والميدان</button>
            <button class="tab-btn" onclick="switchTab('profit')">💰 المحرك المالي والأرباح</button>
        </div>

        <!-- TAB 1: Smart Estimation Engine -->
        <div id="estimation" class="tab-content active">
            <div class="card">
                <h2><span>📐</span> تجربة محرك التقدير الزراعي الآلي</h2>
                <p style="margin-bottom: 20px; color: #6b7280;">أدخل مساحة أرضك ونوع المحصول، وسيوم النظام باحتساب عدد الأشجار والإنتاجية والميزانية التشغيلية تلقائياً:</p>
                
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px;">
                    <div class="form-group">
                        <label>مساحة الأرض (بالدونم):</label>
                        <input type="number" id="landArea" value="10" placeholder="أدخل المساحة برقم">
                    </div>

                    <div class="form-group">
                        <label>نوع المحصول:</label>
                        <select id="cropType">
                            <option value="olive">زيتون</option>
                            <option value="wheat">قمح</option>
                        </select>
                    </div>

                    <div class="form-group">
                        <label>نمط الري:</label>
                        <select id="irrigationType">
                            <option value="rainfed">بعل (اعتماد على المطر)</option>
                            <option value="irrigated">مروي</option>
                        </select>
                    </div>
                </div>

                <button class="btn-submit" onclick="calculateEstimation()">حساب التقديرات الآلية</button>

                <!-- Results Section -->
                <div id="estimationResults" class="metrics-grid">
                    <div class="metric-card">
                        <div class="metric-title">عدد الأشجار المتوقع</div>
                        <div class="metric-value" id="resTrees">200 شجرة</div>
                    </div>
                    <div class="metric-card">
                        <div class="metric-title">إجمالي المحصول المتوقع</div>
                        <div class="metric-value" id="resYield">3,000 كغ</div>
                    </div>
                    <div class="metric-card">
                        <div class="metric-title">الإنتاج الصافي (زيت/طحين)</div>
                        <div class="metric-value" id="resFinalProduct">600 لتر زيت</div>
                    </div>
                    <div class="metric-card warning">
                        <div class="metric-title">التمويل التشغيلي المطلوب</div>
                        <div class="metric-value" id="resBudget">1,200 $</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- TAB 2: Digital Expense Logbook -->
        <div id="expenses" class="tab-content">
            <div class="card">
                <h2><span>📋</span> تسجيل المصاريف الميدانية اليومية</h2>
                <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px;">
                    <div class="form-group">
                        <label>نوع المصروف:</label>
                        <select id="expenseType">
                            <option value="عمالة">أجور عمالة (قطاف/حصاد)</option>
                            <option value="نقل">تكاليف نقل وشحن</option>
                            <option value="عصر/طحن">أجور معصرة / مطحنة</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>المبلغ ($):</label>
                        <input type="number" id="expenseAmount" placeholder="مثال: 150">
                    </div>
                    <div class="form-group">
                        <label>البيان / الملاحظة:</label>
                        <input type="text" id="expenseNote" placeholder="مثال: أجر عمال قطاف اليوم الأول">
                    </div>
                </div>
                <button class="btn-submit" onclick="addExpense()">إضافة المصروف للسجل</button>

                <h3 style="margin-top: 30px; color: var(--primary);">سجل المصاريف الموثقة للموسم:</h3>
                <table>
                    <thead>
                        <tr>
                            <th>نوع المصروف</th>
                            <th>البيان</th>
                            <th>المبلغ ($)</th>
                        </tr>
                    </thead>
                    <tbody id="expenseTableBody">
                        <tr>
                            <td>عمالة</td>
                            <td>دفعة أولى للقطاف الميداني</td>
                            <td>300 $</td>
                        </tr>
                        <tr>
                            <td>نقل</td>
                            <td>شاحنة نقل المحصول إلى المعصرة</td>
                            <td>100 $</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>

        <!-- TAB 3: Profit Calculation Engine -->
        <div id="profit" class="tab-content">
            <div class="card">
                <h2><span>📊</span> حساب وتوزيع صافي الأرباح آلياً</h2>
                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px;">
                    <div class="form-group">
                        <label>إجمالي المبيادات الإجمالية ($):</label>
                        <input type="number" id="totalRevenue" value="5000">
                    </div>
                    <div class="form-group">
                        <label>نسبة مالك الأرض (%):</label>
                        <input type="number" id="ownerShareRatio" value="50">
                    </div>
                </div>
                <button class="btn-submit" onclick="calculateProfit()">تصفية الحسابات المالية</button>

                <div class="metrics-grid" style="margin-top: 25px;">
                    <div class="metric-card">
                        <div class="metric-title">إجمالي الإيرادات</div>
                        <div class="metric-value" id="dispRevenue">5,000 $</div>
                    </div>
                    <div class="metric-card warning">
                        <div class="metric-title">إجمالي المصاريف المخصومة</div>
                        <div class="metric-value" id="dispExpenses">400 $</div>
                    </div>
                    <div class="metric-card">
                        <div class="metric-title">صافي الربح القابل للتوزيع</div>
                        <div class="metric-value" id="dispNetProfit">4,600 $</div>
                    </div>
                </div>

                <div style="margin-top: 25px; padding: 20px; background-color: #e6f4ea; border-radius: 12px; text-align: center;">
                    <h3 style="color: var(--primary); margin-bottom: 10px;">نتيجة التوزيع الآلي حسب العقد:</h3>
                    <p style="font-size: 1.2rem; font-weight: 700;">
                        حصة مالك الأرض: <span id="ownerAmount" style="color: var(--primary);">2,300 $</span> | 
                        حصة المستثمر الممول: <span id="investorAmount" style="color: var(--primary-light);">2,300 $</span>
                    </p>
                </div>
            </div>
        </div>

    </div>

    <script>
        // Tab Switcher
        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
            document.querySelectorAll('.tab-btn').forEach(el => el.classList.remove('active'));
            
            document.getElementById(tabId).classList.add('active');
            event.currentTarget.classList.add('active');
        }

        // Smart Estimation Logic
        function calculateEstimation() {
            const area = parseFloat(document.getElementById('landArea').value) || 0;
            const crop = document.getElementById('cropType').value;
            const irrigation = document.getElementById('irrigationType').value;

            let trees = 0, yieldKg = 0, finalProd = '', budget = 0;

            if (crop === 'olive') {
                const density = (irrigation === 'rainfed') ? 20 : 35;
                trees = area * density;
                yieldKg = trees * 15; // متوسط 15 كغ للشجرة
                const oilLiters = Math.round(yieldKg / 5); // 1 لتر لكل 5 كغ زيتون
                finalProd = oilLiters + ' لتر زيت';
                budget = area * 120; // 120 $ تكلفة الدونم
            } else {
                trees = 0; // القمح لا يوجد به أشجار
                yieldKg = area * 350; // 350 كغ للدونم
                finalProd = (yieldKg / 1000).toFixed(1) + ' طن قمح';
                budget = area * 80; // 80 $ تكلفة الدونم
            }

            document.getElementById('resTrees').innerText = (trees > 0) ? trees + ' شجرة' : 'غير مطبق (حبوب)';
            document.getElementById('resYield').innerText = yieldKg.toLocaleString() + ' كغ';
            document.getElementById('resFinalProduct').innerText = finalProd;
            document.getElementById('resBudget').innerText = budget.toLocaleString() + ' $';
        }

        // Add Expense Logic
        let currentTotalExpenses = 400; // القيمة المبدئية المسجلة بالتطابق مع الجدول
        function addExpense() {
            const type = document.getElementById('expenseType').value;
            const amount = parseFloat(document.getElementById('expenseAmount').value);
            const note = document.getElementById('expenseNote').value;

            if (!amount || amount <= 0) {
                alert('يرجى إدخال مبلغ صحيح للمصروف');
                return;
            }

            const tbody = document.getElementById('expenseTableBody');
            const row = `<tr><td>${type}</td><td>${note || 'بدون ملاحظة'}</td><td>${amount} $</td></tr>`;
            tbody.innerHTML += row;

            currentTotalExpenses += amount;
            document.getElementById('dispExpenses').innerText = currentTotalExpenses.toLocaleString() + ' $';

            // Clear inputs
            document.getElementById('expenseAmount').value = '';
            document.getElementById('expenseNote').value = '';
        }

        // Profit Logic
        function calculateProfit() {
            const revenue = parseFloat(document.getElementById('totalRevenue').value) || 0;
            const ratio = parseFloat(document.getElementById('ownerShareRatio').value) || 50;

            const netProfit = revenue - currentTotalExpenses;
            const ownerShare = (netProfit * ratio) / 100;
            const investorShare = netProfit - ownerShare;

            document.getElementById('dispRevenue').innerText = revenue.toLocaleString() + ' $';
            document.getElementById('dispExpenses').innerText = currentTotalExpenses.toLocaleString() + ' $';
            document.getElementById('dispNetProfit').innerText = (netProfit > 0 ? netProfit.toLocaleString() : 0) + ' $';

            document.getElementById('ownerAmount').innerText = (ownerShare > 0 ? ownerShare.toLocaleString() : 0) + ' $';
            document.getElementById('investorAmount').innerText = (investorShare > 0 ? investorShare.toLocaleString() : 0) + ' $';
        }
    </script>
</body>
</html>
