### Indholdsfortegnelse
* [Introduktion.](https://mpsteenstrup.github.io/numerisk_metode/introduktion)
* [Eulers metode.](https://mpsteenstrup.github.io/numerisk_metode/eulers_metode)
* [Bisektion og Newton-Raphson.](https://mpsteenstrup.github.io/numerisk_metode/bisektion_newton_raphson)
* [Runge-Kutta.](https://mpsteenstrup.github.io/numerisk_metode/runge_kutta)

# Eulers metode
Eulers metode bruges til at lave en tilnærmet løsning til en differentialligning. Differentialligningen skrives som $$y'=g(x,y)$$ og kan både indeholde x og y som variabel.

Man bruger tangenten som bedste approksimation til funktionen i punktet $\( P(x_0, y_0) \)$ til at finde de næste punkter $\( (x_1,y_1),(x_2,y_2),(x_3,y_3),... \)$

Tangentens ligning er
$$ y = f'(x_0)·(x-x_0)+f(x_0) $$ hvilket kan oversættes til 
$$ y_1 = g(x_0,y_0)·(x_1-x_0)+y_0 $$
Hvis vi sætter skridtlængden lands x-aksen til h kan vi få metoden til at opdatere x værdierne,
$$ x_1 = x_0 + h $$
Hvis vi sætter det ind i tangentligningen bliver det
$$ y_1 = y_0 + g(x_0,y_0)·h$$
Hvilket derefter kan bruge til at finde de efterfølgende

### Eksempel
Differentialligningen $$y' = x+y, y(0)=0$$ kan løses analytisk til $$y(x) = -x-1+e^{x}$$
I nedenstående vises en simulering hvor Eulers metode er brugt til at finde en tilnærmelse


[https://glowscript.org/#/user/mps/folder/numeriskmetode/program/em1](https://glowscript.org/#/user/mps/folder/numeriskmetode/program/em1)

* Lav om i skridtlængden h og hvad der sker.
* Vurder hvor lille skridtlængden skal være for at afvigelsen fra den analytiske løsning er ok ved $\(x=3\)$.
* Find ud af hvor i koden eulers metode er implimenteret for at finde de nye x og y værdier?


### Eksempel 2
Differentialligningen $$y' = sin(x)·y, y(1)=1$$ hvilket også har en analytisk løsning.
I nedenstående vises en simulering hvor Eulers metode er brugt til at finde en tilnærmelse


[https://glowscript.org/#/user/mps/folder/numeriskmetode/program/em2](https://glowscript.org/#/user/mps/folder/numeriskmetode/program/em2)

* Vurder igen hvor lille skridtstørrelsen skal være for at simuleringe er god.
* Find de dele af simuleringen som er anderleded i forhold til eksempel 1.

### Eksempel 3
Denne differentialligning har ikke nogen analysitk løsning.
$$y' = sin(x) + 2·sin(y)$$.
Vi kan heldigvis stadigt løse den numerisk.


[https://glowscript.org/#/user/mps/folder/numeriskmetode/program/em3](https://glowscript.org/#/user/mps/folder/numeriskmetode/program/em3)

* Forlæng simuleringen ved at ændre betingelsen i linje 16.