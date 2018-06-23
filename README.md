

```python
# Dependencies and Setup
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import requests
import time
from config import gkey


# Incorporated citipy to determine city based on latitude and longitude
from citipy import citipy

# Output File (CSV)
output_data_file = "output_data/cities.csv"

# Range of latitudes and longitudes
lat_range = (-90, 90)
lng_range = (-180, 180)
```

## Generate Cities List


```python
# list for holding lat_lngs and cities

from collections import defaultdict
lat_lng = defaultdict()

# create a set of random lat and lng combos
lats = np.random.uniform(low=-90.000, high=90.000, size=1500)
lngs = np.random.uniform(low=-180.000, high=180.000, size=1500)
lat_lngs = zip(lats, lngs)

for x in lat_lngs:
    lat, long = x #tuple unpacking
    city = citipy.nearest_city(lat, long).city_name
    lat_lng[city] = (lat, long)
    print(f'Retrieving city: {city} at :(lat, long)')
```

    Retrieving city: kurumkan at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: isangel at :(lat, long)
    Retrieving city: port hardy at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: bar harbor at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: krasnoarmeyskiy at :(lat, long)
    Retrieving city: ahipara at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: muzaffarabad at :(lat, long)
    Retrieving city: east london at :(lat, long)
    Retrieving city: kaitangata at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: saint-philippe at :(lat, long)
    Retrieving city: sitka at :(lat, long)
    Retrieving city: saskylakh at :(lat, long)
    Retrieving city: angicos at :(lat, long)
    Retrieving city: bengkulu at :(lat, long)
    Retrieving city: sorland at :(lat, long)
    Retrieving city: sola at :(lat, long)
    Retrieving city: norman wells at :(lat, long)
    Retrieving city: castro at :(lat, long)
    Retrieving city: port alfred at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: yellowknife at :(lat, long)
    Retrieving city: hermanus at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: lebu at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: touros at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: longyearbyen at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: sirari at :(lat, long)
    Retrieving city: mahebourg at :(lat, long)
    Retrieving city: amderma at :(lat, long)
    Retrieving city: morris at :(lat, long)
    Retrieving city: saleaula at :(lat, long)
    Retrieving city: samusu at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: east london at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: carnarvon at :(lat, long)
    Retrieving city: belushya guba at :(lat, long)
    Retrieving city: saskylakh at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: east london at :(lat, long)
    Retrieving city: berlevag at :(lat, long)
    Retrieving city: port alfred at :(lat, long)
    Retrieving city: tuktoyaktuk at :(lat, long)
    Retrieving city: avarua at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: tilichiki at :(lat, long)
    Retrieving city: hami at :(lat, long)
    Retrieving city: aklavik at :(lat, long)
    Retrieving city: strai at :(lat, long)
    Retrieving city: sao felix do xingu at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: matara at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: hithadhoo at :(lat, long)
    Retrieving city: mahebourg at :(lat, long)
    Retrieving city: ancud at :(lat, long)
    Retrieving city: vilcun at :(lat, long)
    Retrieving city: victor harbor at :(lat, long)
    Retrieving city: mount gambier at :(lat, long)
    Retrieving city: boueni at :(lat, long)
    Retrieving city: karaul at :(lat, long)
    Retrieving city: port alfred at :(lat, long)
    Retrieving city: olafsvik at :(lat, long)
    Retrieving city: tasiilaq at :(lat, long)
    Retrieving city: capao da canoa at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: mount isa at :(lat, long)
    Retrieving city: basco at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: chokurdakh at :(lat, long)
    Retrieving city: avarua at :(lat, long)
    Retrieving city: columbus at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: belushya guba at :(lat, long)
    Retrieving city: zonguldak at :(lat, long)
    Retrieving city: taltal at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: ancud at :(lat, long)
    Retrieving city: ahipara at :(lat, long)
    Retrieving city: qaanaaq at :(lat, long)
    Retrieving city: necochea at :(lat, long)
    Retrieving city: dikson at :(lat, long)
    Retrieving city: lazarev at :(lat, long)
    Retrieving city: verkhoyansk at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: gat at :(lat, long)
    Retrieving city: ambilobe at :(lat, long)
    Retrieving city: ponta do sol at :(lat, long)
    Retrieving city: hermanus at :(lat, long)
    Retrieving city: luderitz at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: kayerkan at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: puri at :(lat, long)
    Retrieving city: nanortalik at :(lat, long)
    Retrieving city: butaritari at :(lat, long)
    Retrieving city: cherskiy at :(lat, long)
    Retrieving city: mildura at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: juba at :(lat, long)
    Retrieving city: balrampur at :(lat, long)
    Retrieving city: mabaruma at :(lat, long)
    Retrieving city: barrow at :(lat, long)
    Retrieving city: khash at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: kruisfontein at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: bethel at :(lat, long)
    Retrieving city: tiksi at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: toungoo at :(lat, long)
    Retrieving city: cabra at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: seoul at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: shingu at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: port lincoln at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: bonavista at :(lat, long)
    Retrieving city: dolinsk at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: cidreira at :(lat, long)
    Retrieving city: tommot at :(lat, long)
    Retrieving city: castro at :(lat, long)
    Retrieving city: kavaratti at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: olafsvik at :(lat, long)
    Retrieving city: amderma at :(lat, long)
    Retrieving city: tsihombe at :(lat, long)
    Retrieving city: beringovskiy at :(lat, long)
    Retrieving city: lukovetskiy at :(lat, long)
    Retrieving city: sao joao da barra at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: barrow at :(lat, long)
    Retrieving city: kodiak at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: sentyabrskiy at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: port blair at :(lat, long)
    Retrieving city: usinsk at :(lat, long)
    Retrieving city: almaty at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: izhma at :(lat, long)
    Retrieving city: mayumba at :(lat, long)
    Retrieving city: diego de almagro at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: barrow at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: harer at :(lat, long)
    Retrieving city: urusha at :(lat, long)
    Retrieving city: fortuna at :(lat, long)
    Retrieving city: pitimbu at :(lat, long)
    Retrieving city: umm durman at :(lat, long)
    Retrieving city: halalo at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: kawalu at :(lat, long)
    Retrieving city: touros at :(lat, long)
    Retrieving city: bintulu at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: gogrial at :(lat, long)
    Retrieving city: sao felix do xingu at :(lat, long)
    Retrieving city: bodden town at :(lat, long)
    Retrieving city: kaitangata at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: avarua at :(lat, long)
    Retrieving city: katsuura at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: meulaboh at :(lat, long)
    Retrieving city: esna at :(lat, long)
    Retrieving city: lompoc at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: luderitz at :(lat, long)
    Retrieving city: doha at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: soe at :(lat, long)
    Retrieving city: norman wells at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: mar del plata at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: axim at :(lat, long)
    Retrieving city: tumannyy at :(lat, long)
    Retrieving city: upernavik at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: aswan at :(lat, long)
    Retrieving city: sibolga at :(lat, long)
    Retrieving city: puerto ayora at :(lat, long)
    Retrieving city: sitka at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: kavieng at :(lat, long)
    Retrieving city: iqaluit at :(lat, long)
    Retrieving city: luganville at :(lat, long)
    Retrieving city: kapoeta at :(lat, long)
    Retrieving city: grand centre at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: bend at :(lat, long)
    Retrieving city: new norfolk at :(lat, long)
    Retrieving city: marawi at :(lat, long)
    Retrieving city: new norfolk at :(lat, long)
    Retrieving city: albion at :(lat, long)
    Retrieving city: mabaruma at :(lat, long)
    Retrieving city: chuy at :(lat, long)
    Retrieving city: samusu at :(lat, long)
    Retrieving city: avarua at :(lat, long)
    Retrieving city: ornskoldsvik at :(lat, long)
    Retrieving city: mancio lima at :(lat, long)
    Retrieving city: luganville at :(lat, long)
    Retrieving city: vryburg at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: port alfred at :(lat, long)
    Retrieving city: tiksi at :(lat, long)
    Retrieving city: bethel at :(lat, long)
    Retrieving city: luanda at :(lat, long)
    Retrieving city: tuktoyaktuk at :(lat, long)
    Retrieving city: domoni at :(lat, long)
    Retrieving city: khatanga at :(lat, long)
    Retrieving city: mar del plata at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: tasiilaq at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: hilo at :(lat, long)
    Retrieving city: soavinandriana at :(lat, long)
    Retrieving city: poum at :(lat, long)
    Retrieving city: east london at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: vaitupu at :(lat, long)
    Retrieving city: khatanga at :(lat, long)
    Retrieving city: pafos at :(lat, long)
    Retrieving city: cherskiy at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: tomatlan at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: tiksi at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: aklavik at :(lat, long)
    Retrieving city: ossora at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: cherskiy at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: ambodifototra at :(lat, long)
    Retrieving city: bredasdorp at :(lat, long)
    Retrieving city: qaanaaq at :(lat, long)
    Retrieving city: avarua at :(lat, long)
    Retrieving city: puerto ayora at :(lat, long)
    Retrieving city: grants pass at :(lat, long)
    Retrieving city: tiksi at :(lat, long)
    Retrieving city: kathu at :(lat, long)
    Retrieving city: attawapiskat at :(lat, long)
    Retrieving city: bredasdorp at :(lat, long)
    Retrieving city: castro at :(lat, long)
    Retrieving city: kudahuvadhoo at :(lat, long)
    Retrieving city: kirillov at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: hamilton at :(lat, long)
    Retrieving city: zhanaozen at :(lat, long)
    Retrieving city: asau at :(lat, long)
    Retrieving city: saldanha at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: vila velha at :(lat, long)
    Retrieving city: krasnovishersk at :(lat, long)
    Retrieving city: neuquen at :(lat, long)
    Retrieving city: jizan at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: alofi at :(lat, long)
    Retrieving city: north bend at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: berdigestyakh at :(lat, long)
    Retrieving city: nikolskoye at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: port elizabeth at :(lat, long)
    Retrieving city: westport at :(lat, long)
    Retrieving city: port augusta at :(lat, long)
    Retrieving city: zaysan at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: lianran at :(lat, long)
    Retrieving city: puerto ayora at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: faanui at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: castro at :(lat, long)
    Retrieving city: belushya guba at :(lat, long)
    Retrieving city: rio grande at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: saskylakh at :(lat, long)
    Retrieving city: san jose at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: verkhnyaya toyma at :(lat, long)
    Retrieving city: ponta delgada at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: saldanha at :(lat, long)
    Retrieving city: torbay at :(lat, long)
    Retrieving city: geraldton at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: burnie at :(lat, long)
    Retrieving city: faanui at :(lat, long)
    Retrieving city: hermanus at :(lat, long)
    Retrieving city: starkville at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: moyo at :(lat, long)
    Retrieving city: keuruu at :(lat, long)
    Retrieving city: yueyang at :(lat, long)
    Retrieving city: rapar at :(lat, long)
    Retrieving city: haines junction at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: lebu at :(lat, long)
    Retrieving city: tambopata at :(lat, long)
    Retrieving city: coahuayana at :(lat, long)
    Retrieving city: olavarria at :(lat, long)
    Retrieving city: barentsburg at :(lat, long)
    Retrieving city: butaritari at :(lat, long)
    Retrieving city: sur at :(lat, long)
    Retrieving city: iqaluit at :(lat, long)
    Retrieving city: mitchell at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: fortuna at :(lat, long)
    Retrieving city: arraial do cabo at :(lat, long)
    Retrieving city: tougue at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: la palma at :(lat, long)
    Retrieving city: port hardy at :(lat, long)
    Retrieving city: talnakh at :(lat, long)
    Retrieving city: angoche at :(lat, long)
    Retrieving city: lafia at :(lat, long)
    Retrieving city: lucea at :(lat, long)
    Retrieving city: oranjemund at :(lat, long)
    Retrieving city: caravelas at :(lat, long)
    Retrieving city: mahebourg at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: thompson at :(lat, long)
    Retrieving city: thompson at :(lat, long)
    Retrieving city: faanui at :(lat, long)
    Retrieving city: puerto baquerizo moreno at :(lat, long)
    Retrieving city: saint-augustin at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: iqaluit at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: thompson at :(lat, long)
    Retrieving city: cabo san lucas at :(lat, long)
    Retrieving city: daru at :(lat, long)
    Retrieving city: barentsburg at :(lat, long)
    Retrieving city: new norfolk at :(lat, long)
    Retrieving city: faanui at :(lat, long)
    Retrieving city: umzimvubu at :(lat, long)
    Retrieving city: hithadhoo at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: rawannawi at :(lat, long)
    Retrieving city: ilulissat at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: bredasdorp at :(lat, long)
    Retrieving city: goderich at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: grindavik at :(lat, long)
    Retrieving city: baruun-urt at :(lat, long)
    Retrieving city: avarua at :(lat, long)
    Retrieving city: geraldton at :(lat, long)
    Retrieving city: comodoro rivadavia at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: nhulunbuy at :(lat, long)
    Retrieving city: codrington at :(lat, long)
    Retrieving city: shenjiamen at :(lat, long)
    Retrieving city: dingle at :(lat, long)
    Retrieving city: bosaso at :(lat, long)
    Retrieving city: yuli at :(lat, long)
    Retrieving city: airai at :(lat, long)
    Retrieving city: yaan at :(lat, long)
    Retrieving city: marzuq at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: lagoa at :(lat, long)
    Retrieving city: katsuura at :(lat, long)
    Retrieving city: marinette at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: namibe at :(lat, long)
    Retrieving city: tsihombe at :(lat, long)
    Retrieving city: nisia floresta at :(lat, long)
    Retrieving city: belushya guba at :(lat, long)
    Retrieving city: akyab at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: geraldton at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: dois vizinhos at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: tasiilaq at :(lat, long)
    Retrieving city: khatanga at :(lat, long)
    Retrieving city: puerto del rosario at :(lat, long)
    Retrieving city: beringovskiy at :(lat, long)
    Retrieving city: yar-sale at :(lat, long)
    Retrieving city: tiarei at :(lat, long)
    Retrieving city: zhanakorgan at :(lat, long)
    Retrieving city: bredasdorp at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: samalaeulu at :(lat, long)
    Retrieving city: santa vitoria do palmar at :(lat, long)
    Retrieving city: kahului at :(lat, long)
    Retrieving city: sistranda at :(lat, long)
    Retrieving city: tessalit at :(lat, long)
    Retrieving city: cayenne at :(lat, long)
    Retrieving city: obo at :(lat, long)
    Retrieving city: dikson at :(lat, long)
    Retrieving city: tuktoyaktuk at :(lat, long)
    Retrieving city: castro at :(lat, long)
    Retrieving city: victoria at :(lat, long)
    Retrieving city: tiksi at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: tuktoyaktuk at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: yokadouma at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: anadyr at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: palmer at :(lat, long)
    Retrieving city: berdigestyakh at :(lat, long)
    Retrieving city: attawapiskat at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: greytown at :(lat, long)
    Retrieving city: avarua at :(lat, long)
    Retrieving city: puerto ayora at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: grand river south east at :(lat, long)
    Retrieving city: hermanus at :(lat, long)
    Retrieving city: provideniya at :(lat, long)
    Retrieving city: goteborg at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: haguenau at :(lat, long)
    Retrieving city: kruisfontein at :(lat, long)
    Retrieving city: port elizabeth at :(lat, long)
    Retrieving city: bonavista at :(lat, long)
    Retrieving city: saint-philippe at :(lat, long)
    Retrieving city: saint-augustin at :(lat, long)
    Retrieving city: praia da vitoria at :(lat, long)
    Retrieving city: rio verde de mato grosso at :(lat, long)
    Retrieving city: petropavlovskoye at :(lat, long)
    Retrieving city: lavrentiya at :(lat, long)
    Retrieving city: kiama at :(lat, long)
    Retrieving city: fuxin at :(lat, long)
    Retrieving city: tommot at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: doha at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: puerto ayora at :(lat, long)
    Retrieving city: aizawl at :(lat, long)
    Retrieving city: cidreira at :(lat, long)
    Retrieving city: geraldton at :(lat, long)
    Retrieving city: provideniya at :(lat, long)
    Retrieving city: hermanus at :(lat, long)
    Retrieving city: new norfolk at :(lat, long)
    Retrieving city: kovdor at :(lat, long)
    Retrieving city: usvyaty at :(lat, long)
    Retrieving city: nouadhibou at :(lat, long)
    Retrieving city: arraial do cabo at :(lat, long)
    Retrieving city: san quintin at :(lat, long)
    Retrieving city: zhanakorgan at :(lat, long)
    Retrieving city: kandrian at :(lat, long)
    Retrieving city: sobradinho at :(lat, long)
    Retrieving city: port alfred at :(lat, long)
    Retrieving city: hermanus at :(lat, long)
    Retrieving city: nikolayevsk-na-amure at :(lat, long)
    Retrieving city: chuy at :(lat, long)
    Retrieving city: nicoya at :(lat, long)
    Retrieving city: traverse city at :(lat, long)
    Retrieving city: castro at :(lat, long)
    Retrieving city: tuktoyaktuk at :(lat, long)
    Retrieving city: lebu at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: bellavista at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: port alfred at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: ilam at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: port alfred at :(lat, long)
    Retrieving city: tsihombe at :(lat, long)
    Retrieving city: la asuncion at :(lat, long)
    Retrieving city: marcona at :(lat, long)
    Retrieving city: galesong at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: calabozo at :(lat, long)
    Retrieving city: tanete at :(lat, long)
    Retrieving city: pokrovsk at :(lat, long)
    Retrieving city: luorong at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: te anau at :(lat, long)
    Retrieving city: vestmannaeyjar at :(lat, long)
    Retrieving city: puerto del rosario at :(lat, long)
    Retrieving city: waddan at :(lat, long)
    Retrieving city: sao miguel do araguaia at :(lat, long)
    Retrieving city: butaritari at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: farmington at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: lavrentiya at :(lat, long)
    Retrieving city: ostrovnoy at :(lat, long)
    Retrieving city: cherskiy at :(lat, long)
    Retrieving city: teguise at :(lat, long)
    Retrieving city: codrington at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: ketchikan at :(lat, long)
    Retrieving city: iroquois falls at :(lat, long)
    Retrieving city: cayenne at :(lat, long)
    Retrieving city: vila franca do campo at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: swift current at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: mount gambier at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: mahebourg at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: nikolskoye at :(lat, long)
    Retrieving city: chokurdakh at :(lat, long)
    Retrieving city: cabedelo at :(lat, long)
    Retrieving city: bandarbeyla at :(lat, long)
    Retrieving city: khatanga at :(lat, long)
    Retrieving city: kodiak at :(lat, long)
    Retrieving city: chokurdakh at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: darab at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: leningradskiy at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: pachora at :(lat, long)
    Retrieving city: lavrentiya at :(lat, long)
    Retrieving city: healdsburg at :(lat, long)
    Retrieving city: leningradskaya at :(lat, long)
    Retrieving city: hermanus at :(lat, long)
    Retrieving city: chokurdakh at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: khatanga at :(lat, long)
    Retrieving city: east london at :(lat, long)
    Retrieving city: saint-philippe at :(lat, long)
    Retrieving city: corpus christi at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: port elizabeth at :(lat, long)
    Retrieving city: challapata at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: nansio at :(lat, long)
    Retrieving city: kavieng at :(lat, long)
    Retrieving city: gurupa at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: bubaque at :(lat, long)
    Retrieving city: lorengau at :(lat, long)
    Retrieving city: san cristobal at :(lat, long)
    Retrieving city: uray at :(lat, long)
    Retrieving city: roald at :(lat, long)
    Retrieving city: afmadu at :(lat, long)
    Retrieving city: melville at :(lat, long)
    Retrieving city: ola at :(lat, long)
    Retrieving city: nikolskoye at :(lat, long)
    Retrieving city: mapastepec at :(lat, long)
    Retrieving city: aviles at :(lat, long)
    Retrieving city: zolotonosha at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: eureka at :(lat, long)
    Retrieving city: kuche at :(lat, long)
    Retrieving city: sao filipe at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: longyearbyen at :(lat, long)
    Retrieving city: myitkyina at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: roma at :(lat, long)
    Retrieving city: vaitupu at :(lat, long)
    Retrieving city: shubarshi at :(lat, long)
    Retrieving city: jian at :(lat, long)
    Retrieving city: tsihombe at :(lat, long)
    Retrieving city: wuwei at :(lat, long)
    Retrieving city: noumea at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: antofagasta at :(lat, long)
    Retrieving city: qaanaaq at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: arraial do cabo at :(lat, long)
    Retrieving city: bolshaya martynovka at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: lavrentiya at :(lat, long)
    Retrieving city: pevek at :(lat, long)
    Retrieving city: rajanpur at :(lat, long)
    Retrieving city: cayenne at :(lat, long)
    Retrieving city: mbarara at :(lat, long)
    Retrieving city: teguldet at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: shingu at :(lat, long)
    Retrieving city: luderitz at :(lat, long)
    Retrieving city: laguna at :(lat, long)
    Retrieving city: mersing at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: prieska at :(lat, long)
    Retrieving city: umzimvubu at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: puerto ayora at :(lat, long)
    Retrieving city: pindi bhattian at :(lat, long)
    Retrieving city: puerto ayora at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: karratha at :(lat, long)
    Retrieving city: torbay at :(lat, long)
    Retrieving city: narsaq at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: mys shmidta at :(lat, long)
    Retrieving city: saskylakh at :(lat, long)
    Retrieving city: barra patuca at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: gamba at :(lat, long)
    Retrieving city: ponta do sol at :(lat, long)
    Retrieving city: upernavik at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: les cayes at :(lat, long)
    Retrieving city: yar-sale at :(lat, long)
    Retrieving city: pochutla at :(lat, long)
    Retrieving city: ponta do sol at :(lat, long)
    Retrieving city: lolua at :(lat, long)
    Retrieving city: buluang at :(lat, long)
    Retrieving city: bredasdorp at :(lat, long)
    Retrieving city: rosamorada at :(lat, long)
    Retrieving city: hilo at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: barrow at :(lat, long)
    Retrieving city: leningradskiy at :(lat, long)
    Retrieving city: pithapuram at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: tilichiki at :(lat, long)
    Retrieving city: coahuayana at :(lat, long)
    Retrieving city: hermanus at :(lat, long)
    Retrieving city: salinopolis at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: bukachacha at :(lat, long)
    Retrieving city: biak at :(lat, long)
    Retrieving city: norman wells at :(lat, long)
    Retrieving city: mareeba at :(lat, long)
    Retrieving city: norrtalje at :(lat, long)
    Retrieving city: aklavik at :(lat, long)
    Retrieving city: bonthe at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: tiksi at :(lat, long)
    Retrieving city: zomba at :(lat, long)
    Retrieving city: bambous virieux at :(lat, long)
    Retrieving city: new norfolk at :(lat, long)
    Retrieving city: taoudenni at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: leningradskiy at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: kudahuvadhoo at :(lat, long)
    Retrieving city: saskylakh at :(lat, long)
    Retrieving city: mahina at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: victoria at :(lat, long)
    Retrieving city: churapcha at :(lat, long)
    Retrieving city: yellowknife at :(lat, long)
    Retrieving city: mys shmidta at :(lat, long)
    Retrieving city: bur gabo at :(lat, long)
    Retrieving city: rudnichnyy at :(lat, long)
    Retrieving city: ilulissat at :(lat, long)
    Retrieving city: east london at :(lat, long)
    Retrieving city: gunjur at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: avarua at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: samusu at :(lat, long)
    Retrieving city: port-gentil at :(lat, long)
    Retrieving city: brae at :(lat, long)
    Retrieving city: saint-philippe at :(lat, long)
    Retrieving city: tsihombe at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: belushya guba at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: nuuk at :(lat, long)
    Retrieving city: laguna at :(lat, long)
    Retrieving city: bucerias at :(lat, long)
    Retrieving city: lorengau at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: hilo at :(lat, long)
    Retrieving city: kochki at :(lat, long)
    Retrieving city: bredasdorp at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: severo-kurilsk at :(lat, long)
    Retrieving city: tsihombe at :(lat, long)
    Retrieving city: fortuna at :(lat, long)
    Retrieving city: faanui at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: maltahohe at :(lat, long)
    Retrieving city: tuktoyaktuk at :(lat, long)
    Retrieving city: bambous virieux at :(lat, long)
    Retrieving city: kahului at :(lat, long)
    Retrieving city: sitka at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: kajaani at :(lat, long)
    Retrieving city: hithadhoo at :(lat, long)
    Retrieving city: saskylakh at :(lat, long)
    Retrieving city: san patricio at :(lat, long)
    Retrieving city: bambous virieux at :(lat, long)
    Retrieving city: kota kinabalu at :(lat, long)
    Retrieving city: seoul at :(lat, long)
    Retrieving city: grand centre at :(lat, long)
    Retrieving city: paradwip at :(lat, long)
    Retrieving city: yaan at :(lat, long)
    Retrieving city: hilo at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: shatalovo at :(lat, long)
    Retrieving city: kentau at :(lat, long)
    Retrieving city: asau at :(lat, long)
    Retrieving city: nome at :(lat, long)
    Retrieving city: cherskiy at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: norman wells at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: bilaspur at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: galiwinku at :(lat, long)
    Retrieving city: ixtapa at :(lat, long)
    Retrieving city: khatanga at :(lat, long)
    Retrieving city: visnes at :(lat, long)
    Retrieving city: arraial do cabo at :(lat, long)
    Retrieving city: udachnyy at :(lat, long)
    Retrieving city: castro at :(lat, long)
    Retrieving city: boshnyakovo at :(lat, long)
    Retrieving city: east london at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: iqaluit at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: camacha at :(lat, long)
    Retrieving city: asau at :(lat, long)
    Retrieving city: margate at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: ngunguru at :(lat, long)
    Retrieving city: ahipara at :(lat, long)
    Retrieving city: broome at :(lat, long)
    Retrieving city: vaitupu at :(lat, long)
    Retrieving city: ardistan at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: boa vista at :(lat, long)
    Retrieving city: nortelandia at :(lat, long)
    Retrieving city: butaritari at :(lat, long)
    Retrieving city: leningradskiy at :(lat, long)
    Retrieving city: upernavik at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: tsihombe at :(lat, long)
    Retrieving city: kaitangata at :(lat, long)
    Retrieving city: hermanus at :(lat, long)
    Retrieving city: kavaratti at :(lat, long)
    Retrieving city: kodiak at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: jardim at :(lat, long)
    Retrieving city: vestmanna at :(lat, long)
    Retrieving city: port elizabeth at :(lat, long)
    Retrieving city: novo aripuana at :(lat, long)
    Retrieving city: sitka at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: nikolskoye at :(lat, long)
    Retrieving city: luderitz at :(lat, long)
    Retrieving city: kuche at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: butaritari at :(lat, long)
    Retrieving city: samusu at :(lat, long)
    Retrieving city: qaanaaq at :(lat, long)
    Retrieving city: bethel at :(lat, long)
    Retrieving city: chifeng at :(lat, long)
    Retrieving city: cabo san lucas at :(lat, long)
    Retrieving city: belushya guba at :(lat, long)
    Retrieving city: port alfred at :(lat, long)
    Retrieving city: khandyga at :(lat, long)
    Retrieving city: nhamunda at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: alyangula at :(lat, long)
    Retrieving city: morondava at :(lat, long)
    Retrieving city: alamosa at :(lat, long)
    Retrieving city: barentsburg at :(lat, long)
    Retrieving city: hoi an at :(lat, long)
    Retrieving city: rexburg at :(lat, long)
    Retrieving city: qaanaaq at :(lat, long)
    Retrieving city: mishkino at :(lat, long)
    Retrieving city: khash at :(lat, long)
    Retrieving city: lithakia at :(lat, long)
    Retrieving city: mahebourg at :(lat, long)
    Retrieving city: paradwip at :(lat, long)
    Retrieving city: miri at :(lat, long)
    Retrieving city: nikolskoye at :(lat, long)
    Retrieving city: maragogi at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: ponta do sol at :(lat, long)
    Retrieving city: surt at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: diego de almagro at :(lat, long)
    Retrieving city: pierre at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: klaksvik at :(lat, long)
    Retrieving city: nizhniy tsasuchey at :(lat, long)
    Retrieving city: tiksi at :(lat, long)
    Retrieving city: vallenar at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: canmore at :(lat, long)
    Retrieving city: davila at :(lat, long)
    Retrieving city: conceicao do rio verde at :(lat, long)
    Retrieving city: belushya guba at :(lat, long)
    Retrieving city: basoko at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: bethel at :(lat, long)
    Retrieving city: kapoeta at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: bocana de paiwas at :(lat, long)
    Retrieving city: hualmay at :(lat, long)
    Retrieving city: zhitikara at :(lat, long)
    Retrieving city: guerrero negro at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: sassandra at :(lat, long)
    Retrieving city: aswan at :(lat, long)
    Retrieving city: karpushikha at :(lat, long)
    Retrieving city: orodara at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: esfahan at :(lat, long)
    Retrieving city: sentyabrskiy at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: cockburn harbour at :(lat, long)
    Retrieving city: guymon at :(lat, long)
    Retrieving city: carnarvon at :(lat, long)
    Retrieving city: lienz at :(lat, long)
    Retrieving city: tuktoyaktuk at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: chauk at :(lat, long)
    Retrieving city: perene at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: hasaki at :(lat, long)
    Retrieving city: haibowan at :(lat, long)
    Retrieving city: bambous virieux at :(lat, long)
    Retrieving city: dikson at :(lat, long)
    Retrieving city: sakakah at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: chara at :(lat, long)
    Retrieving city: krivodol at :(lat, long)
    Retrieving city: bethel at :(lat, long)
    Retrieving city: arraial do cabo at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: bocas del toro at :(lat, long)
    Retrieving city: yellowknife at :(lat, long)
    Retrieving city: mys shmidta at :(lat, long)
    Retrieving city: henties bay at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: new norfolk at :(lat, long)
    Retrieving city: bambous virieux at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: isangel at :(lat, long)
    Retrieving city: cabo san lucas at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: alice springs at :(lat, long)
    Retrieving city: durusu at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: hasaki at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: barrow at :(lat, long)
    Retrieving city: amurzet at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: castro at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: vila franca do campo at :(lat, long)
    Retrieving city: bangassou at :(lat, long)
    Retrieving city: hasaki at :(lat, long)
    Retrieving city: belushya guba at :(lat, long)
    Retrieving city: karratha at :(lat, long)
    Retrieving city: klaksvik at :(lat, long)
    Retrieving city: butaritari at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: xining at :(lat, long)
    Retrieving city: victoria at :(lat, long)
    Retrieving city: hithadhoo at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: sitka at :(lat, long)
    Retrieving city: saint-philippe at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: saskylakh at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: puerto ayora at :(lat, long)
    Retrieving city: mudbidri at :(lat, long)
    Retrieving city: mitzic at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: memphis at :(lat, long)
    Retrieving city: minusinsk at :(lat, long)
    Retrieving city: kokopo at :(lat, long)
    Retrieving city: fujin at :(lat, long)
    Retrieving city: thompson at :(lat, long)
    Retrieving city: saint-philippe at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: la orilla at :(lat, long)
    Retrieving city: matsanga at :(lat, long)
    Retrieving city: portel at :(lat, long)
    Retrieving city: norman wells at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: tuktoyaktuk at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: dingle at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: shimoda at :(lat, long)
    Retrieving city: qaanaaq at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: castro at :(lat, long)
    Retrieving city: banda aceh at :(lat, long)
    Retrieving city: palu at :(lat, long)
    Retrieving city: kangasala at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: butaritari at :(lat, long)
    Retrieving city: kenai at :(lat, long)
    Retrieving city: haines junction at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: taburi at :(lat, long)
    Retrieving city: norman wells at :(lat, long)
    Retrieving city: puerto ayora at :(lat, long)
    Retrieving city: isangel at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: samusu at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: muros at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: grand river south east at :(lat, long)
    Retrieving city: bredasdorp at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: bintulu at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: eureka at :(lat, long)
    Retrieving city: the valley at :(lat, long)
    Retrieving city: tiksi at :(lat, long)
    Retrieving city: north bend at :(lat, long)
    Retrieving city: el dorado at :(lat, long)
    Retrieving city: tiksi at :(lat, long)
    Retrieving city: port elizabeth at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: aasiaat at :(lat, long)
    Retrieving city: guaruja at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: khani at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: winton at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: longyearbyen at :(lat, long)
    Retrieving city: sibolga at :(lat, long)
    Retrieving city: koungou at :(lat, long)
    Retrieving city: mar del plata at :(lat, long)
    Retrieving city: taonan at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: barrow at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: beloha at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: maceio at :(lat, long)
    Retrieving city: saint-philippe at :(lat, long)
    Retrieving city: amderma at :(lat, long)
    Retrieving city: peace river at :(lat, long)
    Retrieving city: san jeronimo at :(lat, long)
    Retrieving city: barrow at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: katsuura at :(lat, long)
    Retrieving city: josanicka banja at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: puerto del rosario at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: dikson at :(lat, long)
    Retrieving city: yellowknife at :(lat, long)
    Retrieving city: castro at :(lat, long)
    Retrieving city: dong hoi at :(lat, long)
    Retrieving city: sigli at :(lat, long)
    Retrieving city: castro at :(lat, long)
    Retrieving city: canutama at :(lat, long)
    Retrieving city: barrow at :(lat, long)
    Retrieving city: mar del plata at :(lat, long)
    Retrieving city: mayskiy at :(lat, long)
    Retrieving city: sovetskiy at :(lat, long)
    Retrieving city: vestmanna at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: victoria at :(lat, long)
    Retrieving city: new norfolk at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: muros at :(lat, long)
    Retrieving city: lerwick at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: arraial do cabo at :(lat, long)
    Retrieving city: lompoc at :(lat, long)
    Retrieving city: sabana abajo at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: dudinka at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: novo aripuana at :(lat, long)
    Retrieving city: malwan at :(lat, long)
    Retrieving city: carnarvon at :(lat, long)
    Retrieving city: misratah at :(lat, long)
    Retrieving city: sabzevar at :(lat, long)
    Retrieving city: rawah at :(lat, long)
    Retrieving city: goundam at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: camacha at :(lat, long)
    Retrieving city: chernyshevskiy at :(lat, long)
    Retrieving city: belushya guba at :(lat, long)
    Retrieving city: airai at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: junction city at :(lat, long)
    Retrieving city: weligama at :(lat, long)
    Retrieving city: lavrentiya at :(lat, long)
    Retrieving city: upernavik at :(lat, long)
    Retrieving city: dunedin at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: barentsburg at :(lat, long)
    Retrieving city: tasiilaq at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: mitsamiouli at :(lat, long)
    Retrieving city: nizhneyansk at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: longyearbyen at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: bredasdorp at :(lat, long)
    Retrieving city: airai at :(lat, long)
    Retrieving city: chokurdakh at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: mount isa at :(lat, long)
    Retrieving city: hilo at :(lat, long)
    Retrieving city: kodiak at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: longyearbyen at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: bethel at :(lat, long)
    Retrieving city: kungurtug at :(lat, long)
    Retrieving city: bethel at :(lat, long)
    Retrieving city: rantepao at :(lat, long)
    Retrieving city: iqaluit at :(lat, long)
    Retrieving city: brokopondo at :(lat, long)
    Retrieving city: narsaq at :(lat, long)
    Retrieving city: port alfred at :(lat, long)
    Retrieving city: nikolskoye at :(lat, long)
    Retrieving city: serowe at :(lat, long)
    Retrieving city: puerto ayora at :(lat, long)
    Retrieving city: east london at :(lat, long)
    Retrieving city: hermanus at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: qaanaaq at :(lat, long)
    Retrieving city: laguna at :(lat, long)
    Retrieving city: saint-philippe at :(lat, long)
    Retrieving city: saint-philippe at :(lat, long)
    Retrieving city: hermanus at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: severo-kurilsk at :(lat, long)
    Retrieving city: tuatapere at :(lat, long)
    Retrieving city: iqaluit at :(lat, long)
    Retrieving city: swan hill at :(lat, long)
    Retrieving city: toliary at :(lat, long)
    Retrieving city: vaitupu at :(lat, long)
    Retrieving city: kendal at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: leningradskiy at :(lat, long)
    Retrieving city: hilo at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: necochea at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: jiwani at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: bethel at :(lat, long)
    Retrieving city: khatanga at :(lat, long)
    Retrieving city: sao luiz gonzaga at :(lat, long)
    Retrieving city: luocheng at :(lat, long)
    Retrieving city: changji at :(lat, long)
    Retrieving city: geraldton at :(lat, long)
    Retrieving city: klaksvik at :(lat, long)
    Retrieving city: lianran at :(lat, long)
    Retrieving city: villa del rosario at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: grass valley at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: tilichiki at :(lat, long)
    Retrieving city: namibe at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: manggar at :(lat, long)
    Retrieving city: kalanguy at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: nichinan at :(lat, long)
    Retrieving city: kangaatsiaq at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: belushya guba at :(lat, long)
    Retrieving city: fez at :(lat, long)
    Retrieving city: eureka at :(lat, long)
    Retrieving city: marcona at :(lat, long)
    Retrieving city: ahuimanu at :(lat, long)
    Retrieving city: longyearbyen at :(lat, long)
    Retrieving city: kloulklubed at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: tsihombe at :(lat, long)
    Retrieving city: kichera at :(lat, long)
    Retrieving city: kavieng at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: barrow at :(lat, long)
    Retrieving city: cabo san lucas at :(lat, long)
    Retrieving city: mar del plata at :(lat, long)
    Retrieving city: palembang at :(lat, long)
    Retrieving city: pangody at :(lat, long)
    Retrieving city: thompson at :(lat, long)
    Retrieving city: quatre cocos at :(lat, long)
    Retrieving city: zambezi at :(lat, long)
    Retrieving city: aklavik at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: victoria at :(lat, long)
    Retrieving city: san patricio at :(lat, long)
    Retrieving city: mareeba at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: plettenberg bay at :(lat, long)
    Retrieving city: yellowknife at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: rewari at :(lat, long)
    Retrieving city: padang at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: namibe at :(lat, long)
    Retrieving city: vostok at :(lat, long)
    Retrieving city: tsihombe at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: qaanaaq at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: barentsburg at :(lat, long)
    Retrieving city: coquimbo at :(lat, long)
    Retrieving city: tommot at :(lat, long)
    Retrieving city: batemans bay at :(lat, long)
    Retrieving city: north bend at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: port alberni at :(lat, long)
    Retrieving city: mantua at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: souillac at :(lat, long)
    Retrieving city: elizabethtown at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: tiksi at :(lat, long)
    Retrieving city: mokhsogollokh at :(lat, long)
    Retrieving city: thompson at :(lat, long)
    Retrieving city: provideniya at :(lat, long)
    Retrieving city: pevek at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: aflu at :(lat, long)
    Retrieving city: bedford at :(lat, long)
    Retrieving city: bengkulu at :(lat, long)
    Retrieving city: corralillo at :(lat, long)
    Retrieving city: thompson at :(lat, long)
    Retrieving city: beringovskiy at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: tuktoyaktuk at :(lat, long)
    Retrieving city: mackay at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: sorland at :(lat, long)
    Retrieving city: taltal at :(lat, long)
    Retrieving city: sunndalsora at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: dikson at :(lat, long)
    Retrieving city: santa maria at :(lat, long)
    Retrieving city: ystad at :(lat, long)
    Retrieving city: palaiokhora at :(lat, long)
    Retrieving city: yellowknife at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: amderma at :(lat, long)
    Retrieving city: ulaangom at :(lat, long)
    Retrieving city: bethel at :(lat, long)
    Retrieving city: sao filipe at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: narsaq at :(lat, long)
    Retrieving city: ostrovnoy at :(lat, long)
    Retrieving city: caravelas at :(lat, long)
    Retrieving city: butaritari at :(lat, long)
    Retrieving city: palmares do sul at :(lat, long)
    Retrieving city: kawalu at :(lat, long)
    Retrieving city: owosso at :(lat, long)
    Retrieving city: fortuna at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: handwara at :(lat, long)
    Retrieving city: plouzane at :(lat, long)
    Retrieving city: zelenoborskiy at :(lat, long)
    Retrieving city: yellowknife at :(lat, long)
    Retrieving city: lorengau at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: poya at :(lat, long)
    Retrieving city: illoqqortoormiut at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: barentsburg at :(lat, long)
    Retrieving city: port hedland at :(lat, long)
    Retrieving city: chagda at :(lat, long)
    Retrieving city: vardo at :(lat, long)
    Retrieving city: loningen at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: riaba at :(lat, long)
    Retrieving city: clyde river at :(lat, long)
    Retrieving city: vila franca do campo at :(lat, long)
    Retrieving city: destin at :(lat, long)
    Retrieving city: mar del plata at :(lat, long)
    Retrieving city: tabou at :(lat, long)
    Retrieving city: tiksi at :(lat, long)
    Retrieving city: faanui at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: altamont at :(lat, long)
    Retrieving city: ilulissat at :(lat, long)
    Retrieving city: colquechaca at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: lorengau at :(lat, long)
    Retrieving city: butaritari at :(lat, long)
    Retrieving city: tiksi at :(lat, long)
    Retrieving city: chokurdakh at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: chabahar at :(lat, long)
    Retrieving city: barentsburg at :(lat, long)
    Retrieving city: belushya guba at :(lat, long)
    Retrieving city: khatanga at :(lat, long)
    Retrieving city: new norfolk at :(lat, long)
    Retrieving city: mahebourg at :(lat, long)
    Retrieving city: solnechnyy at :(lat, long)
    Retrieving city: iqaluit at :(lat, long)
    Retrieving city: provideniya at :(lat, long)
    Retrieving city: togur at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: starosubkhangulovo at :(lat, long)
    Retrieving city: upernavik at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: salinopolis at :(lat, long)
    Retrieving city: hithadhoo at :(lat, long)
    Retrieving city: placido de castro at :(lat, long)
    Retrieving city: cabo san lucas at :(lat, long)
    Retrieving city: dikson at :(lat, long)
    Retrieving city: kruisfontein at :(lat, long)
    Retrieving city: bubaque at :(lat, long)
    Retrieving city: mangan at :(lat, long)
    Retrieving city: tasbuget at :(lat, long)
    Retrieving city: mitsamiouli at :(lat, long)
    Retrieving city: tuatapere at :(lat, long)
    Retrieving city: lokosovo at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: coihaique at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: bethel at :(lat, long)
    Retrieving city: soyo at :(lat, long)
    Retrieving city: port alfred at :(lat, long)
    Retrieving city: amderma at :(lat, long)
    Retrieving city: thinadhoo at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: faanui at :(lat, long)
    Retrieving city: norman wells at :(lat, long)
    Retrieving city: kaoma at :(lat, long)
    Retrieving city: arraial do cabo at :(lat, long)
    Retrieving city: khatanga at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: gat at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: verkh-usugli at :(lat, long)
    Retrieving city: cherskiy at :(lat, long)
    Retrieving city: kismayo at :(lat, long)
    Retrieving city: fuyu at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: south sioux city at :(lat, long)
    Retrieving city: keti bandar at :(lat, long)
    Retrieving city: zlatoustovsk at :(lat, long)
    Retrieving city: souillac at :(lat, long)
    Retrieving city: pelotas at :(lat, long)
    Retrieving city: tasiilaq at :(lat, long)
    Retrieving city: comodoro rivadavia at :(lat, long)
    Retrieving city: itarema at :(lat, long)
    Retrieving city: vega de alatorre at :(lat, long)
    Retrieving city: vanimo at :(lat, long)
    Retrieving city: lorengau at :(lat, long)
    Retrieving city: valley city at :(lat, long)
    Retrieving city: porto seguro at :(lat, long)
    Retrieving city: butaritari at :(lat, long)
    Retrieving city: kaitangata at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: cumpas at :(lat, long)
    Retrieving city: faya at :(lat, long)
    Retrieving city: bakchar at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: upernavik at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: shelburne at :(lat, long)
    Retrieving city: sanbu at :(lat, long)
    Retrieving city: puerto del rosario at :(lat, long)
    Retrieving city: sao filipe at :(lat, long)
    Retrieving city: lebu at :(lat, long)
    Retrieving city: umzimvubu at :(lat, long)
    Retrieving city: bethel at :(lat, long)
    Retrieving city: bethel at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: sao sebastiao at :(lat, long)
    Retrieving city: norman wells at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: hurghada at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: loandjili at :(lat, long)
    Retrieving city: la ronge at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: tazovskiy at :(lat, long)
    Retrieving city: port alfred at :(lat, long)
    Retrieving city: ozernovskiy at :(lat, long)
    Retrieving city: porto santo at :(lat, long)
    Retrieving city: barentsburg at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: vanavara at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: port-gentil at :(lat, long)
    Retrieving city: cherskiy at :(lat, long)
    Retrieving city: zabol at :(lat, long)
    Retrieving city: meulaboh at :(lat, long)
    Retrieving city: katsuura at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: san patricio at :(lat, long)
    Retrieving city: mahebourg at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: the valley at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: butte at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: hasaki at :(lat, long)
    Retrieving city: tabialan at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: kahului at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: saint-pierre at :(lat, long)
    Retrieving city: srednekolymsk at :(lat, long)
    Retrieving city: grand baie at :(lat, long)
    Retrieving city: ribeira grande at :(lat, long)
    Retrieving city: saint-philippe at :(lat, long)
    Retrieving city: bassila at :(lat, long)
    Retrieving city: avarua at :(lat, long)
    Retrieving city: hobart at :(lat, long)
    Retrieving city: yellowknife at :(lat, long)
    Retrieving city: esperance at :(lat, long)
    Retrieving city: north bend at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: clyde river at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: kahului at :(lat, long)
    Retrieving city: kapaa at :(lat, long)
    Retrieving city: yellowknife at :(lat, long)
    Retrieving city: mahebourg at :(lat, long)
    Retrieving city: vao at :(lat, long)
    Retrieving city: evensk at :(lat, long)
    Retrieving city: slavyanka at :(lat, long)
    Retrieving city: pitimbu at :(lat, long)
    Retrieving city: fort nelson at :(lat, long)
    Retrieving city: ambon at :(lat, long)
    Retrieving city: port elizabeth at :(lat, long)
    Retrieving city: coffs harbour at :(lat, long)
    Retrieving city: new norfolk at :(lat, long)
    Retrieving city: bredasdorp at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: cidreira at :(lat, long)
    Retrieving city: yellowknife at :(lat, long)
    Retrieving city: butaritari at :(lat, long)
    Retrieving city: luderitz at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: madimba at :(lat, long)
    Retrieving city: tuktoyaktuk at :(lat, long)
    Retrieving city: yar-sale at :(lat, long)
    Retrieving city: peniche at :(lat, long)
    Retrieving city: keti bandar at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: olinda at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: lebu at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: loa janan at :(lat, long)
    Retrieving city: mao at :(lat, long)
    Retrieving city: mataura at :(lat, long)
    Retrieving city: new norfolk at :(lat, long)
    Retrieving city: faanui at :(lat, long)
    Retrieving city: flinders at :(lat, long)
    Retrieving city: lebu at :(lat, long)
    Retrieving city: clyde river at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: ushuaia at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: gizo at :(lat, long)
    Retrieving city: capoeiras at :(lat, long)
    Retrieving city: albany at :(lat, long)
    Retrieving city: robertsport at :(lat, long)
    Retrieving city: pala at :(lat, long)
    Retrieving city: carnarvon at :(lat, long)
    Retrieving city: chuy at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: mount isa at :(lat, long)
    Retrieving city: avarua at :(lat, long)
    Retrieving city: attawapiskat at :(lat, long)
    Retrieving city: jamestown at :(lat, long)
    Retrieving city: maxixe at :(lat, long)
    Retrieving city: svetlogorsk at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: eyl at :(lat, long)
    Retrieving city: mordovo at :(lat, long)
    Retrieving city: fort walton beach at :(lat, long)
    Retrieving city: layou at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: cape town at :(lat, long)
    Retrieving city: punta arenas at :(lat, long)
    Retrieving city: new norfolk at :(lat, long)
    Retrieving city: atuona at :(lat, long)
    Retrieving city: puerto ayora at :(lat, long)
    Retrieving city: rio grande at :(lat, long)
    Retrieving city: bredasdorp at :(lat, long)
    Retrieving city: busselton at :(lat, long)
    Retrieving city: nanortalik at :(lat, long)
    Retrieving city: sapele at :(lat, long)
    Retrieving city: butaritari at :(lat, long)
    Retrieving city: bluff at :(lat, long)
    Retrieving city: qaanaaq at :(lat, long)
    Retrieving city: cabo san lucas at :(lat, long)
    Retrieving city: ponta do sol at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: tuktoyaktuk at :(lat, long)
    Retrieving city: taolanaro at :(lat, long)
    Retrieving city: horki at :(lat, long)
    Retrieving city: victoria at :(lat, long)
    Retrieving city: boulder city at :(lat, long)
    Retrieving city: vaini at :(lat, long)
    Retrieving city: zhangye at :(lat, long)
    Retrieving city: zhangye at :(lat, long)
    Retrieving city: rikitea at :(lat, long)
    Retrieving city: cabo san lucas at :(lat, long)
    Retrieving city: zhenlai at :(lat, long)
    Retrieving city: georgetown at :(lat, long)
    


```python
df = pd.DataFrame(list(lat_lng.items()))
df.columns = ["city", "lat_long"]
df['lat'] = df.lat_long.map(lambda x: str(x[0]))
df['lon'] = df.lat_long.map(lambda x: str(x[1]))
df.shape
```




    (630, 4)




```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>city</th>
      <th>lat_long</th>
      <th>lat</th>
      <th>lon</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>mys shmidta</td>
      <td>(86.35963611345696, -179.30446668209328)</td>
      <td>86.35963611345696</td>
      <td>-179.30446668209328</td>
    </tr>
    <tr>
      <th>1</th>
      <td>port keats</td>
      <td>(-14.09006513168886, 127.38635613845486)</td>
      <td>-14.09006513168886</td>
      <td>127.38635613845486</td>
    </tr>
    <tr>
      <th>2</th>
      <td>dicabisagan</td>
      <td>(18.594210829707407, 126.68477156377577)</td>
      <td>18.594210829707407</td>
      <td>126.68477156377577</td>
    </tr>
    <tr>
      <th>3</th>
      <td>illoqqortoormiut</td>
      <td>(78.54333873182773, -29.949604466665363)</td>
      <td>78.54333873182773</td>
      <td>-29.949604466665363</td>
    </tr>
    <tr>
      <th>4</th>
      <td>shenjiamen</td>
      <td>(30.971105359699223, 124.63650123168748)</td>
      <td>30.971105359699223</td>
      <td>124.63650123168748</td>
    </tr>
  </tbody>
</table>
</div>



## Perform API Calls


```python
def get_current_weather(df_object):
    # OpenWeatherMap API Key
    # Starting URL for Weather Map API Call
    base_url = "http://api.openweathermap.org/data/2.5/weather"
    params = {
        'APPID' : gkey,
        'lat' : df_object.lat,
        'lon' : df_object.lon,
        'units' : 'Imperial'
    }
    data = requests.get(base_url, params=params)
    return data.json()
    time.sleep(.50)
```


```python
# Test the function on a sample of the dataframe - recall the free edition 
# Limits you to 60 calls per minute
sample = df.sample(n=100)
sample["weather_json"] = sample.apply(get_current_weather, axis=1)
sample["temp"] = sample.weather_json.map(lambda x: x.get('main').get('temp'))
sample.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>city</th>
      <th>lat_long</th>
      <th>lat</th>
      <th>lon</th>
      <th>weather_json</th>
      <th>temp</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>458</th>
      <td>jinxiang</td>
      <td>(26.477998938844365, 120.58029441863658)</td>
      <td>26.477998938844365</td>
      <td>120.58029441863658</td>
      <td>{'coord': {'lon': 120.58, 'lat': 26.48}, 'weat...</td>
      <td>76.06</td>
    </tr>
    <tr>
      <th>456</th>
      <td>presidente medici</td>
      <td>(-11.424771629503567, -62.13860905171518)</td>
      <td>-11.424771629503567</td>
      <td>-62.13860905171518</td>
      <td>{'coord': {'lon': -62.14, 'lat': -11.42}, 'wea...</td>
      <td>76.60</td>
    </tr>
    <tr>
      <th>294</th>
      <td>hurghada</td>
      <td>(26.974811706060564, 33.55503808756319)</td>
      <td>26.974811706060564</td>
      <td>33.55503808756319</td>
      <td>{'coord': {'lon': 33.56, 'lat': 26.97}, 'weath...</td>
      <td>86.00</td>
    </tr>
    <tr>
      <th>601</th>
      <td>merauke</td>
      <td>(-7.161117016547436, 138.24210262482558)</td>
      <td>-7.161117016547436</td>
      <td>138.24210262482558</td>
      <td>{'coord': {'lon': 138.24, 'lat': -7.16}, 'weat...</td>
      <td>79.03</td>
    </tr>
    <tr>
      <th>216</th>
      <td>victoria</td>
      <td>(-10.9006553043654, 63.490501545219956)</td>
      <td>-10.9006553043654</td>
      <td>63.490501545219956</td>
      <td>{'coord': {'lon': 63.49, 'lat': -10.9}, 'weath...</td>
      <td>80.38</td>
    </tr>
  </tbody>
</table>
</div>




```python
df["weather_json"] = df.apply(get_current_weather, axis=1)
```


```python
df["temp"] = df.weather_json.map(lambda x: x.get('main').get('temp'))
df["humidity"] = df.weather_json.map(lambda x: x.get('main').get('humidity'))
df["wind_speed"] = df.weather_json.map(lambda x: x.get('wind').get('speed'))
df["cloudiness"] = df.weather_json.map(lambda x: x.get('clouds').get('all'))
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>city</th>
      <th>lat_long</th>
      <th>lat</th>
      <th>lon</th>
      <th>weather_json</th>
      <th>temp</th>
      <th>humidity</th>
      <th>wind_speed</th>
      <th>cloudiness</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>mys shmidta</td>
      <td>(86.35963611345696, -179.30446668209328)</td>
      <td>86.35963611345696</td>
      <td>-179.30446668209328</td>
      <td>{'coord': {'lon': -179.3, 'lat': 86.36}, 'weat...</td>
      <td>31.60</td>
      <td>100</td>
      <td>21.09</td>
      <td>76</td>
    </tr>
    <tr>
      <th>1</th>
      <td>port keats</td>
      <td>(-14.09006513168886, 127.38635613845486)</td>
      <td>-14.09006513168886</td>
      <td>127.38635613845486</td>
      <td>{'coord': {'lon': 127.39, 'lat': -14.09}, 'wea...</td>
      <td>74.08</td>
      <td>100</td>
      <td>23.40</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>dicabisagan</td>
      <td>(18.594210829707407, 126.68477156377577)</td>
      <td>18.594210829707407</td>
      <td>126.68477156377577</td>
      <td>{'coord': {'lon': 126.68, 'lat': 18.59}, 'weat...</td>
      <td>84.16</td>
      <td>100</td>
      <td>17.63</td>
      <td>64</td>
    </tr>
    <tr>
      <th>3</th>
      <td>illoqqortoormiut</td>
      <td>(78.54333873182773, -29.949604466665363)</td>
      <td>78.54333873182773</td>
      <td>-29.949604466665363</td>
      <td>{'coord': {'lon': -29.95, 'lat': 78.54}, 'weat...</td>
      <td>19.27</td>
      <td>73</td>
      <td>8.79</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>shenjiamen</td>
      <td>(30.971105359699223, 124.63650123168748)</td>
      <td>30.971105359699223</td>
      <td>124.63650123168748</td>
      <td>{'coord': {'lon': 124.64, 'lat': 30.97}, 'weat...</td>
      <td>71.11</td>
      <td>100</td>
      <td>12.03</td>
      <td>64</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['lat'] = pd.to_numeric(df['lat'])
df['lon'] = pd.to_numeric(df['lon'])
type(df['lon'][0])
```




    numpy.float64




```python
plt.scatter(df['temp'], df['lat'])
plt.xlabel('Tempurature')
plt.ylabel('Latitude') 
plt.title('Tempurature vs. Latitude 6/21/18')
```




    Text(0.5,1,'Tempurature vs. Latitude 6/21/18')




![png](output_11_1.png)



```python
plt.scatter(df['humidity'], df['lat'])
plt.xlabel('Humidity')
plt.ylabel('Latitude') 
plt.title('Humidity vs. Latitude 6/21/18')
```




    Text(0.5,1,'Humidity vs. Latitude 6/21/18')




![png](output_12_1.png)



```python
plt.scatter(df['cloudiness'], df['lat'])
plt.xlabel('Cloudiness')
plt.ylabel('Latitude') 
plt.title('Cloudiness vs. Latitude 6/21/18')
```




    Text(0.5,1,'Cloudiness vs. Latitude 6/21/18')




![png](output_13_1.png)



```python
plt.scatter(df['wind_speed'], df['lat'])
plt.xlabel('Wind Speed')
plt.ylabel('Latitude') 
plt.title('Wind Speed vs. Latitude 6/21/18')
```




    Text(0.5,1,'Wind Speed vs. Latitude 6/21/18')




![png](output_14_1.png)



```python
wind_speed_mask = (df['wind_speed'] > 30)
df[wind_speed_mask]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>city</th>
      <th>lat_long</th>
      <th>lat</th>
      <th>lon</th>
      <th>weather_json</th>
      <th>temp</th>
      <th>humidity</th>
      <th>wind_speed</th>
      <th>cloudiness</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>15</th>
      <td>chuy</td>
      <td>(-38.678695418591104, -45.966245187129545)</td>
      <td>-38.678695</td>
      <td>-45.966245</td>
      <td>{'coord': {'lon': -45.97, 'lat': -38.68}, 'wea...</td>
      <td>58.15</td>
      <td>100</td>
      <td>52.75</td>
      <td>88</td>
    </tr>
    <tr>
      <th>17</th>
      <td>cidreira</td>
      <td>(-35.83777317215958, -45.548880618899005)</td>
      <td>-35.837773</td>
      <td>-45.548881</td>
      <td>{'coord': {'lon': -45.55, 'lat': -35.84}, 'wea...</td>
      <td>61.39</td>
      <td>100</td>
      <td>41.29</td>
      <td>44</td>
    </tr>
    <tr>
      <th>41</th>
      <td>albany</td>
      <td>(-53.93091959897851, 118.2571222762831)</td>
      <td>-53.930920</td>
      <td>118.257122</td>
      <td>{'coord': {'lon': 118.26, 'lat': -53.93}, 'wea...</td>
      <td>38.44</td>
      <td>99</td>
      <td>34.18</td>
      <td>88</td>
    </tr>
    <tr>
      <th>52</th>
      <td>maldonado</td>
      <td>(-35.93498245714719, -55.11995464278648)</td>
      <td>-35.934982</td>
      <td>-55.119955</td>
      <td>{'coord': {'lon': -55.12, 'lat': -35.93}, 'wea...</td>
      <td>54.46</td>
      <td>100</td>
      <td>31.79</td>
      <td>0</td>
    </tr>
    <tr>
      <th>75</th>
      <td>saldanha</td>
      <td>(-39.35731208151727, 6.0675145199190865)</td>
      <td>-39.357312</td>
      <td>6.067515</td>
      <td>{'coord': {'lon': 6.07, 'lat': -39.36}, 'weath...</td>
      <td>55.99</td>
      <td>90</td>
      <td>32.95</td>
      <td>68</td>
    </tr>
    <tr>
      <th>95</th>
      <td>laguna</td>
      <td>(-32.266876619102796, -40.42343987839445)</td>
      <td>-32.266877</td>
      <td>-40.423440</td>
      <td>{'coord': {'lon': -40.42, 'lat': -32.27}, 'wea...</td>
      <td>68.50</td>
      <td>94</td>
      <td>33.96</td>
      <td>20</td>
    </tr>
    <tr>
      <th>182</th>
      <td>varhaug</td>
      <td>(57.24536602574946, 2.648857306919922)</td>
      <td>57.245366</td>
      <td>2.648857</td>
      <td>{'coord': {'lon': 2.65, 'lat': 57.25}, 'weathe...</td>
      <td>52.57</td>
      <td>100</td>
      <td>36.19</td>
      <td>76</td>
    </tr>
    <tr>
      <th>187</th>
      <td>avera</td>
      <td>(-33.864163030005905, -156.38958254929366)</td>
      <td>-33.864163</td>
      <td>-156.389583</td>
      <td>{'coord': {'lon': -156.39, 'lat': -33.86}, 'we...</td>
      <td>65.35</td>
      <td>95</td>
      <td>35.19</td>
      <td>92</td>
    </tr>
    <tr>
      <th>283</th>
      <td>rio grande</td>
      <td>(-38.68277371320195, -44.34326012167398)</td>
      <td>-38.682774</td>
      <td>-44.343260</td>
      <td>{'coord': {'lon': -44.34, 'lat': -38.68}, 'wea...</td>
      <td>58.15</td>
      <td>100</td>
      <td>44.25</td>
      <td>24</td>
    </tr>
    <tr>
      <th>343</th>
      <td>den helder</td>
      <td>(55.607367215447795, 2.9758141555412863)</td>
      <td>55.607367</td>
      <td>2.975814</td>
      <td>{'coord': {'lon': 2.98, 'lat': 55.61}, 'weathe...</td>
      <td>51.80</td>
      <td>81</td>
      <td>42.50</td>
      <td>92</td>
    </tr>
    <tr>
      <th>410</th>
      <td>rawson</td>
      <td>(-49.19106429101441, -58.479405494403395)</td>
      <td>-49.191064</td>
      <td>-58.479405</td>
      <td>{'coord': {'lon': -58.48, 'lat': -49.19}, 'wea...</td>
      <td>42.40</td>
      <td>100</td>
      <td>35.25</td>
      <td>88</td>
    </tr>
    <tr>
      <th>415</th>
      <td>plettenberg bay</td>
      <td>(-45.85651253734923, 23.450629617912682)</td>
      <td>-45.856513</td>
      <td>23.450630</td>
      <td>{'coord': {'lon': 23.45, 'lat': -45.86}, 'weat...</td>
      <td>47.44</td>
      <td>88</td>
      <td>32.79</td>
      <td>24</td>
    </tr>
    <tr>
      <th>424</th>
      <td>norden</td>
      <td>(55.18728271143283, 6.570553972141681)</td>
      <td>55.187283</td>
      <td>6.570554</td>
      <td>{'coord': {'lon': 6.57, 'lat': 55.19}, 'weathe...</td>
      <td>53.38</td>
      <td>100</td>
      <td>34.92</td>
      <td>92</td>
    </tr>
    <tr>
      <th>533</th>
      <td>salalah</td>
      <td>(13.5400986040693, 55.18343580419361)</td>
      <td>13.540099</td>
      <td>55.183436</td>
      <td>{'coord': {'lon': 55.18, 'lat': 13.54}, 'weath...</td>
      <td>81.73</td>
      <td>96</td>
      <td>30.11</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>


