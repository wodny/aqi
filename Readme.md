# AQI (Polski)

Narzędzie do wyliczania [Air Quality Index (AQI)][1] na podstawie stężeń 
substancji (ug/m3, ppm, ppb).

Narzędzie powstało, ponieważ niektórzy [specjaliści][5] [twierdzą][2], 
że wartości dostępne w serwisie [aqicn.org][3] są nieprawidłowe 
i chciałem to sprawdzić samodzielnie. Serwis ten dla każdej z substancji 
wylicza AQI na podstawie poziomów wyrażonych w ug/m3 pochodzących 
z warszawskiego [WIOŚ][4].

Na stronach aqicn.org znajduje się ciekawy [artykuł][7] o różnicach 
między skalami -- między innymi między amerykańskim AQI od EPA oraz 
[IJP][9] używanym przez WIOŚ.

Sprawdź proszę samodzielnie i daj znać o błędach. Niektóre wyliczone 
wartości mogą się nieco różnić -- wydaje mi się, że może to być 
spowodowane odmiennym sposobem uśredniania lub inną metodą 
[konwersji][8] ug/m3 na ppm.

Do wyjaśnienia pozostaje kwestia tego, jak [aqicn.org][3] szacuje 
wartości dotyczące substancji, których stężenia dana stacja nie mierzy.  
W szczególności, czy jest to średnia z danych pochodzących z danych od 
WIOŚ.

## Stacje WIOŚ

|    Warszawa   | PM2.5 | PM10  | O3 | NO2 | SO2 | CO |
|:-------------:|:-----:|:-----:|:--:|:---:|:---:|:--:|
| Komunikacyjna |   X   |   X   |    |  X  |     |  X |
| Marszałkowska |   X   |   X   |    |  X  |     |  X |
| Targówek      |   X   |   X   |  X |  X  |  X  |  X |
| Ursynów       |   X   |   X   |  X |  X  |  X  |    |

Obecność czujnika na danej [stacji][6] zaznaczona przez "X". Podano 
tylko te substancje, które uwzględnia aqicn.org. Serwis ten podaje 
poziom wszystkich 6 substancji dla każdej lokalizacji, więc dla 
niektórych z nich musi to być wartość szacunkowa.

Stacja Podleśna wydaje się nie działać. Lokalizacje Porajów i Puszczy 
Solskiej nie wydają się być wprost powiązane ze stacjami WIOŚ.

Stacja Warszawa Komunikacyjna (Al. Niepodległości) jest aktualnie 
niedostępna w serwisie aqicn.org.

## Dane aqicn.org vs WIOŚ vs GIOŚ

Otrzymałem odpowiedź na skierowane do WIOŚ [zapytanie][10] o źródło 
twierdzenia, że aqicn.org podaje błędne dane. Najwyraźniej WIOŚ 
przeliczył swoje dane na AQI, a następnie wyrywkowo porównał z danymi 
prezentowanymi przez chiński serwis. Porównanie potwierdziło 
występowanie znacznych różnic, więc nie jest to jedynie problem innych 
jednostek. WIOŚ zwrócił również ponownie uwagę na fakt, że stacja Krucza 
jest od dawna wyłączona. Serwis aqicn.org odnotował już ten fakt 
i oznaczył [stację][13] w specjalny sposób.

W międzyczasie odkryłem, że serwis WIOŚ oparty o *CMS Made Simple* co 
jakiś czas zwraca błędne dane (dla innej stacji, daty, zestawu 
substancji). Prawdopodobnie wynika to z błędnego działania pamięci 
podręcznej CMS-a. Sytuację można łatwo rozpoznać po tym, że w źródle 
pojawia się fraza:

```
<!-- Generated in 0.91902 seconds by CMS Made Simple 0.10.3 (cached) using 11 SQL queries -->
```

zamiast:

```
<!-- Generated in 0,92187 seconds by CMS Made Simple 0.10.3 (not cached) using 18 SQL queries -->
```

WIOŚ został o tym poinformowany i obiecał przekazanie informacji 
informatykom.  Serwis aqicn.org potwierdził, że problem wpłynął na 
prezentowane przezeń dane.

Tymczasem serwis aqicn.org [rozpoczął prace][11] nad przejściem na 
korzystanie z danych pochodzących z [nowego portalu][12] GIOŚ.

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

On the aqicn.org site you can find a very interesting [article][7] about 
differences between scales -- specifically, the US EPA AQI and [IJP][9] 
used by WIOŚ.

Please check yourself and report bugs. Some calculated values differ 
a bit -- I suppose it may be due to a different averaging method or 
[conversion][8] between ug/m3 and ppm method.

Further investigation is required to clarify how [aqicn.org][3] 
estimates levels of chemicals not monitored at a particular station.  
Specifically, if it is an average of other data from WIOŚ.

## WIOŚ stations

|    Warszawa   | PM2.5 | PM10  | O3 | NO2 | SO2 | CO |
|:-------------:|:-----:|:-----:|:--:|:---:|:---:|:--:|
| Komunikacyjna |   X   |   X   |    |  X  |     |  X |
| Marszałkowska |   X   |   X   |    |  X  |     |  X |
| Targówek      |   X   |   X   |  X |  X  |  X  |  X |
| Ursynów       |   X   |   X   |  X |  X  |  X  |    |

Availability of a sensor at a particular [station][6] is marked with 
"X". Only those chemicals which are reported by aqicn.org are included 
in the table. The site reports levels of all 6 chemicals for every 
location so for some of them they have be estimated values.

The Podleśna station seems to be offline. Porajów and Puszczy Solskiej 
locations don't seem to be directly associated with WIOŚ stations.

The Komunikacyjna (Al. Niepodległości) station is currently unavailable 
on aqicn.org.

## Data from aqicn.org vs WIOŚ vs GIOŚ

I received a reply to my [inquiry][10] to WIOŚ about the basis of the 
statement suggesting that aqicn.org publishes incorrect data. Apparently 
WIOŚ converted their data to AQI values and then compared a couple of 
them with data presented by the Chinese website. The comparison 
confirmed significant differences for some cases, so it wasn't just 
a problem of converting units. WIOŚ pointed out again that the Krucza 
station is long offline. The aqicn.org site has noted that and marked 
the [station][13] as being offline.

In the meantime I discovered that from time to time the WIOŚ site based 
on *CMS Made Simple* responds with incorrect data (wrong station, date, 
set of substances). Probably it's because of the faulty cache mechanism 
of the CMS. The situation is easily detectable by looking for the 
following phrase in the HTML source code:

```
<!-- Generated in 0.91902 seconds by CMS Made Simple 0.10.3 (cached) using 11 SQL queries -->
```

Instead of the following information when a response is correct:

```
<!-- Generated in 0,92187 seconds by CMS Made Simple 0.10.3 (not cached) using 18 SQL queries -->
```

WIOŚ has been notified about the problem and promised to notify the IT 
guys. The aqicn.org site confirmed that it influenced the presented 
data. 

In the meantime aqicn.org [started working][11] on the transition to the 
new source of data, i.e. [new GIOŚ portal][12].

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
[10]: http://o-blache.blogspot.com/2015/11/podanie-do-wios-o-udzielenie-informacji.html
[11]: http://feedback.aqicn.org/forums/162638-general/suggestions/11222325-use-the-new-source-of-data-for-poland-gios-gov-p
[12]: http://powietrze.gios.gov.pl/pjp/current
[13]: http://aqicn.org/city/poland/mazowieckie/warszawa/krucza/
