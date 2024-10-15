<html lang="pl">
<head>
    <meta charset="UTF-8">
    <title>Wyświetlanie treści Markdown z GitHub</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/github-markdown-css/5.1.0/github-markdown.min.css">
    <style>
        .markdown-body {
            box-sizing: border-box;
            min-width: 200px;
            max-width: 980px;
            margin: 0 auto;
            padding: 45px;
        }
    </style>
</head>
<body>
    <div id="markdown-content" class="markdown-body"></div>
    <script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
    <script>
        document.addEventListener('DOMContentLoaded', function () {
            fetch('https://raw.githubusercontent.com/Tusonic/Linux/main/mysql.md')
                .then(response => response.text())
                .then(text => {
                    document.getElementById('markdown-content').innerHTML = marked.parse(text);
                })
                .catch(err => console.error('Error fetching markdown:', err));
        });
    </script>
</body>
</html>