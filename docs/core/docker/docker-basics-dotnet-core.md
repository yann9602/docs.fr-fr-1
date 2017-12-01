---
title: Principes fondamentaux de Docker avec le .NET Core
description: Un didacticiel de base .NET Core et de Docker
keywords: .NET, .NET core, Docker, didacticiel
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
ms.openlocfilehash: 5935f67d7e4ca9c9e8768373e2bcaa9febccfdc5
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2017
---
# <a name="learn-docker-basics-with-net-core"></a>Principes fondamentaux de Docker avec le .NET Core

Il vous apprend le Docker conteneur de générer et déployer des tâches pour une application .NET Core. Au cours de ce didacticiel, vous apprendrez :

> [!div class="checklist"]
> * Comment créer un fichier Dockerfile
> * Comment créer une application .NET Core.
> * Comment déployer votre application dans un conteneur Docker.

Le [plateforme Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) utilise le [moteur Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) pour rapidement générer et empaqueter des applications en tant que [Docker images](https://docs.docker.com/glossary/?term=image). Ces images sont écrits le [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format à être déployé et exécuté un [en couche du conteneur](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

## <a name="net-core-easiest-way-to-get-started"></a>.NET core : Plus facile pour la prise en main

Avant de créer l’image de Docker, vous avez besoin d’une application à mettez en conteneur. Vous pouvez le créer sous Linux, Mac OS ou Windows. La plus rapide et plus simple pour ce faire consiste à utiliser .NET Core.

Si vous n’êtes pas familiarisé avec l’ensemble d’outils CLI .NET Core, consultez [Vue d’ensemble du SDK .NET Core](../tools/index.md).

Vous pouvez créer des conteneurs Windows et Linux avec [arch multiples en fonction des balises](https://github.com/dotnet/announcements/issues/14).

## <a name="your-first-net-core-docker-app"></a>Votre première application .NET Core Docker

### <a name="prerequisites"></a>Conditions préalables

Pour effectuer ce didacticiel :

#### <a name="net-core-20-sdk"></a>.NET core SDK 2.0

* Installer [.NET Core SDK 2.0](https://www.microsoft.com/net/core).

Consultez [.NET Core 2.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 2.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.

* Installez votre éditeur favori de code, si vous n’avez pas déjà.

> [!TIP]
> Vous avez besoin pour installer un éditeur de code ? Essayez [Visual Studio](https://visualstudio.com/downloads)!

#### <a name="installing-docker-client"></a>L’installation du Client Docker

Installer [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) ou une version ultérieure du client Docker.

Le client Docker peut être installé dans :

* Distributions Linux

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

### <a name="create-a-net-core-20-console-app-for-dockerization"></a>Créer une application de console .NET Core 2.0 pour Dockerization

Ouvrez une invite de commandes et créez un dossier nommé *Hello*. Accédez au dossier que vous avez créé et tapez les commandes suivantes :

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
   * La balise `TargetFramework` spécifie l’implémentation .NET que nous ciblons. Dans un scénario avancé, vous pouvez spécifier plusieurs infrastructures de cible et de la build vers les infrastructures spécifiés en une seule opération. Dans ce didacticiel, nous build pour .NET Core 2.0.

   `Program.cs`:

   Le programme démarre par `using System`. Cette instruction signifie, « tout placer le `System` espace de noms dans la portée de ce fichier. » L’espace de noms `System` inclut des constructions de base, telles que `string`, ou des types numériques.

   Ensuite, nous définissons un espace de noms appelé `Hello`. Vous pouvez modifier l’espace de noms à votre gré. Une classe nommée `Program` est définie dans cet espace de noms avec une méthode `Main` qui accepte un tableau de chaînes comme argument. Ce tableau contient la liste des arguments passés quand le programme compilé est appelé. Dans notre exemple, le programme n’écrit « Hello World ! » dans la console.

2. `$ dotnet restore`

   Dans le .NET Core 2.x, **dotnet nouvelle** exécute le [ `dotnet restore` ](../tools/dotnet-restore.md) commande. **Restauration de dotnet** restaure l’arborescence des dépendances avec un [NuGet](https://www.nuget.org/)(Gestionnaire de package .NET) appel.
   NuGet effectue les tâches suivantes :
   * analyse le *Hello.csproj* fichier 
   * télécharge le fichier de dépendances (ou extrait du cache de votre ordinateur)
   * écrit le *obj/project.assets.json* fichier

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   Le *project.assets.json* fichier est un ensemble complet d’autres métadonnées de l’application, le graphique de dépendances de NuGet et résolutions de liaison. Cela requis de fichier est utilisé par d’autres outils, tels que [ `dotnet build` ](../tools/dotnet-build.md) et [ `dotnet run` ](../tools/dotnet-run.md), pour traiter correctement le code source.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md)appels [ `dotnet build` ](../tools/dotnet-build.md) pour confirmer une génération réussie, puis appelle `dotnet <assembly.dll>` pour exécuter l’application.
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    Pour les scénarios avancés, consultez [déploiement des applications .NET](../deploying/index.md) pour plus d’informations.

## <a name="dockerize-the-net-core-application"></a>Dockerize l’application .NET Core

L’application de console Hello .NET Core est exécuté avec succès et localement. Maintenant nous allons franchir une étape supplémentaire et générer et exécuter l’application dans Docker.

### <a name="your-first-dockerfile"></a>Votre première Dockerfile

Ouvrez votre éditeur de texte et c’est parti ! Nous travaillons encore à partir du répertoire Hello que nous avons créé l’application dans.

Ajoutez les instructions suivantes de Docker pour soit Linux ou [les conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) vers un nouveau fichier. Lorsque vous avez terminé, enregistrez-le dans la racine de votre répertoire Hello que **Dockerfile**, sans extension (vous devrez peut-être définir votre type de fichier `All types (*.*)` ou quelque chose de similaire).

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

La première instruction doit être [ **FROM**](https://docs.docker.com/engine/reference/builder/#from). Cette instruction Initialise une nouvelle étape de génération et définit l’Image de Base pour les instructions restantes. Les balises multiples arch extraire les conteneurs Windows ou Linux selon le Docker pour Windows [mode conteneur](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers). L’Image de Base pour notre exemple est l’image du Kit sdk 2.0 à partir du référentiel microsoft/dotnet,

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

Le [ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) instruction définit le répertoire de travail pour exécuter restantes, CMD, point d’entrée, copie et ajouter Dockerfile instructions. Si le répertoire n’existe pas, il est créé. Dans ce cas, WORKDIR est définie dans le répertoire de l’application.

```Dockerfile
WORKDIR /app
```

Le [ **copie** ](https://docs.docker.com/engine/reference/builder/#copy) instruction copie des nouveaux fichiers ou des répertoires du chemin d’accès source et les ajoute au système de fichiers de conteneur de destination. Avec cette instruction, nous copions le fichier de projet c# pour le conteneur.

```Dockerfile
COPY *.csproj ./
```

Le [ **exécuter** ](https://docs.docker.com/engine/reference/builder/#run) instruction exécute toutes les commandes dans une nouvelle couche au-dessus de l’image actuelle et validez les résultats. L’image validée obtenue est utilisé pour l’étape suivante dans le fichier Dockerfile. Nous exécutons **dotnet restauration** pour obtenir les dépendances nécessaires du fichier de projet c#. 

```Dockerfile
RUN dotnet restore
```

Cela **copie** instruction copie le reste des fichiers dans notre conteneur dans nouveaux [couches](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).

```Dockerfile
COPY . ./
```

Nous publions l’application avec cette **exécuter** instruction. Le [ **dotnet publier** ](../tools/dotnet-publish.md) commande compile l’application, lit ses dépendances spécifiées dans le fichier projet et publie le jeu résultant de fichiers dans un répertoire. Notre application publiée avec un **version** configuration et la sortie vers le répertoire par défaut.

```Dockerfile
RUN dotnet publish -c Release -o out
```

Le [ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction permet au conteneur à exécuter en tant qu’un fichier exécutable.

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Maintenant vous disposez d’un fichier Dockerfile que :

* copie de votre application à l’image
* dépendances de votre application à l’image
* génère l’application à exécuter en tant qu’un fichier exécutable

### <a name="build-and-run-the-hello-net-core-20-app"></a>Générer et exécuter l’application Hello .NET Core 2.0

#### <a name="essential-docker-commands"></a>Commandes Docker essentiels

Ces commandes Docker sont essentielles :

* [génération docker](https://docs.docker.com/engine/reference/commandline/build/)
* [exécution de docker](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [arrêt de docker](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [image de docker](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>Générer et exécuter

Vous avez écrit le fichier dockerfile ; maintenant, Docker génère votre application, puis exécute le conteneur.

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

La sortie de la `docker build` commande doit être similaire à la sortie de console suivante :

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

Comme vous pouvez le voir à partir de la sortie, le moteur Docker utilisé le fichier Dockerfile pour créer notre conteneur.

La sortie de la `docker run` commande doit être similaire à la sortie de console suivante :

```console
Hello World!
```

Félicitations ! Vous devez simplement :
> [!div class="checklist"]
> * A créé une application .NET Core locale
> * Création d’un fichier Dockerfile pour créer votre premier conteneur
> * Créer et exécuter votre application Dockerized



## <a name="next-steps"></a>Étapes suivantes

Voici quelques astuces que vous pouvez effectuer :

* [Introduction au .NET Docker Images vidéo](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio, Docker et les Instances du conteneur Azure mieux ensemble !](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [Docker pour Azure Démarrages rapides](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [Déployer votre application sur Docker pour Azure](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> Si vous n’avez pas d’un abonnement Azure, [Inscrivez-vous dès aujourd'hui](https://azure.microsoft.com/free/?b=16.48) pour un compte gratuit de 30 jours et un get 200 $ de crédits Azure permettant de tester n’importe quelle combinaison de services Azure.

## <a name="docker-images-used-in-this-sample"></a>Docker Images utilisées dans cet exemple

Les images Docker suivantes sont utilisées dans cet exemple

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>Ressources connexes

* [Exemples de .NET core Docker](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [Informations sur les conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Exemples .NET framework Docker](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [ASP.NET Core sur docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/)
* [Dockerize d’une application .NET Core - didacticiel de Docker](https://docs.docker.com/engine/examples/dotnetcore/)
* [Utilisation des outils de Visual Studio Docker](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Déploiement d’Images Docker à partir du Registre de conteneur Azure pour les Instances du conteneur Azure](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)