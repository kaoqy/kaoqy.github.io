---
date: '2025-01-04T13:32:44.590708+08:00'
title: 应用
updated: '2025-01-04T13:32:45.945+08:00'
---
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>跳转示例</title>
    <style>
        body {
             font-family: sans-serif; /* 使用更现代的字体 */
            display: flex;
            flex-direction: column; /* 让链接垂直排列 */
            align-items: center; /* 水平居中链接 */
            margin-top: 50px;/* 顶部添加一些边距，更好看 */
        }
        a {
            display: inline-block; /* 让 a 标签可以设置 padding 和 margin */
            padding: 12px 24px;
            margin-bottom: 10px;
            text-decoration: none;
            color: white; /* 按钮文字颜色为白色 */
            background-color: #3498db; /* 按钮默认背景颜色 */
            border-radius: 5px;
            transition: background-color 0.3s ease;
            border: none; /* 移除边框 */
            cursor: pointer; /* 鼠标悬浮时显示为手势 */
        }
        a:hover {
            background-color: #2980b9; /* 鼠标悬浮时颜色略微变深 */
        }
    </style>
</head>
<body>
    <a href="/talks">说说</a>
    <a href="/visitor">访客统计</a>
</body>
</html>
