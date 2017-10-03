---
title: "Déploiement d’applications web .NET Core basées sur un seul conteneur sur des hôtes Linux ou Windows Nano Server"
description: "Architecture des microservices .NET pour les applications .NET en conteneur | Déploiement d’applications web .NET Core basées sur un seul conteneur sur des hôtes Linux ou Windows Nano Server"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: a50c2ad3183c80fd76e6db042674e49367d7ffc9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/05/2017

---
# <a name="deploying-single-container-based-net-core-web-applications-on-linux-or-windows-nano-server-hosts"></a>Déploiement d’applications web .NET Core basées sur un seul conteneur sur des hôtes Linux ou Windows Nano Server

*Vous pouvez utiliser des conteneurs Docker pour effectuer un déploiement monolithique d’applications web simples. Cela a pour effet d’améliorer les pipelines d’intégration continue et de déploiement continu et cela contribuer à la réussite du déploiement en production. Fini les « Comment cela se fait-il que cela fonctionne sur ma machine, mais pas en production ? »*

Une architecture basée sur des microservices présente de nombreux avantages, mais ces avantages se payent par une complexité accrue. Dans certains cas, les inconvénients prennent le pas sur les avantages et vous avez plus à gagner à utiliser une application à déploiement monolithique s’exécutant dans un petit nombre de conteneurs, voire dans un seul conteneur. 

Il n’est pas toujours évident de décomposer une application monolithique en plusieurs microservices bien distincts. Vous avez appris que ce partitionnement devait se faire par fonction : les microservices doivent fonctionner indépendamment les uns des autres pour optimiser la résilience de l’application. Si vous ne pouvez pas proposer l’application par tranches de fonctionnalités, sa séparation ne fait qu’ajouter de la complexité.

Une application n’est pas pour autant nécessairement amenée à mettre à l’échelle les fonctionnalités de façon indépendante. Supposons qu’au début de l’existence de notre application de référence eShopOnContainers, le trafic ne justifiait pas de séparer les fonctionnalités en différents microservices. Le trafic était si faible que le fait d’ajouter des ressources à un service revenait en fait à les ajouter à tous les services. Séparer l’application en services distincts aurait apporté des avantages minimes au regard du travail supplémentaire que cela demandait.

De même, lors de la phase initiale du développement d’une application, vous n’avez peut-être pas une idée précise de là où se trouvent les limites fonctionnelles naturelles. Même à un stade de développement où le produit est viable, il est possible que cette séparation naturelle ne se dégage toujours pas.

Certaines de ces conditions peuvent être passagères. Vous pouvez commencer par créer une application monolithique et séparer par la suite certaines fonctionnalités en les développant et les déployant sous forme de microservices. D’autres conditions peuvent être essentielles à l’espace de problème de l’application, ce qui signifie que l’application risque de ne jamais être divisée en plusieurs microservices.

Séparer une application en divers processus distincts induit aussi des coûts. Il est plus complexe de séparer des fonctionnalités en différents processus. Les protocoles de communication deviennent plus complexes. Au lieu d’appeler des méthodes, vous devez utiliser des communications asynchrones entre les services. Quand il s’agit de déplacer une architecture de microservices, vous devez ajouter la plupart des blocs de construction implémentés dans la version de microservices de l’application eShopOnContainers : gestion du bus d’événements, résilience des messages et nouvelles tentatives, cohérence éventuelle, etc.

Une version très simplifiée d’eShopOnContainers (nommée [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) et figurant dans le même dépôt GitHub) s’exécute en tant qu’application MVC monolithique et, comme nous l’avons vu, ce choix de conception offre des avantages. Vous pouvez télécharger la source de cette application sur GitHub et l’exécuter localement. Même cette application monolithique gagne à être déployée dans un environnement de conteneurs.

Tout d’abord, un déploiement en conteneur signifie que chaque instance de l’application s’exécute dans le même environnement. Cela inclut l’environnement de développement dans lequel les tests de la première heure et le développement ont été réalisés. L’équipe de développement peut exécuter l’application dans un environnement à conteneurs qui correspond à l’environnement de production.

De plus, la montée en charge des applications en conteneur est moins coûteuse. Comme nous l’avons vu précédemment, l’environnement à conteneurs permet un meilleur partage des ressources que les environnements à machines virtuelles classiques.

Enfin, la mise en conteneur de l’application contraint à établir une séparation entre la logique métier et le serveur de stockage. À mesure que l’application monte en charge, les différents conteneurs dépendent tous d’un même support de stockage physique. Il s’agit généralement d’un serveur à haute disponibilité exécutant une base de données SQL Server.

## <a name="application-tour"></a>Exploration de l’application

L’application [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) est une partie de l’application eShopOnContainers s’exécutant en tant qu’application monolithique, c’est-à-dire une application basée sur ASP.NET Core MVC s’exécutant sur .NET Core. Elle propose pour l’essentiel les fonctionnalités de consultation de catalogue que nous avons décrites dans les sections précédentes.

L’application utilise une base de données SQL Server pour le stockage de catalogue. Dans les déploiements basés sur des conteneurs, cette application monolithique peut accéder au même magasin de données que l’application basée sur des microservices. L’application est configurée pour exécuter SQL Server dans un conteneur à côté de l’application monolithique. Dans un environnement de production, SQL Server s’exécuterait sur une machine à haute disponibilité, en dehors de l’hôte Docker. Pour des raisons pratiques, dans un environnement de développement ou de test, nous vous recommandons d’exécuter SQL Server dans son propre conteneur.

L’ensemble initial de fonctionnalités permet uniquement la consultation du catalogue. Par des mises à jour, il serait possible d’activer l’ensemble complet de fonctionnalités de l’application en conteneur. Une architecture d’application web monolithique plus avancée est décrite dans le livre électronique intitulé [ASP.NET Web Application architecture practices](https://aka.ms/webappebook) et l’[exemple d’application eShopOnWeb](http://aka.ms/WebAppArchitecture) y afférent, même si dans ce cas, elle n’exécute pas de conteneurs Docker, car ce scénario s’intéresse tout particulièrement au développement web strict à l’aide d’ASP.NET Core.

Cependant, la version simplifiée disponible dans eShopOnContainers (eShopWeb) s’exécute dans un conteneur Docker.

## <a name="docker-support"></a>Prise en charge de Docker

Le projet eShopOnWeb s’exécute sur .NET Core. Par conséquent, il peut s’exécuter dans des conteneurs Linux ou Windows. Notez que pour le déploiement de Docker, vous devez utiliser le même type d’hôte pour SQL Server. Les conteneurs Linux offrent un plus faible encombrement et sont à privilégier.

Visual Studio propose un modèle de projet qui ajoute la prise en charge de Docker à une solution. Cliquez avec le bouton droit sur le projet, cliquez sur **Ajouter**, puis sur **Prise en charge de Docker**. Le modèle ajoute un fichier Dockerfile à votre projet, ainsi qu’un nouveau projet **docker-composer** qui fournit un fichier docker-compose.yml de démarrage. Cette étape a déjà été effectuée dans le projet eShopOnWeb téléchargé sur GitHub. Vous pourrez constater que la solution contient le projet **eShopOnWeb** et le projet **docker-composer**, comme illustré dans la figure 6-1.

![](./media/image1.png)

**Figure 6-1** : le projet **docker-composer** dans une application web à conteneur unique

Ces fichiers sont des fichiers docker-composer standard, conformément à n’importe quel projet Docker. Vous pouvez les utiliser avec Visual Studio ou à partir de la ligne de commande. Comme cette application s’exécute sur .NET Core et utilise des conteneurs Linux, vous pouvez aussi la coder, la générer et l’exécuter sur une machine Mac ou Linux.

Le fichier docker-compose.yml contient des informations sur les images à générer et les conteneurs à lancer. Les modèles indiquent comment générer l’image eshopweb et lancer les conteneurs de l’application. Vous devez ajouter la dépendance vis-à-vis de SQL Server en incluant une image (par exemple, mssql-server-linux), ainsi qu’un service pour l’image sql.data permettant à Docker de générer et lancer ce conteneur. Ces paramètres sont illustrés dans l’exemple suivant :

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web
    build:
    context: ./eShopWeb
    dockerfile: Dockerfile
    depends_on:
      - sql.data

  sql.data:
    image: microsoft/mssql-server-linux
```

La directive depends\_on indique à Docker que l’image eShopWeb dépend de l’image sql.data. Les lignes situées en dessous sont les instructions visant à générer une image balisée sql.data à partir de l’image microsoft/mssql-server-linux.

Le projet **docker-composer** affiche les autres fichiers docker-compose sous le nœud principal docker-compose.yml pour fournir une indication visuelle que ces fichiers sont apparentés. Le fichier docker-compose-override.yml contient les paramètres des deux services, notamment les chaînes de connexion et d’autres paramètres d’application.

L’exemple suivant présente le fichier docker-compose.vs.debug.yml, qui contient les paramètres utilisés pour le débogage dans Visual Studio. Dans ce fichier, la balise dev est ajoutée à l’image eshopweb. Cela permet de séparer le débogage des images de version et ainsi de vous éviter de déployer accidentellement les informations de débogage dans un environnement de production :

```yml
version: '2'
  
services:
  eshopweb:
    image: eshop/web:dev
    build:
    args:
    source: ${DOCKER_BUILD_SOURCE}
    environment:
      - DOTNET_USE_POLLING_FILE_WATCHER=1
    volumes:
      - ./eShopWeb:/app
      - ~/.nuget/packages:/root/.nuget/packages:ro
      - ~/clrdbg:/clrdbg:ro
    entrypoint: tail -f /dev/null
    labels:
      - "com.microsoft.visualstudio.targetoperatingsystem=linux"
```

Le dernier fichier ajouté est docker-compose.ci.build.yml. Il permet de générer le projet à partir d’un serveur CI depuis la ligne de commande. Ce fichier compose démarre un conteneur Docker qui génère les images nécessaires à votre application. L’exemple suivant présente le contenu du fichier docker-compose.ci.build.yml.

```yml
version: '2'
  
services:
  ci-build:
    image: microsoft/aspnetcore-build:1.0-1.1
    volumes:
      - .:/src
    working_dir: /src
  command: /bin/bash -c "dotnet restore ./eShopWeb.sln && dotnet publish  ./eShopWeb.sln -c Release -o ./obj/Docker/publish"
```

Notez que l’image est une image de build ASP.NET Core. Cette image comprend le kit SDK et les outils de génération permettant de générer votre application et de créer les images nécessaires. Le fait d’exécuter le projet **docker-composer** avec ce fichier a pour effet de démarrer le conteneur de build à partir de l’image, puis de générer l’image de votre application dans ce conteneur. Vous devez spécifier ce fichier docker-compose en ligne de commande pour générer votre application dans un conteneur Docker avant de la lancer.

Dans Visual Studio, vous pouvez exécuter votre application dans des conteneurs Docker en sélectionnant le projet **docker-composer** comme projet de démarrage, puis en appuyant sur Ctrl+F5 (F5 pour déboguer), comme vous le feriez avec n’importe quelle autre application. Quand vous démarrez le projet **docker-compose**, Visual Studio exécute **docker-compose** en utilisant le fichier docker-compose.yml, le fichier docker-compose.override.yml, puis l’un des fichiers docker-compose.vs.\*. Une fois que l’application a démarré, Visual Studio lance automatiquement le navigateur.

Si vous lancez l’application dans le débogueur, Visual Studio s’attache à l’application en cours d’exécution dans Docker.

## <a name="troubleshooting"></a>Résolution des problèmes

Cette section décrit certains problèmes que vous êtes susceptible de rencontrer pendant l’exécution locale de conteneurs et propose des correctifs.

### <a name="stopping-docker-containers"></a>Arrêt des conteneurs Docker 

Après avoir lancé l’application en conteneur, les conteneurs continuent de s’exécuter, même après avoir arrêté le débogage. Vous pouvez exécuter la commande docker ps depuis la ligne de commande pour identifier les conteneurs qui s’exécutent. La commande docker stop permet d’arrêter un conteneur en cours d’exécution, comme le montre la figure 6-2.

![](./media/image2.png)

**Figure 6-2** : affichage et arrêt de conteneurs à l’aide des commandes CLI docker ps et docker stop

Vous pouvez être amené à arrêter les processus en cours d’exécution quand vous basculez d’une configuration à une autre. Sinon, le conteneur qui exécute l’application web utilise le port de votre application (en l’occurrence, le port 5106).

### <a name="adding-docker-to-your-projects"></a>Ajout de Docker à vos projets

L’Assistant qui ajoute la prise en charge de Docker communique avec le processus Docker en cours d’exécution. L’Assistant ne fonctionne pas correctement si Docker n’est pas en cours d’exécution au moment où vous démarrez l’Assistant. Par ailleurs, l’Assistant examine votre choix de conteneur actuel pour ajouter la prise en charge appropriée de Docker. Si vous voulez ajouter la prise en charge des conteneurs Windows, vous devez exécuter l’Assistant pendant que Docker s’exécute avec les conteneurs Windows configurés. Si vous voulez ajouter la prise en charge des conteneurs Linux, exécutez l’Assistant pendant que Docker s’exécute avec les conteneurs Linux configurés.

>[!div class="step-by-step"]
[Précédent] (../docker-application-development-process/docker-app-development-workflow.md) [Suivant] (../containerize-net-framework-applications/index.md)

