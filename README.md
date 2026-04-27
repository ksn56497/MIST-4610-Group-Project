# Team 6 Mist 4610 Group Project 2 

## Team Name: 
71552 Group 6 

## Team Members:

1. Jesse Williams: [@jesnw](https://github.com/jeswn)
2. Tania Saputera: [@tas45087](https://github.com/tas45087)
3. Kate Nelms: [@ksn56497](https://github.com/ksn56497)
4. John Omolon: [@JohnOmolon](https://github.com/JohnOmolon)
5. Johan Jerry: [@johanjerry](https://github.com/johanjerry)

## Dataset Description

### Our Dataset and Why:
The dataset our team selected is from the U.S. Department of Transportation, which provides information on non-stop domestic flight segments such as departures and scheduled flights. Our team selected this dataset because it allows us identify major travel hubs in the USA by analyzing flight patterns, and evaluate differences between scheduled and actual flight activity. With this data we can make an meaningful impact on USA airports operationally, economicly, and socially by understanding travel demand and efficiency across regions in the USA.

### Description:
The US Department of Transportation database contains 7 distinct tables: Aircraft Carrier Index, Aircraft Index, Airport Index, US Department of Transportation Attributes, US Department of Transportation Attributes Point-in-Time History, US Department of Transportation Timeseries, and US Department of Transportation Timeseries Point-in-Time History. 

### Two Analytical Questions:
(Using datetime functions) aggregate data over time and see how specific holiday weeks impact passenger transportation, and which airports are busiest?

Which airports exceed the average number of departing flights and serve as primary travel hubs in the U.S.?

## Questions and Justification
###Query 1:

Question:
(Using datetime functions) aggregate data over time and see how specific holiday weeks impact passenger transportation, and which airports are busiest?

Justification:
This query analyzes how flight activity differs across the seasons (Winter, Spring, Summer, Fall) by comparing the total scheduled flights to actual flights flown, while calculating cancellations and extra flights. Operationally, it is meaningful because it helps airlines and airports understand how patterns change with the seasons to improve scheduling accuracy and better prepare for disruptions such as weather delays and holidays. Economically, it identifies periods of high and low efficiency, showing when airlines may lose revenue due to cancellations or gain revenue from increased demand during peak seasons. Socially, our query displays how reliable air travel is throughout the year (especially during busy travel seasons like holidays) and potential impacts for a passengers ability to travel. The query uses the US_DEPARTMENT_OF_TRANSPORTATION_TIMESERIES table (including DATE, VARIABLE, VALUE, and ORIGIN_AIRPORT_ID) and the AIRPORT_INDEX table (AIRPORT_ID). 

###Query 2: 

Question: 
Which airports exceed the average number of departing flights and serve as primary travel hubs in the U.S.?  

Justification:
This query identifies the airports with the highest number of departing flights by adding the total number of departures and filtering for those above the overall average using a subquery and “having” clause. This query is meaningful because it locates the major travel hubs around the USA, helping airports and the airlines that fly with them make informed operational decisions and better manage air traffic and resources. Economically, it identifies where travel demand and revenue are strongest vs weakest, making certain airports more competitive than others for investment. Socially, our query shows how accessible air travel is across different regions of the USA, locating which areas are more connected than others. The query uses the US_DEPARTMENT_OF_TRANSPORTATION_TIMESERIES table (specifically VALUE, VARIABLE, and ORIGIN_AIRPORT_ID) and the AIRPORT_INDEX table (AIRPORT_ID, AIRPORT_NAME). 

select 
case 
    WHEN MONTH(DATE) IN (12,1,2) THEN 'Winter'
    WHEN MONTH(DATE) IN (3,4,5) THEN 'Spring'
    WHEN MONTH(DATE) IN (6,7,8) THEN 'Summer'
    WHEN MONTH(DATE) IN (9,10,11) THEN 'Fall'
end as season,
SUM(CASE WHEN VARIABLE = 'DEPARTURES_SCHEDULED' THEN VALUE END) AS total_scheduled,
SUM(CASE WHEN VARIABLE = 'DEPARTURES_PERFORMED' THEN VALUE END) AS total_actual,
CASE 
        WHEN SUM(CASE WHEN VARIABLE = 'DEPARTURES_SCHEDULED' THEN VALUE END) > 
             SUM(CASE WHEN VARIABLE = 'DEPARTURES_PERFORMED' THEN VALUE END) 
        THEN SUM(CASE WHEN VARIABLE = 'DEPARTURES_SCHEDULED' THEN VALUE END) - 
             SUM(CASE WHEN VARIABLE = 'DEPARTURES_PERFORMED' THEN VALUE END)
        ELSE 0 
    END AS cancellations,
    CASE 
        WHEN SUM(CASE WHEN VARIABLE = 'DEPARTURES_PERFORMED' THEN VALUE END) > 
             SUM(CASE WHEN VARIABLE = 'DEPARTURES_SCHEDULED' THEN VALUE END)
        THEN SUM(CASE WHEN VARIABLE = 'DEPARTURES_PERFORMED' THEN VALUE END) - 
             SUM(CASE WHEN VARIABLE = 'DEPARTURES_SCHEDULED' THEN VALUE END)
        ELSE 0 
    END AS extra_flights
from US_DEPARTMENT_OF_TRANSPORTATION_TIMESERIES
join AIRPORT_INDEX ON US_DEPARTMENT_OF_TRANSPORTATION_TIMESERIES.ORIGIN_AIRPORT_ID = AIRPORT_INDEX.AIRPORT_ID
where COUNTRY_GEO_ID = 'country/USA'
group by season
limit 10;

SELECT 
    CASE 
        WHEN usdot_airports.STATE_GEO_ID IN ('geoId/09', 'geoId/23', 'geoId/25', 'geoId/33', 'geoId/44', 'geoId/50', 'geoId/34', 'geoId/36', 'geoId/42') THEN 'Northeast'
        WHEN usdot_airports.STATE_GEO_ID IN ('geoId/18', 'geoId/17', 'geoId/26', 'geoId/39', 'geoId/55', 'geoId/19', 'geoId/20', 'geoId/27', 'geoId/29', 'geoId/31', 'geoId/38', 'geoId/46') THEN 'Midwest'
        WHEN usdot_airports.STATE_GEO_ID IN ('geoId/10', 'geoId/11', 'geoId/12', 'geoId/13', 'geoId/24', 'geoId/37', 'geoId/45', 'geoId/51', 'geoId/54', 'geoId/01', 'geoId/21', 'geoId/28', 'geoId/47', 'geoId/05', 'geoId/22', 'geoId/40', 'geoId/48') THEN 'South'
        WHEN usdot_airports.STATE_GEO_ID IN ('geoId/04', 'geoId/08', 'geoId/16', 'geoId/30', 'geoId/32', 'geoId/35', 'geoId/49', 'geoId/56', 'geoId/02', 'geoId/06', 'geoId/15', 'geoId/41', 'geoId/53') THEN 'West'
        ELSE 'Territories'
    END AS region,
    AIRPORT_NAME, 
    SUM(usdot_ts.VALUE) AS total_flights
FROM US_DEPARTMENT_OF_TRANSPORTATION_TIMESERIES AS usdot_ts
JOIN AIRPORT_INDEX AS usdot_airports ON usdot_ts.ORIGIN_AIRPORT_ID = usdot_airports.AIRPORT_ID
WHERE usdot_ts.VARIABLE = 'DEPARTURES_PERFORMED'
GROUP BY region, usdot_airports.AIRPORT_NAME
HAVING total_flights > (
    SELECT AVG(airport_total)
    FROM (
        SELECT SUM(VALUE) as airport_total
        FROM US_DEPARTMENT_OF_TRANSPORTATION_TIMESERIES
        WHERE VARIABLE = 'DEPARTURES_PERFORMED'
        GROUP BY ORIGIN_AIRPORT_ID 
    )
)
ORDER BY total_flights DESC, region
LIMIT 10;


## Data Manipulations
Question 1 (Using datetime functions) aggregate date over time and see how specific holiday weeks impact passenger transportation, and which airports are busiest?
To answer this question, we joined the US Department of Transportation Time Series table to the Airport Index Table to associate each flight record to a specific location. We also filtered the data to include only data involving the U.S, using COUNTRY_GEO_ID = ‘country/USA.’ To make this data more easily readable and usable, we used the DATE column and a GROUP BY to group records by season (Winter, Spring, Summer, Fall)  based on the month. We also used conditional aggregations (case when) to calculate the scheduled and actual amount of flights. We then used more case statements to figure out cancellations and extra flights by comparing the totals for scheduled vs performed departures. If there were more scheduled flights than performed flights, we calculated the difference as cancellations and vice versa with extra flights
## Analysis and Results

## Streamlit App



