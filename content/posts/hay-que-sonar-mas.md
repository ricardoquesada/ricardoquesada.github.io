---
author: ricardoquesada
category: cocos2d
tag:
  - escher
  - sueño
date: "2008-08-04T21:56:00+00:00"
guid: http://www.monociclo.com.ar/?p=57
title: Hay que soñar más
url: /2008/08/04/hay-que-sonar-mas/

---
[![](/wp-content/uploads/2008/08/1a1bc-sueno.png?w=300)](/wp-content/uploads/2008/08/1a1bc-sueno.png)  
Anoche me quedé tratando de fixear un bug de [cocos2d-iphone](http://code.google.com/p/cocos2d-iphone).  
Estuve más o menos 4 o 5 horas... probablemente mucho más. El bug consistia en que las partículas se veian desfazadas. Cuando las movia a los bordes, se iban más allá de los bordes, pero cuando las ponía en el medio de la pantalla se quedaban centradas... a medida que las movia, se movían "más". Y cuanto más grande el tamaño de las particulas, más se desfazaba.

Para intentar encontrar el bug vi el codigo de [transform](http://code.google.com/p/cocos2d-iphone/source/browse/trunk/cocos2d/CocosNode.m#185) varias veces, vi el codigo de las [particulas](http://code.google.com/p/cocos2d-iphone/source/browse/trunk/cocos2d/Particle.m) cientos de veces, vi todo el codigo de todo, y más.  
Luego de hacer varias pruebas descarté que el problema estuviera en otro lugar más que en el sistema de particulas. Prendí/apagué color, texturas, calculos de coma flotante, y nada... el bug seguía.

NO TENIA SENTIDO EL BUG.

En fin... estaba cansado asi que me fuí a dormir, y es ahí cuando en el medio del sueño alguien me dijo: "Estas es dibujando con la coordenada Z... fijate que el tamaño de la particula se esta usando como coordenada Z".

Me desperté... pensé lo que me habían dicho en el sueño y dije: "Ah... claro, tiene sentido"... segui durmiendo, y recién me desperté y lo fixie tal como me habían dicho en el sueño. Ja Ja Ja.

Y no es la primera vez que me pasa... a soñar más! :-)

ps: Ah... relacionado con el post anterior, aca tengo [fotos mias en el museo de Escher](https://photos.app.goo.gl/VhMvJDizmhvphgBq7).
