# COVID-19 Data Sources and Analysis

jupyter feeding charts grafics https://dasn.herokuapp.com/covid19  

this work in references:
- [![Build Status](https://travis-ci.org/infchg/COVID-19.svg)](https://travis-ci.org/infchg/covid-19) 
- https://mybinder.org/v2/gh/infchg/COVID-19/master?filepath=JH-calculate-daily.ipynb
- https://nbviewer.jupyter.org/github/infchg/COVID-19/blob/master/JH-calculate-daily.ipynb

![dasn.herokuapp.com/covid19](dasn-dashboard-covid19.PNG)

## Source: World-cases, Age, Gender, Travel History
  - Data Feed: https://docs.google.com/spreadsheets/d/1itaohdPiAeniCXNlntNztZ_oRvjh0HsGuJXUJWET008/edit#gid=0
  - [] B Xu, M Kraemer, Open access epidemiological data from the COVID-19 outbreak, www.thelancet.com › article › PIIS1473-3099(20)30119-5 › Feb 19, 2020 
  - Curators: University of Oxford , Bo Xu,Bernardo Gutierrez,Sumiko Mekaru,Kara Sewalk,Alyssa Loskill,Lin Wang,Emily Cohn,Sarah Hill,Alexander Zarebski,Sabrina Li,Chieh-His Wu,Erin Hulland,Julia Morgan,Samuel Scarpino,John Brownstein,Oliver Pybus,David Pigott,Moritz Kraemer
  
## Source: World Stats Evolution per Coutry & Status
  - Data Feeds: https://github.com/CSSEGISandData/COVID-19/tree/master/csse_covid_19_data/csse_covid_19_time_series
  - hdx ocha https://data.humdata.org/dataset/novel-coronavirus-2019-ncov-cases https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_19-covid-Confirmed.csv
  - Curators: John Hopkins

## Source: China Summary Live Update
  - Data Feed, Isaac Lin: [API format](https://lab.isaaclin.cn/nCoV/api/overall?latest=0)
  - [Infectious Estimation of R0](https://github.com/yijunwang0805/YijunWang), Y. Wang
  - Li, Q., Guan, X., et al. (2020, January 29). [Early Transmission Dynamics in Wuhan, China, of Novel Coronavirus–Infected Pneumonia.](https://www.nejm.org/doi/full/10.1056/NEJMoa2001316#article_references) The New England Journal of Medicine. 

Note to contributors: aiming to add links closest to the original source or curation, (to avoid duplicated sources)


may16
```
2142,2391,2207,1518,1615,731,1156,1674,1763,1779,1632,1224"
data-datasets="571,650,602,827,639,467,530,808,779,759,963,700" bz
data-datasets="693,649,539,626,346,268,210,627,494,428,384,468"uk
data-datasets="236,197,257,199,193,112,108,353,294,257,290,278"mx
data-datasets="236,369,274,243,194,165,179,172,195,262,242,153"it
data-datasets="100,89,94,87,100,75,72,96,112,98,125,131"pe
data-datasets="95,86,88,98,104,88,94,107,96,93,113,119"ru
data-datasets="127,92,104,96,116,111,82,121,136,98,104,118"in
data-datasets="185,244,213,229,179,143,123,176,184,217,138,104"es
data-datasets="0,49,36,50,13,410,18,182,7,4,256,94"
data-datasets="118,112,121,94,61,142,85,118,89,131,50,82"
data-datasets="92,323,76,106,60,75,51,54,82,60,56,46"be
data-datasets="0,282,117,118,39,20,92,77,123,23,13,41"de
data-datasets="59,64,57,48,50,47,55,53,58,55,48,41"tk
data-datasets="59,55,47,58,61,25,37,64,31,32,24,37"
data-datasets="63,78,68,55,48,51,45,48,50,71,48,35 ir
```

brief summary 

```
 ##JH Source THIS IS THE SOURCE OF ALL CALCULATIONS IN THIS PAGE
! curl -OL https://github.com/CSSEGISandData/COVID-19/raw/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_deaths_global.csv

import pandas as pd
df=pd.read_csv('over50.csv')
df.set_index('Country/Region',inplace=True)  # .T
type(df)
cols20 = df.columns[-13:].tolist()
idx = cols20
df.sort_values(by=[df.columns[-1]],ascending=False)[cols20]
for i in range(1,13):
         df0[df0.columns[-i]] =    (df0[df.columns[-i]]-df0[df0.columns[-i-1]]) # casualties last day

print(','.join('Mr%.0f' %x for x in range(18,30+1))  ,'\ndata-datasets="')
print('"\ndata-datasets="'.join(','.join('%.0f' %x for x in y) for y in df9.values) )

=====================================================================================

  curl -kOL https://github.com/CSSEGISandData/COVID-19/raw/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_deaths_global.csv   #1
  
  <time_series_covid19_deaths_global.csv  perl -pe 's|(\d)/(\d)/20|200${1}0${2}|g; s|(\d)/(\d\d)/20|200${1}${2}|g' >dt #2
  
  nf=$( grep , -o <(head -1 time_series_covid19_deaths_global.csv) | wc -l ) #3
  
  COLS=60 ;cut -d, -f2,$(($nf-$COLS+2))-$(($nf+1)) dt | sort -k$((COLS+1)) -nr -t, | head -21 > dt.csv #4
  
import pandas as pd
df0=pd.read_csv('dt.csv')
df0.set_index('Country/Region',inplace=True)  # .T
type(df0)
#df.sort_values(by=[df.columns[-1]],ascending=False)
for i in range(1,13):
   df0[df0.columns[-i]] = df0[df0.columns[-i]] - df0[df0.columns[-i-1]]
st='\ndata-datasets="'
st='\ns/num%.0f/"'
print(st)
print(  (st % y).join(','.join('%.0f' %x for x in y) for y in df9.values) )

  now sed

```

notes:
```
cp /c/Users/ma*/Down*/JH-calculate-daily*13?.ipynb JH-calculate-daily.ipynb
 ls -ltr /c/Users/ma*/Down*/*nb |tail
cp /c/Users/ma*/Down*/updates*6?.ipynb updates.ipynb
```
