---
name: lt-train-price
description: Paima pigiausią suaugusiojo traukinio bilietą vienai krypčiai tarp dviejų didžiųjų Lietuvos miestų iš LTG Link. Naudok, kai jau yra maršruto kortelė su traukinio stočių ID ir data, ir reikia tik traukinio kainos.
---

# Traukinio kaina

## Tikslas

Pagal `lt-trip-route` kortelę paimk vieną pigiausią parduodamą traukinio bilietą suaugusiajam. Autobuso neieškok ir transporto tarpusavyje nelygink.

Jei kortelės nėra, pirmiausia paruošk ją pagal `lt-trip-route`. Stočių ID nespėk.

## Užklausa

`GET https://bilietas.ltglink.lt/api/v2021/journeys/search`

Parametrai:

```text
departureDate={YYYY-MM-DD}
OriginStopId={išvykimo ID}
DestinationStopId={atvykimo ID}
currencyId=CURRENCY.EUR
Passengers=BONUS_SCHEME_GROUP.ADULT,1;
IsOutbound=true
isPartOfRoundtrip=false
```

`Passengers` palik būtent `BONUS_SCHEME_GROUP.ADULT,1;` su kabliataškiu gale. Valiuta yra `CURRENCY.EUR`, ne `EUR`.

## Kaina

`PriceFrom` jau yra eurais. Jo nesidalink iš 100. Rodyk su dviem skaičiais po kablelio ir prierašu EUR.

Tinkamas variantas yra `Journeys` įrašas, kurio `IsForSale` yra `true`, o `PriceFrom` didesnis už nulį. Iš jų rink pigiausią. Jei kaina vienoda, rink ankstesnį `PlannedDepartureDateTime`.

Jei atsakymas ne `200` arba tinkamo reiso nėra, rašyk „nėra“. Kainos iš autobuso atsakymo neperrašyk.

## Rezultatas

```text
Traukinys: {miestas} → {miestas}
Data: {YYYY-MM-DD}
Išvykimas: {PlannedDepartureDateTime}
Atvykimas: {PlannedArrivalDateTime}
Trukmė: {Duration}
Kaina: {PriceFrom} EUR
Šaltinis: https://bilietas.ltglink.lt/
```

Laikus imk iš `Origin.PlannedDepartureDateTime` ir `Destination.PlannedArrivalDateTime`. Pavyzdžio skaičių nekopijuok.
