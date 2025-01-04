---
date: '2025-01-04T13:29:29.405551+08:00'
title: title
updated: '2025-01-04T13:29:30.770+08:00'
---
<!DOCTYPE html>
<html lang="zh-CN">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>网站统计</title>
    <style>
        body {
             font-family: sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
              margin-top: 30px;
        }

        .statistic-container {
            width: 80%; /* 限定宽度 */
            max-width: 500px;
            background-color: #f9f9f9;
            margin-bottom: 20px;
              padding: 20px;
            border-radius: 8px;
             box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        }

        .statistic-item {
            display: flex;
            justify-content: space-between; /* 两端对齐 */
            align-items: baseline;
            margin-bottom: 10px;
            padding-bottom:5px;
             border-bottom: #eee 1px dotted;

        }

            .statistic-item:last-child {
          margin-bottom:0;
           border-bottom:none;

        }

        .statistic-item span {
            font-weight: bold;
            color:#555;
        }


         .loading {
            color: #999;
            font-style: italic;
        }

        .error {
            color: #f44336;
        }
         .metric-label {
            font-weight: normal;
             color: #777;
         }
    </style>
</head>
<body>
    <div class="statistic-container">
        <div class="statistic-item">
            <span class="metric-label">站点访问量:</span>
            <span id="qexo-site-pv" class="loading">Loading...</span>
        </div>
        <div class="statistic-item">
            <span class="metric-label">站点访客数:</span>
            <span id="qexo-site-uv" class="loading">Loading...</span>
        </div>
        <div class="statistic-item">
            <span class="metric-label">页面访问量:</span>
            <span id="qexo-page-pv" class="loading">Loading...</span>
        </div>
    </div>


    <script src="https://cdn.jsdelivr.net/npm/qexo-static@1.6.0/hexo/statistic.js"></script>
    <script>
         function updateStatistics(data) {
            document.getElementById("qexo-site-pv").textContent = data.site_pv;
             document.getElementById("qexo-site-uv").textContent = data.site_uv;
            document.getElementById("qexo-page-pv").textContent = data.page_pv;
        }

        function showError(elem){
             elem.textContent = "加载失败";
             elem.classList.add('error'); // 添加class标记错误
        }

      function loadStatistic (api, elemID) {
            const element = document.getElementById(elemID)

             fetch(api)
             .then(response => {
              if(!response.ok) { throw new Error('Network response was not ok');
           }
                return response.json();
           })
             .then((data)=>{
                console.log(data);
               updateStatistics(data);
           })
              .catch(error => {
                   console.error('There has been a problem with your fetch operation:', error);
                   showError(element);
               });
        }


       const apiUrl = "https://qexo.kaoqy.us.kg"

        loadStatistic(apiUrl,"qexo-site-pv");

       loadStatistic(apiUrl,"qexo-site-uv");

          loadStatistic(apiUrl,"qexo-page-pv");
    </script>
</body>
</html>
