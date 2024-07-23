# Water-Data-Project
Dig-Deep project to visualize and process water quality data in the US.

**Project and the below description produced in collaboration with Dr. Gasteyer. All coding for the project is my sole authorship. **


Data for to be collected for the United States Water and Sanitation Hygiene Dashboard 
Date: 06/08/2024

The goal of the dashboard is to provide a spatial representation of where existing government data indicates communities that face significant challenges when accessing potable water and sanitation. To this end, three data sets (listed below):  

For the dashboard we will be pulling from three main sources: 
1. The American Community Survey (ACS) 
2. EPA Safe Drinking Water Act (SDWA) 
3. EPA National Pollutant Discharge Elimination System (NPDES). 

The ACS will be accessed through the US Census data portal (https://data.census.gov/).  The SDWA and NPDES data will be gathered through the US Environmental Protection Agency Enforcement and Compliance History Online (ECHO) database (https://echo.epa.gov/).  

One of the challenges of combining these datasets is that they report data at different spatial units.  Further, as the ECHO data are reported from state primacy agencies to the Federal Government, the data may vary by state both in accuracy, and by the unit of analysis reported for SDWA and NPDES data. Data are available always available at the State and County levels. 

We will pull data from the ACS to indicate the percent of households lacking access to complete plumbing facilities at the level of counties and zip codes (ZCTAs – the Census approximation of Zip Code areas).  We will color code by percent lacking complete plumbing with those exceeding a particular cut off (say, those where more than 1 percent of households lack complete access to plumbing facilities exceeds) as hot spots.  We will also use the ACS to collect the basic demographic details for each location including: a)percent race, b) median household income, c) percent poverty.  We will need to think a bit about what other data to include in the dashboard.  For instance, would housing tenure (rent or own) be illuminating, or income by percentile?  

The SDWA dataset will allow us to monitor and aggregate information on code violations committed by public water systems (PWS). We will use the EPA formula of risk severity that assigns violations as falling into 3 categories: Tier 1 – violations that exceed contaminant levels and pose an immediate risk to public health; Tier 2 – violations that exceed contaminant levels but pose a risk to public health that is not immediate; Tier 3 – violations of regulations that do not pose a risk to public health such as failure to report.  (For a more detailed list of violations, see https://www.epa.gov/dwreginfo/public-notification-rule.) 

Based on an EPA formula to consolidate violations into a single score, we assign 10 points to tier 1 violations, 5 points to tier 2 violations, and 1 point to tier 3 violations, adding a point for each year since the oldest violation. We will analyze all available data and report our results. Preliminary analysis of 254,666 systems suggests that PWS scores range from 0 to 917 points, with a mean of 8 and a median of 6 amongst non-zero scores. Experts will be consulted to determine a cutoff point, beyond which we will highlight serious and persistent offenders. We will tabulate this information at the system and county level.  For the purposes of combining this data with ACS data, we will construct a score at the county level.  Within each county, we should build in a layer that can do the tabulation at the system level.  

Further, using the EPA’s Community Water System Service Area Boundaries ( https://www.epa.gov/ground-water-and-drinking-water/community-water-system-service-area-boundaries ) we are able to map the areas serviced by water systems that have at least 15 connections with at least 25 year-round residents. The shape files included in the EPA project include the service areas of 44,415 PWS. This allows us to make more granular analysis and pinpoint communities that the data highlights as being at high risk of contaminated drinking water. However, our query of SDWA data allowed us to score 254,666 public water systems. Therefore, we believe that the combined approach - aggregating at the county level and mapping available service area boundaries - will provide a more holistic review of the water quality. 

We will use a similar method to analyze CWA NPDES violations to monitor water pollution resulting from the improper discharge of waste. The EPA collects information through Quarterly Non-Compliance Reports and logs significant non-compliers according to the codes available here under HLRNC Historic Noncompliance (https://echo.epa.gov/tools/data-downloads/icis-npdes-download-summary). These include effluent violations, permit violations and reporting violations. Using the last 20 years of data, from 2004 onward, we calculated the percentage of quarters for which a facility was deemed in Significant Non-Compliance (SNC). This approach allowed us to analyze records for 552,528 facilities. They average 9.12% quarters in SNC with 8,285 facilities in SNC 100% of the reported quarters. 

The EPA provides latitude and longitude information for all facilities, making their mapping relatively easy. However, it is important to note that the impact of their non-compliance is difficult to quantify, and the affected area is also difficult to determine. Nonetheless, highlighting the counties and communities where facilities are regularly found in significant non-compliance provides information valuable to those in the surrounding areas and allows for the intended spatial and demographic analysis.

We believe that by giving prominence to the affected areas, with special attention to those communities where these issues overlap, we will be able to paint a more complete picture of access to potable water and sanitation across the United States. All of this should result in a comprehensive overview of the issues faced by communities, making quantitative information easily available to activists and other groups interested in closing the Water Gap. 


