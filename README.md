# Ky_louisville_Police_Driver_Data_Analysis
* Police data  on Rhode Island was downloaded from [stanford open policing](https://openpolicing.stanford.edu/data/) and an analyis was conducted on it.
* The dataset was cleaned and filtered to obtain the data necessary data for the analysis, it was viualized using bar and line plots to gain meaningful insights and then a light summary was made based on the insights.
### Details on the original dataset below:
<table>
 <thead>
  <tr>
   <th style="text-align:left;"> feature </th>
   <th style="text-align:left;"> coverage rate </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> date </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> time </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> location </td>
   <td style="text-align:left;"> 99.9% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lat </td>
   <td style="text-align:left;"> 99.6% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lng </td>
   <td style="text-align:left;"> 99.6% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> beat </td>
   <td style="text-align:left;"> 96.3% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> division </td>
   <td style="text-align:left;"> 96.2% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> subject_age </td>
   <td style="text-align:left;"> 73.2% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> subject_race </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> subject_sex </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> officer_race </td>
   <td style="text-align:left;"> 99.9% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> officer_sex </td>
   <td style="text-align:left;"> 99.9% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> type </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> violation </td>
   <td style="text-align:left;"> 73.3% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> citation_issued </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> warning_issued </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> outcome </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> frisk_performed </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> search_conducted </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> search_basis </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> reason_for_search </td>
   <td style="text-align:left;"> 99.8% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raw_activity_division </td>
   <td style="text-align:left;"> 96.2% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raw_division </td>
   <td style="text-align:left;"> 69.4% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raw_activity_beat </td>
   <td style="text-align:left;"> 96.1% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raw_beat </td>
   <td style="text-align:left;"> 69.6% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raw_driver_race </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raw_persons_race </td>
   <td style="text-align:left;"> 73.2% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raw_persons_ethnicity </td>
   <td style="text-align:left;"> 71.2% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raw_driver_age_range </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raw_was_vehcile_searched </td>
   <td style="text-align:left;"> 100.0% </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raw_citation_location </td>
   <td style="text-align:left;"> 73.3% </td>
  </tr>
</tbody>
</table>

**Data notes**:
- While we have raw csvs for all citations, we keep only those records that
  join onto the stops data; the source of this data is here:
  https://data.louisvilleky.gov/dataset/uniform-citation-data
- Data is deduplicated on raw columns officer_gender, officer_race,
  officer_age_range, activity_date, activity_time, activity_location,
  activity_division, division, activity_beat, beat, driver_gender, persons_sex,
  driver_race, persons_race, persons_ethnicity, driver_age_range, person_age,
  persons_home_city, persons_home_state, person_home_zip, reducing the number
  of rows by ~%
- subject_race is based on the raw column driver_race, since it is null 0.03%
  of the time compared to 18.6% for persons_race and 18.60% for
  persons_ethnicity; all are passed through with raw_ prefix
- violation represents raw column charge_desc
- All stops are not null for at least one of the driver_* columns or
  number_of_passengers or was_vehicle_searched columns, implying all stops are
  vehicular
- location used for geocoding is activity_location, which had a lower null rate
  than citation_location, but the latter was passed through as
  raw_citation_location
- subject_age is based on persons_age from the citation data, although it is
  null more often than driver_age_range; the latter, however, only gives a
  range, so couldn't be use for this column; it is passed through though as
  raw_driver_age_range
- search_conducted is based on was_vehcile_searched, which is passed through as
  raw_was_vehcile_searched (sic); there were 3 NAs that were coerced to false
  under the assumption that the officers may simply not have recorded the
  absence of a search
- search_basis was based on reason_for_search; k9 searches matched the pattern
  "K9|K-9|DOG", plain view searches matched anything mentioning plain
  view/smell or anything that could be seen in plain sight and matched the
  following pattern "BAGGIES|DRUGS|GUN|MARIJUANA|ODOR|PILLS|PIPE|PLAIN
  VIEW|SMELL", consent matched "CONSENT|CONSE", probable cause matched
  "PROB|P/C|PC|P.C.", and everything else was classified as "other"; this was
  verified to be accurate for 99.8% of entries; the long tail was not checked,
  but anyone viewing the data can see the original values in the
  reason_for_search column
- data is lacking explicit contraband information, but some of this can be
  inferred from reason_for_search
- frisk_performed is true with reason_for_search matches the pattern "TERRY|PAT",
  it is false otherwise (NA and no match)
- 2018 has data only from January
