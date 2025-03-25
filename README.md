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

    <!-- First input section for Promotion Star -->
    <div class="input-group">
        <label for="name">Name:</label>
        <input type="text" id="name" placeholder="Enter Name">
    </div>
    
    <div class="input-group">
        <label for="product">Product Name:</label>
        <input type="text" id="product" placeholder="Enter Product Name">
    </div>

    <!-- Generate & Copy buttons for Promotion Star -->
    <div class="button-group">
        <button class="btn generate-btn" onclick="generatePromotionStar()">Generate Promotion Star Message</button>
    </div>

    <!-- Message for Promotion Star -->
    <div id="promotionStarMessageBox" class="message">
        <div id="promotionStarCopyContent"></div>
    </div>

    <div class="button-group">
        <button id="promotionStarCopyBtn" class="btn copy-btn" onclick="copyPromotionStarToClipboard()">Copy Promotion Star Message</button>
        <span id="promotionStarTooltip" class="tooltip">Copied!</span>
    </div>

    <!-- Second input section for Top Store -->
    <div class="input-group">
        <label for="storeName">Store Name:</label>
        <input type="text" id="storeName" placeholder="Enter Store Name">
    </div>

    <div class="input-group">
        <label for="tvModel">TV Model:</label>
        <input type="text" id="tvModel" placeholder="Enter TV Model">
    </div>

    <!-- Generate & Copy buttons for Top Store -->
    <div class="button-group">
        <button class="btn generate-btn" onclick="generateTopStore()">Generate Top Store Message</button>
    </div>

    <!-- Message for Top Store -->
    <div id="topStoreMessageBox" class="message">
        <div id="topStoreCopyContent"></div>
    </div>

    <div class="button-group">
        <button id="topStoreCopyBtn" class="btn copy-btn" onclick="copyTopStoreToClipboard()">Copy Top Store Message</button>
        <span id="topStoreTooltip" class="tooltip">Copied!</span>
    </div>

    <script>
        // Function for generating the Promotion Star message
        function generatePromotionStar() {
            const name = document.getElementById("name").value.trim();
            const product = document.getElementById("product").value.trim();
            const messageBox = document.getElementById("promotionStarMessageBox");
            const copyBtn = document.getElementById("promotionStarCopyBtn");

            // Check if the fields are filled
            if (name === "" || product === "") {
                alert("Please enter both Name and Product Name.");
                return;
            }

            // Generate the Promotion Star message
            const message = `🎉 Congratulations to ${name} for landing the first ${product} sale! 🎉<br>
                             Your achievement sets the pace for this campaign!<br>
                             🏆 Let's all learn from ${name}'s achievement - this is the standard we strive for!`;

            // Display the message and copy button
            document.getElementById("promotionStarCopyContent").innerHTML = message;
            messageBox.style.display = "block";
            copyBtn.style.display = "inline-block";
        }

        // Function for copying the Promotion Star message to clipboard
        function copyPromotionStarToClipboard() {
            const copyText = document.getElementById("promotionStarCopyContent").innerText;

            if (navigator.clipboard && navigator.clipboard.writeText) {
                navigator.clipboard.writeText(copyText).then(() => {
                    showTooltip("promotionStarTooltip");
                }).catch(err => {
                    console.error("Clipboard write failed: ", err);
                });
            } else {
                const textArea = document.createElement("textarea");
                textArea.value = copyText;
                document.body.appendChild(textArea);
                textArea.select();
                try {
                    document.execCommand("copy");
                    showTooltip("promotionStarTooltip");
                } catch (err) {
                    console.error("Fallback copy failed: ", err);
                }
                document.body.removeChild(textArea);
            }
        }

        // Function for generating the Top Store message
        function generateTopStore() {
            const storeName = document.getElementById("storeName").value.trim();
            const tvModel = document.getElementById("tvModel").value.trim();
            const messageBox = document.getElementById("topStoreMessageBox");
            const copyBtn = document.getElementById("topStoreCopyBtn");

            // Check if the fields are filled
            if (storeName === "" || tvModel === "") {
                alert("Please enter both Store Name and TV Model.");
                return;
            }

            // Generate the Top Store message
            const message = `🚀 Breaking Records! 🚀<br>
                             ${storeName} just sold ${tvModel}s!<br>
                             🤔 Their secret? Perfecting the art of premium selling!<br>
                             😆 Upselling innovation is everyone's mission. Let's celebrate this outstanding team achievement!`;

            // Display the message and copy button
            document.getElementById("topStoreCopyContent").innerHTML = message;
            messageBox.style.display = "block";
            copyBtn.style.display = "inline-block";
        }

        // Function for copying the Top Store message to clipboard
        function copyTopStoreToClipboard() {
            const copyText = document.getElementById("topStoreCopyContent").innerText;

            if (navigator.clipboard && navigator.clipboard.writeText) {
                navigator.clipboard.writeText(copyText).then(() => {
                    showTooltip("topStoreTooltip");
                }).catch(err => {
                    console.error("Clipboard write failed: ", err);
                });
            } else {
                const textArea = document.createElement("textarea");
                textArea.value = copyText;
                document.body.appendChild(textArea);
                textArea.select();
                try {
                    document.execCommand("copy");
                    showTooltip("topStoreTooltip");
                } catch (err) {
                    console.error("Fallback copy failed: ", err);
                }
                document.body.removeChild(textArea);
            }
        }

        // Function to show tooltip
        function showTooltip(tooltipId) {
            const tooltip = document.getElementById(tooltipId);
            tooltip.style.display = "inline";
            setTimeout(() => {
                tooltip.style.display = "none";
            }, 2000);
        }
    </script>

</body>
</html>
