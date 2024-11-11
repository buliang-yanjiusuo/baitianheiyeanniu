# 手把手教你怎么给静态网页添加白天黑夜按钮步骤及代码

要在静态网页中添加一个白天/黑夜模式切换按钮，你需要通过JavaScript来控制页面的样式，并利用CSS来实现白天和黑夜模式的不同外观。以下是添加该功能的步骤及代码：

### 步骤：
1. **HTML部分**：添加一个按钮来切换白天和黑夜模式。
2. **CSS部分**：为白天和黑夜模式定义不同的样式（如背景色、文本颜色等）。
3. **JavaScript部分**：通过点击按钮切换模式，并存储用户的选择，以便刷新页面后记住用户的偏好。

### 完整代码示例：

```html
<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="白天黑夜模式切换功能，提供用户舒适的浏览体验。">
    <meta name="keywords" content="白天模式, 黑夜模式, 切换按钮, 网站主题">
    <meta name="author" content="您的名字">
    <title>白天黑夜模式切换</title>
    <style>
        /* 基本页面样式 */
        body {
            font-family: Arial, sans-serif;
            transition: background-color 0.3s, color 0.3s;
        }

        /* 白天模式样式 */
        .day-mode {
            background-color: #ffffff;
            color: #333333;
        }

        /* 黑夜模式样式 */
        .night-mode {
            background-color: #121212;
            color: #f0f0f0;
        }

        /* 切换按钮样式 */
        #mode-toggle-btn {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 10px 20px;
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }

        #mode-toggle-btn:hover {
            background-color: #0056b3;
        }

        /* 页面内容样式 */
        .container {
            padding: 20px;
            text-align: center;
        }

        h1 {
            font-size: 36px;
        }

        p {
            font-size: 18px;
        }
    </style>
</head>
<body class="day-mode">

    <button id="mode-toggle-btn">切换到黑夜模式</button>

    <div class="container">
        <h1>欢迎来到白天黑夜模式切换网页</h1>
        <p>点击按钮切换白天和黑夜模式。</p>
    </div>

    <script>
        // 获取按钮元素
        const modeToggleBtn = document.getElementById('mode-toggle-btn');
        const body = document.body;

        // 判断本地存储中是否有用户的主题偏好
        const savedMode = localStorage.getItem('theme');
        if (savedMode) {
            body.className = savedMode; // 设置页面模式
            updateButtonText(savedMode); // 更新按钮文本
        }

        // 切换模式函数
        function toggleMode() {
            if (body.classList.contains('day-mode')) {
                body.className = 'night-mode';  // 切换到黑夜模式
                localStorage.setItem('theme', 'night-mode'); // 保存到本地存储
                updateButtonText('night-mode');
            } else {
                body.className = 'day-mode';   // 切换到白天模式
                localStorage.setItem('theme', 'day-mode'); // 保存到本地存储
                updateButtonText('day-mode');
            }
        }

        // 更新按钮文本
        function updateButtonText(mode) {
            if (mode === 'night-mode') {
                modeToggleBtn.textContent = '切换到白天模式';
            } else {
                modeToggleBtn.textContent = '切换到黑夜模式';
            }
        }

        // 为按钮添加点击事件
        modeToggleBtn.addEventListener('click', toggleMode);
    </script>

</body>
</html>
```

### 代码说明：
1. **HTML部分**：
   - 在页面中添加了一个按钮 (`<button id="mode-toggle-btn">`) 用于切换白天和黑夜模式。
   - 页面中有一个`<div class="container">`，显示标题和一些文本。

2. **CSS部分**：
   - `.day-mode` 和 `.night-mode` 定义了白天模式和黑夜模式的不同样式。例如，背景色和文本颜色分别不同。
   - `#mode-toggle-btn` 是切换按钮的样式，设置了位置、大小、颜色等。

3. **JavaScript部分**：
   - `toggleMode`函数通过判断当前模式来切换白天或黑夜模式，并将用户的选择保存到`localStorage`中。
   - 页面加载时，检查`localStorage`中是否有存储的主题（如果有，自动应用）。
   - 切换按钮的文本会根据当前模式进行更新。

### 说明：
- **`localStorage`**：使用`localStorage`来保存用户的主题选择，这样即使页面刷新或用户重新访问时，也能保留他们上次的模式偏好。
- **`transition`**：为了让切换效果更加流畅，使用了`transition`来平滑地改变背景色和文字颜色。

通过这种方式，你可以轻松实现一个白天/黑夜模式切换功能，提升用户体验。
