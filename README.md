# quantity
quantity
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>حساب كميات البناء</title>
    <style>
        body { font-family: Arial, sans-serif; padding: 20px; }
        table { width: 100%; border-collapse: collapse; margin-top: 20px; }
        th, td { border: 1px solid #ddd; padding: 8px; text-align: center; }
        th { background-color: #f2f2f2; }
        input { width: 100%; padding: 5px; }
    </style>
</head>
<body>
    <h1>حساب كميات مواد البناء</h1>
    <label for="area">مساحة المبنى (م²):</label>
    <input type="number" id="area" placeholder="أدخل المساحة">
    <button onclick="calculate()">احسب</button>

    <table id="results">
        <tr>
            <th>المادة</th>
            <th>الكمية لكل م²</th>
            <th>الإجمالي</th>
        </tr>
        <!-- النتائج تظهر هنا -->
    </table>

    <script>
        const materials = [
            { name: "الخرسانة (م³)", rate: 0.4, unit: "م³" },
            { name: "الحديد (كجم)", rate: 60, unit: "كجم" },
            { name: "الطوب (بلوكة)", rate: 12, unit: "بلوكة" },
            { name: "الأسمنت (كجم)", rate: 50, unit: "كجم" },
            { name: "الرمل (م³)", rate: 0.15, unit: "م³" },
            { name: "الزلط (م³)", rate: 0.2, unit: "م³" },
            { name: "بلاط السيراميك (م²)", rate: 1.1, unit: "م²" }
        ];

        function calculate() {
            const area = parseFloat(document.getElementById("area").value);
            let table = "<tr><th>المادة</th><th>الكمية لكل م²</th><th>الإجمالي</th></tr>";

            materials.forEach(item => {
                const total = (area * item.rate).toFixed(2);
                table += `
                    <tr>
                        <td>${item.name}</td>
                        <td>${item.rate} ${item.unit}</td>
                        <td>${total} ${item.unit}</td>
                    </tr>
                `;
            });

            document.getElementById("results").innerHTML = table;
        }
    </script>
</body>
</html>
