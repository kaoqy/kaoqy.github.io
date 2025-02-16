---
date: '2025-01-25T18:43:50.730170+08:00'
title: 必应壁纸
updated: '2025-02-07T21:25:11.000000+08:00'
---
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bing 每日一图 - 瀑布流展示</title>
    <link href="https://unpkg.com/masonry-layout@4/dist/masonry.min.css" rel="stylesheet">
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f7f7f7;
            margin: 0;
            padding: 0;
        }
        .container {
            max-width: 1200px;
            margin: 20px auto;
            padding: 20px;
        }
        .grid {
            display: flex;
            flex-wrap: wrap;
            gap: 40px; /* 增加间距 */
        }
        .grid-item {
            width: 32%;
            background-color: #fff;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
            overflow: hidden;
            position: relative;
            transition: transform 0.2s ease-in-out;
        }
        .grid-item:hover {
            transform: translateY(-5px);
        }
        .grid-item img {
            width: 100%;
            height: auto;
            cursor: pointer;
        }
        .grid-item .info {
            padding: 12px;
            text-align: left;
        }
        .grid-item .info h3 {
            margin: 0;
            font-size: 18px;
            color: #333;
        }
        .grid-item .info p {
            color: #555;
            font-size: 14px;
            white-space: pre-wrap; /* 让版权信息换行 */
            line-height: 1.6; /* 增加行距 */
        }
        /* 日期栏 */
        .date-container {
            width: 100%;
            background-color: #fff;
            padding: 10px 15px;
            font-size: 16px;
            font-weight: bold;
            color: #555;
            text-align: left;
            border-radius: 8px 8px 0 0;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }
        /* 复制提示框 */
        .copy-toast {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: rgba(0, 0, 0, 0.7);
            color: #fff;
            padding: 10px 15px;
            border-radius: 5px;
            font-size: 14px;
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Bing 每日一图 - 瀑布流展示</h1>
        <div class="grid" id="grid"></div>
    </div>

    <!-- 复制成功提示 -->
    <div id="copyToast" class="copy-toast">图片 URL 已复制！</div>

    <script src="https://unpkg.com/masonry-layout@4/dist/masonry.pkgd.min.js"></script>
    <script>
        // 从外部 URL 获取 JSON 数据
        fetch('https://bing.kaoqy.me/data.json')
            .then(response => response.json())
            .then(data => {
                // 渲染数据
                const grid = document.getElementById('grid');
                data.forEach(item => {
                    const gridItem = document.createElement('div');
                    gridItem.classList.add('grid-item');
                    gridItem.innerHTML = `
                        <div class="date-container">${item.date}</div>
                        <img src="${item.image_url}" alt="${item.title}" onclick="copyImageUrl('${item.image_url}')">
                        <div class="info">
                            <h3>${item.title}</h3>
                            <p>${item.copyright}</p>
                        </div>
                    `;
                    grid.appendChild(gridItem);
                });

                // 初始化 Masonry 瀑布流布局
                new Masonry(grid, {
                    itemSelector: '.grid-item',
                    columnWidth: '.grid-item',
                    percentPosition: true
                });
            })
            .catch(error => {
                console.error('获取数据失败:', error);
                alert('无法加载数据！');
            });

        // 复制图片 URL 并显示提示框
        function copyImageUrl(url) {
            const tempInput = document.createElement('input');
            document.body.appendChild(tempInput);
            tempInput.value = url;
            tempInput.select();
            document.execCommand('copy');
            document.body.removeChild(tempInput);

            // 显示复制成功提示
            const toast = document.getElementById('copyToast');
            toast.style.display = 'block';
            setTimeout(() => {
                toast.style.display = 'none';
            }, 2000);
        }
    </script>
</body>
</html>
