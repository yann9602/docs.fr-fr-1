---
title: "Migration d’applications ASP.NET MVC vers des conteneurs Windows"
description: "Découvrez comment prendre une application ASP.NET MVC et l’exécuter dans un conteneur Docker Windows"
keywords: Conteneurs Windows, Docker, ASP.NET MVC
author: BillWagner
manager: wpickett
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework-4.6
ms.technology: dotnet-mvc
ms.devlang: dotnet
ms.assetid: c9f1d52c-b4bd-4b5d-b7f9-8f9ceaf778c4
translationtype: Human Translation
ms.sourcegitcommit: 15c55a87beb64f265a164db918c7721c7690fadf
ms.openlocfilehash: bde267042883d2f25848747047845a16b181e549

---

# <a name="migrating-aspnet-mvc-applications-to-windows-containers"></a>Migration d’applications ASP.NET MVC vers des conteneurs Windows

Exécuter une application existante basée sur .NET Framework dans un conteneur Windows requiert la création de l’image Docker qui contient l’application et le démarrage d’un ou de plusieurs conteneurs pour exécuter cette image. Cette rubrique décrit les tâches à effectuer pour prendre une [application ASP.NET MVC](http://www.asp.net/mvc) existante et la déployer sur un conteneur Windows.

Vous allez partir d’une application ASP.NET MVC existante. Ensuite, vous allez générer les ressources publiées à l’aide de Visual Studio. Vous allez utiliser Docker pour créer l’image qui contient votre application et l’exécute à son démarrage. Quand vous aurez terminé, vous pourrez connecter un navigateur au site exécuté dans un conteneur Windows et vérifier que l’application est en cours d’exécution.

Cet article suppose une connaissance élémentaire de Docker. Vous pouvez en savoir plus sur l’architecture de Docker en consultant [Docker Overview](https://docs.docker.com/engine/understanding-docker/) (Vue d’ensemble de Docker) sur le site Docker, si ces concepts sont nouveaux pour vous.

L’application que vous allez exécuter dans un conteneur est un site web simple qui répond à des questions de manière aléatoire. Cette application est une application MVC de base sans prise en charge d’authentification ou stockage de base de données, qui vous permet de vous concentrer sur le déplacement de la couche web vers un conteneur. Des rubriques futures montreront comment déplacer et gérer le stockage persistant dans des applications en conteneur.

Le déplacement de votre application implique les étapes suivantes :

1. [Création d’une tâche de publication pour générer les ressources d’une image](#publish-script)
2. [Génération d’une image Docker destinée à exécuter votre application](#build-the-image)
3. [Démarrage d’un conteneur Docker qui exécute votre image](#start-a-container)
4. [Vérification de l’application à l’aide de votre navigateur](#verify-in-the-browser)

L’application terminée se trouve dans le [dépôt dotnet / docs sur GitHub](https://github.com/dotnet/docs/tree/master/samples/framework/docker/MVCRandomAnswerGenerator).

## <a name="prerequisites"></a>Conditions préalables

Au minimum, votre ordinateur de développement doit exécuter la [Mise à jour anniversaire Windows 10](https://www.microsoft.com/en-us/software-download/windows10/) ou [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server). 

Avant de commencer, vous devez installer [Docker pour Windows](https://docs.docker.com/docker-for-windows/), version 1.12 bêta 26 ou plus récente. La prise en charge des conteneurs Windows n’est disponible que dans le canal de la version bêta à ce stade.

> [!IMPORTANT]
> Si vous utilisez Windows Server 2016, vous devez suivre les instructions indiquées dans [Déploiement d’un hôte de conteneurs – Windows Server](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/deployment/deployment) avant de pouvoir exécuter des conteneurs Docker.

Après avoir installé et démarré Docker, vous devez cliquer avec le bouton droit sur l’icône de barre d’état système et sélectionner **Switch to Windows containers** (Basculer vers les conteneurs Windows) pour exécuter des images Docker basées sur Windows. Cette commande prend quelques secondes :

![Conteneur Windows][windows-container]

## <a name="publish-script"></a>Script de publication

La première étape consiste à récupérer à un seul emplacement toutes les ressources à charger dans une image Docker. Heureusement, vous pouvez utiliser la commande **Publier** de Visual Studio pour créer un profil de publication pour votre application. Ce profil placera toutes les ressources dans une arborescence que vous copierez dans votre image cible plus loin dans ce didacticiel.

**Étapes de la publication**

1. Cliquez avec le bouton droit sur le projet web dans Visual Studio et sélectionnez **Publier**.
2. Cliquez sur le bouton **Custom profile (Profil personnalisé), puis sélectionnez **Système de fichiers** en guise de méthode.
3. Choisissez le répertoire. Par convention, l’exemple téléchargé utilise `bin/PublishOutput`.

![Connexion pour la publication][publish-connection]

Ensuite, ouvrez la section **Options de publication des fichiers** sous l’onglet **Paramètres**. Sélectionnez **Précompiler durant la publication**. Cette optimisation signifie que quand vous compilez les vues dans le conteneur Docker, vous copiez les vues précompilées.

![Paramètres de publication][publish-settings]

Cliquez sur **Publier** ; Visual Studio copie alors toutes les ressources nécessaires dans le dossier de destination. 

## <a name="build-the-image"></a>Générer l’image

Vous définissez votre image Docker dans un fichier Dockerfile qui contient des instructions pour l’image de base, des composants supplémentaires éventuels, l’application que vous souhaitez exécuter et une image de configuration.  Le fichier Dockerfile est le paramètre d’entrée de la commande `docker build`, qui crée l’image.

Vous allez générer une image basée sur l’image `microsft/aspnet` qui se trouve sur le [Hub Docker](https://hub.docker.com/r/microsoft/aspnet/).
L’image de base, `microsoft/aspnet`, est une image Windows Server. Outre Windows Server Core, elle a IIS et ASP.NET 4.6.2 installés et activés. Quand vous exécutez cette image dans un conteneur, elle démarre automatiquement IIS et tous les sites web installés sont actifs.

Le fichier Dockerfile qui crée votre image ressemble à ceci :

```
# The `FROM` instruction specifies the base image. You are
# extending the `microsoft/aspnet` image.

FROM microsoft/aspnet

# Next, this Dockerfile creates a directory for your application
RUN mkdir C:\randomanswers

# configure the new site in IIS.
RUN powershell -NoProfile -Command \
    Import-module IISAdministration; \
    New-IISSite -Name "ASPNET" -PhysicalPath C:\randomanswers -BindingInformation "*:8000:"

# This instruction tells the container to listen on port 8000. 
EXPOSE 8000

# The final instruction copies the site you published earlier into the container.
ADD containerImage/ /randomanswers
```

Ce fichier Dockerfile ne comprend pas de commande `ENTRYPOINT`. Vous n’en avez pas besoin.
Grâce à l’image de base, IIS démarre quand le conteneur démarre. 

Ensuite, vous devez exécuter une commande de génération Docker pour créer l’image qui exécutera votre application ASP.NET. Pour ce faire, ouvrez une fenêtre PowerShell et tapez la commande suivante dans le répertoire de la solution :

```
docker build -t mvcrandomanswers .
```

Cette commande génère la nouvelle image en suivant les instructions indiquées dans votre fichier Dockerfile. Celles-ci peuvent inclure l’extraction de l’image de base du [Hub Docker](http://hub.docker.com), avant d’ajouter votre application à cette image.

Une fois cette commande terminée, vous pouvez exécuter la commande `docker images` pour afficher des informations sur la nouvelle image :

```
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
mvcrandomanswers              latest              86838648aab6        2 minutes ago       8.104 GB
```

L’ID de l’image sera différent sur votre ordinateur. À présent, exécutons l’application.

## <a name="start-a-container"></a>Démarrer un conteneur

Vous démarrez un conteneur en exécutant la commande `docker run` suivante :

```
docker run -d -p 8000:8000 --name randomanswers mvcrandomanswers
```

L’argument `-d` indique à Docker de démarrer l’image en mode détaché. Cela signifie que l’image Docker s’exécute déconnectée de l’interpréteur de commandes actuel.

L’argument `-p 8000:8000` indique à Docker comment mapper les ports entrants. Dans cet exemple, nous utilisons le port 8000 sur l’hôte et sur le conteneur.

La portion `--name randomanswers` donne un nom au conteneur en cours d’exécution. Vous pouvez utiliser ce nom au lieu de l’ID de conteneur dans la plupart des commandes.

`mvcrandomanswers` est le nom de l’image à démarrer.

## <a name="verify-in-the-browser"></a>Vérifier dans le navigateur

> [!NOTE]
> Avec la version actuelle, vous ne pouvez pas utiliser `http://localhost` pour accéder à votre site. Cela est dû à un comportement connu dans WinNAT, qui sera résolu dans le futur. En attendant, vous devez utiliser l’adresse IP du conteneur.

Une fois le conteneur démarré, vous devez rechercher son adresse IP pour pouvoir vous connecter à votre conteneur en cours d’exécution à partir d’un navigateur :

```
docker inspect -f "{{ .NetworkSettings.Networks.nat.IPAddress }}" randomanswers
172.31.194.61
```

Vous pouvez vous connecter au conteneur en cours d’exécution à l’aide de l’adresse IPv4 et du port configuré (8000), `http://172.31.194.61:8000` dans l’exemple. Tapez cette URL dans votre navigateur ; vous devriez voir le site en cours d’exécution.

> [!NOTE]
> Certains logiciels VPN ou proxy peuvent vous empêcher d’accéder à votre site.
> Vous pouvez les désactiver temporairement pour vérifier que votre conteneur fonctionne.

Le répertoire d’exemples sur GitHub contient un [script PowerShell](https://github.com/dotnet/docs/tree/master/samples/framework/docker/MVCRandomAnswerGenerator/run.ps1) qui exécute ces commandes pour vous. Ouvrez une fenêtre PowerShell, accédez au répertoire de votre solution et tapez la commande suivante :

```
./run.ps1
```

Elle génère l’image, affiche la liste des images sur votre ordinateur, démarre un conteneur et affiche l’adresse IP de ce dernier. 

Quand vous avez terminé et que vous souhaitez arrêter votre conteneur, exécutez une commande `docker
stop` :

```
docker stop randomanswers
```

Pour supprimer le conteneur, exécutez une commande `docker rm` :

```
docker rm randomanswers
```

## <a name="summary"></a>Résumé

Dans cette rubrique, vous avez vu comment déplacer et exécuter une application ASP.NET MVC dans un conteneur Windows Server. L’exécution d’une application existante ne nécessite aucune modification de celle-ci. Vous devez exécuter les tâches consistant à publier votre application, à générer une image Docker et à démarrer cette image dans un nouveau conteneur. Tirer parti des conteneurs Windows Server est la solution la plus simple pour migrer vos applications existantes vers cet environnement.

[Windows-container]: media/aspnetmvc/SwitchContainer.png "Basculer vers le conteneur Windows"
[publish-connection]: media/aspnetmvc/PublishConnection.png "Publier dans le système de fichiers"
[publish-settings]: media/aspnetmvc/PublishSettings.png "Paramètres de publication"



<!--HONumber=Nov16_HO1-->


