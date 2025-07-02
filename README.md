<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>บอร์ดความรู้ฟิสิกส์</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 10px;
            animation: backgroundShift 10s ease-in-out infinite;
            margin: 0;
        }

        @keyframes backgroundShift {
            0%, 100% { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); }
            50% { background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%); }
        }

        .container {
            max-width: 100%;
            margin: 0 auto;
            padding: 0 5px;
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            color: white;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .header h1 {
            font-size: 2em;
            margin-bottom: 10px;
            animation: glow 2s ease-in-out infinite alternate;
        }

        @media (min-width: 768px) {
            .header h1 {
                font-size: 3em;
            }
        }

        @keyframes glow {
            from { text-shadow: 0 0 20px #fff, 0 0 30px #fff, 0 0 40px #0ff; }
            to { text-shadow: 0 0 10px #fff, 0 0 20px #fff, 0 0 30px #0ff; }
        }

        .header p {
            font-size: 1.2em;
            opacity: 0.9;
        }

        .physics-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 15px;
            margin-bottom: 30px;
        }

        @media (min-width: 600px) {
            .physics-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 20px;
            }
        }

        @media (min-width: 900px) {
            .physics-grid {
                grid-template-columns: repeat(3, 1fr);
                gap: 25px;
            }
        }

        .physics-card {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 20px;
            border: 2px solid rgba(255, 255, 255, 0.2);
            transition: all 0.4s ease;
            cursor: pointer;
            position: relative;
            overflow: hidden;
            -webkit-tap-highlight-color: transparent;
            touch-action: manipulation;
        }

        @media (min-width: 600px) {
            .physics-card {
                padding: 25px;
            }
        }

        .physics-card:hover {
            transform: translateY(-10px) scale(1.05);
            box-shadow: 0 20px 40px rgba(0,0,0,0.2);
            background: rgba(255, 255, 255, 0.25);
        }

        .physics-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent);
            transition: left 0.5s;
        }

        .physics-card:hover::before {
            left: 100%;
        }

        .card-icon {
            font-size: 3em;
            margin-bottom: 15px;
            display: block;
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
            40% { transform: translateY(-10px); }
            60% { transform: translateY(-5px); }
        }

        .card-title {
            font-size: 1.5em;
            font-weight: bold;
            color: white;
            margin-bottom: 10px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
        }

        .card-description {
            color: rgba(255, 255, 255, 0.9);
            line-height: 1.6;
            font-size: 0.95em;
        }

        .mechanics { background: linear-gradient(135deg, #ff6b6b, #ff8e8e); }
        .thermodynamics { background: linear-gradient(135deg, #4ecdc4, #44a08d); }
        .electromagnetism { background: linear-gradient(135deg, #ffd93d, #ff6b6b); }
        .optics { background: linear-gradient(135deg, #a8edea, #fed6e3); }
        .modern-physics { background: linear-gradient(135deg, #667eea, #764ba2); }
        .waves { background: linear-gradient(135deg, #74b9ff, #0984e3); }

        .formula-section {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            border-radius: 20px;
            padding: 30px;
            margin-top: 30px;
            border: 2px solid rgba(255, 255, 255, 0.3);
        }

        .formula-title {
            color: white;
            font-size: 2em;
            text-align: center;
            margin-bottom: 25px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .formula-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 15px;
        }

        @media (min-width: 600px) {
            .formula-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 20px;
            }
        }

        @media (min-width: 900px) {
            .formula-grid {
                grid-template-columns: repeat(3, 1fr);
            }
        }

        .formula-card {
            background: rgba(255, 255, 255, 0.2);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.3);
        }

        .formula-card:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: scale(1.05);
        }

        .formula {
            font-size: 1.5em;
            font-weight: bold;
            color: #fff;
            margin-bottom: 10px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
        }

        .formula-name {
            color: rgba(255, 255, 255, 0.9);
            font-size: 0.9em;
        }

        .interactive-demo {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            border-radius: 20px;
            padding: 30px;
            margin-top: 30px;
            text-align: center;
            border: 2px solid rgba(255, 255, 255, 0.3);
        }

        .demo-title {
            color: white;
            font-size: 2em;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .pendulum-container {
            position: relative;
            height: 150px;
            margin: 20px auto;
            width: 250px;
        }

        @media (min-width: 600px) {
            .pendulum-container {
                height: 200px;
                width: 300px;
            }
        }

        .pendulum {
            position: absolute;
            top: 0;
            left: 50%;
            width: 2px;
            height: 150px;
            background: white;
            transform-origin: top center;
            animation: swing 2s ease-in-out infinite;
        }

        .pendulum::after {
            content: '';
            position: absolute;
            bottom: -15px;
            left: -13px;
            width: 28px;
            height: 28px;
            background: radial-gradient(circle, #ffd700, #ffed4e);
            border-radius: 50%;
            box-shadow: 0 0 20px #ffd700;
        }

        @keyframes swing {
            0%, 100% { transform: rotate(-30deg); }
            50% { transform: rotate(30deg); }
        }

        .fun-facts {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            border-radius: 20px;
            padding: 30px;
            margin-top: 30px;
            border: 2px solid rgba(255, 255, 255, 0.3);
        }

        .facts-title {
            color: white;
            font-size: 2em;
            text-align: center;
            margin-bottom: 25px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .fact-item {
            background: rgba(255, 255, 255, 0.15);
            padding: 15px;
            margin: 15px 0;
            border-radius: 10px;
            color: white;
            border-left: 4px solid #ffd700;
            transition: all 0.3s ease;
        }

        .fact-item:hover {
            background: rgba(255, 255, 255, 0.25);
            transform: translateX(10px);
        }

        .floating-particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: rgba(255, 255, 255, 0.8);
            border-radius: 50%;
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); opacity: 1; }
            50% { transform: translateY(-20px) rotate(180deg); opacity: 0.5; }
        }
    </style>
</head>
<body>
    <div class="floating-particles" id="particles"></div>
    
    <div class="container">
        <div class="header">
            <h1>🔬 บอร์ดความรู้ฟิสิกส์ 🌟</h1>
            <p>สำรวจโลกแห่งวิทยาศาสตร์ฟิสิกส์อันน่าทึ่ง</p>
        </div>

        <div class="physics-grid">
            <div class="physics-card mechanics">
                <div class="card-icon">⚙️</div>
                <div class="card-title">กลศาสตร์ (Mechanics)</div>
                <div class="card-description">
                    ศึกษาการเคลื่อนที่ของวัตถุ แรง พลังงาน และโมเมนตัม รวมถึงกฎของนิวตัน กฎการเปลี่ยนแปลงของพลังงาน และการเคลื่อนที่แบบต่างๆ
                </div>
            </div>

            <div class="physics-card thermodynamics">
                <div class="card-icon">🌡️</div>
                <div class="card-title">เทอร์โมไดนามิกส์</div>
                <div class="card-description">
                    ศึกษาความร้อน อุณหภูมิ พลังงานความร้อน และการเปลี่ยนแปลงสถานะของสสาร รวมถึงกฎข้อที่ 1 และ 2 ของเทอร์โมไดนามิกส์
                </div>
            </div>

            <div class="physics-card electromagnetism">
                <div class="card-icon">⚡</div>
                <div class="card-title">แม่เหล็กไฟฟ้า</div>
                <div class="card-description">
                    ศึกษาประจุไฟฟ้า กระแสไฟฟ้า สนามไฟฟ้า สนามแม่เหล็ก และคลื่นแม่เหล็กไฟฟ้า รวมถึงกฎของคูลอมบ์และกฎของแมกซ์เวลล์
                </div>
            </div>

            <div class="physics-card optics">
                <div class="card-icon">🔍</div>
                <div class="card-title">ทัศนศาสตร์ (Optics)</div>
                <div class="card-description">
                    ศึกษาแสง การหักเห การสะท้อน การแทรกสอด การเลี้ยวเบน และเครื่องมือออปติกต่างๆ เช่น กล้องจุลทรรศน์ กล้องโทรทรรศน์
                </div>
            </div>

            <div class="physics-card modern-physics">
                <div class="card-icon">🔬</div>
                <div class="card-title">ฟิสิกส์สมัยใหม่</div>
                <div class="card-description">
                    ศึกษาทฤษฎีสัมพัทธภาพ ฟิสิกส์ควอนตัม โครงสร้างอะตอม นิวเคลียร์ และอนุภาคมูลฐาน รวมถึงการประยุกต์ใช้ในเทคโนโลยีสมัยใหม่
                </div>
            </div>

            <div class="physics-card waves">
                <div class="card-icon">🌊</div>
                <div class="card-title">คลื่นและการสั่นสะเทือน</div>
                <div class="card-description">
                    ศึกษาคลื่นกล คลื่นเสียง คลื่นแม่เหล็กไฟฟ้า การสั่นสะเทือน การแทรกสอด การเลี้ยวเบน และปรากฏการณ์ดอปเปลอร์
                </div>
            </div>
        </div>

        <div class="formula-section">
            <div class="formula-title">🧮 สูตรสำคัญทางฟิสิกส์</div>
            <div class="formula-grid">
                <div class="formula-card">
                    <div class="formula">F = ma</div>
                    <div class="formula-name">กฎข้อที่ 2 ของนิวตัน</div>
                </div>
                <div class="formula-card">
                    <div class="formula">E = mc²</div>
                    <div class="formula-name">สมการของไอน์สไตน์</div>
                </div>
                <div class="formula-card">
                    <div class="formula">P = IV</div>
                    <div class="formula-name">กำลังไฟฟ้า</div>
                </div>
                <div class="formula-card">
                    <div class="formula">v = fλ</div>
                    <div class="formula-name">ความเร็วคลื่น</div>
                </div>
                <div class="formula-card">
                    <div class="formula">PV = nRT</div>
                    <div class="formula-name">กฎของแก๊สอุดมคติ</div>
                </div>
                <div class="formula-card">
                    <div class="formula">KE = ½mv²</div>
                    <div class="formula-name">พลังงานจลน์</div>
                </div>
            </div>
        </div>

        <div class="interactive-demo">
            <div class="demo-title">🎯 การสาธิตโต้ตอบ</div>
            <p style="color: white; margin-bottom: 20px;">ลูกตุ้มอย่างง่าย - แสดงการแกว่งไปมา</p>
            <div class="pendulum-container">
                <div class="pendulum"></div>
            </div>
            <p style="color: rgba(255,255,255,0.8); font-size: 0.9em;">
                ลูกตุ้มแสดงให้เห็นการเปลี่ยนแปลงระหว่างพลังงานศักย์และพลังงานจลน์
            </p>
        </div>

        <div class="fun-facts">
            <div class="facts-title">💡 ข้อเท็จจริงน่าสนใจ</div>
            <div class="fact-item">
                <strong>🚀 ความเร็วแสง:</strong> แสงเดินทางด้วยความเร็ว 299,792,458 เมตรต่อวินาที ซึ่งเป็นความเร็วสูงสุดในจักรวาล
            </div>
            <div class="fact-item">
                <strong>🌡️ ศูนย์สัมบูรณ์:</strong> อุณหภูมิต่ำสุดที่เป็นไปได้คือ -273.15°C หรือ 0 เคลวิน ซึ่งการเคลื่อนที่ของอนุภาคจะหยุดนิ่ง
            </div>
            <div class="fact-item">
                <strong>⚡ ฟ้าผา:</strong> ฟ้าผามีอุณหภูมิสูงกว่าพื้นผิวดวงอาทิตย์ถึง 5 เท่า และมีแรงดันไฟฟ้าสูงถึง 1 พันล้านโวลต์
            </div>
            <div class="fact-item">
                <strong>🌊 คลื่นเสียง:</strong> เสียงเดินทางเร็วกว่าในของแข็งมากกว่าในอากาศ เช่น ในเหล็กเร็วกว่าในอากาศประมาณ 17 เท่า
            </div>
        </div>
    </div>

    <script>
        // สร้างอนุภาคลอยตัว
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 50;

            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 6 + 's';
                particle.style.animationDuration = (Math.random() * 3 + 3) + 's';
                particlesContainer.appendChild(particle);
            }
        }

        // เพิ่มเอฟเฟกต์เมื่อคลิกการ์ด
        document.querySelectorAll('.physics-card').forEach(card => {
            card.addEventListener('click', function() {
                this.style.transform = 'scale(0.95)';
                setTimeout(() => {
                    this.style.transform = '';
                }, 150);
            });
        });

        // เริ่มต้นอนุภาค
        createParticles();

        // ตรวจสอบว่าอยู่ใน Glide App หรือไม่
        const isInGlideApp = window.parent !== window || window.frameElement;
        
        if (isInGlideApp) {
            // ปรับแต่งสำหรับ Glide App
            document.body.style.margin = '0';
            document.body.style.padding = '5px';
            
            // ลบ particle effects บน mobile ใน Glide เพื่อประสิทธิภาพ
            if (window.innerWidth < 768) {
                document.getElementById('particles').style.display = 'none';
            }
        }

        // เพิ่มเอฟเฟกต์เมาส์ (เฉพาะบน desktop)
        if (window.innerWidth > 768) {
            document.addEventListener('mousemove', function(e) {
                const cards = document.querySelectorAll('.physics-card');
                const mouseX = e.clientX;
                const mouseY = e.clientY;

                cards.forEach(card => {
                    const rect = card.getBoundingClientRect();
                    const cardX = rect.left + rect.width / 2;
                    const cardY = rect.top + rect.height / 2;
                    
                    const angle = Math.atan2(mouseY - cardY, mouseX - cardX);
                    const distance = Math.min(Math.sqrt(Math.pow(mouseX - cardX, 2) + Math.pow(mouseY - cardY, 2)), 100);
                    
                    const rotateX = (mouseY - cardY) / 10;
                    const rotateY = (cardX - mouseX) / 10;
                    
                    if (distance < 200) {
                        card.style.transform = `perspective(1000px) rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale(1.02)`;
                    } else {
                        card.style.transform = '';
                    }
                });
            });
        }
    </script>
</body>
</html>
