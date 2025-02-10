---
date: '2025-01-25T18:43:50.730170+08:00'
title: 必应壁纸
updated: '2025-02-07T21:25:11.000000+08:00'
---
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bing 每日一图</title>
    <style>
        /* 全局样式 */
        body {
            font-family: "Arial", sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            margin: 20px;
            padding: 0;
        }

        h1 {
            font-size: 28px;
            color: #333;
            margin-bottom: 15px;
        }

        /* 图片展示区域 */
        .gallery {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            max-width: 1200px;
            margin: auto;
            padding: 10px;
        }

        /* 图片卡片 */
        .image-card {
            width: 30%;
            background: linear-gradient(135deg, #ffffff, #f8f8f8);
            border-radius: 12px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            padding: 10px;
            transition: transform 0.3s, box-shadow 0.3s;
            overflow: hidden;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 0.5s forwards;
        }

        .image-card:hover {
            transform: scale(1.05);
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
        }

        /* 图片 */
        .image-card img {
            width: 100%;
            height: auto;
            border-radius: 8px;
            transition: opacity 0.3s ease-in-out;
        }

        /* 日期样式 */
        .date {
            font-size: 14px;
            color: #666;
            margin-top: 8px;
            font-weight: bold;
        }

        /* 响应式布局 */
        @media (max-width: 768px) {
            .image-card {
                width: 45%;
            }
        }

        @media (max-width: 480px) {
            .image-card {
                width: 100%;
            }
        }

        /* 动画效果 */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
    </style>
</head>
<body>

    <h1>Bing 每日一图</h1>
    <div class="gallery" id="gallery"></div>

    <script>
        async function fetchBingImages() {
            try {
                const response = await fetch("https://bing.kaoqy.me/urls.txt", { cache: "no-store" });
                if (!response.ok) throw new Error("无法获取图片数据");

                const text = await response.text();
                let images = text.trim().split("\n").map(line => {
                    let [date, url] = line.split(" ");
                    return { date, url };
                });

                // 按日期降序排列（最新的图片在最上方）
                images.sort((a, b) => b.date.localeCompare(a.date));

                const gallery = document.getElementById("gallery");
                images.forEach((image, index) => {
                    let card = document.createElement("div");
                    card.className = "image-card";
                    card.style.animationDelay = `${index * 0.1}s`; // 添加动画延迟

                    card.innerHTML = `
                        <img src="${image.url}" alt="Bing ${image.date}" loading="lazy">
                        <div class="date">${image.date}</div>
                    `;
                    gallery.appendChild(card);
                });

            } catch (error) {
                console.error("获取图片数据失败", error);
            }
        }

        fetchBingImages();
    </script>

</body>
</html>
