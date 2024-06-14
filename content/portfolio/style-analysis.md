---
title: Asset Management
date: 2023-10-13T12:49:27.000+06:00
thumbnail: images/portfolio/asset.png
service: Style analysis 
client: Bocconi University
shortDescription: The project explores the performance of a unique investment fund that strategically combines a 50% stake in the MSCI World Index with another 50% in the Bloomberg Aggregate Bond Index, both hedged into Euros. Through style analysis, it aims to understand how this blend of global equity and fixed-income exposure, along with currency hedging, shapes the fund's overall strategy and returns.
challenge: The challenge lies in accurately attributing the performance of the investment portfolio to different styles and understanding the underlying drivers of portfolio returns. Traditional methods like OLS regression are not suitable due to their focus on minimizing squared differences, necessitating the need for a specialized method like style analysis that minimizes tracking error volatility (TEV) with positive weights constraints.
solution: The project employs both Strategic Style Analysis and Rolling Style Analysis. Strategic Style Analysis offers insights into long-term strategic planning and understanding core investment styles, while Rolling Style Analysis provides a dynamic perspective by examining style dynamics over shorter, rolling periods. By combining these approaches, the project gains a comprehensive understanding of the fund's style exposures, allowing for informed decision-making and adaptability to changing market conditions.

---
{{< bootstrap_button link="https://github.com/MsNose/style-analysis" alignment="vertical" >}}Look at the Project on Github!{{< /bootstrap_button >}}

---------------------


The goal of the project was to explain the returns of a fund by established indices.


By conducting style analysis, investors and portfolio managers can make informed decisions about the suitability of their portfolios for different market conditions. It offers static and dynamic perspective, acknowledging that market environments change over time, and portfolios need to be adaptable to deliver consistent performance.

## Startegic Style Analysis
In this analysis covering 60 months, we explore the performance of a unique investment fund. This fund strategically combines a 50% stake in the MSCI World Index with another 50% in the Bloomberg Aggregate Bond Index, both hedged into Euros. By examining its performance, we aim to understand how this blend of global equity and fixed-income exposure, along with currency hedging, shapes the fund's overall strategy and returns.

Compared to OLS regression, which minimizes the sum of squared differences, style analysis aims to minimize the tracking error volatility (TEV). Moreover, it has no intercepts, and poses positive weights constraints. Thus, style analysis is a specialized method tailored for assessing and attributing the performance of investment portfolios to different styles. This is crucial in finance for understanding the underlying drivers of portfolio returns and making informed investment decisions.  

Error volatilitly minimazitaion process is used for the selected indices with the weight constraints. As a result, positive optimized weights are assigned to each of the indexes, showing how similar their style is to the fund.


## Rolling Style Analysis
Strategic Style Analysis is useful for long-term strategic planning, understanding the core investment styles of a portfolio, and assessing its alignment with the investor's objectives. However, to gain a dynamic perspective, Rolling Style Analysis is the ideal approach. Rolling Style Analysis examines style dynamics over shorter, rolling periods. Thus, it is more sensitive to changes in style composition over time, making it useful for detecting shifts in investment strategy and allows for adaptability to changing market conditions and provides a more dynamic view of how a portfolio's style exposures evolve. In this case a 36 months rolling period, referred to as windows.   

Therefore, the base of the code is the similar to the strategic part, but the effective weights depend now also on the window size. The main predictors over time are the LE57TREU and MXUS indices, in harmony with the findings of the the strategic analysis. Together with the I31914EU index these three seem to have a stable significant presence. However, the role of the other indices are rather fluctuating, and they just appear in the second half of the rolling. The complexity of predicting the fund with these indices is represented with the path of the r-squared over time, which is rather volatile. But after having a closer look it is clear that the r-square moves between 85% and 90%, which implies trustworthy results.

{{< bootstrap_button link="/images/portfolio/style-analysis/results.pdf" alignment="horizontal" >}}Results{{< /bootstrap_button >}}


-----------------



