# Mesterséges intelligencia

https://www.kmooc.uni-obuda.hu/course/68

> Az online tanfolyam az optimális problémamegoldásra összpontosít. A diákoknak alkalmuk lesz megismerkedni olyan klasszikus feladatokkal, mint a 8-királynő, vagy a térképszínezés, és ezeknek a problémáknak a megoldási stratégiájával. A kétszemélyes játékoknál az optimális döntéshozatal a Nim és az Othello játékokon kerül bemutatásra. A természet ihlette algoritmusok közül a genetikus algoritmusokra van fektetve a legnagyobb hangsúly, de a kurzus foglalkozik a hangyakolóniával és a részecske-raj optimalizációval is. A kurzus utolsó harmada pedig a gépi tanulásról és a mesterséges neurális hálókról ad ismertetést. A felügyelt betanítási módszerek közül a diákok megismerkednek a perceptron módszerrel és a hiba-visszaterjesztéssel, míg a felügyeletlen módszerek a Kohonen háló segítségével kerülnek bemutatásra.

## Tartalom
-    Informálatlan keresés I.
-    Informálatlan keresés II.
-    Informált keresés I.
-    Informált keresés II.
-    Lokális keresés
-    Kényszerkielégítési problémák I.
-    Kényszerkielégítési problémák II.
-    Genetikus algoritmusok I.
-    Genetikus algoritmusok II.
-    Neurális hálózatok I.
-    Neurális hálózatok II.

----
## Bevezetés
**Mi a mesterséges intelligencia?**
- Olyan gépek építése melyek emberi módon gondolkoznak
- Nem kell törődni azzal, hogyan gondolkozik a gép, a lényeg, hogy emberi módon cselekedjen
- Racionálisan gondolkodó gépeket kell építeni <- ez lesz a téma
  - memorizáljuk a rossz döntéseket
  - szimuláljuk az összes döntési helyzetet, és a rossz előre kizárható

**Nyelvfeldolgozás**
- ASR - automatikus beszéd felismerés
- TTX - szöveg beszéddé alakítása
- ASR+TTX dialógus rendszerek
- gépi fordítás

**Gépi látás**
- objektumok felismerése stb.
- arc stb. detektálás/azonosítása

**Döntéshozatal**
- ütemezési feladatok
- útvonaltervezés
- orvosi diagnózis
- web keresés

## Informálatlan keresés I.
> Ebben az előadásban definiáljuk a kereséssel kapcsolatos alapvető fogalmakat, rámutatunk a keresőtér kezelhetetlen nagyságára.
>
> Megismerkedünk a keresési algoritmusok értékelési kritériumaival, végül pedig egyenként részletesen ismertetjük az egyes informálatlan keresési algoritmusokat.

- kiindulóállapot
- rendelkezésre álló cselekvések
- célteszt, hogy állapot célállapot-e
- útköltség

A megoldás a kiindulóállapot-célállapot közti út, amit az útköltség mér. A legkisebb költségű út a legoptimálisabb.

- teljesség: biztosan találunk megoldást, ha létezik
- optimalitás: az optimális utat találja meg ha van megoldás
- időigény: szükséges idő mértéke
- tárigény: szükséges memória mértéke

**Perem(hullámfront)**: a legenerált, de még nem mkifejtett csomópontok halmaza.

- **szélességi keresés**:
    - a legsekélyebben fekvő(legkevesebb lépéssel elérhető) csomópontot fejti ki.
    - a perem egy First In First Out - FIFO jellegű sor.
    - ez a stratégia minden adott mélységű csomópontot hamarabb fejt ki, mint bármelyik mélyebb szinten lévő csomópontot. 
    - akkor optimális, ha a lépésköltség állandó, mert az algoritmus mindig a legsekélyebben fekvő pontot fejti ki.
    - Tulajdonságok:
      - Teljesség: Mindig megtalálja a megoldást ha **b** véges 
      - Optimalitás: Optimális, ha a mélyebben fekvő megoldások kevésbé optimálisak, tehát ha minden lépés költsége 1.
      - Időigény: O(b^(d+1)), ahol d a elágazási tényező
      - Tárigény: O(b^(d+1)), mert minden csomópontot a futás végéig meg kell jegyezni.
- **egyenletes költségű keresés**:
    - Ez a módszer mindig a legkisebb útköltségű csomópontot fejti ki.
    - Végtelen ciklusba kerül, ha egy csomópont útköltsége 0, ezt helyettesítő 0 értékkel küszöbölhetjük ki.
- **mélységi keresés**:
    - a legmélyebben fekvő még nem kifejtett csomópontot fejtjűk ki.
    - a perem egy Last In First Out - LIFO sor, ahol a kifejtett csomópont utódai mindig a sor elejére kerülnek.
    - Tulajdonságok:
      - Teljesség: Nem teljes, mert végtelen mélység esetén elakadhat.
      - Optimalitás: Nem optimális, mert nem optimális célt hamarabb megtalálhat az optimálisnál.
      - Időigény: O(b^m), ahol m maximális mélység
      - Tárigény: O(bm) - kis tárigény, ahol csak az aktuális útvonalat és az eddig még nem kifejtett csomópontokat kell tárolni
- **mélységkorlátozott keresés**:
    - egy L korlátot szabunk a mélység vizsgálásában, és mélységi keresést használunk.
    - Tulajdonságok:
      - Teljesség: Ha d > L, akkor a megoldást nem találjuk meg
      - Optimalitás: Nem optimális, mert nem optimális célt hamarabb megtalálhat az optimálisnál.
      - Időigény: O(b^L)
      - Tárigény: O(bm)
- **iteratív mélységi keresés**:
    - kezdjük egy mélységgel a mélységi keresést, majd növeljük addig amíg találunk valamit vagy amíg tudjuk...
    - Tulajdonságok:
      - Teljesség: Teljes
      - Optimalitás: Optimális, ha a lépésköltség 1 vagy a mélység növekvő függvénye.
      - Időigény: exponenciális
      - Tárigény: lineáris
- **kétirányú keresés**:
    - két keresést indítunk: egyiket a kezdő, másikat a célcsomópontból
    - Nehéz lehet meghatározni a célállapot elődeit
    - Több megoldás esetén sem biztos mit kell lépni
    - Időigény: O(b ^(d/2))
    - Tárigény: O(b ^(d/2))

## Informálatlan keresés II
> Ebben az előadásban bemutatjuk hogyan lehet különböző példákat keresési algoritmusokkal megoldani. Levezetjük a "kancsó" feladatot, felvázoljuk a folyóátkelő játékokat és a "békás" logikai játékot, és meglátjuk hogyan lehet elvégezni a keresést listák segítségével.

### Kancsó feladat - szélességi kereséssel
Adott két kancsó egy 4 és egy 3 literes, nincs rajtuk jelölés. Hogy töltjük félig a 4 literes kancsót?

Célállapot (2,x) ahol `(első_kancsóban_levő_víz, második_kancsóban_levő_víz)`. AZ első kancsó a 4 a második a 3 literes. Kezdőállapot (0,0).

- (0,0)
  - (4,0)
    - (4,3)
    - (1,3)
      - (1,0)
        - (0,1) 
          - (4,1)
            - **(2,3)**
  - (0,3)
    - (3,0) 
      - (3,3)
        - (4,2)
          - (0,2)
            - **(2,0)**

### Szélességi keresés listákkal
1. Létrehozunk két üres listát:
   - open lista
   - closed lista
2. kezdeti csomópontot, illetve a gyökércsomópontot hozzáadjuk az open listához.
3. Amíg az open lista nem lesz üres:
   - kivesszük az első csomópontot az open listából
   - ellenőrizzük, hogy a csomópont célcsomópont-e, 
     - ha igen, ciklus vége, csomópontot a closed listához adjuk, a megoldás a closed lista pillanatnyi állapota
     - ha nem, folytatjuk a ciklust
   - meghatározzuk a kivett csomópont utódait
   - az utódokat az open lista **végéhez**, a kivett csomópontot a closed lista végéhez adjuk. Folytatjuk a ciklust.

### Mélységi keresés listákkal
1. Létrehozunk két üres listát:
   - open lista
   - closed lista
2. kezdeti csomópontot, illetve a gyökércsomópontot hozzáadjuk az Open listához.
3. Amíg az open lista nem lesz üres:
   - kivesszük az első csomópontot az open listából
   - ellenőrizzük, hogy a csomópont célcsomópont-e, 
     - ha igen, ciklus vége, csomópontot a closed listához adjuk, a megoldás a closed lista pillanatnyi állapota
     - ha nem, folytatjuk a ciklust
   - meghatározzuk a kivett csomópont utódait
   - az utódokat az open lista **elejéhez**, a kivett csomópontot a closed lista végéhez adjuk. Folytatjuk a ciklust.

### Folyóátkelés
> juttassuk át a farkast, kecskét és káposztát a folyón egy hajós segítségével, ha valamelyik kettesben marad a hajós nélkül, megeszi a másikat, és vesztünk. Alapállapot: `(farkas, kecske, káposzta, hajós)`. 0 az érték, ha bal, 1 ha jobb oldalon van az adott utas.

## INFORMÁLT KERESÉS I
> Ide azokat az algoritmusokat soroljuk, amelyek a kereséshez kiértékelő heurisztikus függvényeket használnak. Ilyen módszerek a mohó keresés és az A* keresés.

Heurisztikus függvény adja meg, merre keresse a válaszokat. Csökkenti a számításigényt, és növeli a hatékonyságot. A heurisztika minden állapothoz egy számot rendel.

### Mohó keresés
- Nem törődik az eddig megtett úttal, csak mindig épp közelebb akar kerülni a célállapothoz!
- könnyen végtelen ciklusba kerül, mert nem veszi figyelembe a már bejárt útvonalat
- gyakran talál nem optimális útvonalat!

### A*
f(n) = g(n)+h(n) elven működik, ahol g(n) az aktuálisan eddig megtett út költsége, h(n) a cél költsége

**Mindig az aktuálisan legkisebb értéket fejti ki és nincs visszalépés!**

## INFORMÁLT KERESÉS II
> Példákon keresztül kerülnek bemutatásra az egyes algoritmusok. Külön kitérünk a heurisztikus függvények tulajdonságaira.

Az elfogadható heurisztika sosem becsüli túl a költséget! Két heurisztikát összehasonlítva, akkor dominálja egyik a másikat, ha garantálja, hogy legfeljebb ugyanannyi csomópontot fog kifejteni.

Ha heurisztika konzisztens akkor elfogadható is.

## Lokális keresés
> A lokális keresők az állapottérfelszín görbén végzik a keresést. A hegymászó algoritmuson mutatjuk be a módszert.

Az ilyen feladatoknál a megoldás nem egy útvonal, hanem egy állapot, pl. sakknál, nem érdekel, hogy éri el, csak a győzelmi felállás.

Hegymászó keresés: nem tartja nyilván az útvonalat, csak egy maximuma van, ha azonban vannak lokális maximumok akkor gondban lehetünk, ekkor az eredmény helyessége a kiindulási ponttól függ. Ebben az esetben a függvényen előbb kiválasztjuk a lokális maximumokat és minimumokat.

## KÉNYSZERKIELÉGÍTÉSI PROBLÉMÁK I (CSP)
> Megoldás keresése azzal, hogy előre meghatározott kényszereket is ki kell elégíteni. Forward Checking szűrőalgoritmussal gyorsítjuk a keresést.

Identifikációs probléma, mikor a változókhoz érétket rendelünk, a megoldás ez a hozzárendelés maga. 

Pl minden sornak vagy oszlopnak adunk egy értéket. Használhatunk kényszereket, amik adott változókat érintenek.

- Backtrack algoritmusoknál visszalépünk, ha hibás megállapításhoz jutottunk. 
- Forward checking mindent hozzárendel mindenhez.

## KÉNYSZERKIELÉGÍTÉSI PROBLÉMÁK II (arc consistency)
> Hatékony ág-konzisztencia algoritmus, példák kidolgozása ezzel a módszerrel.

Egy ág akkor konzisztens, ha minden értékre a kezdőponttól létezik érték a csúcsban, és nem történik kényszermegszegés.

Gyorsabb megoldást ad, mint a forward check, kevesebbet kell backtrackelni, mert előre vizsgál.

## GENETIKUS ALGORITMUSOK I
> Ismerkedés a genetikai algoritmus alapfogalmaival. Fitnesz függvény, rulettkerék szelekció.

A gyenge egyedek kihalnak, a legjobbaknak van esélye a túlélésre. Az adatokat a kromoszómákon tároljuk, amik génekből állnak.

Egypontos keresztezésnél kettévágjuk a kromoszómát, a bal oldalt hagyjuk a jobb oldalt cseréljük.

## GENETIKUS ALGORITMUSOK II
> Genetikus műveletek: rekombináció, mutáció, elitizmus. Szemléltető példák kidolgozása.

Nincs garancia arra, hogy valaha is megtalálja az optimális megoldást a genetikus algoritmusunk!
 
### Részecske raj optimalizáció (PSO)
Egyszerű élőlények, de rajban kollektív tudattal rendelkeznek. 

Lépések: 
1. minden részecske fitnesz meghatározása
2. egyéni és globális fitnesz frissítése
3. sebesség és helyzet frissítése

Kilépési feltétel lehet adott iterációszám, vagy adott idejű stagnálás stb.
Nem rendelkezik genetikus operátorral! Csak a legjobb egyed szolgál információt a többi egyednek!


## NEURÁLIS HÁLÓZATOK I
> Mesterséges neurális hálózatok, biológiai háttér, logikai műveletek megvalósítása.

**átviteli függvények:**
- hard limit: 0/1
- lineáris: egyenes mentén +00
- log-szigmoidális: -1-+1 között vagy 0-+1 között

**felügyelt tanítás:**
- mindig azokat a súlyokat csökkentjük, amikre a bemenet 1, így mindig a nagyobb érték lesz csökkentve! Növelésnél is ez igaz.

**felügyelet nélküli tanítás - kohonen hálózat:** (self organizing map)
- feltételezzük, hogy van egy két bemenetes három neuronos hálózat
- az adott bemeneten a három értékből az egyik nagyobb, ekkor az egyik neuron győz, ezek után csak azt a neuront használjuk.
- `súly_értéke_betanítás_után = súly_eredeti_érétke + betnítási_együttható * (input - súly_eredeti_érétke)`








