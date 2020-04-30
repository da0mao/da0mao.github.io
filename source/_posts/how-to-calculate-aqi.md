---
title: How to calculate AQI
author: Jun Hu
tags:
  - AQI
date: 2020-04-30 22:07:54
---

An air quality index (AQI) is used to communicate to the public how polluted the air currently is. Public health risks increase as the AQI rises. Different countries have their own air quality indices, corresponding to different national air quality standards.
The air quality index is a piecewise linear function of the pollutant concentration. At the boundary between AQI categories, there is a discontinuous jump of one AQI unit. To convert from concentration to AQI this equation is used:

<!-- more -->

$I=\frac{I_{high}-I_{low}}{C_{high}-C_{low}}(C-C_{low})+I_{low}$

where:

$I$=the AQI
$C$=the pollutant concentration
$C_{low}$=the concentration breakpoint that is $\leq C$
$C_{high}$=the concentration breakpoint that is  $\geq C$
$I_{low}$=the index breakpoint corresponding to $C_{low}$
$I_{high}$=the index breakpoint corresponding to $C_{high}$

It is the breakpoint which makes AQI values vary in different countries.

Below is a table of PM2.5 breakpoints from [China](http://www.mee.gov.cn/ywgz/fgbz/bz/bzwb/jcffbz/201203/W020120410332725219541.pdf) and the [US](https://www.airnow.gov/sites/default/files/2018-05/aqi-technical-assistance-document-may2016.pdf):

| Index   | US                       |China      |
|-----------------------------------------------------|
| 0            | 0                        | 0         |
| 50           | 12                       | 35        |
| 100          | 35.4                     | 75        |
| 150          | 55.4                     | 115       |
| 200          | 150.4                    | 150       |
| 300          | 250.4                    | 250       |
| 400          |                          | 350       |
| 500          | 500                      | 500       |

For example, if the PM2.5 concentration is 50 $\mu g/m^3$ then AQI in two countries are:

$I_{China}=\frac{I_{high}-I_{low}}{C_{high}-C_{low}}(C-C_{low})+I_{low}=\frac{100-50}{75-35}(50-35)+50=68.75$

$I_{US}=\frac{I_{high}-I_{low}}{C_{high}-C_{low}}(C-C_{low})+I_{low}=\frac{150-100}{55.4-35.4}(50-35.4)+100=136.5$

From below plot we can see that the difference increases when the PM2.5 concentration is less than ~70 $\mu g/m^3$ and decreases until the concentration hits ~150 $\mu g/m^3$ where the difference is gone.

![AQI1](/images/AQI1.png)

---



Reference:

*- [Wikipedia: Air quality index](https://en.wikipedia.org/wiki/Air_quality_index)*

*- [United States Environmental Protection Agency: Technical Assistance Document for the Reporting of Daily Air Quality – the Air Quality Index (AQI) May 2016](https://www.airnow.gov/sites/default/files/2018-05/aqi-technical-assistance-document-may2016.pdf)*

*- [中华人民共和国生态环境部：环境空气质量指数（AQI）技术规定（试行）（HJ 633—2012 ）](http://www.mee.gov.cn/ywgz/fgbz/bz/bzwb/jcffbz/201203/W020120410332725219541.pdf)*