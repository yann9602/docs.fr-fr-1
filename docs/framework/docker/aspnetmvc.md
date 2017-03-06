---
title: "Migration d’applications ASP.NET MVC vers des conteneurs Windows"
description: "Découvrez comment prendre une application ASP.NET MVC et l’exécuter dans un conteneur Docker Windows"
keywords: Conteneurs Windows, Docker, ASP.NET MVC
author: BillWagner
ms.author: wiwagn
ms.date: 02/01/2017
ms.topic: article
ms.prod: .net-framework
ms.technology: dotnet-mvc
ms.devlang: dotnet
ms.assetid: c9f1d52c-b4bd-4b5d-b7f9-8f9ceaf778c4
translationtype: Human Translation
ms.sourcegitcommit: fcfd1053cdb161b3ebe1ae61b84c90e68b94a26b
ms.openlocfilehash: 6534435823e32aa5c61802ccc587c2761a3fe893

---

# <a name="migrating-aspnet-mvc-applications-to-windows-containers"></a>Migration d’applications ASP.NET MVC vers des conteneurs Windows

L’exécution d’une application .NET Framework existante dans un conteneur Windows ne nécessite aucune modification de votre application. Pour exécuter votre application dans un conteneur Windows, vous créez une image Docker contenant votre application et lancez le conteneur. Cette rubrique décrit comment prendre une [application ASP.NET MVC](http://www.asp.net/mvc) existante et la déployer dans un conteneur Windows.

Vous partez d’une application ASP.NET MVC existante, puis générez les ressources publiées à l’aide de Visual Studio. Vous utilisez Docker pour créer l’image qui contient et exécute votre application. Vous allez accéder au site en cours d’exécution dans un conteneur Windows et vérifier que l’application fonctionne.

Cet article suppose une connaissance élémentaire de Docker. Vous pouvez en savoir plus sur Docker en lisant l’article [Docker Overview](https://docs.docker.com/engine/understanding-docker/).

L’application que vous allez exécuter dans un conteneur est un site web simple qui répond à des questions de manière aléatoire. Cette application est une application MVC de base sans authentification ni stockage de base de données, qui vous permet de vous concentrer sur le déplacement de la couche web vers un conteneur. Des rubriques futures montreront comment déplacer et gérer le stockage persistant dans des applications en conteneur.

Le déplacement de votre application implique les étapes suivantes :

1. [Création d’une tâche de publication pour générer les ressources d’une image](#publish-script)
2. [Génération d’une image Docker destinée à exécuter votre application](#build-the-image)
3. [Démarrage d’un conteneur Docker qui exécute votre image](#start-a-container)
4. [Vérification de l’application à l’aide de votre navigateur](#verify-in-the-browser)

L’[application terminée](https://github.com/dotnet/docs/tree/master/samples/framework/docker/MVCRandomAnswerGenerator) se trouve sur GitHub.

## <a name="prerequisites"></a>Conditions préalables

L’ordinateur de développement doit être en cours d’exécution
- [Mise à jour anniversaire Windows 10](https://www.microsoft.com/en-us/software-download/windows10/) (ou version ultérieure) ou [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server) (ou version ultérieure). 
- [Docker pour Windows](https://docs.docker.com/docker-for-windows/), version stable 1.13.0 ou 1.12 bêta 26 (ou versions plus récentes)
- [Visual Studio 2015](https://www.visualstudio.com/en-us/visual-studio-homepage-vs.aspx).

> [!IMPORTANT]
> Si vous utilisez Windows Server 2016, suivez les instructions indiquées dans [Déploiement d’un hôte de conteneurs – Windows Server](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment).

Après avoir installé et démarré Docker, cliquez avec le bouton droit sur l’icône de barre d’état système et sélectionnez **Basculer vers les conteneurs Windows**. Cette opération est nécessaire pour exécuter des images Docker basées sur Windows. Cette commande prend quelques secondes :

![Conteneur Windows][windows-container]

## <a name="publish-script"></a>Script de publication

Collectez à un seul emplacement toutes les ressources à charger dans une image Docker. Vous pouvez utiliser la commande **Publier** de Visual Studio pour créer un profil de publication pour votre application. Ce profil placera toutes les ressources dans une arborescence de répertoires que vous copierez dans votre image cible plus loin dans ce didacticiel.

**Étapes de la publication**

1. Cliquez avec le bouton droit sur le projet web dans Visual Studio et sélectionnez **Publier**.
2. Cliquez sur le bouton **Profil personnalisé**, puis sélectionnez **Système de fichiers** comme méthode.
3. Choisissez le répertoire. Par convention, l’exemple téléchargé utilise `bin/PublishOutput`.

![Connexion pour la publication][publish-connection]

Ouvrez la section **Options de publication des fichiers** sous l’onglet **Paramètres**. Sélectionnez **Précompiler durant la publication**. Cette optimisation signifie que, quand vous compilez les vues dans le conteneur Docker, vous copiez les vues précompilées.

![Paramètres de publication][publish-settings]

Cliquez sur **Publier** ; Visual Studio copie alors toutes les ressources nécessaires dans le dossier de destination. 

## <a name="build-the-image"></a>Générer l’image

Définissez votre image Docker dans un fichier Dockerfile. Ce fichier contient des instructions pour l’image de base, des composants supplémentaires, l’application que vous souhaitez exécuter et d’autres images de configuration.  Le fichier Dockerfile est le paramètre d’entrée de la commande `docker build`, qui crée l’image.

Vous allez générer une image basée sur l’image `microsft/aspnet` qui se trouve sur le [Hub Docker](https://hub.docker.com/r/microsoft/aspnet/).
L’image de base, `microsoft/aspnet`, est une image Windows Server. Elle contient Windows Server Core, IIS et ASP.NET 4.6.2. Quand vous exécutez cette image dans votre conteneur, elle démarre automatiquement IIS et tous les sites web installés.

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

Exécutez la commande de génération Docker pour créer l’image qui exécute votre application ASP.NET. Pour ce faire, ouvrez une fenêtre PowerShell et tapez la commande suivante dans le répertoire de la solution :

```
docker build -t mvcrandomanswers .
```

Cette commande génère la nouvelle image en suivant les instructions indiquées dans votre fichier Dockerfile. Celles-ci peuvent inclure l’extraction de l’image de base du [Hub Docker](http://hub.docker.com), puis l’ajout de votre application à cette image.

Une fois cette commande terminée, vous pouvez exécuter la commande `docker images` pour afficher des informations sur la nouvelle image :

```
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
mvcrandomanswers              latest              86838648aab6        2 minutes ago       8.104 GB
```

L’ID de l’image sera différent sur votre ordinateur. À présent, exécutons l’application.

## <a name="start-a-container"></a>Démarrer un conteneur

Démarrez un conteneur en exécutant la commande `docker run` suivante :

```
docker run -d -p 8000:8000 --name randomanswers mvcrandomanswers
```

L’argument `-d` indique à Docker de démarrer l’image en mode détaché. Cela signifie que l’image Docker s’exécute déconnectée de l’interpréteur de commandes actuel.

L’argument `-p 8000:8000` indique à Docker comment mapper les ports entrants. Dans cet exemple, nous utilisons le port 8000 sur l’hôte et sur le conteneur.

La portion `--name randomanswers` donne un nom au conteneur en cours d’exécution. Vous pouvez utiliser ce nom au lieu de l’ID de conteneur dans la plupart des commandes.

`mvcrandomanswers` est le nom de l’image à démarrer.

## <a name="verify-in-the-browser"></a>Vérifier dans le navigateur

> [!NOTE]
> Avec la version actuelle, vous ne pouvez pas accéder à `http://localhost`.
> Il s’agit d’un comportement connu dans WinNAT qui va être résolu. En attendant, vous devez utiliser l’adresse IP du conteneur.

Une fois le conteneur démarré, recherchez son adresse IP pour pouvoir vous connecter à votre conteneur en cours d’exécution à partir d’un navigateur :

```
docker inspect -f "{{ .NetworkSettings.Networks.nat.IPAddress }}" randomanswers
172.31.194.61
```

Connectez-vous au conteneur en cours d’exécution à l’aide de l’adresse IPv4 et du port configuré (8000), `http://172.31.194.61:8000` dans l’exemple. Tapez cette URL dans votre navigateur ; vous devriez voir le site en cours d’exécution.

> [!NOTE]
> Certains logiciels VPN ou proxy peuvent vous empêcher d’accéder à votre site.
> Vous pouvez les désactiver temporairement pour vérifier que votre conteneur fonctionne.

Le répertoire d’exemples sur GitHub contient un [script PowerShell](https://github.com/dotnet/docs/tree/master/samples/framework/docker/MVCRandomAnswerGenerator/run.ps1) qui exécute ces commandes pour vous. Ouvrez une fenêtre PowerShell, accédez au répertoire de votre solution et tapez la commande suivante :

```
./run.ps1
```

La commande ci-dessus génère l’image, affiche la liste des images sur votre ordinateur, démarre un conteneur et affiche l’adresse IP de ce dernier. 

Pour arrêter le conteneur, exécutez une commande `docker
stop` :

```
docker stop randomanswers
```

Pour supprimer le conteneur, exécutez une commande `docker rm` :

```
docker rm randomanswers
```

[windows-container]: media/aspnetmvc/SwitchContainer.png "Basculer vers le conteneur Windows"
[publish-connection]: media/aspnetmvc/PublishConnection.png "Publier dans le système de &fichiers"
[publish-settings]: media/aspnetmvc/PublishSettings.png "Paramètres de publication"



<!--HONumber=Feb17_HO3-->


