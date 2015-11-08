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

Sprawdź proszę samodzielnie i daj znać o błędach. Niektóre wyliczone 
wartości mogą się nieco różnić -- wydaje mi się, że może to być 
spowodowane odmiennym sposobem uśredniania lub inną metodą konwersji 
ug/m3 na ppm.

Do wyjaśnienia pozostaje kwestia tego, jak [aqicn.org][3] szacuje 
wartości dla lokalizacji, które nie odpowiadają stacjom WIOŚ 
(nieistniejące lub wyłączone) oraz dane dotyczące substancji, których
stężenia dana stacja nie mierzy. W szczególności, czy jest to średnia 
z danych pochodzących z danych od WIOŚ.

Dostępne substancje:
* ozon (O3),
* pył zawieszony poniżej 10 mikronów (PM10),
* pył zawieszony poniżej 2.5 mikrona (PM2.5),
* tlenek węgla (CO),
* dwutlenek siarki (SO2),
* dwutlenek azotu (NO2).

Przykłady:
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

Please check yourself and report bugs. Some calculated values differ 
a bit -- I suppose it may be due to a different averaging method or 
conversion between ug/m3 and ppm method.

Further investigation is required to clarify how [aqicn.org][3] 
estimates values for locations which don't correspond to WIOŚ stations 
(non-existent or disabled) and how it estimates levels of chemicals not 
monitored at a particular station. Specifically, if it is an average of 
other data from WIOŚ.

Available chemicals:
* ozone (O3),
* particulate matter under 10um (PM10),
* particulate matter under 2.5um (PM2.5),
* carbon monoxide (CO),
* sulphur dioxide (SO2),
* nitrogen dioxide (NO2).

Examples:
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
