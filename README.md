# Simulating-Zero-Coupon-Bond-Dynamics-Valuing-Rate-Caps
In this case study, we execute a curve model for risk-neutral dynamics of zero-coupon bonds, simulate the evolution of bond prices, and calculate various par rates. We further use the model to estimate the values of several caps on specific time-frame rates. The study also includes valuing a 5-year resettable cap and a 5-year CMS cap, providing comprehensive insights into financial instrument modeling and valuation.


Please go through the "questions asked" to understand what all I did in depth. A brief is given below As park of my Fixed income assignment I implemented the following steps:

To start off, I focused on implementing the curve model which had been discussed in class. This model was primarily concerned with the risk-neutral dynamics of zero-coupon bonds, given by the equation dB(t, Ti) = rB(t, Ti)dt + σ(Ti − t)B(t, Ti)dZi, where each bond is driven by its own unique Brownian motion process.

To assist with this, I used a provided spreadsheet that contained the data required for the task. The first sheet contained a 20x20 correlation matrix for the first 20 zero-coupon bond prices. The second sheet provided the Cholesky decomposition of the correlation matrix. On the third sheet, I could find the zero-coupon bond prices, and the fourth sheet contained the volatility function.

Next, I followed the methodology taught in class to simulate the evolution of zero-coupon prices over a period of 10 years. While it would be ideal to simulate several thousand paths for these bond prices, I made a judgment call on the number of paths to simulate, based on the computational resources at my disposal and the accuracy required.

I then used the initial B(T) function provided in the spreadsheet to solve for the 2-year, 3-year, 5-year, and 10-year par rates. This was a key step to gain an understanding of the current rate structure and to prepare for the valuation of rate caps in the next steps.

With the curve model in place, I proceeded to find the values of 2-year, 3-year, 5-year, and 10-year caps on Lt, where Lt represents the six-month rate at time t, as implied by the six-month zero-coupon bond price B(t, t+0.50). I set the strike rate of each cap to the par rate identified in the previous step. I kept the caplets semiannual for simplicity, and I didn't forget to omit the first caplet due to the setting in advance feature.

I then calculated the value of a 5-year resettable cap with a strike of 0.07, considering semiannual caplets. The cash flows from each caplet were given by the formula 0.50max(0,L0.5−L0.0), 0.50max(0,L1.0−L0.50), and so forth, where Lt is the six-month rate at time t, implied by the six-month zero-coupon bond price B(t, t + 0.50).

Finally, I valued a 5-year CMS cap with a strike of 0.05, again considering semiannual caplets. The cash flow for the caplet expiring at time t + 0.50 was calculated as 0.50max(0,CMSt − .05), where CMSt denotes the 5-year par rate implied by the vector of zero-coupon bond prices at time t. As per the setting in advance feature, I omitted the first caplet.

This systematic approach allowed me to efficiently and accurately model, simulate, and analyze the dynamics of the zero-coupon bonds, calculate par rates, and value various interest rate caps.
