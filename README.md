Stock Return Prediction Using Machine Learning

Predicting short-term stock price movements is one of the most widely studied problems in quantitative finance. During my internship at a securities firm, I observed that most analysts rely heavily on subjective judgment when making investment decisions. This project explores whether a data-driven approach — using only historical price and volume information — can systematically identify patterns that predict next-day price direction (up or down) for A-share stocks.

The goal is not to build a profitable trading strategy, but to understand how machine learning models perform on financial time-series data, and which features carry the most predictive signal.

Raw price data alone is not meaningful input for a classifier, so I engineered 7 features to capture different aspects of price behaviour: daily return, 5-day and 20-day moving averages, 5-day momentum, 10-day rolling volatility, price relative to MA20, and daily volume change. Each feature was chosen to reflect a distinct dimension — trend, momentum, volatility, and trading activity — rather than simply adding more variables.

Two models were chosen to represent different approaches. Random Forest is a non-linear ensemble method that can capture complex interactions between features without strong distributional assumptions, and provides feature importance scores for interpretation. Logistic Regression serves as a linear baseline — comparing the two shows whether non-linear patterns add meaningful predictive value over a simpler model.

A strict time-series split (no shuffling) was used, with the last 20% of observations reserved for testing. This is critical in financial data: random shuffling would allow the model to train on future data and inflate accuracy — a form of look-ahead bias that would make results meaningless in practice.

Both models were evaluated on accuracy, precision, recall, and F1-score. Feature importance analysis from the Random Forest indicates which variables contribute most to the prediction.

<img width="577" height="236" alt="屏幕截图 2026-05-20 224847" src="https://github.com/user-attachments/assets/960818ef-b1ca-4975-a9e9-d9f287456b97" />
<img width="1652" height="463" alt="屏幕截图 2026-05-20 224842" src="https://github.com/user-attachments/assets/498901a9-9805-4a54-ba51-a4639a7e7eea" />
<img width="591" height="547" alt="屏幕截图 2026-05-20 224833" src="https://github.com/user-attachments/assets/4968cb89-2191-4241-b9f4-a3228f07a9f5" />
<img width="399" height="42" alt="屏幕截图 2026-05-20 224825" src="https://github.com/user-attachments/assets/e3f19a74-d05f-49fa-b8df-b30836eab654" />
<img width="1460" height="312" alt="屏幕截图 2026-05-20 224813" src="https://github.com/user-attachments/assets/f7f07ace-a0f0-4ec9-b7a8-7fb862a869a0" />
<img width="524" height="305" alt="屏幕截图 2026-05-20 224800" src="https://github.com/user-attachments/assets/c69c085b-e4f1-4031-b89b-67fc71d97b1c" />

It is worth noting that accuracy close to 50% on this task is expected and does not indicate a bug. Stock prices are influenced by macroeconomic conditions, news events, and market sentiment — none of which are captured by technical indicators alone. This project is intended as a learning exercise in applied machine learning on financial time-series data, not as a production trading system.

Tools used: Python · pandas · numpy · scikit-learn · matplotlib · akshare


