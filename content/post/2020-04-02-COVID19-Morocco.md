---
title: COVID 19 - Morocco
author: Iliass TAHIRI
date: 2018-12-03
slug: data-science
categories: []
tags: []
subtitle: ''
---

<!--more-->

## Where data come from ?
Johns Hopkins University Center for Systems Science and Engineering (JHU CSSE) provide a useful data repository hosted on Github. To construct and update this database, JHU CSSE collect everyday informations from WHO, China CDC, US CDC, European Centre for Disease Prevention and Control (ECDC) and other more. They also provide a visual dashboard based on their collected data.

## Data exploration

The dataset provided by JHU CSSE begins from 22/01/2020 and updated on a daily basis.


## Data exploration



```python
#import train and test CSV files
link_confirmed_cases='https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv'
link_deaths='https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_deaths_global.csv'
df_confirmed_cases = pd.read_csv(link_confirmed_cases)
df_deaths = pd.read_csv(link_deaths)
```


![Enhaced coalbed methane recovery](/img/Cases.jpg)
![Enhaced coalbed methane recovery](/img/Fatalities.jpg)
