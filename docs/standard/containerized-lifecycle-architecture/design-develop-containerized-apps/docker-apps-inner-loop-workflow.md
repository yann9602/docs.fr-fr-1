---
title: "Flux de travail de développement de la boucle interne pour les applications de Docker"
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3605a6cd53db695de3af015a777e3c1a0e92af58
ms.sourcegitcommit: 672c9cd122c13c9813f57f022c86ebdf6dd69b4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Flux de travail de développement de la boucle interne pour les applications de Docker

Avant de déclencher le flux de travail de boucle externe couvrant l’ensemble DevOps cycle, tout commence sur l’ordinateur de chaque développeur, le codage de l’application elle-même, à l’aide de leurs langues par défaut ou les plateformes et de le tester localement la (Figure 4-14). Mais dans tous les cas, vous aurez un point très important, en commun, quel que soit le langage, framework ou plateformes que vous choisissez. Dans ce flux de travail spécifique, vous toujours développez et testez les conteneurs Docker, mais localement.

![](./media/image18.png)

Contexte de développement de la boucle interne de la figure 4-14 :

Le conteneur ou l’instance d’une image Docker contiendra ces composants :

-   Une sélection de système d’exploitation (par exemple, une distribution Linux ou Windows)

-   Fichiers ajoutés par le développeur (par exemple, les binaires d’application)

-   Configuration (par exemple, les paramètres d’environnement et les dépendances)

-   Instructions pour les processus à exécuter par Docker

Vous pouvez configurer le flux de travail de développement de la boucle interne qui utilise des Docker en tant que le processus (décrit dans la section suivante). Prendre en compte que les premières étapes pour configurer l’environnement n’est pas inclus, car vous devez le faire une seule fois.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Création d’une application unique dans un conteneur Docker à l’aide de Code Visual Studio et l’interface CLI de Docker

Les applications sont constituées à partir de vos propres services ainsi que des bibliothèques supplémentaires (dépendances).

Figure 4-15 montre les étapes de base que vous devez généralement exécuter lors de la création d’une application de Docker, suivie d’une description détaillée de chaque étape.

![](./media/image19.png)

Figure 4-15 : les flux de haut niveau pour le cycle de vie des applications de Docker placées dans des conteneurs à l’aide de Docker CLI

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Étape 1 : Commencer à coder dans le Code de Visual Studio et créez votre ligne de base initiale du service d’applications /

La méthode de développement de votre application est très similaire à la façon dont vous le faire sans Docker. La différence est que lors du développement, vous déployez et testez votre application ou les services qui s’exécutent dans des conteneurs Docker placés dans votre environnement local (comme une Linux VM ou de Windows).

**Configuration de votre environnement local**

Avec les versions plus récentes de Docker pour Mac et Windows, il est plus facile que jamais à développer des applications de Docker, et le programme d’installation est simple.

**Plus d’informations** pour obtenir des instructions sur la configuration de Docker pour Windows, accédez à [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).

Pour obtenir des instructions sur la configuration de Docker pour Mac, accédez à <https://docs.docker.com/docker-for-mac/>.

Vous devez en outre, un éditeur de code afin que vous pouvez développer effectivement de votre application lors de l’utilisation de Docker CLI.

Microsoft fournit le Code de Visual Studio, qui est un éditeur de code léger qui est pris en charge sur Windows, Mac et Linux et fournit la fonctionnalité IntelliSense avec [prise en charge de nombreux langages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python et la plupart les langages modernes), [débogage](https://code.visualstudio.com/Docs/editor/debugging), [integration avec Git](https://code.visualstudio.com/Docs/editor/versioncontrol) et [prise en charge des extensions](https://code.visualstudio.com/docs/extensions/overview). Cet éditeur est parfait pour les développeurs Mac et Linux. Dans Windows, vous pouvez également utiliser l’application complète de Visual Studio.

**Plus d’informations** pour obtenir des instructions sur l’installation de Visual Studio pour Windows, Mac ou Linux, accédez à [http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).

Vous pouvez utiliser avec l’interface CLI de Docker et écrire votre code à l’aide de n’importe quel éditeur de code, mais si vous utilisez Visual Studio Code, il rend faciles à l’auteur du fichier Dockerfile et docker-compose.yml fichiers dans votre espace de travail. De plus, vous pouvez exécuter des tâches de Code Visual Studio à partir de l’IDE qui invite les scripts qui peuvent exécuter des opérations élaborées à l’aide de CLI Docker en dessous.

Code Visual Studio est fourni par une extension, vous devez installer. Pour ce faire, appuyez sur Ctrl + Maj + P, tapez **ext installer**, puis exécutez les Extensions : commande d’installer l’Extension pour afficher la liste des extensions Marketplace. Ensuite, tapez **docker** pour filtrer les résultats, puis sélectionnez le fichier Dockerfile et Docker composer des fichier (yml), extension de la prise en charge, comme illustré dans la Figure 4-16.

![](./media/image20.png)

Figure 4-16 : l’installation de l’Extension Docker dans Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Étape 2 : Créer un fichier DockerFile lié à une image existante (système d’exploitation standard ou les environnements de développement, Ruby, Node.js et .NET Core)

Vous aurez besoin d’un fichier DockerFile par une image personnalisée doit être créé et par le conteneur à déployer, par conséquent, si votre application est composée d’un simple service personnalisé, vous devez un fichier DockerFile unique. Toutefois, si votre application est composée de plusieurs services (comme dans une architecture microservices), vous aurez besoin d’un fichier Dockerfile par service.

Le fichier DockerFile est généralement placé dans le dossier racine de votre application ou le service et contient les commandes requises pour que cette Docker sache comment configurer et exécuter cette application ou un service. Vous pouvez créer votre fichier DockerFile et ajoutez-le à votre projet, ainsi que votre code (node.js, .NET Core, etc.), ou, si vous ne connaissez pas l’environnement, regardez l’info-bulle suivante.

> [!TIP]
> Vous pouvez utiliser un outil de ligne de commande appelé [v docker](https://github.com/Microsoft/generator-docker), lequel micro-capsules des fichiers à partir de votre projet dans la langue que vous choisissez et ajoute les fichiers de configuration de Docker requis. En fait, pour aider les développeurs de la mise en route, il crée le fichier DockerFile approprié, docker-compose.yml et autres scripts associés pour générer et exécuter vos conteneurs Docker. Ce générateur yeoman vous invitera à quelques questions, vous demandant de votre hôte de conteneur de langue et de destination sélectionné de développement.

![v docker](./media/image21.png)

Par exemple, la Figure 4-17 présente deux captures d’écran les terminaux de dans Windows et sur un Mac, dans les deux cas, en cours d’exécution v docker, ce qui génère les projets de code exemple (actuellement .NET Core, Golang et Node.js que les langues prises en charge) déjà configurés pour fonctionner sur haut de Docker.

![](./media/image22.PNG)  ![](./media/image23.png)

Figure 4-17 : v docker outil de commande dans Windows (à gauche) et sur un Mac

Figure 4-18 présente un exemple d’utilisation v docker une fois que vous avez un projet .NET Core existant en place pour être structuré.

![](./media/image24.PNG)

Figure 4-18 : v docker avec un .NET Core existants du projet en place

À partir du fichier DockerFile, vous spécifiez quelle image Docker base, vous allez utiliser (par exemple, à l’aide de « de microsoft/dotnet:1.0.0-core »). Vous allez généralement créer votre image personnalisée sur une image de base que vous pouvez obtenir à partir de n’importe quel référentiel officiel à partir de la [Registre du Hub Docker](https://hub.docker.com/) (comme un [image pour .NET Core](https://hub.docker.com/r/microsoft/dotnet/) ou un [pour Node.js](https://hub.docker.com/_/node/)).

***Option a : utiliser une image Docker officielle existante***

À l’aide d’un dépôt officiel d’une pile de langage avec un numéro de version garantit que les mêmes fonctionnalités de langage sont disponibles sur tous les ordinateurs (y compris le développement, test et production).

Voici un exemple de fichier DockerFile pour un conteneur de .NET Core :

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

Dans ce cas, il est à l’aide de la version 1.0.1 de l’image de ASP.NET Core Docker officiel pour Linux nommé microsoft/aspnetcore:1.0.1. Pour plus d’informations, consultez la [page ASP.NET Core Docker images](https://hub.docker.com/r/microsoft/aspnetcore/) et [page de l’Image de Docker .NET Core](https://hub.docker.com/r/microsoft/dotnet/). Vous également susceptibles d’utiliser une autre image comparable comme nœud : 4-onbuild pour Node.js ou de nombreux autres images préconfigurées pour les langages de développement, qui sont disponibles à [Hub Docker](https://hub.docker.com/explore/).

Dans le fichier DockerFile, vous devez également indiquent à Docker pour écouter le port TCP que vous utiliserez lors de l’exécution (par exemple le port 80).

Il existe des autres lignes de configuration que vous pouvez ajouter dans le fichier DockerFile en fonction de la langue/framework que vous utilisez, pour que Docker sache comment exécuter l’application. Par exemple, vous devez la ligne de point d’entrée \[« dotnet », « MyCustomMicroservice.dll »\] pour exécuter une application .NET Core, bien que vous pouvez avoir plusieurs variantes selon l’approche pour générer et exécuter votre service. Si vous utilisez le Kit de développement logiciel et dotnet CLI pour générer et exécuter l’application .NET, il est légèrement différent. L’essentiel est que la ligne de point d’entrée ainsi que des lignes supplémentaires sera différentes selon la langue/plateforme que vous choisissez pour votre application.

**Plus d’informations** pour plus d’informations sur la création d’images Docker pour les applications .NET Core, accédez à <https://docs.microsoft.com/dotnet/articles/core/docker/building-net-docker-images>.

Pour en savoir plus sur la création de vos propres images, accédez à [https://docs.docker.com/engine/ \didacticiels/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).

**Référentiels d’images multiplateforme**

Comme les conteneurs Windows répandu, un référentiel unique peut contenir des variantes de plateforme, par exemple une image Linux et Windows. Il s’agit d’une nouvelle fonctionnalité disponible dans Docker qui rend possible pour les fournisseurs d’utiliser un référentiel unique pour couvrir plusieurs plateformes, telles que [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) référentiel, qui est disponible sur le Registre de docker Hub. Lorsque la fonctionnalité revient active, extraction de cette image à partir d’un hôte Windows extraira la variante de Windows, alors que l’extraction du même nom de l’image à partir d’un hôte Linux extraira la variante de Linux.

***Option b : créer votre image de base à partir de zéro***

Vous pouvez créer votre propre image de base de Docker à partir de zéro, comme expliqué dans cet [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) à partir de Docker. Il s’agit d’un scénario qui n’est probablement pas adapté si vous débutez avec Docker, mais si vous souhaitez définir les bits spécifiques de votre propre image de base, vous pouvez le faire.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Étape 3 : Créer vos images Docker personnalisées, incorporation de votre service qu’il contient

Pour chaque service personnalisée qui compose votre application, vous devez créer une image associée. Si votre application est composée d’un seul service ou une application web, vous aurez besoin d’une seule image.

> [!NOTE]
> Lors de la prise en compte le « boucle externe DevOps flux de travail », les images sont créées par un processus de génération automatisé chaque fois que vous effectuez un push votre code source vers un référentiel Git (intégration continue) pour les images seront créés dans cet environnement global à partir de votre code source.

Toutefois, nous considérons atteindre cet itinéraire de la boucle externe, nous devons vérifier que l’application Docker réellement fonctionne correctement afin qu’ils ne poussent le code qui peut ne pas fonctionne correctement dans le système de contrôle de source (Git, etc.).

Par conséquent, chaque développeur doit tout d’abord effectuer tout le processus de la boucle interne pour tester localement et continuer à développer jusqu'à ce qu’ils souhaitent push d’une fonctionnalité complète ou de modifier le système de contrôle source.

Pour créer une image dans votre environnement local et à l’aide du fichier DockerFile, vous pouvez utiliser la commande de génération docker, comme illustré dans la Figure 4-19 (vous pouvez également exécuter docker-composer des--créer pour les applications composées par plusieurs conteneurs/services).

![](./media/image25.png)

Figure 4-19 : génération docker en cours d’exécution

Si vous le souhaitez, au lieu d’exécuter directement des docker build à partir du dossier du projet, vous pouvez tout d’abord générer un dossier peut être déployé avec les bibliothèques .NET nécessaires à l’aide de l’exécution dotnet publication de commande et exécutez génération docker.

Dans cet exemple, cela crée une image Docker avec le nom cesardl/netcore-webapi-microservice-docker : premier ( : tout d’abord est une balise, comme une version spécifique). Vous pouvez effectuer cette étape pour chaque image personnalisée, que vous devez créer pour votre application Docker composée avec plusieurs conteneurs.

Vous trouverez les images existantes dans votre référentiel local (votre ordinateur de développement) à l’aide de la docker commande d’images, comme illustré dans la Figure 4-20.

![](./media/image26.png)

Figure 4-20 : affichage des images existantes à l’aide d’images docker

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Étape 4 : (Facultatif) définir vos services dans docker-compose.yml lors de la création d’une application composée de Docker avec plusieurs services

Avec le fichier compose.yml de docker, vous pouvez définir un ensemble de services liés à être déployée comme une application composée avec les commandes de déploiement expliqués dans la section étape suivante.

Vous devez créer ce fichier dans votre main ou un dossier de solution racine ; Il doit avoir un contenu similaire dans le fichier docker-compose.yml suivant :

```yml
version: '2'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

Dans ce cas particulier, ce fichier définit deux services : le service web (votre service personnalisé) et le service de redis (un service de cache populaires). Chaque service sera déployé en tant que conteneur, afin que nous devons utiliser une image Docker concrète pour chacun. Pour ce service web spécifique, l’image devez effectuer les opérations suivantes :

-   Génération du fichier dockerfile dans le répertoire actif

-   Transférer l’exposé port 80 sur le conteneur sur le port 81 sur l’ordinateur hôte

-   Monter le répertoire du projet sur l’ordinateur hôte à /code au sein du conteneur, ce qui vous permet de modifier le code sans avoir à recréer l’image

-   Lier le service web pour le service de redis

Le service redis utilise le [dernière image redis public](https://hub.docker.com/_/redis/) extraite à partir du Registre du Hub d’ancrage. [redis](http://redis.io/) est un système de cache très populaire pour les applications côté serveur.

### <a name="step-5-build-and-run-your-docker-app"></a>Étape 5 : Générer et exécuter votre application de Docker

Si votre application a uniquement un seul conteneur, vous devez l’exécuter en la déployant sur l’hôte Docker (machine virtuelle ou serveur physique). Toutefois, si votre application est composée de plusieurs services, vous devez *composer*, trop. Nous allons voir les différentes options.

***Option a : exécuter un seul conteneur ou service***

Vous pouvez exécuter l’image Docker à l’aide de la commande docker run, comme illustré ici :

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

Notez que pour ce déploiement particulier, nous allons rediriger les demandes envoyées au port 80 pour le port interne 5000. À présent, l’application est à l’écoute sur le port externe 80 au niveau de l’hôte.

***Option b : composer et exécuter une application de plusieurs conteneurs***

Dans la plupart des scénarios d’entreprise, une application de Docker sera composée de plusieurs services. Dans ce cas, vous pouvez exécuter la commande docker-composer des (Figure 4-21), qui utilise le fichier docker-compose.yml que vous avez peut-être créé précédemment. Exécution de cette commande déploie une application composée avec tous ses conteneurs connexes.

![](./media/image27.png)

Figure 4-21 : les résultats de l’exécution de la commande « docker-composer des »

Après avoir exécuté docker-composer des, vous déployez votre application et ses conteneurs connexes dans l’hôte Docker, comme illustré dans la Figure 4-22, dans la représentation sous forme de la machine virtuelle.

![](./media/image28.png)

Machine virtuelle de la figure 4-22 : avec des conteneurs Docker déployé

Docker Remarque-composer des et docker exécuter peut être assez vos conteneurs de test dans votre environnement de développement, mais vous ne pouvez pas à les utiliser si vous prévoyez de travailler avec des clusters de Docker et orchestrators comme Docker Swarm, mésosphère contrôleur de domaine/système d’exploitation ou Kubernetes Pour pouvoir évoluer. Si vous utilisez un cluster comme [Docker Swarm le mode](https://docs.docker.com/engine/swarm/) (disponible dans Docker pour Windows et Mac depuis la version 1.12), vous devez déployer et tester avec des commandes supplémentaires, telles que la création du service de docker pour les services uniques, ou lorsque vous êtes déploiement d’une application composée de plusieurs conteneurs, à l’aide de docker Composer offre groupée et docker déployer myBundleFile, en déployant l’application composée comme une pile, comme expliqué dans l’article [groupes d’applications distribuées](https://blog.docker.com/2016/06/docker-app-bundle/) à partir de Docker.

Pour [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) et [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) vous utiliseriez les commandes de déploiement différentes et des scripts, ainsi.

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Étape 6 : Tester votre application Docker (localement, dans votre machine virtuelle d’un local CD)

Cette étape varie en fonction de ce que fait votre application.

Dans une très .NET Core API Web simple « Hello World » déployé comme un seul conteneur ou un service, vous devez simplement accéder au service en fournissant le port TCP spécifié dans le fichier DockerFile.

Si localhost n’est pas activé, pour accéder à votre service, vous pouvez rechercher l’adresse IP de l’ordinateur à l’aide de cette commande :

machine de docker ip *votre nom de conteneur*

Sur l’hôte Docker, ouvrez un navigateur et accédez à ce site. Vous devez voir votre service / d’application en cours d’exécution, comme illustré dans la Figure 4-23.

![](./media/image29.png)

Figure 4-23 : test de votre application de Docker localement en utilisant localhost

Notez qu’il utilise le port 80, mais en interne qu’il a été redirigé vers le port 5000, car c’est la façon dont elle a été déployée avec docker, exécuter, comme expliqué plus haut.

Vous pouvez le tester à l’aide de CURL à partir du terminal. Dans une installation Docker sur Windows, l’adresse IP par défaut est 10.0.75.1, comme illustré dans la Figure 4-24.

![](./media/image30.png)

Figure 4-24 : test d’une application de Docker localement à l’aide de CURL

**Débogage d’un conteneur en cours d’exécution sur Docker**

Code Visual Studio prend en charge le débogage Docker si vous utilisez Node.js et autres plateformes comme des conteneurs de .NET Core.

Vous également pourrez déboguer les conteneurs .NET Core dans Docker lors de l’utilisation de Visual Studio, comme décrit dans la section suivante.

**Plus d’informations :** pour en savoir plus sur le débogage des conteneurs Docker de Node.js, accédez à <https://blog.docker.com/2016/07/live-debugging-docker/> et [https://blogs.msdn.microsoft.com/ \ utilisateur\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).


>[!div class="step-by-step"]
[Précédente] (docker-applications-développement-environment.md) [suivant] (visual-studio-outils-de-docker.md)
