<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>API Key VIP</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap');

        body {
            margin: 0;
            font-family: 'Roboto', Arial, sans-serif;
            background: linear-gradient(135deg, #a8e6cf, #88d3ce);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            color: #333;
        }

        header {
            text-align: center;
            padding: 30px 20px;
        }

        h1 {
            font-size: 48px;
            font-weight: 700;
            color: white;
            text-shadow: 0 2px 10px rgba(0,0,0,0.2);
            margin: 0;
        }

        .avatar-container {
            margin: 40px auto;
            width: 180px;
            height: 180px;
            border-radius: 50%;
            overflow: hidden;
            border: 8px solid white;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
        }

        .avatar {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .key-card {
            background: white;
            margin: 20px auto;
            max-width: 500px;
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.15);
            text-align: center;
        }

        .key-card h2 {
            font-size: 24px;
            margin-bottom: 20px;
            color: #444;
        }

        .key-display {
            background: #f0f8ff;
            padding: 20px;
            border-radius: 12px;
            font-size: 28px;
            font-family: monospace;
            letter-spacing: 2px;
            word-break: break-all;
            border: 2px dashed #88d3ce;
            margin-bottom: 20px;
            user-select: all;
            cursor: text;
        }

        .copy-hint {
            font-size: 18px;
            color: #666;
            margin-top: 10px;
        }

        footer {
            text-align: center;
            padding: 20px;
            color: white;
            font-size: 16px;
        }

        footer a {
            color: #ffff66;
            text-decoration: none;
            font-weight: 500;
        }

        @media (max-width: 600px) {
            h1 { font-size: 38px; }
            .avatar-container { width: 140px; height: 140px; }
            .key-display { font-size: 22px; }
        }
    </style>
</head>
<body>
    <header>
        <h1>CẢM ƠN BẠN!</h1>
        <div class="avatar-container">
            <!-- Bạn có thể thay bằng ảnh của mình -->
            <img src="https://sf-static.upanhlaylink.com/img/image_2025122179ba358d668d57ecaa5f0cad9b8a5e37.jpg" alt="Avatar" class="avatar">
        </div>
    </header>

    <main class="key-card">
        <h2>Chúc Bạn Ngày Mới Tốt Lành!</h2>
        <p>API Key ngày <strong>24/12/2025</strong> là:</p>
        
        <div class="key-display" id="apiKey">
            NULL
        </div>
        
        <p class="copy-hint">(Nhấn vào key để sao chép)</p>
    </main>

    <footer>
        Copyright ©2025 | Facebook: <a href="https://facebook.com/yourprofile" target="_blank">Tran Minh Duc</a>
    </footer>

    <script>
        // Đọc key từ URL: ?key=ABC123
        window.onload = function() {
            const params = new URLSearchParams(window.location.search);
            const key = params.get('key');
            
            const keyElement = document.getElementById('apiKey');
            keyElement.textContent = key || 'NULL';  // Nếu không có key thì hiển thị NULL

            // Click để copy tự động
            keyElement.onclick = function() {
                const keyText = this.textContent.trim();
                
                if (navigator.clipboard && keyText !== 'NULL') {
                    navigator.clipboard.writeText(keyText).then(() => {
                        const original = this.textContent;
                        this.textContent = 'Đã copy: ' + keyText;
                        setTimeout(() => {
                            this.textContent = original;
                        }, 2000);
                    }).catch(() => {
                        selectText(this);
                    });
                } else {
                    selectText(this);
                }
            };
        };

        function selectText(element) {
            const range = document.createRange();
            range.selectNodeContents(element);
            const selection = window.getSelection();
            selection.removeAllRanges();
            selection.addRange(range);
        }
    </script>
</body>
</html>
