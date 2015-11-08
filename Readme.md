# AQI (Polski)

Narzędzie do wyliczania [Air Quality Index (AQI)][1] na podstawie stężeń 
substancji (ug/m3, ppm, ppb).

Narzędzie powstało, ponieważ niektórzy [specjaliści][5] [twierdzą][2], 
że wartości dostępne w serwisie [aqicn.org][3] są nieprawidłowe 
i chciałem to sprawdzić samodzielnie. Serwis ten dla każdej z substancji 
wylicza AQI na podstawie poziomów wyrażonych w ug/m3 pochodzących 
z warszawskiego [WIOŚ][4].

Co zaskakujące, chiński serwis podaje całkiem dokładne dane m.in. dla 
stacji Warszawa-Komunikacyjna.

Na stronach aqicn.org znajduje się ciekawy [artykuł][7] o różnicach 
między skalami -- między innymi między amerykańskim AQI od EPA oraz 
[IJP][8] używanym przez WIOŚ.

Sprawdź proszę samodzielnie i daj znać o błędach. Niektóre wyliczone 
wartości mogą się nieco różnić -- wydaje mi się, że może to być 
spowodowane odmiennym sposobem uśredniania lub inną metodą 
[konwersji][8] ug/m3 na ppm.

Do wyjaśnienia pozostaje kwestia tego, jak [aqicn.org][3] szacuje 
wartości dla lokalizacji, które nie odpowiadają stacjom WIOŚ 
(nieistniejące lub wyłączone) oraz dane dotyczące substancji, których
stężenia dana stacja nie mierzy. W szczególności, czy jest to średnia 
z danych pochodzących z danych od WIOŚ.

## Stacje WIOŚ

|    Warszawa   | PM2.5 |     PM10    | O3 | NO2 | SO2 | CO |
|:-------------:|:-----:|:-----------:|:--:|:---:|:---:|:--:|
| Komunikacyjna |   X   |      X      |    |  X  |  X  |  X |
| Marszałkowska |       | X (no data) |    |  X  |     |  X |
| Targówek      |   X   |      X      |  X |  X  |  X  |  X |
| Ursynów       |   X   |      X      |  X |  X  |  X  |    |

Obecność czujnika na danej [stacji][6] zaznaczona przez "X". Podano 
tylko te substancje, które uwzględnia aqicn.org. Serwis ten podaje 
poziom wszystkich 6 substancji dla każdej lokalizacji, więc dla 
niektórych z nich musi to być wartość szacunkowa.

Stacja Podleśna wydaje się nie działać. Lokalizacje Krucza, Porajów 
i Puszczy Solskiej nie wydają się być wprost powiązane ze stacjami WIOŚ.

## Dostępne substancje

* ozon (O3),
* pył zawieszony poniżej 10 mikronów (PM10),
* pył zawieszony poniżej 2.5 mikrona (PM2.5),
* tlenek węgla (CO),
* dwutlenek siarki (SO2),
* dwutlenek azotu (NO2).

## Przykłady

```
$ ./aqi pm25 114.3
concentration = 114.30ug/m3
concentration = 114.30ug/m3
concentration = 114.30ug/m3, range 55.5-150.4ug/m3
AQI = 181, level 3 = Unhealthy, range 151-200

$ ./aqi no2 35.2
concentration = 35.20ug/m3
concentration = 18.72ppb
concentration = 18.72ppb, range 0-53ppb
AQI = 18, level 0 = Good, range 1-50

```

# AQI (English)

A tool to calculate the [Air Quality Index (AQI)][1] from chemicals 
concentration levels (ug/m3, ppm, ppb).

This tool has been created because some [specialists][5] [state][2] that 
values available on [aqicn.org][3] are incorrect and I wanted to verify 
it. That site calculates AQI from ug/m3 levels for every chemical 
reported by the Varsovian [WIOŚ][4].

Surprisingly it seems that the Chinese site actually reports quite 
accurate data at least for the Warszawa-Komunikacyjna station.

On the aqicn.org site you can find a very interesting [article][7] about 
differences between scales -- specifically, the US EPA AQI and [IJP][8] 
used by WIOŚ.

Please check yourself and report bugs. Some calculated values differ 
a bit -- I suppose it may be due to a different averaging method or 
[conversion][8] between ug/m3 and ppm method.

Further investigation is required to clarify how [aqicn.org][3] 
estimates values for locations which don't correspond to WIOŚ stations 
(non-existent or disabled) and how it estimates levels of chemicals not 
monitored at a particular station. Specifically, if it is an average of 
other data from WIOŚ.

## WIOŚ stations

|    Warszawa   | PM2.5 |     PM10    | O3 | NO2 | SO2 | CO |
|:-------------:|:-----:|:-----------:|:--:|:---:|:---:|:--:|
| Komunikacyjna |   X   |      X      |    |  X  |  X  |  X |
| Marszałkowska |       | X (no data) |    |  X  |     |  X |
| Targówek      |   X   |      X      |  X |  X  |  X  |  X |
| Ursynów       |   X   |      X      |  X |  X  |  X  |    |

Availability of a sensor at a particular [station][6] is marked with 
"X". Only those chemicals which are reported by aqicn.org are included 
in the table. The site reports levels of all 6 chemicals for every 
location so for some of them they have be estimated values.

The Podleśna station seems to be offline. Krucza, Porajów and Puszczy 
Solskiej locations don't seem to be directly associated with WIOŚ 
stations.

## Available chemicals

* ozone (O3),
* particulate matter under 10um (PM10),
* particulate matter under 2.5um (PM2.5),
* carbon monoxide (CO),
* sulphur dioxide (SO2),
* nitrogen dioxide (NO2).

## Examples

```
$ ./aqi pm25 114.3
concentration = 114.30ug/m3
concentration = 114.30ug/m3
concentration = 114.30ug/m3, range 55.5-150.4ug/m3
AQI = 181, level 3 = Unhealthy, range 151-200

$ ./aqi no2 35.2
concentration = 35.20ug/m3
concentration = 18.72ppb
concentration = 18.72ppb, range 0-53ppb
AQI = 18, level 0 = Good, range 1-50

```

[1]: https://en.wikipedia.org/wiki/Air_quality_index#United_States
[2]: http://warszawa.wyborcza.pl/warszawa/1,34862,19138088,warszawa-nie-paryz-ani-nie-pekin-truja-nas-podwarszawskie.html
[3]: http://aqicn.org/city/poland/mazowieckie/warszawa/komunikacyjna/
[4]: http://sojp.wios.warszawa.pl/index.php?page=raport-godzinowy
[5]: http://wios.warszawa.pl/pl/aktualnosci-i-komunika/komunikaty/1057,KOMUNIKAT-MAZOWIECKIEGO-WOJEWODZKIEGO-INSPEKTORA-OCHRONY-SRODOWISKA-z-dnia-31032.html
[6]: http://sojp.wios.warszawa.pl/?page=opisy-stacji&t=1&site_id=11
[7]: http://aqicn.org/faq/2015-09-03/air-quality-scale-in-poland/
[8]: http://aqicn.org/faq/2015-09-06/ozone-aqi-using-concentrations-in-milligrams-or-ppb/
[9]: http://sojp.wios.warszawa.pl/index.php?page=ggg
