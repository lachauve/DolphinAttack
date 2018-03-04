# DolphinAttack
Projet étudiant pour la THC du 9 et 10 mars 2018.
https://toulousehackingconvention.fr/

Qu'est-ce que la Dolphin Attack ? 

La dolphin Attack est une attaque par ultrasons qui cible les appareils à reconnaissance vocale tels que Siri, Alexa (Amazon Echo), OkGoogle, Cortana (Microsoft) mais aussi ceux de certaines voitures. L'objectif est de reproduire la voix humaine dans des fréquences inaudibles pour un humain (au delà de 20kHz). 


Matériel nécessaire à l'attaque.
- Un émetteur : expérience faite avec un MacBook Pro (Retina - macOS HighSierra - processor 2,2 GHz Intel Core i7)
Attention, un ordinateur trop ancien ne sera pas capable d'émettre des ultrasons, avant de lancer l'attaque pensez à vérifier que votre ordinateur peut bien émettre à des fréquences supérieures à 20000 Hz. L'émetteur peut aussi être un téléphone tel qu'un Samsung s6 Edge (non testé personnellement). 
- Dans le cas où l'émetteur n'est pas assez puissant vous pouvez rajouter un amplificateur avant la sortie. J'ai testé avec des enceintes de musique de type : M-audio av40 cela marchait parfaitement bien jusqu'à une distance de 20 cm (environ). J'ai aussi essayé avec un emetteur à ultra sons http://fr.farnell.com/multicomp/mcpct-g5100-4139/ultrasonic-transducer/dp/1801068?ost=1801068&ddkey=http%3Afr-FR%2FElement14_France%2Fsearch pour lequel j'ai rajouté un amplificateur maison cela marchait bien à condition que la fréquence soit assez élevée. Il faut cependant que la carte son puisse tout de même créer les ultrasons sinon cela ne marchera pas.
