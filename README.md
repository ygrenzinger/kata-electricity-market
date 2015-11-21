# Power Time step converter
The context of this Kata is the electricity market where you can trade it in term of power or energy. 
Power is the metered net electrical transfer rate at any given moment and is measured in megawatts (MW).
Energy is electricity that flows through a metered point for a given period and is measured in megawatt hours (MWh).
Markets for energy-related commodities trade net generation output for a number of intervals usually in increments (time steps) of 15, 30 and 60 minutes. 

The kata has the hope to make you do TDD, use mostly Java 8 Time API and push you to do it in functionnal style because it's mainly data processing.

## Client requirements

### time step conversion

The client wants a tool capable of converting a list of power values in kilowatts in a specific time step into a different time step.
It's important to know that power value are special. Going from a larger time step to a smaller time step doesn't change the power values.

    For example, a list of a power values of 100MW in one hour will remain  100MW for a time step of 15 or 30 minutes.
    
However a smaller time step to a larger time step requires an averaging of the power values

    For example, a list of a power values of 25MW, 25MW, 75MW, 75MW for each quarter hour in one hour will be averaged to 50MW for the hour.
    
You have to include this conversion:

Starting time step  | Ending time step
------------------- | ------------------
60                  | 30
60                  | 15
30                  | 60
30                  | 15
15                  | 30
15                  | 60

### Getting the data from an external source

The cient wants the tool to get the data from an external source (an old one) giving you a map of results with pairs of java.util.Date and BigDecimal for the power value.
The map contains a period between two dates. The time step is 15 minutes to offer maximum precision. 

Warning, the client is french and want to trade electricity in France. There is a difficulty with the season's time change like summer time and winter time.
* The transition to winter's time happens the last sunday of october of each year and has 25 hours.
* The transition to summer's time happens the last sunday of october of each year and has 23 hours.
* Other days has the classic 24 hours.

### Sum of energy traded for a period

At last, the client wants the tool to give the sum of energy traded between two dates (start date inclusive - end date exclusive).
The energy is not the same as power. It's the power during one hour. This is why the unit is MWh. 






