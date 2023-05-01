// Get user inputs for technical indicators and additional factors
let price = parseFloat(prompt("Enter the stock price:"));
let ma10 = parseFloat(prompt("Enter the 10-day moving average:"));
let ma50 = parseFloat(prompt("Enter the 50-day moving average:"));
let ma200 = parseFloat(prompt("Enter the 200-day moving average:"));
let ema100 = parseFloat(prompt("Enter the 100-day exponential moving average:"));
let rsi14 = parseFloat(prompt("Enter the 14-day relative strength index:"));
let ema50 = parseFloat(prompt("Enter the 50-day exponential moving average:"));
let vwap = parseFloat(prompt("Enter the volume-weighted average price:"));
let ema10 = parseFloat(prompt("Enter the 10-day exponential moving average:"));
let macd = parseFloat(prompt("Enter the MACD(12,26,9) signal:"));
let volume = parseFloat(prompt("Enter the volume:"));
let changeOverOneYear = parseFloat(prompt("Enter the change over one year (%):"));

// Determine current state of the market based on technical indicators and additional factors
let state = "";
if (price > ma10 && ma10 > ma50 && ma50 > ma200 && ema100 > ma200 && rsi14 > 50 && ema50 > ma200 && price > vwap && ema10 > ma50 && macd > 0) {
  state = "bullish";
} else if (price < ma10 && ma10 < ma50 && ma50 < ma200 && ema100 < ma200 && rsi14 < 50 && ema50 < ma200 && price < vwap && ema10 < ma50 && macd < 0) {
  state = "bearish";
} else {
  state = "neutral";
}

// Map current state to a value on a 0-1000 scale
let scaleValue = 0;
switch (state) {
  case "bullish":
    scaleValue = Math.min(1000, Math.round(500 + (macd - 1) * 500)); // Map MACD range (1, inf) to (500, 1000)
    break;
  case "bearish":
    scaleValue = Math.max(0, Math.round(500 + macd * 500)); // Map MACD range (-inf, -1) to (0, 500)
    break;
  case "neutral":
    scaleValue = 500;
    break;
}

// Determine if the stock is overvalued or undervalued
let valuation = "";
if (price > vwap) {
  valuation = "overvalued";
} else if (price < vwap) {
  valuation = "undervalued";
} else {
  valuation = "fairly valued";
}

console.log(`The market is currently ${state}. Scale value: ${scaleValue}`);
console.log(`The stock is ${valuation}.`);
console.log(`Volume: ${volume}`);
console.log(`Change over one year: ${changeOverOneYear}%`);
