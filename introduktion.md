### INTRODUKTION
Fysikkens love indeholder ofte kræfter og acceleration og kan derfor beskrives som 2. ordens differentialligninger. Disse er ofte svære eller umulige at løse analytisk, d.v.s. finde ligningen, men den kan ofte klares numerisk. I denne introduktion prøver vi at arbejde os frem til at kunne gøre det.

### Indholdsfortegnelse
* [Introduktion.](https://mpsteenstrup.github.io/numerisk_metode/introduktion)
* [Eulers metode.](https://mpsteenstrup.github.io/numerisk_metode/eulers_metode)
* [Bisektion og Newton-Raphson.](https://mpsteenstrup.github.io/numerisk_metode/bisektion_newton_raphson)
* [Runge-Kutta.](https://mpsteenstrup.github.io/numerisk_metode/runge_kutta)



### FORDELE

* Vi kan løse problemer som ikke er analytisk løsbare.
* Vi kan visualisere løsninger grafisk.
* Dynamisk se systemet udvikle sig, mens relevante grafer bliver tegnet.
* Eleverne kan ret let ændre i kode som allerede er lavet.

### SETUP 
Vi bruger online siden trinket.io. Her kan man dele med elever og eleverne kan selv gemme og lave egne programmer.

### MATEMATIKKEN, Eulers metode

Vi vil gerne gå fra krafter til bevægelse. Det er altså en øvelse i at gå fra
$$
a \rightarrow v \rightarrow x.  
$$
Det svare jo til
$$
\frac{d^2 x}{dt^2} \rightarrow \frac{d x}{dt} \rightarrow x.
$$
Vi vil fokuserer på det enkelt step $\( \frac{d x}{dt} \rightarrow x \)$.



Tænk tilbage til hvordan I definerede en differentialkvotient,
$$
\frac{f(t)-f(t_0)}{t-t_0}=f'(t), \text{ for }  t \rightarrow t_0
$$ 
Nu ganger jeg med $\( \Delta t = t-t_0 \)$, hvilket giver
$$
f(t)-f(t_0) = f'(t)\Delta t
$$
hvilket giver
$$
f(t) = f(t_0) + f'(t)\Delta t.
$$

`
$x^2 + y^2 = z^2$`

Her har jeg droppet, $\(t\rightarrow t_0\)$, hvilket svarer til $\(\Delta t \rightarrow 0 \)$. En af opgaverne er netop at lave $\( \Delta t\)$ tilstrækkeligt lille når systemet skal simuleres.

Vi kan altså hvis vi kender startpositionen $\(x_0\)$ og den afledte $\( v \)$ finde positionen efter t sekunder ved at beregne
\begin{align}
x1&=x0+v0\Delta t, \\\
x2&=x1+v1\Delta t, \\\
x3&=x2+v2\Delta t, ...
\end{align}
Denne metode kaldes Eulers metode til løsning af differentialligninger. Der findes andre og mere avancerede, men denne er fin til en start.

I programmering er sproget lidt anderledes, her kan man godt skrive,
$\(x = x+1\)$ , hvilket betyder at x variablen skal opdateres med den oprindelige x værdi plus 1.

### Simulering  med Python

Python bruger tabulator indrykning når den laver løkker. Det er ofte her det går galt når man kopierer kode fra andre steder. Løsningen er at slette indrykkene og lave dem igen, med tabulator knappen.

** Det simpleste eksempel **
Vi starter med det lodrette kast uden luftmodstand. Fysikken er kendt som bevægelse med konstant acceleration. Startbetingerlserne er
* y = 10 m
* v = 0 m/s
* g = -9.82 m/s/s
* m = 1 kg

Hvilket svare til at en bold slippes 10 meter oppe og accelereres mod jorden. Kør simuleringen ved at trykke på 'play' knappen

[https://glowscript.org/#/user/mps/folder/nummeriskmetode/program/introduktion1](https://glowscript.org/#/user/mps/folder/nummeriskmetode/program/introduktion1)

Jeg gennemgår koden i denne video: [video](https://youtu.be/iz6A1Nj_tE0)


** Prøv selv **

Den bedste måde at få forståelse for programmet er at lave om i det. Prøv jer frem, men gør kun én ting af gangen, så kan I altid komme tilbage. Hver gang I laver noget om skal I prøve at baskrive hvad der er forandret i simulaitonen.
* Lav om på startbetingelserne, så hastigheden ikke er lig nul v = .
* Lav om på massen af bolden ved at ændre på m.
* Lav om på tyngdeaccelerationen så simuleringen er helt på månen, g=1.6.

Systemet udvikler sig efter newtons love, men vi kan vælge at studere dem udvikle sig langsommere. I linje 26 angives rate(100), hvilket betyder at løkken kører 100 gange i sekundet. Dette giver den rigtige tid da vi har sat tidsskridtet til $\(dt=0.01\)$. Hvis man vil have den rigtige udvikling skal man sætte sin rate til $\(1/dt)\$. Hvis man skal kunne holde øje med grafer og bolde der flyver er det ofte en god ide at skrue tempoet ned.

* Prøv at lav om i rate så simuleringen kører langsommere.


### data og grafer

Hvis vi skal kunne arbejde kvantitativt med simuleringen skal vi have grafer og tal ud. Det er heldigtvist ikke så svært. I nedenstående simulering bliver der tegnet en graf og data for y-positionen bliver udskrevet. Det er igen det lodrette kast, men med en starthastighed på v = 10m/s.

Udover at der nu bliver tegnet grafer så er boldens egenskaber nu skrevet som vektorer. GlowScript har det som standard når det laver objekter og det meste materiale er udviklet den gang alle 1.g elever skulle have om vektorer. Det giver en del større fleksibilitet, men gør også koden lidt mere uoverskuelig.

Kør koden i full screen ved at trykke på de tre streger i venstre hjørne.


[https://glowscript.org/#/user/mps/folder/numeriskmetode/program/introduktion1](https://glowscript.org/#/user/mps/folder/numeriskmetode/program/introduktion1)

Her skal I fokusere på graferne og data-output.
* Beskriv boldens bevægelse ved at se på simuleringen.
* Beskriv boldens bevægelse ved at se på grafen.
* aflæs højden af kastet på grafen.
* Hvor lang tid tager det før bolden rammer jorden.
* Gem data fra simulaitonen for både, t og y, og tjek i loggerpro om det faktisk er en kasteparabel. I bliver nød til at køre simulationen to gange for at få printet t og y separat. 
* lav om i grafen så I får hastigheden i y retningen,  (t,bold.v.y) graf. Husk at lav om på labels på akserne så de passer i linje 3.

## Nyt

Vi vil nu prøve at simulere det skrå kast med luftmodstand. Det er nu at simulering for alvor bliver lettere end at beregne det analytisk. I kan jo prøve at løse differentialligningen hvis I vil, men I skal først prøve det her.

Fysikken bag luftmodstand er ikke så svær. Luftmodstanden er proportional med hastigheden i anden og vender altid væk fra bevægelsesretningen,
$$
F_{luftmodstand} = -k·v^2.
$$
Sammen med tyngdekraften bliver den samlede kraft,

op
$$
F = F_t + F_{luftmodstand} = -g·m - m·v^2
$$
ned
$$
F = F_t + F_{luftmodstand} = -g·m + m·v^2
$$
For at få det fortegnet rigtigt definerer vi luftmodstanden som $\( -k·v^2 \)$ som ``` -k·bold.v*bold.v.mag```. ```bold.v.mag``` giver den numeriske værdi af vektoren og ```bold.v``` giver skifter fortegn ved ændret regning.


[https://glowscript.org/#/user/mps/folder/numeriskmetode/program/introduktion2](https://glowscript.org/#/user/mps/folder/numeriskmetode/program/introduktion2)

* Eksperimenter med ændring af vinklen, er $\( 45^{\circ} \)$ stadigt der hvor den kommer længst?
* Hvis det forventede ned, hvorfor og hvornår kommer den længst?