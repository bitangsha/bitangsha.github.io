<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>English to Bengali Dictionary</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
        }
        input {
            padding: 10px;
            width: 300px;
        }
        button {
            padding: 10px;
            cursor: pointer;
        }
        #result {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <h1>English to Bengali Dictionary</h1>
    <input type="text" id="word" placeholder="Enter a word">
    <button onclick="getDefinition()">Search</button>
    <div id="result"></div>

    <script>
        async function getDefinition() {
            const word = document.getElementById('word').value;
            const resultDiv = document.getElementById('result');
            resultDiv.innerHTML = "Loading...";

            try {
                const response = await fetch(`https://api.mymemory.translated.net/get?q=${word}&langpair=en|bn`);
                const data = await response.json();

                if (data.responseData.translatedText) {
                    resultDiv.innerHTML = `<h2>${word}</h2><p>${data.responseData.translatedText}</p>`;
                } else {
                    resultDiv.innerHTML = "No translation found.";
                }
            } catch (error) {
                resultDiv.innerHTML = "Error fetching translation.";
            }
        }
    </script>
</body>
</html>
