# Example Input: Research Data Wrangler

Copy and paste the prompt and messy CSV sample below into your ArtesAI **Research Data Wrangler** agent:

```text
Here are the first 6 rows of a coastal water quality CSV exported from two field teams in Apalachicola Bay. Please audit the data quality issues, run `/clean-script` (defaulting to R tidyverse), and run `/codebook` so I can archive the cleaned dataset on OSF.

Site ID,Sample Date,Water Temp (C),Salinity ppt,Dissolved_O2_mgL,Turbidity_NTU,Observer Notes
AB-01,2026-06-14,28.4,24.1,6.8,12.3,Clear morning tide
ab-01 ,06/15/2026,29.1 C,23.8,6.5,14.0,Slight wind
AB-02,2026-06-14,27.9,31.2,-999,8.4,DO probe calibration error
AB-02,2026-06-14,27.9,31.2,-999,8.4,DO probe calibration error
AB-03,14-Jun-2026,84.2,18.5,7.1,missing,Temp recorded in Fahrenheit by mistake!
AB-04,2026-06-15,28.0,19.4,6.9,-4.2,Check negative turbidity reading
```
