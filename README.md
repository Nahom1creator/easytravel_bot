<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Easy Travel - Lowest Unique Bid Auction</title>
    <script src="https://telegram.org/js/telegram-web-app.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: var(--tg-theme-bg-color, #f4f6f9);
            color: var(--tg-theme-text-color, #000);
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 400px;
            margin: auto;
            background: var(--tg-theme-secondary-bg-color, white);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }
        h2 { color: #00853f; text-align: center; }
        label { font-weight: bold; display: block; margin-top: 10px; }
        select, input {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border: 1px solid #ccc;
            border-radius: 5px;
            box-sizing: border-box;
        }
        button {
            width: 100%;
            background-color: #00853f;
            color: white;
            border: none;
            padding: 12px;
            margin-top: 20px;
            font-size: 16px;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover { background-color: #006c32; }
    </style>
</head>
<body>

    <div class="container">
        <h2>Easy Travel Auction</h2>
        
        <label for="route">Select Flight Route:</label>
        <select id="route">
            <option value="Addis Ababa to Lalibela">Addis Ababa ➔ Lalibela</option>
            <option value="Addis Ababa to Gondar">Addis Ababa ➔ Gondar</option>
            <option value="Addis Ababa to Bahir Dar">Addis Ababa ➔ Bahir Dar</option>
            <option value="Addis Ababa to Dubai">Addis Ababa ➔ Dubai</option>
        </select>

        <label for="bidAmount">Your Unique Bid Amount (ETB):</label>
        <input type="number" id="bidAmount" placeholder="e.g. 1450" min="1">

        <button onclick="submitBid()">Submit Lowest Unique Bid</button>
    </div>

    <script>
        let tg = window.Telegram.WebApp;
        tg.expand();

        function submitBid() {
            const route = document.getElementById('route').value;
            const bidAmount = document.getElementById('bidAmount').value;
            
            if (!bidAmount) {
                alert("Please enter a valid bid amount!");
                return;
            }

            const auctionData = {
                route: route,
                bidAmount: bidAmount
            };

            // Sends the auction bid back to your Telegram bot and closes the mini app
            tg.sendData(JSON.stringify(auctionData));
        }
    </script>
</body>
</html>****
