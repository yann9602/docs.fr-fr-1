---
title: "Création d’images Docker .NET Core"
description: "Présentation des images Docker et de .NET Core"
keywords: .NET, .NET Core, Docker
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
ms.openlocfilehash: 3ec2d5a58b46e332de41b618f1c3fac663b29bee
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2017
---
# <a name="building-docker-images-for-net-core-applications"></a>Création d’images Docker pour les applications .NET Core

 Dans ce didacticiel, nous concentrer sur l’utilisation de .NET Core sur Docker. Tout d’abord, nous explorons les images Docker différentes proposées et gérés par Microsoft et les cas d’usage. Nous avons ensuite apprendre à générer et dockerize d’une application ASP.NET Core.

Au cours de ce didacticiel, vous apprendrez :
> [!div class="checklist"]
> * En savoir plus sur Microsoft .NET Core Docker images 
> * Obtenir un ASP.NET Core exemple d’application pour Dockerize
> * Exécuter l’exemple d’application ASP.NET localement
> * Générer et exécuter l’exemple avec Docker pour les conteneurs Linux
> * Générer et exécuter l’exemple avec des conteneurs Docker pour Windows

## <a name="docker-image-optimizations"></a>Optimisations des images Docker

Lors de la création d’images Docker pour les développeurs, nous nous sommes concentrés sur trois scénarios principaux :

* Images utilisées pour développer des applications .NET Core
* Images utilisées pour générer des applications .NET Core
* Images utilisées pour exécuter des applications .NET Core

Pourquoi trois images ?
Lorsque le développement, la création et exécution d’applications en conteneur, nous avons des priorités différentes.

* **Développement :** les vues de la priorité sur itérer rapidement les modifications et la possibilité de déboguer les modifications. La taille de l’image n’est pas aussi importante, au lieu de cela pourrez vous apporter des modifications à votre code et les afficher rapidement ?

* **Build :** cette image contient tous les éléments nécessaires pour compiler votre application, ce qui inclut le compilateur et autres dépendances pour optimiser les fichiers binaires.  L’image de la build vous permet de créer les composants que vous placez dans une image de production. L’image de la build doit être utilisé pour l’intégration continue, ou dans un environnement de génération. Cette approche permet à un agent de build compiler et générer l’application (avec toutes les dépendances requises) dans une instance d’image de build. L’agent de build doit seulement savoir comment exécuter cette image Docker.

* **Production :** la vitesse à laquelle vous pouvez déployer et démarrer votre image ? Cette image est petite afin d’optimiser les performances du réseau à partir de votre Registre Docker à vos hôtes Docker. Le contenu est prêt à s’exécuter, ce qui permet d’obtenir le temps le plus court entre l’exécution Docker et les résultats du traitement. Compilation de code dynamique n’est pas nécessaire dans le modèle de Docker. Le contenu que vous placez dans cette image est limité aux fichiers binaires et au contenu nécessaires pour exécuter l’application.

    Par exemple, le `dotnet publish` sortie contient :

    * les fichiers binaires compilés
    * fichiers .js et .css


La raison pour inclure la `dotnet publish` sortie de la commande dans votre image de production consiste à conserver son ' taille au minimum.

Certaines images .NET Core partagent des couches entre des balises différentes afin de télécharger la dernière balise est un processus relativement simples. Si vous avez déjà une version antérieure sur votre ordinateur, cette architecture diminue l’espace disque nécessaire.

Lorsque plusieurs applications utilisent des images communes sur le même ordinateur, la mémoire est partagée entre les images courantes. Les images doivent être identiques pour être partagés.

## <a name="docker-image-variations"></a>Variantes des images Docker

Pour atteindre les objectifs ci-dessus, nous fournissons des variantes d’image sous [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) Cette image contient le SDK .NET Core, qui inclut le .NET Core et les outils de ligne de commande (CLI). Cette image est adaptée au **scénario de développement**. Vous utilisez cette image pour le développement local, de débogage et de test unitaire. Cette image peut également être utilisée pour vos scénarios de **génération**. À l’aide de `microsoft/dotnet:sdk` vous donne toujours la version la plus récente.

> [!TIP]
> Si vous ne savez pas vos besoins, vous souhaitez utiliser le `microsoft/dotnet:<version>-sdk` image. Comme « fait », il est conçu pour être utilisé comme une clause throw conteneur absent (monter votre code source et démarrez le conteneur pour démarrer votre application) et en tant que l’image de base pour créer d’autres images à partir de.

* `microsoft/dotnet:<version>-runtime`: Cette image contient le .NET Core (runtime et bibliothèques) et est optimisée pour l’exécution des applications .NET Core dans **production**.

## <a name="alternative-images"></a>Images alternatives

En plus des scénarios de développement, de génération et de production optimisés, nous fournissons des images supplémentaires :

* `microsoft/dotnet:<version>-runtime-deps`: Le **Dép. de runtime** image contient le système d’exploitation avec toutes les dépendances natives requis par le .NET Core. Cette image est pour [applications autonomes](https://docs.microsoft.com/dotnet/core/deploying/index).

Versions les plus récentes de chaque variante :

* `microsoft/dotnet`ou `microsoft/dotnet:latest` (alias pour l’image du Kit de développement logiciel)
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>Pour Explorer les exemples

* [Cet exemple ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) illustre un modèle pratique meilleures pour générer des images Docker pour ASP.NET Core des applications de production. L’exemple fonctionne avec les conteneurs Linux et Windows.

* Cet exemple de .NET Core Docker montre un modèle pratique meilleures pour [génération Docker images pour les applications .NET Core pour la production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)

## <a name="your-first-aspnet-core-docker-app"></a>Votre première application ASP.NET Core Docker

Pour ce didacticiel, vous permet d’utiliser un exemple d’application ASP.NET Core Docker pour l’application que vous souhaitez dockerize. Cet exemple d’application ASP.NET Core Docker illustre un modèle de pratiques meilleures pour générer des images Docker pour ASP.NET Core des applications de production. L’exemple fonctionne avec les conteneurs Linux et Windows.

L’exemple de fichier Dockerfile crée une image Docker d’application ASP.NET Core basés sur l’image de base ASP.NET Core Runtime Docker.

Elle utilise le [multi-étapes Docker build fonctionnalité](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) à :

* Générez l’exemple dans un conteneur selon le **supérieure** image de base ASP.NET Core génération Docker 
* copie le résultat de la version finale dans une image Docker basée sur le **plus petits** image de base ASP.NET Core Docker Runtime

> [!Note]
> L’image de build contient les outils requis pour créer des applications n’est pas le cas de l’image d’exécution.

### <a name="prerequisites"></a>Conditions préalables

Pour générer et exécuter, installez les éléments suivants :

#### <a name="net-core-20-sdk"></a>.NET core SDK 2.0

* Installer [.NET Core SDK 2.0](https://www.microsoft.com/net/core).

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

#### <a name="installing-git-for-sample-repository"></a>L’installation de Git pour le dépôt d’exemples

* Installer [git](https://git-scm.com/download) si vous souhaitez cloner le référentiel.

### <a name="getting-the-sample-application"></a>Mise en route de l’exemple d’application

Pour obtenir l’exemple le plus simple est en clonant la [référentiel d’exemples](https://github.com/dotnet/dotnet-docker-samples) avec git, utilisez la procédure suivante : 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

Vous pouvez également télécharger le référentiel (elle est petite) comme un fichier zip à partir du référentiel d’exemples .NET Core Docker.

### <a name="run-the-aspnet-app-locally"></a>Exécutez l’application ASP.NET localement

Pour établir un point de référence, avant de mettre l’application dans un conteneur, exécutez l’application localement.

Vous pouvez générer et exécuter l’application localement avec le .NET Core 2.0 SDK à l’aide des commandes suivantes (les instructions supposent la racine du référentiel) :

```console
cd aspnetapp
dotnet run
```

Une fois que l’application démarre, visitez **http://localhost : 5000** dans votre navigateur web.

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>Générer et exécuter l’exemple avec Docker pour les conteneurs Linux

Vous pouvez générer et exécuter l’exemple dans Docker à l’aide de conteneurs Linux à l’aide des commandes suivantes (les instructions supposent la racine du référentiel) :

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!Note] Le `docker run` '-p' argument mappages de port 5000 sur votre ordinateur local vers le port 80 dans le conteneur (la forme de mappage de port est `host:container`). Pour plus d’informations, consultez la [docker exécuter](https://docs.docker.com/engine/reference/commandline/exec/) référence sur les paramètres de ligne de commande.

Une fois que l’application démarre, visitez **http://localhost : 5000** dans votre navigateur web.

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>Générer et exécuter l’exemple avec des conteneurs Docker pour Windows

Vous pouvez générer et exécuter l’exemple dans Docker à l’aide de conteneurs Windows à l’aide des commandes suivantes (les instructions supposent la racine du référentiel) :

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> Vous devez naviguer jusqu'à la **adresse IP de conteneur** (par opposition à http://localhost) dans votre navigateur directement lors de l’utilisation de conteneurs Windows. Vous pouvez obtenir l’adresse IP de votre conteneur en procédant comme suit :

* Ouvrez une autre invite de commandes.
* Exécutez `docker ps` pour voir vos conteneurs en cours d’exécution. Le conteneur « aspnetcore_sample » doit être visible.
* Exécutez `docker exec aspnetcore_sample ipconfig`.
* Copiez l’adresse IP de conteneur et le coller dans votre navigateur (par exemple, 172.29.245.43).

> [!Note]
> Exec de docker prend en charge l’identification des conteneurs avec le nom ou le hachage. Dans notre exemple, le nom (aspnetcore_sample) est utilisé.

Consultez l’exemple suivant illustrant comment obtenir l’adresse IP d’un conteneur Windows en cours d’exécution.

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!Note]
> Exec de docker s’exécute une commande dans un conteneur en cours d’exécution. Pour plus d’informations, consultez la [référence exec de docker](https://docs.docker.com/engine/reference/commandline/exec/) sur les paramètres de ligne de commande.

Vous pouvez générer une application qui est prête à déployer en production localement à l’aide de la [dotnet publier](../tools/dotnet-publish.md) commande.

```console
dotnet publish -c release -o published
```

> [!Note]
> L’argument de version - c génère l’application en mode version finale (la valeur par défaut est le mode débogage). Pour plus d’informations, consultez la [dotnet exécuter référence](../tools/dotnet-run.md) sur les paramètres de ligne de commande.

Vous pouvez exécuter l’application sur **Windows** à l’aide de la commande suivante.

```console
dotnet published\aspnetapp.dll
```

Vous pouvez exécuter l’application sur **Linux** ou **macOS** à l’aide de la commande suivante.

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>Docker Images utilisées dans cet exemple

Les images Docker suivantes sont utilisées dans cet exemple

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

Félicitations ! Vous devez simplement :
> [!div class="checklist"]
> * Appris sur les images de Microsoft .NET Core Docker
> * Vous avez une ASP.NET Core exemple d’application pour Dockerize
> * Exécution de l’exemple d’application ASP.NET localement
> * Créer et exécuter l’exemple avec Docker pour les conteneurs Linux
> * Créer et exécuter l’exemple avec des conteneurs Docker pour Windows


**Étapes suivantes**

Voici quelques astuces que vous pouvez effectuer :

* [Utilisation des outils de Visual Studio Docker](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Déploiement d’Images Docker à partir du Registre de conteneur Azure pour les Instances du conteneur Azure](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Débogage avec Visual Studio Code](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [Prise en mains avec Visual Studio pour Mac, les conteneurs et sans code dans le cloud](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Prise en main Docker et Visual Studio pour Mac Lab](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!Note]
> Si vous n’avez pas d’un abonnement Azure, [Inscrivez-vous dès aujourd'hui](https://azure.microsoft.com/free/?b=16.48) pour un compte gratuit de 30 jours et un get 200 $ de crédits Azure permettant de tester n’importe quelle combinaison de services Azure.
