---
title: "Création d’images Docker .NET Core"
description: "Présentation des images Docker et de .NET Core"
keywords: .NET, .NET Core, Docker
author: spboyer
ms.author: shboyer
ms.date: 08/29/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.translationtype: HT
ms.sourcegitcommit: 9dc52f3a8c74c1aa575a83cb3bbd579b93fae9ae
ms.openlocfilehash: 0e679ffc22f52de5e2ce8194942efbb2f5299ee4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---

#<a name="building-docker-images-for-net-core-applications"></a>Création d’images Docker pour les applications .NET Core

 
> [!IMPORTANT]
> Nous procédons actuellement à une mise à jour pour .NET Core 2.0. Les instructions ci-dessous sont obsolètes. Veuillez nous excuser pour ce désagrément.

Pour comprendre comment utiliser .NET Core et Docker ensemble, nous devons d’abord examiner les différentes images Docker qui sont proposées et comment choisir celle qui convient. Nous allons ici parcourir les variantes proposées, créer une API Web Core ASP.NET, utiliser les outils Docker Yeoman pour créer un conteneur pouvant être débogué, et regarder comment Visual Studio Code peut apporter une aide au cours du processus. 

## <a name="docker-image-optimizations"></a>Optimisations des images Docker

Lors de la création d’images Docker pour les développeurs, nous nous sommes concentrés sur trois scénarios principaux :

- Images utilisées pour développer des applications .NET Core
- Images utilisées pour générer des applications .NET Core
- Images utilisées pour exécuter des applications .NET Core

Pourquoi trois images ?
Lors du développement, de la génération et de l’exécution d’applications en conteneur, nous avons des priorités différentes.
- **Développement :** la rapidité avec laquelle vous pouvez apporter des modifications de façon itérative, et la possibilité de déboguer les modifications. La taille de l’image est moins importante que la possibilité d’apporter des modifications à votre code et de les voir rapidement. Certains de nos outils, comme [yo docker](https://aka.ms/yodocker) destiné à Visual Studio Code, utilisent cette image pendant la phase de développement. 
- **Génération :** ce qui est nécessaire pour compiler votre application. Ceci inclut le compilateur et toutes les autres dépendances pour optimiser les fichiers binaires. Cette image n’est pas l’image que vous déployez : il s’agit d’une image que vous utilisez pour générer le contenu que vous placez dans une image de production. Cette image est destinée à être utilisée dans votre intégration continue ou votre environnement de génération. Par exemple, au lieu d’installer toutes les dépendances directement sur un agent de build, l’agent de build instancie une image de build pour compiler l’application avec toutes les dépendances nécessaires pour générer l’application contenue dans l’image. L’agent de build doit seulement savoir comment exécuter cette image Docker. 
- **Production :** la rapidité avec laquelle vous pouvez déployer et démarrer votre image. Cette image est de petite taille et elle peut donc transiter rapidement sur le réseau de votre Registre Docker à vos hôtes Docker. Le contenu est prêt à s’exécuter, ce qui permet d’obtenir le temps le plus court entre l’exécution Docker et les résultats du traitement. Dans le modèle Docker non modifiable, la compilation dynamique du code n’est pas nécessaire. Le contenu que vous placez dans cette image est limité aux fichiers binaires et au contenu nécessaires pour exécuter l’application. Par exemple, la sortie publiée en utilisant `dotnet publish`, qui contient les fichiers binaires, les images, et les fichiers .js et .css compilés. Au fil du temps, vous allez voir des images qui contiennent des packages prétraités avec JiT.  

Bien qu’il existe plusieurs versions de l’image .NET Core, elles partagent toutes une ou plusieurs couches. La quantité d’espace disque nécessaire pour stocker ou le delta à extraire de votre Registre sont beaucoup plus petits que la totalité car toutes les images partagent la même couche de base et potentiellement d’autres couches.  

## <a name="docker-image-variations"></a>Variantes des images Docker

Pour atteindre les objectifs ci-dessus, nous fournissons des variantes d’images sous [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/).

- `microsoft/dotnet:<version>-sdk` : c’est-à-dire **microsoft/dotnet:1.0.0-preview2-sdk**, cette image contient le SDK .NET Core, qui inclut le .NET Core et les outils de ligne de commande (CLI). Cette image est adaptée au **scénario de développement**. Vous utilisez cette image pour le développement local, le débogage et les tests unitaires. Par exemple, tous les développements que vous faites, avant d’archiver votre code. Cette image peut également être utilisée pour vos scénarios de **génération**.

- `microsoft/dotnet:<version>-core` : c’est-à-dire **microsoft/dotnet:1.0.0-core**, image qui exécute des [applications .NET Core portables](../deploying/index.md) et qui est optimisée pour l’exécution de votre application en **production**. Elle ne contient pas le SDK et est destinée à prendre la sortie optimisée de `dotnet publish`. Le runtime portable est adapté aux scénarios de conteneur Docker car l’exécution de plusieurs conteneurs bénéficie des couches d’image partagées.  

## <a name="alternative-images"></a>Images alternatives

En plus des scénarios de développement, de génération et de production optimisés, nous fournissons des images supplémentaires :

- `microsoft/dotnet:<version>-onbuild` : c’est-à-dire **microsoft/dotnet:1.0.0-preview2-onbuild**, qui contient des déclencheurs [ONBUILD](https://docs.docker.com/engine/reference/builder/#/onbuild). La génération effectue une opération [COPY](https://docs.docker.com/engine/reference/builder/#/copy) sur votre application, exécute `dotnet restore` et crée une instruction [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) `dotnet run` pour exécuter l’application quand l’image Docker est exécutée. Bien que ce ne soit pas une image optimisée pour la production, elle peut être pratique pour copier simplement le code source dans une image et l’exécuter. 

- `microsoft/dotnet:<version>-core-deps` : c’est-à-dire **microsoft/dotnet:1.0.0-core-deps**. Si vous voulez exécuter des applications autonomes, utilisez cette image. Il contient le système d’exploitation avec toutes les dépendances natives nécessaires à .NET Core. Cette image peut également être utilisée comme image de base pour vos propres builds CoreFX ou CoreCLR personnalisées. Alors que la variante **onbuild** est optimisée simplement pour placer votre code dans une image et l’exécuter, cette image est optimisée pour que seules les dépendances de système d’exploitation nécessaires à l’exécution des applications .NET Core ayant le runtime .NET soient packagées avec l’application. Cette image n’est en général pas optimisée pour l’exécution de plusieurs conteneurs .NET Core sur le même hôte car chaque image inclut le runtime .NET Core dans l’application. Vous ne tirez donc pas parti de la disposition en couches de l’image.   

Versions les plus récentes de chaque variante :

- `microsoft/dotnet` ou `microsoft/dotnet:latest` (inclut le SDK)
- `microsoft/dotnet:onbuild`
- `microsoft/dotnet:core`
- `microsoft/dotnet:core-deps`

Voici une liste des images provenant d’une commande `docker pull <imagename>` sur une machine de développement pour montrer les différentes tailles. Notez que la variante de développement/génération, `microsoft/dotnet:1.0.0-preview2-sdk`, est d’une taille plus importante car elle contient le SDK pour développer et générer votre application. La variante de production, `microsoft/dotnet:core`, est plus petite car elle ne contient que le runtime .NET Core. L’image minimale qui peut être utilisée sur Linux, `core-deps`, est relativement plus petite, mais votre application doit copier avec elle une copie privée du runtime .NET. Comme les conteneurs sont déjà des barrières d’isolation privées, vous perdez cette optimisation lors de l’exécution de plusieurs conteneurs basés sur .NET. 

```
REPOSITORY          TAG                     IMAGE ID            SIZE
microsoft/dotnet    1.0.0-preview2-onbuild  19b6a6c4b1db        540.4 MB
microsoft/dotnet    onbuild                 19b6a6c4b1db        540.4 MB
microsoft/dotnet    1.0.0-preview2-sdk      a92c3d9ad0e7        540.4 MB
microsoft/dotnet    core                    5224a9f2a2aa        253.2 MB
microsoft/dotnet    1.0.0-core-deps         c981a2eebe0e        166.2 MB
microsoft/dotnet    core-deps               c981a2eebe0e        166.2 MB
microsoft/dotnet    latest                  03c10abbd08a        540.4 MB
microsoft/dotnet    1.0.0-core              b8da4a1fd280        253.2 MB
```

## <a name="prerequisites"></a>Prérequis

Pour générer et exécuter, plusieurs éléments doivent être installés :

- [.NET Core](http://dot.net)
- [Docker](https://www.docker.com/products/docker), pour exécuter vos conteneurs Docker localement
- [Node.js](https://nodejs.org/)
- [Générateur yeoman pour ASP.NET](https://github.com/omnisharp/generator-aspnet) pour la création de l’application API Web
- [Générateur yeoman pour Docker](http://aka.ms/yodocker) de Microsoft

Installer les générateurs Yeoman pour ASP.NET Core et Docker avec npm 

```
npm install -g yo generator-aspnet generator-docker
```

> [!NOTE]
> Cet exemple utilise [Visual Studio Code](http://code.visualstudio.com) pour l’éditeur.

## <a name="creating-the-web-api-application"></a>Création de l’application API Web

Pour établir un point de référence, avant de mettre l’application dans un conteneur, exécutez l’application localement. 

L’application terminée se trouve dans le [dépôt dotnet/docs sur GitHub](https://github.com/dotnet/docs/tree/master/samples/core/docker/building-net-docker-images). Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Créez un répertoire pour votre application.

Ouvrez une session de commande ou une session Terminal Server dans ce répertoire, et utilisez le générateur Yeoman ASP.NET en tapant ce qui suit :
```
yo aspnet
```

Sélectionnez **Application API Web** et tapez **api** pour le nom de l’application, puis appuyez sur Entrée.  Une fois l’application structurée, accédez au répertoire `/api` et restaurez les dépendances NuGet en utilisant `dotnet restore`.

```
cd api
dotnet restore
```

Tester l’application en utilisant `dotnet run` et en accédant à **http://localhost:5000/api/values.**

```javascript
[
    "value1",
    "value2"
]
```

Utilisez `Ctrl+C` pour arrêter l’application.

## <a name="adding-docker-support"></a>Ajout de la prise en charge de Docker

L’ajout de la prise en charge de Docker au projet s’effectue en utilisant le générateur Yeoman de Microsoft. Il prend actuellement en charge les projets .NET Core, Node.js et Go en créant un fichier Dockerfile et des scripts qui permettent la génération et l’exécution de projets dans des conteneurs. Des fichiers spécifiques à Visual Studio Code sont également ajoutés (launch.json, tasks.json) pour la prise en charge du débogage et de la palette de commandes de l’éditeur.

```console
$ yo docker

     _-----_     ╭──────────────────────────╮
    |       |    │   Welcome to the Docker  │
    |--(o)--|    │        generator!        │
   `---------´   │     Let's add Docker     │
    ( _´U`_ )    │  container magic to your │
    /___A___\   /│           app!           │
     |  ~  |     ╰──────────────────────────╯
   __'.___.'__
 ´   `  |° ´ Y `

? What language is your project using? (Use arrow keys)
❯ .NET Core
  Golang
  Node.js
```

- Sélectionnez `.NET Core` comme type de projet
- `rtm` pour la version de .NET Core
- `Y` le projet utilise un serveur web
- `5000` est le port sur lequel l’application API Web écoute (http://localhost:5000)
- `api` pour le nom de l’image
- `api` pour le nom du service
- `api` pour le projet de composition 
- `Y` pour remplacer le fichier Dockerfile actuel

Lorsque le générateur a terminé, les fichiers suivants sont ajoutés au projet

- .vscode/launch.json
- Dockerfile.debug
- Dockerfile
- docker-compose.debug.yml
- docker-compose.yml
- dockerTask.ps1
- dockerTask.sh
- .vscode/tasks.json

Le générateur crée deux fichiers Dockerfile.

**Dockerfile.Debug** : ce fichier est basé sur l’image **microsoft/dotnet:1.0.0-preview2-sdk** qui, comme vous pouvez le voir dans la liste des variantes d’images, inclut le SDK, CLI et .NET Core, et qui est l’image utilisée pour le développement et le débogage (F5). L’inclusion de tous ces composants produit une image plus grande, avec une taille d’environ 540 Mo.

**Dockerfile** : cette image est l’image publiée, basée sur **microsoft/dotnet:1.0.0-core** et qui doit être utilisé pour la production. Cette image une fois générée a une taille approximative de 253 Mo.

### <a name="creating-the-docker-images"></a>Création des images Docker
En utilisant le script `dockerTask.sh` ou `dockerTask.ps1`, nous pouvons générer ou composer l’image et le conteneur pour l’application **api** pour un environnement spécifique. Générez l’image **debug** en exécutant la commande suivante.

```bash
./dockerTask.sh build debug
```

L’image génère l’application ASP.NET, exécute `dotnet restore`, ajoute le débogueur à l’image, définit un `ENTRYPOINT` et enfin copie l’application dans l’image. Le résultat est une image Docker nommée *api* avec `TAG` ayant la valeur *debug*.  Affichez les images sur l’ordinateur en utilisant `docker images`.

```bash
docker images

REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        a few seconds ago   779.8 MB
```

Une autre façon de générer l’image et d’exécuter l’application au sein du conteneur Docker consiste à ouvrir l’application dans Visual Studio Code et à utiliser les outils de débogage. 

Sélectionnez l’icône de débogage dans la barre d’affichage sur le côté gauche de Visual Studio Code.

![icône de débogage de Visual Studio Code](./media/building-net-docker-images/debugging_debugicon.png)

Cliquez ensuite sur l’icône de lecture ou sur F5 pour générer l’image et démarrer l’application au sein du conteneur. L’API Web est lancée en utilisant votre navigateur par défaut à l’adresse http://localhost:5000.

![Outils de débogage Docker de Visual Studio Code](./media/building-net-docker-images/docker-tools-vscode-f5.png)

Vous pouvez définir des points d’arrêt dans votre application, exécuter pas à pas, etc., comme si l’application s’exécutait localement sur votre machine de développement et non pas à l’intérieur du conteneur. L’intérêt de déboguer dans le conteneur est qu’il s’agit de la même image que celle qui sera déployée dans un environnement de production.

La création de l’image de version ou de production nécessite simplement l’exécution de la commande à partir du terminal en passant le nom de l’environnement `release`.

```bash
./dockerTask build release
```

La commande crée l’image à partir de l’image de base **microsoft/dotnet:core** plus petite, [EXPOSE](https://docs.docker.com/engine/reference/builder/#/expose) le port 5000, définit le [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) pour `dotnet api.dll` et la copie dans le répertoire `/app`. Il n’existe pas de débogueur, SDK ou `dotnet restore` aboutissant à une image beaucoup plus petite. L’image est nommée **api** avec `TAG` ayant la valeur **latest**.

```
REPOSITORY          TAG                  IMAGE ID            CREATED             SIZE
api                 debug                70e89fbc5dbe        1 hour ago        779.8 MB
api                 latest               ef17184c8de6        1 hour ago        260.7 MB
```

## <a name="summary"></a>Résumé

L’utilisation du générateur Docker pour ajouter les fichiers nécessaires à l’application API Web a simplifié le processus de création des versions de développement et de production des images.  Les outils sont multiplateformes : ils fournissent également un script PowerShell pour obtenir les mêmes résultats sur Windows, et Visual Studio Code permet le débogage pas à pas de l’application au sein du conteneur. En comprenant les variantes des images et les scénarios cibles, vous pouvez optimiser votre processus de développement interne, tout en obtenant des images optimisées pour les déploiements de production.  



