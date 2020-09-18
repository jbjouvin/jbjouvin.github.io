# `GiTips`
### Handling two Git accounts !

Hello,

Recently, I was faced with a problem.
How to manage two git accounts on the same computer?
I explain myself, a "`personal`" account and a "`work`" account, on the same computer.
Yes, I know that working on personal things with work materials is a bad habit ... but that's another question.

So, to get rid of just that (I did not invent anything, there are a lot of tutorials on the web), you will need to create a separate directory.
One for work, one for the person.

Regarding git, you will have to manage your \ $ HOME .gitconfig like this:

```bash
[includeIf "gitdir:~/perso/"]
    path = ~/perso/.gitconfig

[includeIf "gitdir:~/work/"]
    path = ~/work/.gitconfig

[user]
```

So as you see, **[user]** is not define. So you'll have to define it in __another__ `.gitconfig`.
So in each directory, create a `.gitconfig`

in the `/perso` directory:

``` bash
[user]
   email = perso@perso.com
   name = name
```

in the `/work` directory:

``` bash
[user]
   email = work@work.com
   name = name
```

And that's it. Each time you'll go into the folder, your "`git user`" will change.

### Bonus
Here is my git alias for log:

yes there is 3, 3 differents view.

``` bash
[alias]
    lg1 = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate
    lg2 = log --pretty=format:"%C(yellow)%h%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --numstat
    l = log --graph --pretty=tformat:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%an %cr)%Creset' --abbrev-commit --date=relative
```

**See you !**
___
# `MaisTéO`
*Météo? Mais t'es ou ?*
___
#### **NewPlayer**

Fevrier 2018 restera un tournant pour moi.
Je suis entré dans une grosse boite de geek et c'est... déroutant...
Déroutant car rien ne fonctionne comme j'ai pu le voir durant mes précedentes années de boulot.
##### *le contexte*
Autant le dire tout de suite, c'est pas évident. Je faisais le malin...
Mais pour apprivoiser la bête ça va pas être simple. 

C'est aussi un poste ingrat sur le papier mais nous (l'équipe) comptons bien lui donner un rôle et un atrait tout particulier.

Il y a aussi pas mal de mouvement, des gens partent d'autre arrivent, quelque reorganisation de service, et du coup c'est pas evident de determiner si ce sera difficile, ou tres difficile.

Une chose est sur c'est que je vais apprendre. C'est pour cela que j'ai dit oui. Et je ne suis pas déçu pour le moment.

> *Et on rigole bien. Et ça c'est encore plus important.*

___
#### **Apprentissage**
Niveau learning j'ai dans ma toDo: (trop de trucs !)

1. [`Django`](https://www.djangoproject.com) ou [`Flask`](http://flask.pocoo.org)

    Rien que la faut déja que je choissise.
    Django a l'air bien, mais la modularité de flask m'attire... beaucoup. Et en ce moment y'a un petit mec bien sympa qui tutote la dessus en mode "one lesson per week" c'est [`Miguel Grinberg`](https://blog.miguelgrinberg.com/)

2. [`React`](https://www.reactjs.org)

    J'ai quelque notions avec ce blog, mais j'aimerais vraiment aller plus loin.

3. [`Chef`](https://www.chef.io/)

    La encore je me dis qu'il faudrait que je me fasse quelque heure dessus.

4. [`Ma femme`](http://mafemme.com)

    Faut vraiment que j'apprenne comment elle fonctionne :D

++


# `HappyNewYear2018`
*Mes sources, podcasts, blogs etc. en français !*

___
#### [`Putain de code !`](http://putaindecode.io)

Si vous etes un dev, front ou pas mais front c'est mieux le site putaindecode.io est vachement bien foutu.

Au départ on tombe dessus car on a besoin d'info sur react. C'était mon cas. Ensuite il se trouve que les mecs ont lancés un podcast. On écoute. Au début c'est le bordel. 

C'est une bande de pote qui se fait chier au taf mais qui aime ce qu'ils font.

Apres l'episode bordelique de cet été les mecs sont revenus avec un épisode de barbus et du coup j'ai kiffé. Comme j'ai kiffé je partage ! 

Bravo a la team

___
#### [`Sam & Max`](http://sametmax.com)
Si vous aimez le python vous aimerez sam. Et vous aimerez max. Et si vous etes un coquin vous aimerez sam et max. 

Au début on peut avoir peur. "Sam et max, du code et du cul" voila comment est présenté le site. Mais derriere se cache un méchan pythonista qui sait de quoi il parle. 

Quel que soit votre niveau, expert debutant, quel que soit votre désir, apprendre ou juste pouvoir débugguer, sam et max c'est ce qu'il vous faut.

___
#### En vrac

* [`Vulgaire dev`](http://vulgairedev.fr/)
* [`Buzut`](https://buzut.fr/)
* [`seboss666`](https://blog.seboss666.info/)
* [`Geekeries`](https://geekeries.org/)
* [`Florian Dambrine`](http://floriandambrine.com/fr/blogposts/)


++

# `Vidéo de présentation des modules terraform:`
___

Faite par un des co fondateurs de [gruntWork](https://www.gruntwork.io), pendant la HashiConf de 2017

#### Vidéo:

<html>
    <body>
        <iframe width="560" height="315" src="https://www.youtube.com/embed/LVgP63BkhKQ">
        </iframe>
    </body>
</html>

#### RegistryTerraForm:

[`https://registry.terraform.io/`](https://registry.terraform.io/)


++

# `Mise à jour du Resume`
___

* Dispo sur [`jbjouvin.pro`](http://www.jbjouvin.pro) en vanillajs
* Dispo sur l'onglet [`Resume`](https://jbjouvin.github.io/resume) en reactjs

++

# `Bienvenue`
___
Bonjour et bienvenue si vous etes arrivé [`ici`](https://fr.wiktionary.org/wiki/ici).

Ce site me permet de blogger quand j'en ai le temps et l'envie et aussi de pense bête.

Il est fait avec create-react-app. 
* L'onglet Resume va chercher ses données dans des json qui sont ensuite parsé en js.
* Les onglets blog et cheatsheet, j'utilise react-markdown, et pour linter le code c'est code-block

Si cela vous interesse ou que vous voulez vous en inspirer, tout le code est sous github:
[`branch dev`](https://github.com/jbjouvin/jbjouvin.github.io/tree/dev)


++

___
```sh
export GITHUB=https://jbjouvin.github.io
```

