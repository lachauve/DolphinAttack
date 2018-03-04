# DolphinAttack
Projet étudiant pour la THC du 9 et 10 mars 2018.
https://toulousehackingconvention.fr/

Qu'est-ce que la Dolphin Attack ? 

La dolphin Attack est une attaque par ultrasons qui cible les appareils à reconnaissance vocale tels que Siri, Alexa (Amazon Echo), OkGoogle, Cortana (Microsoft) mais aussi ceux de certaines voitures. L'objectif est de reproduire la voix humaine dans des fréquences inaudibles pour un humain (au delà de 20kHz). 


Matériel nécessaire à l'attaque.
- Un émetteur : expérience faite avec un MacBook Pro (Retina - macOS HighSierra - processor 2,2 GHz Intel Core i7)
Attention, un ordinateur trop ancien ne sera pas capable d'émettre des ultrasons, avant de lancer l'attaque pensez à vérifier que votre ordinateur peut bien émettre à des fréquences supérieures à 20000 Hz. L'émetteur peut aussi être un téléphone tel qu'un Samsung s6 Edge (non testé personnellement). 
- Dans le cas où l'émetteur n'est pas assez puissant vous pouvez rajouter un amplificateur avant la sortie. J'ai testé avec des enceintes de musique de type : M-audio av40 cela marchait parfaitement bien jusqu'à une distance de 20 cm (environ). J'ai aussi essayé avec un emetteur à ultra sons http://fr.farnell.com/multicomp/mcpct-g5100-4139/ultrasonic-transducer/dp/1801068?ost=1801068&ddkey=http%3Afr-FR%2FElement14_France%2Fsearch pour lequel j'ai rajouté un amplificateur maison associé à un générateur de courant, cela marchait bien à condition que la fréquence soit assez élevée. Il faut cependant que la carte son puisse tout de même créer les ultrasons sinon cela ne marchera pas.
- Un récepteur : mes expériences ont été réalisées avec "OK Google" sur un Sony Xperia E5, les résultats étaient très concluants. J'ai aussi essayé avec Alexa de Amazon Echo mais les résultats étaient moins concluants, de même avec Siri. 


Pour transporter le message sonore dans les fréquences à ultrasons, il faut réaliser une modulation d'amplitude. Celle-ci est faite logiciellement avec Matlab (ou Octave). Il est aussi possible de créer un modulateur à amplitude de façon matérielle (électronique), ce que je vous conseille dans le cas où votre carte son ne parvient pas à émettre d'ultrasons. Pour obtenir le signal de sortie, c'est-à-dire le signal modulé on réalise l'opération suivante : s(t) = m(t)cos(2*pi*fc*t) + cos(2*pi*fc*t) . Pour un meilleur résulat, je vous conseil de passer votre signal d'entrée dans un filtre passe bas (fonction butter sous matlab).
