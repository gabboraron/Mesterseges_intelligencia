# Mesterséges intelligencia

https://www.kmooc.uni-obuda.hu/course/68

> Az online tanfolyam az optimális problémamegoldásra összpontosít. A diákoknak alkalmuk lesz megismerkedni olyan klasszikus feladatokkal, mint a 8-királynő, vagy a térképszínezés, és ezeknek a problémáknak a megoldási stratégiájával. A kétszemélyes játékoknál az optimális döntéshozatal a Nim és az Othello játékokon kerül bemutatásra. A természet ihlette algoritmusok közül a genetikus algoritmusokra van fektetve a legnagyobb hangsúly, de a kurzus foglalkozik a hangyakolóniával és a részecske-raj optimalizációval is. A kurzus utolsó harmada pedig a gépi tanulásról és a mesterséges neurális hálókról ad ismertetést. A felügyelt betanítási módszerek közül a diákok megismerkednek a perceptron módszerrel és a hibavisszaterjesztéssel, míg a felügyeletlen módszerek a Kohonen háló segítségével kerülnek bemutatásra.

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
- Olyan gépek építése melyek emberien gondlkoznak
- Nem kell törődni azzal, hogyan gondolkozik a gép, a lényeg, hogy emberi módon cselekedjen
- Racioinálisan gondolkodó gépeket kell építeni <- ez lesz a téma
  - memorizáljuk a rossz döntéseket
  - szmuláljuk az összes döntési helyzetet, és a rossz előre kizárható

**Nyelvfeldolgozás**
- ASR - automatikus besézd felismerés
- TTX - szöveg beszéddé alakítása
- ASR+TTX dialógus rendszerek
- gépi fordítás

**Gépi látás**
- objektumok felismerése, stb
- arc stb detektálás/azonosítása

**Döntéshozatal**
- ütemezési fleadatok
- útvonaltervezés
- orvosi diagnózis
- web keresés

## Informálatlan keresés I.
- kiindulóállapot
- rendlekezésre áló cselekvések
- célteszt, hogy állapot célállapot-e
- útköltség

A megoldás a kiindulóállapot-célállapot út, amit az útköltség mér.

- telejsség: bizotsan stalálunk megoldást ha létezik
- optimalitás: az optimális utat találja meg ha van megoldás
- időígény: szükséges idő mérétke
- tárigény: szükséges memória mérétke

- szélkeysségi keresés akkor optimális ha épésköltség állandó mert az algoritmus mindig a legsekéylebben fekvő pontot fejti ki.
- egyenletes öltségű keresés: 
