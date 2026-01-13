# WeGo Public Transit
[WeGo Public Transit](https://www.wegotransit.com/) is a public transit system serving the Greater Nashville and Davidson County area. WeGo provides local and regional bus routes, the WeGo Star train service connecting Lebanon to downtown Nashville, along with several other transit services.

The data for this project can be downloaded from [here](https://drive.google.com/drive/folders/1L8d3xEaPD13BMz_k-3G8XRRLvPIbNRq9?usp=sharing).

Since 2019, WeGo has been using [**Transit Signal Priority (TSP)**](https://www.wegotransit.com/projects/transit-signal-priority/), a technology that helps to manage traffic flow more efficiently. For buses it reduces wait times at traffic signals by holding green lights longer, shortening red lights or in some cases allowing buses to bypass traffic. 

The data that you have been provided was collected for trips on Route 50, Charlotte Pike. TSP has been used on portions of this route, with different periods of being on or off, either conditionally or unconditionally, , which creates a real-world “natural experiment.” For these timespans, TSP was used between White Bridge and MCC, including all intervening timepoints, in both directions.
The important dates are as follows:

* February 3rd @ 12 noon: TSP Turned On (Unconditional)

* February 10th @ 12 noon: TSP Schedule-Conditional Priority Begins (Only buses more than 2 minutes late receive priority)

* April 28th @ 12 noon: TSP Turned Off

* May 5th @ 12 noon: TSP Turned On (Unconditional)

* May 12th @ 12 noon: TSP Headway-Conditional TSP Priority Begins (Only gapped buses with actual leading headway more than 120% of scheduled headway receive priority)

You should create a categorical TSP variable that reflects these phases.

The main variable you will be studying in this project is **adherence**, which compares the actual departure time to the scheduled time and is included in the ADHERENCE column. A negative adherence value means that a bus left a time point late and a positive adherence indicates that the bus left the time point early. Buses with adherence values beyond negative 6 are generally considered late and beyond positive 1 are considered early. However, there is some additional logic where the staff applies waivers to allow early departures. For example, express buses that have already picked up everyone at a park-and-ride lot and are only dropping off passengers may be allowed to leave early.  Early departures are also permitted at the end of a trip (when TRIP_EDGE = 2), since they do not affect upstream passengers. **Note:** When determining whether a bus is early or late, it is advised that you use the 'ADJUSTED_EARLY_COUNT', 'ADJUSTED_LATE_COUNT', and 'ADJUSTED_ONTIME_COUNT' columns in order to account for the adjustments.

**Main Research Question:** Does Transit Signal Priority (TSP) reduce the probability that a bus leaves a stop late?

Keep in mind that there are many other factors that could also be contributing, so be sure to take into account things like day of the week, time of day, time of year (school in session or not), or other factors that may also be affecting adherence or headway deviation.

**Presentation Requirement**
As part of this project, your group will give a short (5-7 minutes total), informal presentation of your findings. You should create a short slide deck for this presentation.

Your presentation should cover:

1. The Question: What were you trying to predict?  
2. Your Model: What variables did you use in your logistic regression?  
3. Key Results: Did TSP lower the probability of buses being late?

**Stretch Goal**

The second main variable in the dataset is **headway**.  This is the amount of time between a bus and the prior bus at the same stop. In the dataset, the amount of headway scheduled is contained in the SCHEDULED_HDWY column and indicates the difference between the scheduled time for a particular stop and the scheduled time for the previous bus on that same stop.
This dataset contains a column HDWY_DEV, which shows the amount of deviation from the scheduled headway. **Bunching** occurs when there is shorter headway than scheduled, which would appear as a negative HDWY_DEV value. **Gapping** is when there is more headway than scheduled and appears as a positive value in the HDWY_DEV column. Note that you can calculate headway deviation percentage as HDWY_DEV/SCHEDULED_HDWY. The generally accepted range of headway deviation is 50% to 150% of the scheduled headway, so if scheduled headway is 10 minutes, a headway deviation of up to 5 minutes would be acceptable (but not ideal).

How has TSP affected headway?