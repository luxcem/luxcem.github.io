---
layout: post
title: Programmer Beop
---

Création d’une disposition de clavier française ergonomique
et adaptée à la programmation.

La disposition de clavier AZERTY est largement utilisée en France,
mais elle n’est pas idéale, de nombreuses critiques ont été apportées
au clavier, la disposition des touches parait aléatoire et n’est pas
pensée pour la langue française, des lettres très fréquemment frappées
sont situées à des positions difficiles, de plus de nombreuses
spécificités de la langue française sont oubliées[^3] : majuscules
accentuées, guillemets typographiques (« et »), caractères ligaturés
(œ, æ, Œ, Æ), etc.

Le clavier AZERTY est dérivé du clavier QWERTY dont la disposition a
été pensée à l’époque des machines à écrire mécaniques. La disposition
QWERTY permettait [d’éviter les
blocages](https://en.wikipedia.org/wiki/QWERTY#History_and_purposes)
des touches lors de la frappe rapide). Aujourd’hui ne nous somme plus
limité par la vitesse de frappe, mais on a gardé le reliquat de ces
dispositions de clavier.

# Le bépo

Le clavier **bépo** est assez récent et est aujourd’hui l’alternative
à l’AZERTY la plus utilisée en France. Il se démocratise de plus en
plus[^2]. Il est inspiré de la disposition Dvorak et adapté au
français.

![Disposition bépo]({{ site.url }}/images/programmer_beop/bepo.png)

*Disposition bépo[^3]*

La disposition bépo est formidable, mais elle ne correspond pas à tous
les usages de l’informatique. Elle correspond majoritairement à un
usage en traitement de texte et à la saisie de textes longs. Mes
usages de l'informatique contiennent aussi une part importante de
programmation et d’administration système. Ces taches utilisent des
touches spécifiques, peu utilisées dans la langue naturelle :
accolades { et }, crochets [ et ], chevrons < et >, etc.

# Le Programmer Beop

J’ai donc cherché des variations du bépo plus adaptées à mes usages,
il y en a [quelques
unes](http://bepo.fr/wiki/Variantes_du_b%C3%A9po). Je me suis
particulièrement intéressé à la disposition
[beop](http://beop.free.fr/) de
[Laurent](http://bepo.fr/wiki/Utilisateur:Laurent/disposition) elle
contient de très bonnes idées et remarques sur le bépo classique :

+ Certains caractères utilisés en programmation sont très mal placés
  (#, $, < et >),
+ Certaines lettres sont mal placées (ç, w),
+ Faciliter les roulements sur les groupes de voyelles courants (au,
  eu, ou, ai, ei, oi, ie…),
+ Utilisation de l’**alt gr** symétrique;
+ Échange du M et du F pour limiter les risques de faute de frappe
  entre « n » et « m »

Je n’aimais pas la disposition des chiffres de cette distribution, je
voulais conserver celle du bépo classique.

J’ai tenu compte de ces remarques et j’ai rajouté quelques contraintes
personnelles :

+ Les paires : (,);{,};<,>;[,] sur les touches fortes en AltGr
  (e,i,y,x,t,s,q,g) en sacrifiant quelques majuscules de caractères
  étrangers;
+ Rapprocher les signes **$, #, &**;
+ Accès direct aux appostrophes et guillemets droits (',");
+ ; en AltGr plutôt qu'en maj pour soulager le petit doigt (**;** est très
  fréquent en programmation);
+ Un ñ en accès direct et une tilde non morte (ñ pour l’espagnol et la
  tilde utile en administration système);
+ Inversion du K et de l'apostrophe typographique (apostrophe
  typographique par défaut);
+ Touche compose monétaire (pour taper ¥, ฿, £)
+ Touche compose pour le grec (α, β, γ, λ, π)

## Le cas des modificateurs

Pour cette disposition j’ai également réfléchi à la position des
[modificateurs](https://fr.wikipedia.org/wiki/Touche_de_combinaison).
Deux logiciels que j’utilise quotidiennement font un grand usage des
touches modificatrices : [Emacs](https://www.gnu.org/software/emacs/)
et [i3](https://i3wm.org/). Par ailleurs, sur la plupart des logiciels
les raccourcis claviers sont accessibles en **Ctrl+␣**. Sur les
claviers d’aujourd’hui, la touche contrôle est sous le petit doigt, ce
qui oblige à se contorsionner pour la déclencher. Ce n’a pas toujours
été le cas[^4]. J’ai donc décidé de modifier également la position des
modificateurs :
+ La touche **Ctrl** gauche se trouve à inversé avec la
touche **Alt** pour tomber sous le pouce
+ La touche **Caps Lock** inutile pour moi se trouve en touche
[**Hyper**](http://ergoemacs.org/emacs/emacs_hyper_super_keys.html)
cette touche me permet de rajouter à Emacs des raccourcis
supplémentaires.
+ La touche **AltGr** et la touche
**[Window](https://fr.wikipedia.org/wiki/Windows_(touche))**
permmettent d’accéder aux combinaisons en **AltGr**.
+ La touche **Contrôle** droit devient la touche
  **[Menu](https://fr.wikipedia.org/wiki/Touche_de_menu)** sur les
  claviers laptop cette touche est souvent absente.

## La disposition

![Photo]({{ site.url }}/images/programmer_beop/prbeop.png)

*Clavier Programmer béop*

Voici la disposition que j’utilise actuellement, baptisé le
«programmer béop».

Le temps d’apprentissage n’est pas plus long que le bépo, et il est
plus facile de passer du bépo au **programmer béop** (il vaut mieux
commencer avec les inversions **e**, **i** et **o**, **p**).

## Installation

Les fichiers nécessaire à l’installation sont disponible sur
[github](https://github.com/luxcem/programmer-beop), un script
d’installation en langage python est également fourni (sans garantie).

Pour une installation manuelle, il faut

+ Ajouter le contenu du fichier **symbols** dans le fichier
```/usr/share/X11/xkb/symbols/fr```
+ Ajouter une entrée dans les fichiers
    * ```/usr/share/X11/xkb/rules/base.lst```
    * ```/usr/share/X11/xkb/rules/evdev.lst```
    * ```/usr/share/X11/xkb/rules/base.xml```
    * ```/usr/share/X11/xkb/rules/evdev.xml```

## Comparaison

Le site [Keyboard Layout
Analyzer](http://patorjk.com/keyboard-layout-analyzer/#/main) permet
d’évaluer une disposition de clavier vis à vis d’un corpus, je me suis
amusé à tester le **programmer béop** contre le **bépo**, l’**azerty**
et le **programmer dvorak** sur différents corpus.

![Score Les Misérables]({{ site.url }}/images/programmer_beop/test-miserables.png)

Score sur le premier chapitre des [Misérables](https://fr.wikisource.org/wiki/Les_Mis%C3%A9rables_TI_L1#Chapitre1) de *Victor Hugo*


![Score Alice]({{ site.url }}/images/programmer_beop/alice.png)

Score sur le premier
[chapitre d’Alice au Pays des Merveilles en anglais](https://en.wikisource.org/wiki/Alice's_Adventures_Under_Ground/Chapter_1)
de *Lewis Caroll*


![Score Python]({{ site.url }}/images/programmer_beop/python.png)

Score sur le fichier [basehttp.py](https://github.com/django/django/blob/master/django/core/servers/basehttp.py) du *framework django*

Il est possible de lancer d’autres comparaisons sur le site de
[Keyboard Layout
Analyzer](http://patorjk.com/keyboard-layout-analyzer/#/main) avec le
fichier
[programmer-beop](https://github.com/luxcem/programmer-beop/blob/master/programmer-beop)
disponible sur *github*.


![xkcd.com/554](https://imgs.xkcd.com/comics/not_enough_work.png)

*[https://xkcd.com/554/](https://xkcd.com/554/)*

[^1]: [Vers une norme française pour les claviers informatiques](http://www.culturecommunication.gouv.fr/Politiques-ministerielles/Langue-francaise-et-langues-de-France/Politiques-de-la-langue/Langues-et-numerique/Les-technologies-de-la-langue-et-la-normalisation/Vers-une-norme-francaise-pour-les-claviers-informatiques)
[^2]: [https://linuxfr.org/sondages/la-disposition-bépo…](https://linuxfr.org/sondages/la-disposition-b%C3%A9po%E2%80%A6)
[^3]: © Michka_B / [Wikimedia Commons](https://fr.wikipedia.org/wiki/Disposition_b%C3%A9po#/media/File:KB_French_Dvorak_b%C3%A9po.svg) / CC-BY-SA
[^4]: [The Tragedy of Ctrl/Meta Swap](http://ergoemacs.org/emacs/emacs_kb_shortcuts_pain.html)
