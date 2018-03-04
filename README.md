# DolphinAttack
Projet étudiant pour la THC du 9 et 10 mars 2018.
https://toulousehackingconvention.fr/

Qu'est-ce que la Dolphin Attack ? 

La dolphin Attack est une attaque par ultrasons qui cible les appareils à reconnaissance vocale tels que Siri, Alexa (Amazon Echo), OkGoogle, Cortana (Microsoft) mais aussi ceux de certaines voitures. L'objectif est de reproduire la voix humaine dans des fréquences inaudibles pour un humain (au-delà de 20kHz). 

A quoi peut servir cette attaque ? 

Aujourd'hui, de plus en plus de gens utilisent les appareils à reconnaissance vocale et leurs fonctionnalités/capacités augmentent de jour en jour. Même si dans la majorité des cas les attaques n'auront pas des conséquences catastrophiques (car les appareils à reconnaissance vocale préviennent leurs utilisateurs dès lors qu'ils exécutent une commande), on peut tout de même citer quelques attaques ayant des conséquences un petit peu plus graves : 
- Faire se connecter le téléphone à un site web malveillant, ou lui faire télécharger une application malveillante créée au préalable par l'attaquant. 
- Faire téléphoner l'appareil à un numéro surtaxé ; si l'utilisateur n'est pas proche de son téléphone des coûts importants peuvent être à prévoir, et si ce numéro surtaxé a été créé par l'attaquant, voilà une bonne façon de se faire de l'argent facilement (et pas très légalement...)
- Les appareils à reconnaissance vocale permettent d'avoir des maisons de plus en plus connectées, imaginez qu'un appareil puisse gérer l'ouverture des volets ou voir même celle des portes d'un appartement. Dans le cas où le résident est absent pensez aux dégâts que cette attaque peut causer !
- La dernière attaque n'est pas encore actuelle, elle concerne les voitures autonomes/ intelligentes. Je vous laisse imaginer toutes les attaques qu'il pourra être possible de réaliser dans le cas où les constructeurs ne tiennent pas compte de cette faille.

Pour résumer, la DolphinAttack peut servir de base pour des attaques ayant des conséquences plus importantes, mais la DolphinAttack seule ne peut pas être qualifiée de dévastatrice.

Matériel nécessaire à l'attaque.
- Un émetteur : expérience faite avec un MacBook Pro (Retina - macOS HighSierra - processor 2,2 GHz Intel Core i7)
Attention, un ordinateur trop ancien ne sera pas capable d'émettre des ultrasons, avant de lancer l'attaque pensez à vérifier que votre ordinateur peut bien émettre à des fréquences supérieures à 20000 Hz. L'émetteur peut aussi être un téléphone tel qu'un Samsung s6 Edge (non testé personnellement). 
- Dans le cas où l'émetteur n'est pas assez puissant vous pouvez rajouter un amplificateur avant la sortie. J'ai testé avec des enceintes de musique de type : M-audio av40 cela marchait parfaitement bien jusqu'à une distance de 20 cm (environ). J'ai aussi essayé avec un émetteur à ultra-sons http://fr.farnell.com/multicomp/mcpct-g5100-4139/ultrasonic-transducer/dp/1801068?ost=1801068&ddkey=http%3Afr-FR%2FElement14_France%2Fsearch pour lequel j'ai rajouté un amplificateur maison associé à un générateur de courant, cela marchait bien à condition que la fréquence soit assez élevée. Il faut cependant que la carte son puisse tout de même créer les ultrasons sinon cela ne marchera pas.
- Un récepteur : mes expériences ont été réalisées avec "OK Google" sur un Sony Xperia E5, les résultats étaient très concluants. J'ai aussi essayé avec Alexa de Amazon Echo mais les résultats étaient moins concluants, de même avec Siri. 


Pour transporter le message sonore dans les fréquences à ultrasons, il faut réaliser une modulation d'amplitude. Celle-ci est faite logiciellement avec Matlab (ou Octave) (cf : dolphinAttack.m dans les sources). Il est aussi possible de créer un modulateur à amplitude de façon matérielle (électronique), ce que je vous conseille dans le cas où votre carte son ne parvient pas à émettre d'ultrasons. Pour obtenir le signal de sortie, c'est-à-dire le signal modulé on réalise l'opération suivante : s(t) = m(t)cos(2*pi*fc*t) + cos(2*pi*fc*t) . Pour un meilleur résultat, il est préférable de passer votre signal d'entrée dans un filtre passe bas (fonction butter sous matlab, utilisée dans le fichier dolphinAttack.m). 

Lancer l'attaque : 
Vous pouvez utiliser le fichier napo48.wav ou réaliser votre propre son d'attaque. Dans ce second cas veillez à ce que votre son soit parfaitement audible avec très peu de bruit, privilégiez un enregistrement échantillonné à 48kHz de façon à pouvoir utiliser des fréquences d'émission plus importantes - Théorème de Nyquist). Le son dans napo58.wav est " OK Google, Quand est mort napoléon ? ". Il faut ensuite lancer le programme matlab en utilisant la commande suivante : soundsc(x_hf_2, Fs). soundsc permet de lire le nouveau fichier dont la fréquence a été modifiée, x_hf_2 est le 2ie type de modulation en amplitude c'est-à-dire celui utilisé pour l'attaque, Fs est la fréquence d'émission.
Approchez le microphone de votre appareil à reconnaissance vocale de votre émetteur et assurez-vous qu'il n'y a pas de bruit autour de vous, surtout si la puissance d'émission est faible. 


Les résultats des expériences peuvent être plus ou moins aléatoires surtout dans le cas où les appareils à reconnaissance vocale sont "speaker-dependant" c'est-à-dire qu'ils reconnaissent la voix de l'utilisateur. C'est le cas de Siri par exemple. Dans ce cas assurez-vous que la voix utilisée est bien celle qui permet de déverrouiller le téléphone. Il est possible de faire une attaque par force brute car deux voix qui se ressemblent peuvent activer la reconnaissance vocale. Pour cela je vous conseille d'utiliser des TTS (text-to-speech) qui permettent d'imiter la majorité des voix humaines. Cependant, l'attaque est plus facile dans le cas des "speaker-independant", ce qui est le cas de OK Google, ou Alexa par exemple.


N'hésitez pas à aller lire les deux exploits suivants, ce sont ceux de collègues sur l'attaque BlueBone. Vous pouvez les utiliser afin d'attaquer les assistants vocaux tels que Alexa afin d'obtenir les droits root dessus.
https://github.com/AxelRoudaut/THC_BlueBorne
https://github.com/2Dai/Bluesploit
