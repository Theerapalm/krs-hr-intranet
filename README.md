<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>K.R.S. HR Intranet</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: 
                radial-gradient(circle at 20% 80%, rgba(255, 107, 107, 0.3) 0%, transparent 50%),
                radial-gradient(circle at 80% 20%, rgba(205, 133, 63, 0.2) 0%, transparent 50%),
                radial-gradient(circle at 40% 40%, rgba(139, 69, 19, 0.1) 0%, transparent 50%),
                linear-gradient(135deg, #d63031 0%, #e17055 25%, #fd79a8 50%, #fdcb6e 75%, #e84393 100%);
            background-size: 100% 100%, 100% 100%, 100% 100%, 100% 100%;
            background-attachment: fixed;
            min-height: 100vh;
            padding: 15px;
            position: relative;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" fill="rgba(139,69,19,0.03)"><circle cx="20" cy="20" r="2"/><circle cx="80" cy="80" r="1.5"/><circle cx="60" cy="30" r="1"/><circle cx="30" cy="70" r="1.5"/><circle cx="90" cy="40" r="1"/><circle cx="10" cy="90" r="2"/></svg>');
            background-size: 200px 200px;
            animation: float 20s ease-in-out infinite;
            pointer-events: none;
            z-index: -1;
        }

        body::after {
            content: '';
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 100px;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 50" fill="rgba(139,69,19,0.05)"><text x="20" y="25" font-size="16" font-family="serif">เจ๊เล็ก</text><text x="120" y="35" font-size="12">คลองรังสิต</text><text x="220" y="25" font-size="14">40+ ปี</text><text x="300" y="35" font-size="12">OEM</text></svg>');
            background-repeat: repeat-x;
            opacity: 0.3;
            pointer-events: none;
            z-index: -1;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            33% { transform: translateY(-10px) rotate(1deg); }
            66% { transform: translateY(5px) rotate(-1deg); }
        }

        .container {
            max-width: 1000px;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 15px;
            box-shadow: 
                0 8px 32px rgba(0, 0, 0, 0.1),
                0 0 0 1px rgba(255, 255, 255, 0.2);
            overflow: hidden;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.18);
        }

        .header {
            background: linear-gradient(135deg, #d63031 0%, #e17055 50%, #8b4513 100%);
            color: white;
            padding: 20px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '🌶️';
            position: absolute;
            font-size: 3rem;
            top: -10px;
            right: 20px;
            opacity: 0.2;
            animation: spiceFloat 3s ease-in-out infinite;
        }

        .header::after {
            content: 'เจ๊เล็ก';
            position: absolute;
            font-size: 0.8rem;
            bottom: 5px;
            right: 30px;
            opacity: 0.4;
            color: rgba(255, 255, 255, 0.7);
            font-style: italic;
        }

        @keyframes spiceFloat {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-5px) rotate(5deg); }
        }

        .header-left {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo-icon {
            width: 60px;
            height: 50px;
            background: rgba(255, 255, 255, 0.15);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
            padding: 5px;
        }

        .logo-icon img {
            width: 100%;
            height: auto;
            object-fit: contain;
            border-radius: 4px;
            filter: brightness(1.1) contrast(1.1);
        }

        /* ถ้าไม่มีรูป จะแสดง K.R.S. */
        .logo-icon::before {
            content: 'K.R.S.';
            position: absolute;
            font-size: 1.1rem;
            font-weight: bold;
            color: #d63031;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.3);
            animation: logoGlow 3s ease-in-out infinite;
        }

        .logo-icon:has(img)::before {
            display: none;
        }

        @keyframes logoGlow {
            0%, 100% { opacity: 0.8; transform: scale(1); }
            50% { opacity: 1; transform: scale(1.05); }
        }

        /* สไตล์สำหรับภาพพื้นหลัง */
        .background-image {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            opacity: 0.03;
            z-index: -2;
            object-fit: cover;
        }

        /* สไตล์สำหรับโลโก้ในโมดูล */
        .module-icon img {
            width: 35px;
            height: 35px;
            object-fit: contain;
        }

        /* เพิ่มสไตล์สำหรับ logo ขนาดใหญ่ในหน้าหลัก */
        .main-logo {
            width: 120px;
            height: auto;
            opacity: 0.1;
            position: absolute;
            top: 20px;
            right: 20px;
            z-index: 0;
        }

        .header-title {
            font-size: 1.8rem;
            font-weight: 600;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        .header-subtitle {
            font-size: 0.9rem;
            opacity: 0.9;
            margin-top: 2px;
        }

        .header-subtitle::after {
            content: ' • Spicy Food Manufacturing';
            font-weight: 500;
            opacity: 0.9;
        }

        .header-right {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .contact-hr-btn {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .contact-hr-btn:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-1px);
        }

        .main-content {
            padding: 30px;
            background: 
                radial-gradient(circle at 10% 20%, rgba(255, 107, 107, 0.05) 0%, transparent 40%),
                radial-gradient(circle at 90% 80%, rgba(238, 90, 36, 0.05) 0%, transparent 40%),
                #f8f9fa;
            position: relative;
        }

        .main-content::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background-image: 
                url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" fill="rgba(255,107,107,0.03)"><text x="10" y="20" font-size="12">🌶️</text><text x="70" y="60" font-size="8">🔥</text><text x="30" y="80" font-size="10">🌶️</text></svg>');
            background-size: 300px 300px;
            pointer-events: none;
        }

        .top-section {
            display: grid;
            grid-template-columns: 2fr 1fr;
            gap: 20px;
            margin-bottom: 25px;
        }

        .main-panel {
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            border-radius: 12px;
            padding: 30px;
            color: white;
            position: relative;
            overflow: hidden;
        }

        .main-panel::before {
            content: '🥄';
            position: absolute;
            font-size: 8rem;
            top: -20px;
            right: -20px;
            opacity: 0.1;
            transform: rotate(-15deg);
        }

        .main-panel::after {
            content: 'เจ๊เล็ก';
            position: absolute;
            font-size: 2rem;
            bottom: -5px;
            left: 20px;
            opacity: 0.15;
            font-style: italic;
            color: rgba(255, 255, 255, 0.3);
        }

        .main-title {
            font-size: 1.6rem;
            font-weight: 600;
            margin-bottom: 10px;
            position: relative;
            z-index: 1;
        }

        .main-description {
            font-size: 1rem;
            opacity: 0.9;
            line-height: 1.5;
            position: relative;
            z-index: 1;
        }

        .login-panel {
            background: white;
            border-radius: 12px;
            padding: 25px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
        }

        .login-title {
            color: #2d3436;
            font-size: 1.2rem;
            font-weight: 600;
            margin-bottom: 20px;
            text-align: center;
        }

        .login-form {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .form-group {
            display: flex;
            flex-direction: column;
            gap: 5px;
        }

        .form-label {
            color: #636e72;
            font-size: 0.9rem;
            font-weight: 500;
        }

        .form-input {
            padding: 12px;
            border: 2px solid #e9ecef;
            border-radius: 8px;
            font-size: 0.95rem;
            transition: border-color 0.3s ease;
        }

        .form-input:focus {
            outline: none;
            border-color: #d63031;
            box-shadow: 0 0 0 3px rgba(214, 48, 49, 0.1);
        }

        .login-btn {
            background: linear-gradient(135deg, #d63031, #e17055);
            color: white;
            padding: 12px;
            border: none;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-top: 10px;
            position: relative;
            overflow: hidden;
        }

        .login-btn::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 50%;
            transform: translate(-50%, -50%);
            transition: all 0.3s ease;
        }

        .login-btn:hover {
            transform: translateY(-1px);
            box-shadow: 0 4px 15px rgba(214, 48, 49, 0.4);
        }

        .login-btn:hover::before {
            width: 300px;
            height: 300px;
        }

        .modules-section {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 25px;
        }

        .module-card {
            background: white;
            border-radius: 12px;
            padding: 20px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
            transition: all 0.3s ease;
            cursor: pointer;
            text-align: center;
            border-top: 4px solid var(--module-color);
        }

        .module-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.12);
        }

        .module-card.knowledge {
            --module-color: #d63031;
        }

        .module-card.employee {
            --module-color: #e17055;
        }

        .module-card.organization {
            --module-color: #8b4513;
        }

        .module-card.learning {
            --module-color: #cd853f;
        }

        .module-card.job {
            --module-color: #d63031;
        }

        .module-card.dashboard {
            --module-color: #a0522d;
        }

        .module-card.safety {
            --module-color: #e17055;
        }

        .module-card.events {
            --module-color: #cd853f;
        }

        .module-icon {
            width: 60px;
            height: 60px;
            margin: 0 auto 15px;
            background: var(--module-color);
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            color: white;
        }

        .module-title {
            color: #2d3436;
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 8px;
        }

        .module-subtitle {
            color: #636e72;
            font-size: 0.85rem;
            line-height: 1.4;
        }

        .bottom-section {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
        }

        .info-panel {
            background: white;
            border-radius: 12px;
            padding: 20px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
        }

        .panel-title {
            color: #2d3436;
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .panel-content {
            color: #636e72;
            font-size: 0.9rem;
            line-height: 1.5;
        }

        .news-item {
            padding: 12px 0;
            border-bottom: 1px solid #e9ecef;
            display: flex;
            align-items: center;
            gap: 12px;
            cursor: pointer;
            transition: background-color 0.2s ease;
        }

        .news-item:hover {
            background-color: #f8f9fa;
            border-radius: 6px;
            padding: 12px;
        }

        .news-item:last-child {
            border-bottom: none;
        }

        .news-date {
            background: linear-gradient(135deg, #d63031, #e17055);
            color: white;
            padding: 4px 8px;
            border-radius: 6px;
            font-size: 0.8rem;
            font-weight: 500;
            min-width: 60px;
            text-align: center;
        }

        .news-text {
            flex: 1;
            color: #2d3436;
            font-size: 0.9rem;
        }

        .footer {
            background: linear-gradient(135deg, #2d3436, #636e72);
            color: white;
            text-align: center;
            padding: 15px;
            font-size: 0.85rem;
            position: relative;
        }

        .footer::before {
            content: '🌶️ จากครัวเจ๊เล็ก สู่โรงงานระดับโลก • 40+ Years of Excellence 🏆';
            position: absolute;
            top: -25px;
            left: 50%;
            transform: translateX(-50%);
            background: rgba(214, 48, 49, 0.9);
            color: white;
            padding: 5px 15px;
            border-radius: 15px;
            font-size: 0.75rem;
            font-weight: 500;
            white-space: nowrap;
        }

        @media (max-width: 768px) {
            .container {
                margin: 10px;
            }
            
            .header {
                flex-direction: column;
                gap: 15px;
                text-align: center;
            }
            
            .main-content {
                padding: 20px;
            }
            
            .top-section {
                grid-template-columns: 1fr;
            }
            
            .modules-section {
                grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
                gap: 15px;
            }
            
            .bottom-section {
                grid-template-columns: 1fr;
            }
        }

        .status-indicator {
            position: absolute;
            top: 15px;
            right: 15px;
            width: 12px;
            height: 12px;
            background: #d63031;
            border-radius: 50%;
            border: 2px solid white;
            animation: traditionalPulse 2s infinite;
        }

        @keyframes traditionalPulse {
            0% { 
                opacity: 1; 
                box-shadow: 0 0 0 0 rgba(214, 48, 49, 0.7);
            }
            70% { 
                opacity: 0.7; 
                box-shadow: 0 0 0 10px rgba(214, 48, 49, 0);
            }
            100% { 
                opacity: 1; 
                box-shadow: 0 0 0 0 rgba(214, 48, 49, 0);
            }
        }

        .search-section {
            background: white;
            border-radius: 12px;
            padding: 15px;
            margin-bottom: 20px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
        }

        .search-input {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e9ecef;
            border-radius: 25px;
            font-size: 0.95rem;
            transition: border-color 0.3s ease;
        }

        .search-input:focus {
            outline: none;
            border-color: #d63031;
            box-shadow: 0 0 0 3px rgba(214, 48, 49, 0.1);
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- เพิ่มภาพพื้นหลัง (ทางเลือก) -->
        <!-- <img src="images/spicy-background.jpg" alt="Spicy Food Background" class="background-image"> -->
        
        <!-- Header Section -->
        <header class="header">
            <div class="header-left">
                <div class="logo-icon">
                    <!-- วางโลโก้ K.R.S. ตรงนี้ -->
                    <!-- <img src="krs-logo.png" alt="K.R.S. Logo"> -->
                    <!-- หรือใช้ base64 ของรูปที่ upload -->
                </div>
                <div>
                    <div class="header-title">K.R.S.</div>
                    <div class="header-subtitle">e-Learning</div>
                </div>
            </div>
            <div class="header-right">
                <button class="contact-hr-btn" onclick="contactHR()">
                    📞 Contact HR
                </button>
            </div>
        </header>

        <!-- Main Content -->
        <main class="main-content">
            <!-- Search Section -->
            <div class="search-section">
                <input type="text" class="search-input" placeholder="🔍 ค้นหาข้อมูล หลักสูตร หรือเอกสาร...">
            </div>

            <!-- Top Section -->
            <div class="top-section">
                <div class="main-panel">
                    <div class="status-indicator"></div>
                    <!-- โลโก้ใหญ่ในพื้นหลัง -->
                    <!-- <img src="krs-logo.png" alt="K.R.S." class="main-logo"> -->
                    <div class="main-title">home</div>
                    <div class="main-description">
                        ยินดีต้อนรับสู่ระบบ e-Learning ของบริษัท K.R.S.<br>
                        🌶️ <strong>Spicy Food Co., Ltd.</strong> 🔥<br>
                        <small style="opacity: 0.8;">ผู้เชี่ยวชาญด้านซอสและน้ำพริกแกงไทยมากกว่า 40 ปี</small><br>
                        <small style="opacity: 0.9;">เจ๊เล็ก • คลองรังสิต • OEM Manufacturing</small><br>
                        <small>Job description • Orientation • e-learning</small>
                    </div>
                </div>

                <div class="login-panel">
                    <div class="login-title">เข้าสู่ระบบ</div>
                    <form class="login-form">
                        <div class="form-group">
                            <label class="form-label">Username</label>
                            <input type="text" class="form-input" placeholder="รหัสพนักงาน">
                        </div>
                        <div class="form-group">
                            <label class="form-label">Password</label>
                            <input type="password" class="form-input" placeholder="รหัสผ่าน">
                        </div>
                        <button type="submit" class="login-btn">เข้าสู่ระบบ</button>
                    </form>
                </div>
            </div>

            <!-- Modules Section -->
            <div class="modules-section">
                <div class="module-card knowledge" onclick="openModule('knowledge')">
                    <div class="module-icon">
                        <!-- <img src="images/knowledge-icon.png" alt="Knowledge"> -->
                        📚
                    </div>
                    <div class="module-title">Knowledge Update</div>
                    <div class="module-subtitle">ข่าวสาร ความรู้ และนโยบายใหม่</div>
                </div>

                <div class="module-card employee" onclick="openModule('employee')">
                    <div class="module-icon">
                        <!-- <img src="images/employee-icon.png" alt="Employee"> -->
                        👥
                    </div>
                    <div class="module-title">Employee Dashboard</div>
                    <div class="module-subtitle">ข้อมูลส่วนตัว และประวัติการทำงาน</div>
                </div>

                <div class="module-card organization" onclick="openModule('organization')">
                    <div class="module-icon">
                        <!-- <img src="images/organization-icon.png" alt="Organization"> -->
                        🏗️
                    </div>
                    <div class="module-title">Organization</div>
                    <div class="module-subtitle">โครงสร้างองค์กร และข้อมูลแผนก</div>
                </div>

                <div class="module-card learning" onclick="openModule('learning')">
                    <div class="module-icon">
                        <!-- <img src="images/learning-icon.png" alt="Learning"> -->
                        🎓
                    </div>
                    <div class="module-title">e-Learning</div>
                    <div class="module-subtitle">หลักสูตรอบรม และการพัฒนาทักษะ</div>
                </div>

                <div class="module-card job" onclick="openModule('job')">
                    <div class="module-icon">
                        <!-- <img src="images/job-icon.png" alt="Job Description"> -->
                        📋
                    </div>
                    <div class="module-title">Job Description</div>
                    <div class="module-subtitle">คำอธิบายงาน และหน้าที่รับผิดชอบ</div>
                </div>

                <div class="module-card dashboard" onclick="openModule('dashboard')">
                    <div class="module-icon">
                        <!-- <img src="images/dashboard-icon.png" alt="Dashboard"> -->
                        📊
                    </div>
                    <div class="module-title">Dashboard</div>
                    <div class="module-subtitle">ภาพรวมข้อมูล และรายงานสำคัญ</div>
                </div>

                <div class="module-card safety" onclick="openModule('safety')">
                    <div class="module-icon">
                        <!-- <img src="images/safety-icon.png" alt="Safety"> -->
                        🦺
                    </div>
                    <div class="module-title">Safety Manual</div>
                    <div class="module-subtitle">คู่มือความปลอดภัย และมาตรฐาน</div>
                </div>

                <div class="module-card events" onclick="openModule('events')">
                    <div class="module-icon">
                        <!-- <img src="images/events-icon.png" alt="Events"> -->
                        📅
                    </div>
                    <div class="module-title">News & Events</div>
                    <div class="module-subtitle">ข่าวสาร กิจกรรม และประกาศ</div>
                </div>
            </div>

            <!-- Bottom Section -->
            <div class="bottom-section">
                <div class="info-panel">
                    <div class="panel-title">
                        📢 ข่าวสารและประกาศ
                    </div>
                    <div class="panel-content">
                        <div class="news-item">
                            <div class="news-date">19 มิ.ย.</div>
                            <div class="news-text">อัพเดทมาตรฐาน GMP และ HACCP ปี 2025</div>
                        </div>
                        <div class="news-item">
                            <div class="news-date">18 มิ.ย.</div>
                            <div class="news-text">หลักสูตรอบรม: การควบคุมคุณภาพอาหาร</div>
                        </div>
                        <div class="news-item">
                            <div class="news-date">17 มิ.ย.</div>
                            <div class="news-text">ประกาศ: รางวัล Top Thai Brand 2025</div>
                        </div>
                    </div>
                </div>

                <div class="info-panel">
                    <div class="panel-title">
                        🔗 ลิงก์ที่เป็นประโยชน์
                    </div>
                    <div class="panel-content">
                        <div class="news-item">
                            <div class="news-text">📋 คู่มือการผลิตซอสและน้ำพริกแกง</div>
                        </div>
                        <div class="news-item">
                            <div class="news-text">🌶️ สูตรต้นตำรับเจ๊เล็ก</div>
                        </div>
                        <div class="news-item">
                            <div class="news-text">🏭 มาตรฐาน OEM Manufacturing</div>
                        </div>
                        <div class="news-item">
                            <div class="news-text">📞 ติดต่อฝ่าย Quality Control</div>
                        </div>
                    </div>
                </div>
            </div>
        </main>

        <!-- Footer -->
        <footer class="footer">
            &copy; 2025 บริษัท K.R.S. Spicy Food Co., Ltd. - ระบบ e-Learning และ HR Management
        </footer>
    </div>

    <script>
        function contactHR() {
            alert('📞 เปิดช่องทางติดต่อฝ่าย HR\n\n- โทรศัพท์: 02-xxx-xxxx\n- อีเมล: hr@krs.com\n- Line Official: @krs-hr');
        }

        function openModule(moduleName) {
            const messages = {
                'knowledge': '📚 เข้าสู่ระบบอัพเดทความรู้และข่าวสาร',
                'employee': '👥 เปิดแดชบอร์ดข้อมูลพนักงาน',
                'organization': '🏗️ ดูโครงสร้างองค์กรและข้อมูลแผนก',
                'learning': '🎓 เข้าสู่ระบบ e-Learning และหลักสูตรอบรม',
                'job': '📋 เข้าสู่ระบบดูคำอธิบายงานและหน้าที่รับผิดชอบ',
                'dashboard': '📊 เปิดแดชบอร์ดและรายงานสำคัญ',
                'safety': '🦺 เปิดคู่มือความปลอดภัยและมาตรฐาน',
                'events': '📅 ดูข่าวสาร กิจกรรม และประกาศใหม่'
            };
            
            alert(messages[moduleName] || 'เปิดโมดูล');
            
            // เพิ่มเอฟเฟกต์การคลิก
            if (event.target.closest('.module-card')) {
                event.target.closest('.module-card').style.transform = 'scale(0.95)';
                setTimeout(() => {
                    event.target.closest('.module-card').style.transform = '';
                }, 150);
            }
        }

        // ฟังก์ชันเข้าสู่ระบบ
        document.querySelector('.login-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const username = this.querySelector('input[type="text"]').value;
            const password = this.querySelector('input[type="password"]').value;
            
            if (username && password) {
                alert(`✅ เข้าสู่ระบบสำเร็จ!\nยินดีต้อนรับ: ${username}`);
                // ในระบบจริงจะเชื่อมต่อกับ backend
            } else {
                alert('❌ กรุณากรอกข้อมูลให้ครบถ้วน');
            }
        });

        // ฟังก์ชันค้นหา
        document.querySelector('.search-input').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                const searchTerm = this.value.trim();
                if (searchTerm) {
                    alert(`🔍 ค้นหา: "${searchTerm}"\n\nระบบจะแสดงผลลัพธ์ที่เกี่ยวข้อง`);
                }
            }
        });

        // เพิ่มการโต้ตอบเมื่อคลิกข่าวสาร
        document.querySelectorAll('.news-item').forEach(item => {
            item.addEventListener('click', function() {
                const newsText = this.querySelector('.news-text').textContent;
                alert(`📰 ${newsText}\n\nคลิกเพื่อดูรายละเอียดเพิ่มเติม`);
            });
        });
    </script>
</body>
</html># krs-hr-intranet
