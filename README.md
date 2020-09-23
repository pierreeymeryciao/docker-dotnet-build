# Docker .NET - Compilation dans un conteneur

Ce projet sert d'exemple pour démontrer la facilté de compiler une application .NET avec Docker, à l'aide d'un conteneur de compilation.

## Pré-requis

Une installation de Docker >= 17.03 sur une machine Windows, Linux ou Mac : https://docs.docker.com/get-docker/
Une installation de .NET Core sur une machine Windows, Linux ou Max : https://docs.microsoft.com/en-us/dotnet/core/install/

## Technologies utilisées

* .NET Core CLI
* Docker

## Comment exécuter le projet

Dans une invite de commande, récupérer le code source avec `git clone https://github.com/pierreeymeryciao/docker-dotnet-build.git`

Se placer dans le nouveau répertoire créé par cette commande.

Exécuter la commande `docker run --rm -it -v ${PWD}:/<nom du répertoire de l'application> mcr.microsoft.com/dotnet/core/sdk:3.1`

À la fin de l'exécution de cette commande, vous êtes placé dans le shell du conteneur nouvellement créé.

Dans le shell du conteneur, se placer dans le répertoire de l'application à compiler avec la commande `cd /<nom du répertoire de l'application>`

Afin de partir d'une base saine, supprimer les répertoires /bin et /obj avec la commande `rm -rf bin/ obj/`

Exécuter `dotnet restore` pour restaurer les dépendances du projet.

Exécuter `dotnet build` pour construire l'application.

Enfin, exécuter `dotnet publish` pour publier l'application.

Fermer le shell du conteneur en tapant la commande `exit`. Vous êtes de nouveau dans le shelle de la machine hôte.

Se placer dans `<répertoire de l'application>/bin/debug/netcoreapp3.1/`

Exécuter `dotnet myWebApp.dll`

L'application est maintenant accessible à l'adresse localhost:5000 sur la machine hôte.
