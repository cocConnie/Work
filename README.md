<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sales Achievement</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            text-align: left;
        }
        .input-group {
            margin-bottom: 10px;
        }
        label {
            font-weight: bold;
        }
        input {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .message {
            padding: 15px;
            border: 2px solid #ddd;
            border-radius: 10px;
            background: #f9f9f9;
            font-size: 18px;
            line-height: 1.6;
            display: none;
        }
        .button-group {
            margin-top: 15px;
        }
        .btn {
            padding: 10px 15px;
            font-size: 16px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
            color: #fff;
        }
        .generate-btn {
            background: #28a745;
        }
        .generate-btn:hover {
            background: #218838;
        }
        .copy-btn {
            background: #007bff;
            display: none;
        }
        .copy-btn:hover {
            background: #0056b3;
        }
        .tooltip {
            display: none;
            margin-left: 10px;
            color: green;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="input-group">
        <label for="name">Name:</label>
        <input type="text" id="name" placeholder="Enter Name">
    </div>
    
    <div class="input-group">
        <label for="product">Product Name:</label>
        <input type="text" id="product" placeholder="Enter Product Name">
    </div>

    <div class="button-group">
        <button class="btn generate-btn" onclick="generateMessage()">Generate Message</button>
    </div>

    <div id="messageBox" class="message">
        <div id="copyContent"></div>
    </div>

    <div class="button-group">
        <button id="copyBtn" class="btn copy-btn" onclick="copyToClipboard()">Copy to Clipboard</button>
        <span id="tooltip" class="tooltip">Copied!</span>
    </div>

    <script>
        function generateMessage() {
            const name = document.getElementById("name").value.trim();
            const product = document.getElementById("product").value.trim();
            const messageBox = document.getElementById("messageBox");
            const copyBtn = document.getElementById("copyBtn");

            if (name === "" || product === "") {
                alert("Please enter both Name and Product Name.");
                return;
            }

            const message = `🎉 Congratulations to ${name} for landing the first ${product} sale! 🎉<br>
                             Your achievement sets the pace for this campaign!<br>
                             🏆 Let's all learn from ${name}'s achievement - this is the standard we strive for!`;

            document.getElementById("copyContent").innerHTML = message;
            messageBox.style.display = "block";
            copyBtn.style.display = "inline-block";
        }

        function copyToClipboard() {
            const copyText = document.getElementById("copyContent").innerText;

            if (navigator.clipboard && navigator.clipboard.writeText) {
                navigator.clipboard.writeText(copyText).then(() => {
                    showTooltip();
                }).catch(err => {
                    console.error("Clipboard write failed: ", err);
                });
            } else {
                // Fallback for older browsers
                const textArea = document.createElement("textarea");
                textArea.value = copyText;
                document.body.appendChild(textArea);
                textArea.select();
                try {
                    document.execCommand("copy");
                    showTooltip();
                } catch (err) {
                    console.error("Fallback copy failed: ", err);
                }
                document.body.removeChild(textArea);
            }
        }

        function showTooltip() {
            const tooltip = document.getElementById("tooltip");
            tooltip.style.display = "inline";
            setTimeout(() => {
                tooltip.style.display = "none";
            }, 2000);
        }
    </script>

</body>
</html>
# Work
