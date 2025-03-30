# DA-11-Summer-Olympic-Medal
This Power BI dashboard provides a comprehensive analysis of Olympic winners from 1970 to 2010. The dashboard includes key insights such as total medals, medal distribution by athletes, sports, cities, and years. Users can filter data based on year, country, sport, gender, and event-gender.

# Summer Olympic Dashboard (1970 - 2010)

## Overview

![olympic dashboard](https://github.com/user-attachments/assets/ec7ff614-b808-4d8e-a96b-71067ccaa377)

## Key Insights
1. **Total Medals Won**: 15,316 medals were awarded during this period, with:
   - **Gold Medals**: 5,042
   - **Silver Medals**: 5,016
   - **Bronze Medals**: 5,258
2. **Medals by Year**:
   - The highest number of medals were awarded in the early 2000s, with peaks in 2004 and 2008.
   - A general increase in medal distribution over the years.
3. **Total Medals by City**:
   - Major Olympic cities include **Los Angeles, Barcelona, Moscow, Seoul, Atlanta, Athens, Beijing, and Sydney**.
   - The size of the circles represents the volume of medals awarded.
4. **Top 5 Athletes Winning Medals**:
   - **Michael Phelps** dominates with 14 gold medals and a total of 19 medals.
   - Other high-achieving athletes include **Nikolay Andrianov, Birgit Fischer, Alexei Nemov, and Jenny Thompson**.
5. **Total Winning Medals by Sports**:
   - **Aquatics** has the highest number of gold medals (1,328), followed by **Athletics** (1,127).
   - **Rowing, Hockey, and Handball** also show significant medal counts.

## DAX Formulas Used
1. **Total Medal Calculation:**
   ```DAX
   Total Medals = COUNTROWS(OlympicData)
   ```
2. **Gold, Silver, and Bronze Medals Calculation:**
   ```DAX
   Gold Medal = CALCULATE(COUNTROWS(OlympicData), OlympicData[Medal] = "Gold")
   Silver Medal = CALCULATE(COUNTROWS(OlympicData), OlympicData[Medal] = "Silver")
   Bronze Medal = CALCULATE(COUNTROWS(OlympicData), OlympicData[Medal] = "Bronze")
   ```
3. **Medals by Year:**
   ```DAX
   Medals by Year = SUMMARIZE(OlympicData, OlympicData[Year], "Total Medals", COUNT(OlympicData[Medal]))
   ```
4. **Top 5 Athletes Winning Medals:**
   ```DAX
   Top Athletes = TOPN(5, SUMMARIZE(OlympicData, OlympicData[Athlete], "Total Medals", COUNT(OlympicData[Medal])), [Total Medals], DESC)
   ```
5. **Total Medals by Sport:**
   ```DAX
   Medals by Sport = SUMMARIZE(OlympicData, OlympicData[Sport], "Gold", COUNTAX(FILTER(OlympicData, OlympicData[Medal] = "Gold"), OlympicData[Medal]),
                                             "Silver", COUNTAX(FILTER(OlympicData, OlympicData[Medal] = "Silver"), OlympicData[Medal]),
                                             "Bronze", COUNTAX(FILTER(OlympicData, OlympicData[Medal] = "Bronze"), OlympicData[Medal]))
   ```

## Recommendations
1. **Trend Analysis**:
   - Explore trends in medal distribution over the years and identify factors influencing changes.
   - Identify patterns in top-performing countries and their dominance over time.
2. **Athlete Performance Analysis**:
   - Further breakdown by country or sport to analyze which nations produce the highest number of winning athletes.
3. **Predictive Analysis**:
   - Implement forecasting techniques to predict medal trends for future Olympics.
4. **Interactivity Enhancements**:
   - Include tooltips with additional statistics.
   - Add drill-through features to explore individual athlete performances in depth.

![image](https://github.com/user-attachments/assets/a9a49ea4-5196-4ba1-ad12-d4f196ad1512)

## Conclusion
This dashboard provides a clear visual representation of Olympic winners from 1970-2010. The use of Power BI's interactive features allows for deep insights into medal distribution by year, athlete, sport, and city. Future enhancements could include country-level analysis, athlete performance tracking, and predictive modeling for upcoming Olympic events.

