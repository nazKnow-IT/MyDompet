# MyDompet

A personal spending tracker for everyday expenses in Ringgit (RM). Snap a receipt and MyDompet reads the shop, date and total for you, sorts the expense into a category, and shows how you are doing against your spending limits.

Everything runs in the browser and is saved on your own device. There is no account, no server and no bank connection.

## Features

- **Add, edit and delete expenses** with shop or description, amount, date, category and payment method (card, cash, online banking, e-wallet).
- **Receipt scanning:** take or choose a photo and the app reads the merchant, date and total using [Tesseract.js](https://github.com/naptha/tesseract.js) OCR, then fills in the form for you to check before saving.
- **Automatic categories** from the description or receipt text, across 11 categories, including local words like *kopi* and *nasi*.
- **Spending goals** with daily, weekly, monthly and yearly limits and progress bars.
- **Insights:** a daily spending chart for the month and a breakdown by category.
- **Transactions:** month-by-month history with search and CSV export.
- Works on phones, with a bottom navigation bar on small screens.

## Run it

Open `index.html` in a modern browser. No install or build step is needed.

The first receipt scan downloads the OCR engine, so it needs an internet connection. Receipt photos are processed in the browser and are not uploaded anywhere.

## How receipt reading works

1. The photo is resized and compressed on a canvas so recognition is faster on a phone.
2. Tesseract.js extracts the text in the browser.
3. The parser picks the merchant from the first meaningful line, reads day-first or year-first dates, and takes the amount from the strongest total line (grand total, amount due, net total, then total, never subtotal). Amounts such as `RM14.70`, `RM 14.70` and `14.70` are all recognised.
4. Keyword rules suggest a category, and the form is pre-filled. Nothing is saved until you press **Save expense**.

## Data

Expenses and goals are stored in the browser's `localStorage` under the key `mydompet-v1`. Clearing your browser data removes them, so use **Export CSV** to keep a copy.
