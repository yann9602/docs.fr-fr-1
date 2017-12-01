---
title: "Flux de travail de développement pour les applications de Docker"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Flux de travail de développement pour les applications de Docker"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5a53aee4261a5a0bfc25b3520c50cf505b84f287
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="development-workflow-for-docker-apps"></a>Flux de travail de développement pour les applications de Docker

Le cycle de vie de développement d’application démarre sur l’ordinateur de chaque développeur, où le développeur les codes de l’application à l’aide de leur langue par défaut et il teste localement. Quel que soit le langage, d’infrastructure et plateforme choisit par le développeur, ce flux de travail, le développeur est toujours développement et test des conteneurs Docker, mais en localement.

Chaque conteneur (il s’agit d’une instance d’une image Docker) inclut les composants suivants :

-   Une sélection de système d’exploitation (par exemple, une distribution Linux, Windows Nano Server ou Windows Server Core).

-   Fichiers ajoutés par le développeur (fichiers binaires d’application, etc.).

-   Informations de configuration (paramètres d’environnement et dépendances).

## <a name="workflow-for-developing-docker-container-based-applications"></a>Flux de travail pour développer des applications de conteneur Docker

Cette section décrit la *la boucle interne* flux de travail de développement pour les applications de conteneur Docker. Le flux de travail de la boucle interne signifie qu’il ne prend pas en compte le flux de travail DevOps plus large et que vous venez se concentre sur le travail de développement effectué sur l’ordinateur du développeur. Les étapes initiales pour configurer l’environnement ne sont pas inclus, étant donné que celles sont effectuées une seule fois.

Une application se compose de vos propres services ainsi que des bibliothèques supplémentaires (dépendances). Voici les étapes de base généralement lors de la création d’une application de Docker, comme illustré dans la Figure 5-1.

![](./media/image1.png)

**Figure 5-1.** Flux de travail pas à pas pour le développement d’applications de Docker placées dans des conteneurs

Dans ce guide, ce processus est détaillé et chaque étape majeure est expliquée en se concentrant sur un environnement Visual Studio.

Lorsque vous utilisez une approche du développement de l’éditeur/CLI (par exemple, Visual Studio Code plus CLI Docker sur macOS ou Windows), vous devez connaître toutes les étapes, généralement dans plus de détails que si vous utilisez Visual Studio. Pour plus d’informations sur l’utilisation dans un environnement CLI, consultez le livre électronique [cycle de vie des applications en conteneur géré Docker avec Platforms Microsoft et les outils](http://aka.ms/dockerlifecycleebook/).

Lorsque vous utilisez Visual Studio 2015 ou Visual Studio 2017, nombre de ces opérations sont gérées pour vous, ce qui améliore considérablement votre productivité. Cela est particulièrement vrai lorsque vous êtes à l’aide de Visual Studio 2017 et ciblage des applications conteneur multiples. Par exemple, avec juste un clic de souris, Visual Studio ajoute le fichier Dockerfile et docker-compose.yml à vos projets avec la configuration de votre application. Lorsque vous exécutez l’application dans Visual Studio, il génère l’image Docker et exécute l’application conteneur multi directement dans Docker. Il vous permet même de déboguer plusieurs conteneurs en même temps. Ces fonctionnalités augmentera la vitesse de votre développement.

Toutefois, parce que Visual Studio apporte ces étapes automatique ne signifie pas que vous n’avez pas besoin de savoir ce qui se passe en dessous d’on avec Docker. Par conséquent, dans les instructions qui suivent, nous avons décrit en détail chaque étape.

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Étape 1. Commencer à coder et créer votre application initiale ou la ligne de base du service

Développement d’une application de Docker est similaire à celle que vous développez une application sans Docker. La différence est que lors du développement de Docker, vous déployez et testez votre application ou les services qui s’exécutent dans des conteneurs Docker dans votre environnement local. Le conteneur peut être un conteneur de Linux ou un conteneur Windows.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Configurer votre environnement local avec Visual Studio

Pour commencer, assurez-vous que vous avez [Docker Community Edition (CE)](https://www.docker.com/community-edition) pour Windows est installé, comme expliqué dans les instructions suivantes :

[Prise en main Docker CE pour Windows](https://docs.docker.com/docker-for-windows/)

En outre, vous devez Visual Studio 2017 installé. Cela est préférable Visual Studio 2015 avec Visual Studio Tools pour Docker au complément, car Visual Studio 2017 d’autres avancées prise en charge pour Docker, telles que la prise en charge pour le débogage des conteneurs. Visual Studio 2017 inclut les outils pour Docker si vous avez sélectionné le **.NET Core et Docker** la charge de travail pendant l’installation, comme indiqué dans la Figure 5-2.

![](./media/image3.png)

**Figure 5-2**. En sélectionnant le **.NET Core et Docker** la charge de travail lors de l’installation de Visual Studio 2017

Vous pouvez démarrer le codage de votre application dans le .NET brut (généralement dans le .NET Core si vous envisagez d’utiliser des conteneurs) même avant l’activation de Docker dans votre application et de déploiement et de test dans Docker. Toutefois, il est recommandé que vous commencez à travailler sur Docker dès que possible, car qui correspond à l’environnement réel et les problèmes peuvent être découverts dès que possible. Cela est recommandé, car Visual Studio facilite ainsi travailler avec Docker que lui semble presque transparent, l’exemple suivant lors du débogage d’applications de conteneur multiples à partir de Visual Studio.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Prise en main Docker CE pour Windows**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

-   **Visual Studio 2017**
    [*https://www.visualstudio.com/vs/visual-studio-2017/*](https://www.visualstudio.com/vs/visual-studio-2017/)

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Étape 2. Créez un fichier Dockerfile lié à une image de base .NET existante

Vous avez besoin d’un fichier Dockerfile pour chaque image personnalisée que vous souhaitez générer ; Vous devez également un fichier Dockerfile pour chaque conteneur pour le déploiement, si vous déployez automatiquement à partir de Visual Studio ou manuellement à l’aide de l’interface CLI Docker (docker exécuter et docker-composer des commandes). Si votre application contient un seul service personnalisé, vous avez besoin d’un fichier Dockerfile unique. Si votre application contient plusieurs services (comme dans une architecture microservices), vous avez besoin d’un fichier Dockerfile pour chaque service.

Le fichier Dockerfile est placé dans le dossier racine de votre application ou service. Il contient les commandes qui indiquent à Docker comment configurer et exécuter votre application ou service dans un conteneur. Vous pouvez manuellement créer un fichier Dockerfile dans le code et l’ajouter à votre projet, ainsi que les dépendances de .NET.

Avec Visual Studio et ses outils pour Docker, cette tâche nécessite seulement quelques clics de souris. Lorsque vous créez un nouveau projet dans Visual Studio 2017, il existe une option nommée **prise en charge du conteneur activer (Docker)**, comme illustré dans la Figure 5-3.

![](./media/image5.png)

**Figure 5-3**. Activer la prise en charge Docker lors de la création d’un nouveau projet dans Visual Studio 2017

Vous pouvez également activer la prise en charge Docker sur un projet nouveau ou existant en cliquant votre fichier projet dans Visual Studio et en sélectionnant l’option **Add-Docker projet prend en charge**, comme illustré dans la Figure 5-4.

![](./media/image6.png)

**Figure 5-4**. L’activation de la prise en charge Docker dans un projet Visual Studio 2017 existant

Cette action sur un projet (par exemple, une application Web ASP.NET ou un service de l’API Web) ajoute un fichier Dockerfile pour le projet avec la configuration requise. Il ajoute également un fichier compose.yml de docker pour la solution dans son intégralité. Dans les sections suivantes, nous décrivons les informations qui sont placées dans chacun de ces fichiers. Visual Studio peut effectuer cette tâche pour vous, mais il est utile de comprendre ce qui se passe dans un fichier Dockerfile.

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>Option a : création d’un projet à l’aide d’une image existante de .NET Docker officielle

Généralement, vous générez une image personnalisée pour votre conteneur par-dessus une image de base que vous pouvez obtenir à partir d’un référentiel officiel à la [Hub Docker](https://hub.docker.com/) Registre. C’est précisément ce qui se passe en arrière-plan lorsque vous activez la prise en charge Docker dans Visual Studio. Votre fichier Dockerfile utilisera une image aspnetcore existante.

Précédemment, nous avons expliqué les images Docker et les référentiels que vous pouvez utiliser, en fonction de la structure et le système d’exploitation que vous avez choisi. Par exemple, si vous souhaitez utiliser ASP.NET Core (Windows ou Linux), l’image à utiliser est microsoft / aspnetcore:2.0. Par conséquent, vous devez simplement spécifier quelle image Docker base à utiliser pour votre conteneur. Pour ce faire, l’ajout de microsoft / aspnetcore:2.0 à votre fichier Dockerfile. Cela sera effectuée automatiquement par Visual Studio, mais si vous mettez à jour la version, vous mettez à jour cette valeur.

À l’aide d’un référentiel d’images officiel .NET à partir du Hub d’ancrage avec un numéro de version garantit que les mêmes fonctionnalités de langage sont disponibles sur tous les ordinateurs (y compris le développement, test et production).

L’exemple suivant montre un exemple de fichier Dockerfile pour un conteneur ASP.NET Core.

```
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

Dans ce cas, le conteneur est basé sur la version 2.0 de l’image ASP.NET Core Docker officiel (arch multiples pour Linux et Windows). Il s’agit du paramètre `FROM microsoft/aspnetcore:2.0`. (Pour plus d’informations sur cette image de base, consultez le [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page et le [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) Dans le fichier Dockerfile, vous devez également indiquent à Docker à l’écoute sur le port TCP que vous utiliserez lors de l’exécution (dans ce cas, le port 80, tel que configuré avec le paramètre exposer).

Vous pouvez spécifier des paramètres de configuration supplémentaires dans le fichier Dockerfile, en fonction de la langue et le framework que vous utilisez. Par exemple, la ligne de point d’entrée avec \[« dotnet », « MySingleContainerWebApp.dll »\] indique à Docker pour exécuter une application .NET Core. Si vous utilisez le Kit de développement et de l’interface CLI (dotnet CLI) de .NET Core pour générer et exécuter l’application .NET, ce paramètre est différent. L’essentiel est que la ligne de point d’entrée et d’autres paramètres sera différentes selon le langage et la plateforme choisie pour votre application.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Création d’Images de Docker pour les Applications .NET Core**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images)

-   **Créer votre propre image**. Dans la documentation officielle de Docker.
    [*https://docs.docker.com/Engine/Tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>À l’aide de référentiels d’images arch multiples

Un référentiel unique peut contenir des variantes de plateforme, par exemple une image Linux et une image système Windows. Cette fonctionnalité permet aux fournisseurs comme Microsoft (créateurs d’image de base) créer un référentiel unique pour couvrir plusieurs plateformes (c'est-à-dire Linux et Windows). Par exemple, le [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) référentiel disponible dans le Registre du Hub Docker fournit la prise en charge de Linux et Windows Nano Server en utilisant le même nom de référentiel.

Si vous spécifiez une balise, cibler une plateforme qui est explicite, comme dans les cas suivants :

-   **Microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux 

-   **Microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

Cependant et cela est nouveau depuis mid 2017, si vous spécifiez le même nom d’image, même avec la même balise, les nouvelles images multiples arch (par exemple, l’image aspnetcore qui prend en charge plusieurs arch) utiliseront la version de Windows ou Linux en fonction de l’hôte Docker du système d’exploitation que vous déployez , comme indiqué dans l’exemple suivant :

-   **Microsoft / aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

Ainsi, lorsque vous extrayez une image d’un hôte Windows, il sera extrait la variante de Windows et extraire le même nom de l’image à partir d’un hôte Linux extraira la variante de Linux.

### <a name="option-b-creating-your-base-image-from-scratch"></a>Option b : créer votre image de base à partir de zéro

Vous pouvez créer votre propre image de base de Docker à partir de zéro. Ce scénario n’est pas recommandé pour une personne qui démarre avec Docker, mais si vous souhaitez définir les bits spécifiques de votre propre image de base, vous pouvez le faire.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Les images de .NET Core multiples arch**.
https://github.com/dotnet/Announcements/issues/14 
-   **Créer une image de base**. Documentation officielle de Docker.
    [*https://docs.docker.com/Engine/UserGuide/ENG-image/BaseImages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Étape 3. Créer vos images Docker personnalisées et d’intégrer votre application ou service dans les

Pour chaque service dans votre application, vous devez créer une image associée. Si votre application est constituée d’un seul service ou une application web, vous devez simplement une seule image.

Notez que les images Docker sont créées automatiquement pour vous dans Visual Studio. Les étapes suivantes sont uniquement nécessaires pour le flux de travail de l’éditeur/CLI et expliqués par souci de clarté sur ce qui se passe en dessous.

Vous, en tant que développeur, avez besoin développer et tester localement jusqu'à ce que vous appuyez sur une opération de fonctionnalité ou une modification à votre système de contrôle de code source (par exemple, pour GitHub). Cela signifie que vous devez créer les images Docker et déployer des conteneurs à un hôte Docker local (Windows ou Linux VM) exécuter, tester et déboguer par rapport à ces conteneurs locales.

Pour créer une image personnalisée dans votre environnement local à l’aide de Docker CLI et que votre fichier Dockerfile, vous pouvez utiliser la commande de génération docker, comme dans la Figure 5-5.

![](./media/image8.png)

**Figure 5-5**. Création d’une image Docker personnalisée

Si vous le souhaitez, au lieu d’exécuter directement la génération docker à partir du dossier de projet, vous pouvez générer tout d’abord un dossier peut être déployé avec les bibliothèques .NET obligatoires et binaires en exécutant dotnet publient, puis utilisent la commande de génération docker.

Cela va créer une image de Docker avec le nom cesardl/netcore-webapi-microservice-docker : premier. Dans ce cas, : tout d’abord est une balise qui représente une version spécifique. Vous pouvez répéter cette étape pour chaque image personnalisée, que vous devez créer pour votre application composée de Docker.

Lorsqu’une application est constituée de plusieurs conteneurs (autrement dit, il est une application conteneur multi), vous pouvez également utiliser le composer docker haut : commande de génération pour générer toutes les images associées avec une seule commande à l’aide des métadonnées exposées dans le fichiers compose.yml de docker.

Vous trouverez les images existantes dans votre référentiel local à l’aide de la docker commande d’images, comme indiqué dans la Figure 5-6.

![](./media/image9.png)

**Figure 5-6.** Afficher des images existantes à l’aide de la commande d’images docker

### <a name="creating-docker-images-with-visual-studio"></a>Création d’images de Docker avec Visual Studio

Lorsque vous utilisez Visual Studio pour créer un projet avec prise en charge de Docker, vous ne créez pas explicitement une image. Au lieu de cela, l’image est créée pour vous lorsque vous appuyez sur F5 et exécutez l’application dockerized ou un service. Cette étape est automatique dans Visual Studio et vous ne le voit pas se produire, mais il est important de connaître ce qui se passe en dessous de suite.

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Étape 4. Définir vos services dans docker-compose.yml lors de la création d’une application de Docker conteneur multiples

Le [docker-compose.yml](https://docs.docker.com/compose/compose-file/) fichier vous permet de définir un ensemble de services liés à être déployée comme une application composée avec les commandes de déploiement.

Pour utiliser un fichier compose.yml de docker, vous devez créer le fichier dans votre principal ou le dossier racine de la solution, avec un contenu semblable à celui de l’exemple suivant :

```yml
version: '3'
  
services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment: 
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"

```

Notez que ce fichier docker-compose.yml est une version simplifiée et fusionnée. Il contient des données de configuration statique pour chaque conteneur (telles que le nom de l’image personnalisée), qui s’applique toujours, ainsi que les informations de configuration qui peuvent dépendre de l’environnement de déploiement, telles que la chaîne de connexion. Dans les sections suivantes, vous allez apprendre comment vous pouvez fractionner la configuration de docker-compose.yml en plusieurs docker-composer des fichiers et des valeurs de remplacement en fonction du type d’environnement et l’exécution (debug ou release).

L’exemple de fichier docker-compose.yml définit cinq services : le webmvc service (une application web), deux microservices (catalog.api et ordering.api) et les données une seule source conteneur, sql.data, basée sur SQL Server pour Linux en cours d’exécution en tant que conteneur. Chaque service est déployé en tant que conteneur, une image Docker est nécessaire pour chacun.

Le fichier docker-compose.yml spécifie non seulement quels conteneurs sont utilisés, mais comment elles sont configurées individuellement. Par exemple, la webmvc définition de conteneur dans le fichier .yml :

-   Utilise un Shopping avant génération / image de web : plus tard. Toutefois, vous pouvez également configurer l’image à générer dans le cadre de la composition de docker l’exécution avec une configuration supplémentaire est basé sur une build : section dans le fichier docker-compose.

-   Initialise les deux variables d’environnement (URL du catalogue et OrderingUrl).

-   Transfère l’exposé port 80 sur le conteneur pour le port externe 80 sur l’ordinateur hôte.

-   Des liens de l’application web vers le catalogue et le classement de service avec le dépend\_sur la configuration. Ainsi, le service d’attente jusqu'à ce que ces services sont démarrés.

Nous examinerons le fichier docker-compose.yml dans une section ultérieure, lorsque nous expliquent comment implémenter microservices et le conteneur de plusieurs applications.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Utilisation de docker-compose.yml dans Visual Studio 2017

Lorsque vous ajoutez une prise en charge de la solution Docker à un projet de service dans une solution Visual Studio, comme illustré dans la Figure 5-7, Visual Studio ajoute un fichier Dockerfile à votre projet, et il ajoute une section de service (projet) dans votre solution avec les fichiers compose.yml de docker. Il s’agit d’une méthode simple pour démarrer la composition de votre solution de plusieurs conteneurs. Vous pouvez ensuite ouvrir les fichiers compose.yml de docker et les mettre à jour avec des fonctionnalités supplémentaires.

![](./media/image6.png)

**Figure 5-7**. Ajout de prise en charge Docker dans Visual Studio 2017 en double-cliquant sur un projet ASP.NET Core

Ajout de prise en charge Docker dans Visual Studio non seulement ajoute le fichier Dockerfile à votre projet, mais ajoute les informations de configuration à plusieurs fichiers de docker-compose.yml globales sont définies au niveau de la solution.

Après avoir ajouté la prise en charge Docker à votre solution dans Visual Studio, vous verrez également un nouveau nœud (dans le fichier de projet docker-compose.dcproj) dans l’Explorateur de solutions qui contient les fichiers ajoutés docker-compose.yml, comme indiqué dans la Figure 5-8.

![](./media/image11.PNG)

**Figure 5 à 8**. Le **composer de docker** du nœud d’arbre ajouté dans l’Explorateur de solutions de Visual Studio 2017

Vous pourriez déployer une application conteneur multiples avec un fichier de docker-compose.yml unique à l’aide de la composition docker commande. Toutefois, Visual Studio ajoute un groupe d’éléments afin de vous pouvez remplacer les valeurs en fonction de l’environnement (de développement et de production) et l’exécution (release et debug) de type. Cette fonctionnalité est expliquée dans les sections suivantes.

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Étape 5. Générer et exécuter votre application de Docker

Si votre application n’a qu’un seul conteneur, vous pouvez l’exécuter en la déployant sur l’hôte Docker (machine virtuelle ou serveur physique). Toutefois, si votre application contient plusieurs services, vous pouvez déployer il comme une application composée, soit à l’aide d’une seule commande CLI (docker-composer des), ou avec Visual Studio, qui sera utilisée dans la zone d’arrière-plan. Examinons les différentes options.

### <a name="option-a-running-a-single-container-with-docker-cli"></a>Option a : exécutant un simple conteneur avec Docker CLI

Vous pouvez exécuter un conteneur Docker à l’aide de la commande docker run, comme dans la Figure 5-9 :

```
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

**Figure 5-9**. Un conteneur Docker à l’aide de la commande docker run en cours d’exécution

Dans ce cas, la commande lie le port interne 5000 du conteneur vers le port 80 de l’ordinateur hôte. Cela signifie que l’ordinateur hôte est à l’écoute sur le port 80 et au port 5000 sur le conteneur de transfert.

### <a name="option-b-running-a-multi-container-application"></a>Option b : exécution d’une application de conteneur multiples

Dans la plupart des scénarios d’entreprise, une application de Docker sera composée de plusieurs services, ce qui signifie que vous avez besoin exécuter une application conteneur multiples, comme indiqué dans la Figure 5-10.

![](./media/image14.png)

**Figure 5-10**. Machine virtuelle avec des conteneurs Docker déployé

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a>Exécution d’une application de conteneur multiples avec l’interface CLI de Docker

Pour exécuter une application conteneur multiples avec l’interface CLI de Docker, vous pouvez exécuter la docker-composer des commandes. Ce fichier utilise le compose.yml de docker de commande que vous avez au niveau de la solution pour déployer une application conteneur multiples. Figure 5-11 montre les résultats lors de l’exécution de la commande à partir de votre répertoire de projet principal, qui contient le fichier compose.yml de docker.

![](./media/image15.png)

**Figure 5-11**. Exemple de résultats lors de l’exécution le composer docker commande

Après le docker-composer des exécutions de commande, l’application et ses conteneurs connexes sont déployés dans votre hôte Docker, comme illustré dans la représentation sous forme de machine virtuelle dans la Figure 5-10.

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a>En cours d’exécution et débogage d’une application conteneur multiples avec Visual Studio 

Exécution d’une application conteneur multiples à l’aide de Visual Studio 2017 Impossible d’obtenir la plus simple. Vous ne pouvez pas exécuter uniquement l’application conteneur multiples, mais vous êtes en mesure de déboguer tous ses conteneurs directement à partir de Visual Studio en définissant des points d’arrêt normales.

Comme indiqué plus haut, chaque fois que vous ajoutez prise en charge de la solution Docker à un projet dans une solution, ce projet est configuré dans le fichier global (au niveau solution) docker-compose.yml, ce qui vous permet d’exécuter ou déboguer la solution dans son intégralité à la fois. Visual Studio démarre un conteneur pour chaque projet dont la prise en charge de la solution Docker activée et effectuer toutes les étapes internes pour vous (publier dotnet, génération docker, etc.).

Le point important ici est que, comme indiqué dans la Figure 5-12, dans Visual Studio 2017 est un autre **Docker** commande pour l’action clée F5. Cette option vous permet d’exécuter ou déboguer une application conteneur multiples par tous les conteneurs qui sont définies dans les fichiers de docker-compose.yml au niveau de la solution en cours d’exécution. La possibilité de déboguer des solutions de plusieurs conteneurs signifie que vous pouvez définir plusieurs points d’arrêt, chaque point d’arrêt dans un autre projet (conteneur), et pendant le débogage à partir de Visual Studio vous s’arrête aux points d’arrêt définis dans différents projets et en cours d’exécution conteneurs différents.

![](./media/image16.png)

**Figure 5-12**. Conteneur de plusieurs applications en cours d’exécution dans Visual Studio 2017

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Déployer un conteneur ASP.NET à un hôte Docker distant**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Une note sur le test et le déploiement avec orchestrators

Le composer docker des et commandes docker exécuter (ou en cours d’exécution et débogage dans Visual Studio, les conteneurs) conviennent pour les conteneurs de test dans votre environnement de développement. Mais vous ne devez pas utiliser cette approche si vous ciblez des clusters de Docker et orchestrators comme Docker Swarm, mésosphère contrôleur de domaine/système d’exploitation ou Kubernetes. Si vous utilisez un cluster comme [Docker Swarm le mode](https://docs.docker.com/engine/swarm/) (disponible dans Docker CE pour Windows et Mac depuis la version 1.12), vous devez déployer et tester avec des commandes supplémentaires comme [de création du service de docker](https://docs.docker.com/engine/reference/commandline/service_create/) pour services unique. Si vous déployez une application composée de plusieurs conteneurs, vous utilisez [docker Composer offre groupée](https://docs.docker.com/compose/reference/bundle/) et [docker déployer myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) pour déployer l’application composée comme un *pile*. Pour plus d’informations, voir le blog [présentation expérimentale Distributed groupes d’applications de](https://blog.docker.com/2016/06/docker-app-bundle/) dans la documentation de Docker. sur le site Docker.

Pour [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) et [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) vous utiliseriez les commandes de déploiement différentes et des scripts ainsi.

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Étape 6. Tester votre application de Docker à l’aide de l’hôte Docker local

Cette étape varie en fonction de ce que fait votre application. Dans une application .NET Core Web simple qui est déployée comme un seul conteneur ou un service, vous pouvez accéder au service en ouvrant un navigateur sur l’hôte Docker à ce site comme indiqué dans la Figure 5-13. (Si la configuration dans le fichier Dockerfile est mappé le conteneur à un port sur l’ordinateur hôte autre que 80, incluent la publication de l’hôte dans l’URL).

![](./media/image18.png)

**Figure 5-13**. Exemple de test de votre application Docker localement en utilisant localhost

Si localhost ne pointe pas vers le Docker IP de l’hôte (par défaut, lorsque vous utilisez CE de Docker, il doit), pour accéder à votre service, utilisez l’adresse IP de la carte réseau de votre ordinateur.

Notez que cette URL dans le navigateur utilise le port 80 pour l’exemple de conteneur particulier présentées ici. Toutefois, en interne les demandes sont en cours redirigées vers le port 5000, car il s’agit de façon dont il a été déployée avec la commande docker run, comme expliqué à l’étape précédente.

Vous pouvez également tester l’application à l’aide de curl à partir du terminal, comme indiqué dans la Figure 5-14. Dans une installation Docker sur Windows, la valeur par défaut IP de l’hôte Docker est toujours 10.0.75.1 en plus de l’adresse IP réelle de votre ordinateur.

![](./media/image19.png)

**Figure 5-14**. Exemple de test de votre application Docker localement à l’aide de curl

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Test et débogage des conteneurs avec Visual Studio 2017

Lorsqu’en cours d’exécution et les conteneurs avec Visual Studio 2017 le débogage, vous pouvez déboguer l’application .NET de la même façon, comme vous le feriez lors de l’exécution sans les conteneurs.

### <a name="testing-and-debugging-without-visual-studio"></a>Test et débogage sans Visual Studio

Si vous développez à l’aide de l’approche de l’éditeur/CLI, conteneurs de débogage est plus difficile et vous souhaitez déboguer en générant des traces.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Débogage des applications dans un conteneur Docker local**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

-   **Steve Lasker. Générer, déboguer, déployer des applications ASP.NET Core avec Docker.** Vidéo.
    [*https://channel9.msdn.com/events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Flux de travail simplifié lors du développement des conteneurs avec Visual Studio

En effet, le flux de travail à l’aide de Visual Studio est beaucoup plus simple que si vous utilisez l’approche de l’éditeur/CLI. La plupart des étapes requises par Docker liées au fichier Dockerfile et docker-compose.yml fichiers sont masqués ou simplifiés par Visual Studio, comme illustré dans la Figure 5-15.

![](./media/image20.png)

**Figure 5-15**. Flux de travail simplifié lors du développement avec Visual Studio

En outre, vous devez effectuer l’étape 2 (ajout Docker prise en charge pour vos projets) une seule fois. Par conséquent, le flux de travail est similaire à vos tâches de développement habituelles lors de l’utilisation de .NET pour n’importe quel autre développement. Vous devez savoir ce qui se passe en arrière-plan (le processus de génération d’image, les images de base que vous utilisez, le déploiement de conteneurs, etc.) et parfois que vous devez également modifier le fichier Dockerfile ou compose.yml de docker pour personnaliser les comportements. Mais la plupart du travail est considérablement simplifiée à l’aide de Visual Studio, vous apporter beaucoup plus productif.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Steve Lasker. Développement de docker .NET avec Visual Studio 2017**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

-   **Jeffrey T. Fritz. Placer une application de base .NET dans un conteneur avec les nouveaux outils de Docker pour Visual Studio**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>À l’aide des commandes PowerShell dans un fichier Dockerfile pour configurer les conteneurs Windows 

[Les conteneurs Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) vous permettent de convertir vos applications Windows existantes dans les images Docker et les déployer avec les mêmes outils que le reste de l’écosystème Docker. Pour utiliser les conteneurs Windows, vous exécutez des commandes PowerShell dans le fichier Dockerfile, comme indiqué dans l’exemple suivant :

```
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

Dans ce cas, nous sommes à l’aide d’une image de base Windows Server Core (le paramètre FROM) et l’installation d’IIS avec une commande PowerShell (le paramètre d’exécution). De la même façon, vous pouvez également utiliser commandes PowerShell pour configurer des composants supplémentaires comme ASP.NET 4.x, .NET 4.6 ou tout autre logiciel de Windows. Par exemple, la commande suivante dans un fichier Dockerfile définit les ASP.NET 4.5 :

```
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Ressources supplémentaires

-   **ASPNET-docker/Dockerfile.** Exemples de commandes Powershell pour exécuter à partir de fichiers dockerfile pour inclure les fonctionnalités de Windows.
    [*https://github.com/Microsoft/ASPNET-docker/BLOB/Master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
[Précédente] (index.md) [suivant] (.. / net-core-single-containers-linux-windows-server-hosts/index.md)
