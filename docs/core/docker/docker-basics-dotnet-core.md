---
title: "Découvrir les concepts de base de Docker avec .NET Core"
description: Didacticiel de base .NET Core et Docker
keywords: .NET, .NET Core, Docker, didacticiel
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.workload: dotnetcore
ms.openlocfilehash: 79ded2ce5de5100c18301127a2654f8791b8ed76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="learn-docker-basics-with-net-core"></a>Découvrir les concepts de base de Docker avec .NET Core

Ce didacticiel vous apprend la création de conteneur Docker et les tâches de déploiement pour une application .NET Core. Au cours de ce didacticiel, vous apprenez à :

> [!div class="checklist"]
> * Créer un fichier Dockerfile
> * Créer une application .NET Core
> * Déployer votre application dans un conteneur Docker

La [plateforme Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) utilise le [moteur Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) pour générer et empaqueter rapidement des applications comme [images Docker](https://docs.docker.com/glossary/?term=image). Ces images sont écrites au format [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) pour être déployées et exécutées dans un [conteneur en couches](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

## <a name="net-core-easiest-way-to-get-started"></a>.NET Core : la façon la plus simple de bien démarrer

Avant de créer l’image Docker, vous avez besoin d’une application à mettre en conteneur. Vous pouvez la créer sous Linux, MacOS ou Windows. La façon la plus rapide et la plus simple de procéder consiste à utiliser .NET Core.

Si vous n’êtes pas familiarisé avec l’ensemble d’outils CLI .NET Core, consultez [Vue d’ensemble du SDK .NET Core](../tools/index.md).

Vous pouvez créer des conteneurs Windows et Linux avec des [balises multi-arch](https://github.com/dotnet/announcements/issues/14).

## <a name="your-first-net-core-docker-app"></a>Votre première application Docker .NET Core

### <a name="prerequisites"></a>Prérequis

Pour suivre ce didacticiel :

#### <a name="net-core-20-sdk"></a>Kit SDK .NET Core 2.0

* Installez le [Kit SDK .NET Core 2.0](https://www.microsoft.com/net/core).

Consultez [.NET Core 2.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 2.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.

* Installez votre éditeur de code favori, si ce n’est pas déjà fait.

> [!TIP]
> Vous avez besoin d’installer un éditeur de code ? Essayez [Visual Studio](https://visualstudio.com/downloads) !

#### <a name="installing-docker-client"></a>Installation du client Docker

Installez la version [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) ou ultérieure du client Docker.

Le client Docker peut être installé dans :

* Distributions Linux

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

### <a name="create-a-net-core-20-console-app-for-dockerization"></a>Créer une application console .NET Core 2.0 pour la dockerisation

Ouvrez une invite de commandes et créez un dossier nommé *Hello*. Accédez au dossier créé et tapez les commandes suivantes :

```console
dotnet new console
dotnet run
```

Suivons une procédure pas à pas rapide :

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) crée un fichier projet `Hello.csproj` à jour avec les dépendances nécessaires pour générer une application console.  Il crée également `Program.cs`, un fichier de base contenant le point d’entrée pour l’application.
   
   `Hello.csproj`:

   Le fichier projet spécifie tout ce qui est nécessaire pour restaurer les dépendances et générer le programme.

   * La balise `OutputType` spécifie que nous générons un fichier exécutable, autrement dit une application console.
   * La balise `TargetFramework` spécifie l’implémentation .NET que nous ciblons. Dans un scénario avancé, vous pouvez spécifier plusieurs frameworks cibles et y effectuer une génération globale en une seule opération. Dans ce didacticiel, nous effectuons une génération pour .NET Core 2.0.

   `Program.cs`:

   Le programme commence par `using System`. Cette instruction signifie « Placer tout ce qui se trouve dans l’espace de noms `System` dans la portée de ce fichier ». L’espace de noms `System` inclut des constructions de base, telles que `string`, ou des types numériques.

   Ensuite, nous définissons un espace de noms appelé `Hello`. Vous pouvez le modifier à votre gré. Une classe nommée `Program` est définie dans cet espace de noms avec une méthode `Main` qui accepte un tableau de chaînes comme argument. Ce tableau contient la liste des arguments passés quand le programme compilé est appelé. Dans notre exemple, le programme écrit uniquement « Hello World! » dans la console.

2. `$ dotnet restore`

   Dans .NET Core 2.x, **dotnet new** exécute la commande [`dotnet restore`](../tools/dotnet-restore.md). **Dotnet restore** restaure l’arborescence des dépendances avec un appel [NuGet](https://www.nuget.org/) (gestionnaire de package .NET).
   NuGet exécute les tâches suivantes :
   * il analyse le fichier *Hello.csproj* ; 
   * il télécharge les dépendances de fichiers (ou les extrait du cache de votre ordinateur) ;
   * il écrit le fichier *obj/project.assets.json*.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   Le fichier *project.assets.json* réunit le graphique des dépendances NuGet, les résolutions de liaisons et d’autres métadonnées d’application. Ce fichier requis est utilisé par d’autres outils, tels que [`dotnet build`](../tools/dotnet-build.md) et [`dotnet run`](../tools/dotnet-run.md), pour traiter correctement le code source.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) appelle [`dotnet build`](../tools/dotnet-build.md) pour confirmer une génération réussie, puis appelle `dotnet <assembly.dll>` pour exécuter l’application.
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    Pour les scénarios avancés, consultez [Déploiement d’applications .NET Core](../deploying/index.md) pour plus d’informations.

## <a name="dockerize-the-net-core-application"></a>Dockeriser l’application .NET Core

L’application console .NET Core Hello est exécutée correctement en local. Franchissons maintenant une étape supplémentaire pour générer et exécuter l’application dans Docker.

### <a name="your-first-dockerfile"></a>Votre premier fichier Dockerfile

Ouvrez votre éditeur de texte et c’est parti ! Nous travaillons encore à partir du répertoire Hello dans lequel nous avons créé l’application.

Ajoutez les instructions Docker suivantes pour les [conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) ou Linux à un nouveau fichier. Quand vous avez terminé, enregistrez-le à la racine de votre répertoire Hello comme **Dockerfile**, sans extension (vous devrez peut-être définir le type de fichier `All types (*.*)` ou un type similaire).

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Le fichier Dockerfile contient des instructions de génération Docker qui s’exécutent de manière séquentielle.

La première instruction doit être [**FROM**](https://docs.docker.com/engine/reference/builder/#from). Cette instruction initialise une nouvelle étape de génération et définit l’image de base pour les instructions restantes. Les balises multi-arch extraient les conteneurs Windows ou Linux selon le [mode conteneur](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) Docker pour Windows. L’image de base pour notre exemple est l’image 2.0-sdk du dépôt microsoft/dotnet,

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

L’instruction [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) définit le répertoire de travail pour toute instruction Dockerfile RUN, CMD, ENTRYPOINT, COPY et ADD restante. Si le répertoire n’existe pas, il est créé. Dans ce cas, WORKDIR est définie sur le répertoire de l’application.

```Dockerfile
WORKDIR /app
```

L’instruction [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) copie les nouveaux fichiers ou répertoires du chemin source et les ajoute au système de fichiers du conteneur de destination. Avec cette instruction, nous copions le fichier projet C# dans le conteneur.

```Dockerfile
COPY *.csproj ./
```

L’instruction [**RUN**](https://docs.docker.com/engine/reference/builder/#run) exécute toutes les commandes dans une nouvelle couche sur l’image actuelle et valide les résultats. L’image validée obtenue est utilisée pour l’étape suivante dans le fichier Dockerfile. Nous exécutons **dotnet restore** pour obtenir les dépendances nécessaires du fichier projet C#. 

```Dockerfile
RUN dotnet restore
```

Cette instruction **COPY** copie le reste des fichiers dans notre conteneur dans de nouvelles [couches](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).

```Dockerfile
COPY . ./
```

Nous publions l’application avec cette instruction **RUN**. La commande [**dotnet publish**](../tools/dotnet-publish.md) compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire. Notre application est publiée avec une configuration **Release** et une sortie vers le répertoire par défaut.

```Dockerfile
RUN dotnet publish -c Release -o out
```

L’instruction [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) permet d’exécuter le conteneur comme un fichier exécutable.

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Vous disposez maintenant d’un fichier Dockerfile qui :

* Copie votre application sur l’image
* Ajoute les dépendances de votre application à l’image
* Génère l’application pour l’exécuter comme un fichier exécutable

### <a name="build-and-run-the-hello-net-core-20-app"></a>Générer et exécuter l’application .NET Core 2.0 Hello

#### <a name="essential-docker-commands"></a>Commandes Docker essentielles

Ces commandes Docker sont essentielles :

* [docker build](https://docs.docker.com/engine/reference/commandline/build/)
* [docker run](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [docker image](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>Générer et exécuter

Vous avez écrit le fichier Dockerfile ; maintenant, Docker génère votre application, puis exécute le conteneur.

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

La sortie de la commande `docker build` doit être similaire à la sortie de console suivante :

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

Comme vous pouvez le voir dans la sortie, le moteur Docker a utilisé le fichier Dockerfile pour créer notre conteneur.

La sortie de la commande `docker run` doit être similaire à la sortie de console suivante :

```console
Hello World!
```

Félicitations ! Vous venez de :
> [!div class="checklist"]
> * Créer une application .NET Core locale
> * Créer un fichier Dockerfile pour générer votre premier conteneur
> * Générer et exécuter votre application dockerisée



## <a name="next-steps"></a>Étapes suivantes

Voici quelques étapes suivantes que vous pouvez effectuer :

* [Introduction to .NET Docker Images Video](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio, Docker & Azure Container Instances better together!](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [Guides de démarrage rapide Docker pour Azure](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [Déployer votre application sur Docker pour Azure](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> Si vous ne disposez pas d’abonnement Azure, [inscrivez-vous dès aujourd'hui](https://azure.microsoft.com/free/?b=16.48) pour obtenir un compte gratuit pendant 30 jours et 200 dollars US en crédits Azure pour essayer une combinaison quelconque de services Azure.

## <a name="docker-images-used-in-this-sample"></a>Images Docker utilisées dans cet exemple

Les images Docker suivantes sont utilisées dans cet exemple

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>Ressources connexes

* [Exemples Docker .NET Core](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [Dockerfile sur les conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Exemples Docker .NET Framework](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [ASP.NET Core sur DockerHub](https://hub.docker.com/r/microsoft/aspnetcore/)
* [Dockeriser une application .NET Core - Didacticiel Docker](https://docs.docker.com/engine/examples/dotnetcore/)
* [Utilisation des outils Docker dans Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Déploiement d’images Docker à partir du Registre de conteneurs Azure dans Azure Container Instances](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)