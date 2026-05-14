# MOADLLL
معادلات
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>اختبار المعادلات التفاضلية - شرط لبشر</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700&display=swap');
        
        body {
            font-family: 'Tajawal', sans-serif;
            background-color: #0f0f0f;
            color: #d4af37;
        }

        .gold-border {
            border: 1px solid #d4af37;
        }

        .gold-gradient {
            background: linear-gradient(135deg, #d4af37 0%, #f2d06b 50%, #b8860b 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .gold-bg {
            background: linear-gradient(135deg, #d4af37 0%, #b8860b 100%);
        }

        .card {
            background-color: #1a1a1a;
            border-radius: 15px;
            transition: transform 0.3s ease;
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(212, 175, 55, 0.1);
        }

        .option-btn {
            display: block;
            width: 100%;
            text-align: right;
            padding: 12px;
            margin: 8px 0;
            border: 1px solid #333;
            border-radius: 8px;
            transition: all 0.2s;
            background: #252525;
        }

        .option-btn:hover {
            border-color: #d4af37;
            background: #2a2a2a;
        }

        .correct {
            background: #1b4332 !important;
            border-color: #2d6a4f !important;
            color: #fff !important;
        }

        .wrong {
            background: #431b1b !important;
            border-color: #6a2d2d !important;
            color: #fff !important;
        }
    </style>
</head>
<body class="p-4 md:p-8">

    <div class="max-w-4xl mx-auto">
        <header class="text-center mb-12">
            <h1 class="text-4xl md:text-5xl font-bold gold-gradient mb-4">اختبار نظرية المعادلات التفاضلية</h1>
            <p class="text-gray-400">أسئلة شاملة حول شرط لبشر (Lipschitz Condition) وجود ووحدانية الحل</p>
        </header>

        <!-- Section 1: True/False -->
        <div class="mb-12">
            <h2 class="text-2xl font-bold mb-6 border-b-2 border-gold pb-2 inline-block">أولاً: أسئلة الصح والخطأ (20 سؤال)</h2>
            <div id="true-false-container" class="space-y-4">
                <!-- Questions injected by JS -->
            </div>
        </div>

        <!-- Section 2: Multiple Choice -->
        <div class="mb-12">
            <h2 class="text-2xl font-bold mb-6 border-b-2 border-gold pb-2 inline-block">ثانياً: أسئلة الاختيار من متعدد (20 سؤال)</h2>
            <div id="mcq-container" class="space-y-6">
                <!-- Questions injected by JS -->
            </div>
        </div>

        <footer class="text-center py-8 text-gray-500 border-t border-gray-800">
            جميع الأسئلة مستوحاة من محتوى ملف المعادلات التفاضلية المرفوع.
        </footer>
    </div>

    <script>
        const tfQuestions = [
            { q: "يركز المستوى العميق في دراسة المعادلات التفاضلية على إيجاد الحل الصريحة فقط.", a: false },
            { q: "النموذج الرياضي يصف الواقع بكل تفاصيله الدقيقة دون استثناء.", a: false },
            { q: "شرط لبشر (Lipschitz) هو شرط أساسي لضمان وجود ووحدانية الحل.", a: true },
            { q: "إذا كانت المشتقة الجزئية بالنسبة لـ y مقيدة، فإن الدالة تحقق شرط لبشر.", a: true },
            { q: "في النماذج الفيزيائية، يمكن دائماً إيجاد حل صريح للمعادلة التفاضلية.", a: false },
            { q: "تستخدم المعادلات التفاضلية في علم الاقتصاد لوصف التغيرات الزمنية.", a: true },
            { q: "النظرية الرياضية توفر ضماناً قبل البدء بالحسابات العددية.", a: true },
            { q: "الدالة f(x,y) تحقق شرط لبشر إذا وجد ثابت موجب L يحقق المتراجحة المطلوبة.", a: true },
            { q: "ثابت لبشر L يجب أن يكون دائماً عدداً سالباً.", a: false },
            { q: "دراسة سلوك الحل أهم أحياناً من إيجاد قيمة الحل نفسه.", a: true },
            { q: "النمو السكاني هو مثال على النمذجة الرياضية في علم الأحياء.", a: true },
            { q: "لا يشترط وجود حل وحيد لضمان صحة النموذج الرياضي.", a: false },
            { q: "يستخدم 'شرط لبشر' بالنسبة للمتغير y فقط في نظرية الوجود والوحدانية.", a: true },
            { q: "إذا كانت الدالة مستمرة، فهذا يضمن وحدانية الحل تلقائياً.", a: false },
            { q: "النماذج الرياضية هي تمثيل لظاهرة واقعية باستخدام أدوات رياضية.", a: true },
            { q: "يتم التحقق من شرط لبشر على مجموعة محددة D في المستوى xy.", a: true },
            { q: "التركيز في المراحل السابقة كان على الطرق الحسابية فقط.", a: true },
            { q: "تغيير الشرط الابتدائي لا يؤثر على السلوك العام للحل.", a: false },
            { q: "معدل التغير في الظاهرة يعبر عنه رياضياً بالمعادلة التفاضلية.", a: true },
            { q: "إذا لم تكن f مستمرة، فلا يمكن أن تحقق شرط لبشر.", a: true }
        ];

        const mcqQuestions = [
            { q: "ما هو الهدف الأساسي من النموذج الرياضي؟", o: ["وصف الواقع بكل تفاصيله", "فهم سلوك الظاهرة أو التنبؤ بها", "تعقيد المسائل الحسابية", "إلغاء الحاجة للحسابات"], a: 1 },
            { q: "أي مما يلي ليس من مجالات تطبيق المعادلات التفاضلية المذكورة؟", o: ["الفيزياء", "الاقتصاد", "الأحياء", "التاريخ الأدبي"], a: 3 },
            { q: "ماذا يسمى الثابت الموجب L في نظرية الوحدانية؟", o: ["ثابت نيوتن", "ثابت لبشر", "ثابت التكامل", "ثابت الجذب"], a: 1 },
            { q: "الشرط الأساسي لنظرية بيكار لندلوف هو:", o: ["الاستمرارية فقط", "شرط لبشر", "أن تكون الدالة خطية", "أن يكون الحل صفرياً"], a: 1 },
            { q: "تستخدم المعادلات التفاضلية في الفيزياء لوصف:", o: ["حركة جسم أو اهتزازه", "النمو السكاني", "تغير الأسعار", "بنية الخلية"], a: 0 },
            { q: "ماذا تعني وحدانية الحل؟", o: ["وجود حل واحد فقط", "وجود أكثر من حل", "عدم وجود حل", "أن الحل هو الرقم 1"], a: 0 },
            { q: "إذا كان |f(x,y1) - f(x,y2)| ≤ L |y1 - y2|، فإن هذا يعبر عن:", o: ["قاعدة السلسلة", "شرط لبشر", "قانون أوم", "مبرهنة فيثاغورس"], a: 1 },
            { q: "النمو السكاني يتبع نموذجاً رياضياً في علم:", o: ["الاقتصاد", "الأحياء", "الفلك", "الهندسة"], a: 1 },
            { q: "لماذا نحتاج دراسة نظرية المعادلات؟", o: ["لأن أغلبها لا يمكن حله صريحاً", "لأنها سهلة جداً", "لأنها غير مفيدة واقعياً", "لأنها تعتمد على الحفظ"], a: 0 },
            { q: "المعادلة y' = x + y عند y(0)=0 تحقق شرط لبشر لأن:", o: ["المشتقة بالنسبة لـ y تساوي 1", "المشتقة بالنسبة لـ x تساوي 1", "الدالة صفرية", "الدالة تربيعية"], a: 0 },
            { q: "في الاقتصاد، نهتم بدراسة التغيرات:", o: ["المكانية", "الزمنية", "الجغرافية", "اللغوية"], a: 1 },
            { q: "أي من هذه الدوال لا تحقق شرط لبشر عند y=0؟", o: ["y^2", "x+y", "جذر y (sqrt)", "5y"], a: 2 },
            { q: "تعتبر النظرية ضماناً رياضياً قبل:", o: ["تحديد اسم المادة", "الحساب العددي أو التقريب", "كتابة السؤال", "رسم المنحنى"], a: 1 },
            { q: "المجموعة D التي يدرس عليها شرط لبشر تكون في المستوى:", o: ["R1", "xy", "xyz", "القطبي"], a: 1 },
            { q: "الاستمرارية شرط ______ لوجود الحل.", o: ["كافٍ فقط", "ضروري", "غير مهم", "مستحيل"], a: 1 },
            { q: "عندما تتغير الشروط الابتدائية، فإننا ندرس:", o: ["اسم الدالة", "السلوك العام للحل", "لون الرسم", "تاريخ المعادلة"], a: 1 },
            { q: "شرط لبشر يضمن أن الدالة f تتغير بشكل:", o: ["عشوائي", "مقيد", "لانهائي", "متقطع"], a: 1 },
            { q: "المسافة بين y1 و y2 في شرط لبشر يعبر عنها بـ:", o: ["المربع", "القيمة المطلقة", "الجذر التكعيبي", "اللوغاريتم"], a: 1 },
            { q: "النماذج الرياضية في التطبيقات الواقعية تهدف إلى:", o: ["تعقيد الواقع", "الوصول لنتائج موثوقة", "إضاعة الوقت", "تجاهل الفيزياء"], a: 1 },
            { q: "إذا كانت المشتقة ∂f/∂y مستمرة على منطقة مغلقة، فإن L هو:", o: ["القيمة الصغرى", "القيمة العظمى للمشتقة", "الصفر", "المالانهاية"], a: 1 }
        ];

        // Inject TF Questions
        const tfContainer = document.getElementById('true-false-container');
        tfQuestions.forEach((item, index) => {
            const div = document.createElement('div');
            div.className = 'card p-4 flex flex-col md:flex-row justify-between items-center gap-4';
            div.innerHTML = `
                <span class="text-lg font-medium">${index + 1}. ${item.q}</span>
                <div class="flex gap-2">
                    <button onclick="checkTF(this, true, ${item.a})" class="px-6 py-2 border border-gold rounded-full hover:bg-gold-bg hover:text-black transition">صح</button>
                    <button onclick="checkTF(this, false, ${item.a})" class="px-6 py-2 border border-gold rounded-full hover:bg-gold-bg hover:text-black transition">خطأ</button>
                </div>
            `;
            tfContainer.appendChild(div);
        });

        // Inject MCQ Questions
        const mcqContainer = document.getElementById('mcq-container');
        mcqQuestions.forEach((item, index) => {
            const div = document.createElement('div');
            div.className = 'card p-6';
            let optionsHtml = '';
            item.o.forEach((opt, optIndex) => {
                optionsHtml += `<button onclick="checkMCQ(this, ${optIndex}, ${item.a})" class="option-btn">${opt}</button>`;
            });
            div.innerHTML = `
                <p class="text-xl font-bold mb-4 gold-gradient">${index + 21}. ${item.q}</p>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-2">
                    ${optionsHtml}
                </div>
            `;
            mcqContainer.appendChild(div);
        });

        function checkTF(btn, userAns, correctAns) {
            const parent = btn.parentElement;
            const buttons = parent.querySelectorAll('button');
            buttons.forEach(b => b.disabled = true);
            
            if (userAns === correctAns) {
                btn.style.backgroundColor = '#1b4332';
                btn.style.color = '#fff';
            } else {
                btn.style.backgroundColor = '#431b1b';
                btn.style.color = '#fff';
                // Highlight correct
                buttons.forEach(b => {
                   if((b.innerText === 'صح' && correctAns) || (b.innerText === 'خطأ' && !correctAns)) {
                       b.style.borderColor = '#2d6a4f';
                       b.style.borderWidth = '2px';
                   }
                });
            }
        }

        function checkMCQ(btn, userIdx, correctIdx) {
            const parent = btn.parentElement;
            const buttons = parent.querySelectorAll('button');
            buttons.forEach(b => b.disabled = true);

            if (userIdx === correctIdx) {
                btn.classList.add('correct');
            } else {
                btn.classList.add('wrong');
                buttons[correctIdx].classList.add('correct');
            }
        }
    </script>
</body>
</html>
