---
title: "Définition de votre application conteneur multiples avec docker-compose.yml"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Définition de votre application conteneur multiples avec docker-compose.yml"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c5d4d2c9fb9fbb595f6f6ea195247474f353a32f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>Définition de votre application conteneur multiples avec docker-compose.yml 

Dans ce guide, les [docker-compose.yml](https://docs.docker.com/compose/compose-file/) fichier a été introduit dans la section [étape 4. Définir vos services dans docker-compose.yml lors de la création d’une application de Docker conteneur multi](#step4_define_svcs_in_docker_compose_yml). Toutefois, il existe d’autres façons d’utiliser les fichiers docker-compose peine d’Explorer plus en détail.

Par exemple, vous pouvez décrire de façon explicite comment vous souhaitez déployer votre application conteneur multiples dans le fichier compose.yml de docker. Si vous le souhaitez, vous pouvez également décrire la manière dont vous vous apprêtez à créer vos images Docker personnalisés. (Les images Docker personnalisé peuvent également être générées avec l’interface CLI de Docker.)

En fait, vous définissez chacune des conteneurs que vous souhaitez déployer plus certaines caractéristiques pour chaque déploiement de conteneur. Une fois que vous avez un fichier de description du déploiement de plusieurs conteneurs, vous pouvez déployer la solution dans son intégralité en une seule action orchestrée par le [docker-composer des](https://docs.docker.com/compose/overview/) commande CLI, ou vous pouvez déployer en toute transparence à partir de Visual Studio. Dans le cas contraire, vous devez utiliser l’interface CLI de Docker pour déployer un conteneur en conteneur en plusieurs étapes à l’aide de la commande docker run à partir de la ligne de commande. Par conséquent, chaque service défini dans docker-compose.yml doit spécifier exactement une image ou générer. Autres clés sont facultatifs et sont analogues à leur docker exécuter équivalents de ligne de commande.

Le code YAML suivant est la définition d’un fichier possible globale mais unique docker-compose.yml pour l’exemple eShopOnContainers. Cela n’est pas le fichier réel docker-compose eShopOnContainers. Au lieu de cela, elle est une version simplifiée et consolidée dans un seul fichier, qui n’est pas le meilleur moyen de travailler avec docker-composer des fichiers, comme vous le verrez plus tard.

```yml
version: '2'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
    ports:
      - "5100:80"
    depends_on:
      - catalog.api
      - ordering.api
      - basket.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  basket.api:
    image: eshop/basket.api
    environment:
      - ConnectionString=sql.data
    ports:
      - "5103:80"
    depends_on:
      - sql.data

  sql.data:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basket.data:
    image: redis
```

La clé racine de ce fichier est services. Sous cette clé, vous définissez les services que vous souhaitez déployer et exécuter lorsque vous exécutez le composer docker commande ou lorsque vous déployez à partir de Visual Studio à l’aide de ce fichier compose.yml de docker. Dans ce cas, le fichier compose.yml de docker a plusieurs services définis, comme décrit dans la liste suivante.

-   webmvc conteneur, y compris l’application ASP.NET MVC de base consomme la microservices du côté serveur C\#

-   Catalog.API conteneur, y compris l’API Web de catalogue ASP.NET Core microservice

-   Ordering.API conteneur, y compris le classement l’API Web ASP.NET principale microservice

-   SQL.Data conteneur en cours d’exécution SQL Server pour Linux, contenant les bases de données microservices

-   basket.API conteneur avec l’API Web de panier d’achat ASP.NET Core microservice

-   basket.Data conteneur en cours d’exécution du service de cache REDIS, avec la base de données du panier d’achat comme un cache REDIS

### <a name="a-simple-web-service-api-container"></a>Un conteneur d’API du Service Web simple

En mettant l’accent sur un seul conteneur, le conteneur-microservice catalog.api a une définition simple :

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=catalog.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data
```

Ce service en conteneur dispose de la configuration de base suivante :

-   Il est basé sur l’image eshop/catalog.api personnalisé. Par souci de simplicité, il n’existe aucune build : paramètre dans le fichier de clé. Cela signifie que l’image doit avoir été créé précédemment (avec la génération docker) ou ont été téléchargés (avec la commande d’extraction docker) à partir d’un Registre Docker.

-   Il définit une variable d’environnement nommée ConnectionString avec la chaîne de connexion à utiliser par Entity Framework pour accéder à l’instance de SQL Server qui contient le modèle de données de catalogue. Dans ce cas, le même conteneur de SQL Server contient plusieurs bases de données. Vous devez donc moins de mémoire dans votre ordinateur de développement pour Docker. Toutefois, vous pouvez également déployer un conteneur de SQL Server pour chaque base de données de microservice.

-   Le nom SQL Server est sql.data, qui est le même nom que celui utilisé pour le conteneur qui exécute l’instance de SQL Server pour Linux. Ceci est pratique ; Pour pouvoir utiliser cette résolution de noms (interne à l’hôte Docker) résout l’adresse réseau vous n’avez pas besoin de connaître l’adresse IP interne pour les conteneurs que vous accédez à partir d’autres conteneurs.

Étant donné que la chaîne de connexion est définie par une variable d’environnement, vous pouvez définir cette variable via un mécanisme différent et à un autre moment. Par exemple, vous pouvez définir une chaîne de connexion différentes lors du déploiement en production finales hôtes d’ou en procédant à partir de vos pipelines de l’élément de configuration/CD dans VSTS ou votre système DevOps préféré.

-   Il expose le port 80 pour l’accès interne au service catalog.api au sein de l’hôte Docker. L’hôte est actuellement un VM Linux, car il est basé sur une image Docker pour Linux, mais vous pouvez configurer le conteneur à exécuter sur une image Windows à la place.

-   Il transfère l’exposé le port 80 sur le conteneur au port 5101 sur l’ordinateur hôte de Docker (la VM Linux).

-   Il lie le service web pour le service sql.data (l’instance de SQL Server pour Linux de base de données en cours d’exécution dans un conteneur). Lorsque vous spécifiez cette dépendance, le conteneur catalog.api ne démarrera pas tant que le conteneur sql.data a déjà été démarré ; C’est tout d’abord important car catalog.api doit avoir au plus la base de données SQL Server et en cours d’exécution. Toutefois, ce type de dépendance de conteneur n’est pas suffisant dans de nombreux cas, étant donné que Docker vérifie uniquement au niveau du conteneur. Parfois le service (dans ce cas de SQL Server) peut toujours pas être prêt, il est recommandé d’implémenter la logique de nouvelle tentative avec interruption exponentielle dans votre microservices client. De cette façon, si un conteneur de dépendance n’est pas prêt pour une courte période, l’application sera toujours être résiliente.

-   Il est configuré pour autoriser l’accès aux serveurs externes : extra\_hôtes définition permet d’accéder aux serveurs externes ou des ordinateurs en dehors de l’hôte Docker (autrement dit, en dehors de la valeur par défaut VM Linux qui est un développement Docker en hôte), par exemple un serveur SQL local Instance de serveur sur votre ordinateur de développement.

Il existe également des autres, docker-compose.yml des paramètres plus avancés que nous aborderons dans les sections suivantes.

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>À l’aide de docker-composer des fichiers pour cibler plusieurs environnements

Les fichiers de docker-compose.yml sont des fichiers de définition et peuvent être utilisées par plusieurs infrastructures qui comprennent ce format. L’outil plus simple est le docker-composition de commande, mais les autres outils, tels qu’orchestrators (par exemple, Docker Swarm) également comprennent ce fichier.

Par conséquent, à l’aide de la commande, vous pouvez cibler les principaux scénarios suivants docker-composer.

#### <a name="development-environments"></a>Environnements de développement

Lorsque vous développez des applications, il est important d’être en mesure d’exécuter une application dans un environnement de développement isolé. Vous pouvez utiliser la commande CLI pour créer cet environnement ou utiliser Visual Studio qui docker utilise-composer en coulisse docker-composer.

Le fichier docker-compose.yml vous permet de configurer et de documenter les dépendances du service de tous les votre application (autres services, du cache, bases de données, les files d’attente, etc.). À l’aide de la docker-composer des commandes CLI, vous pouvez créer et démarrer un ou plusieurs conteneurs pour chaque dépendance avec une seule commande (docker-composer des).

Les fichiers de compose.yml de docker sont interprétés par le moteur Docker les fichiers de configuration, mais servent également à des fichiers de documentation pratique sur la composition de votre application conteneur multiples.

#### <a name="testing-environments"></a>Environnements de test

Une partie importante de tout déploiement continu (CD) ou le processus d’intégration continue (CI) sont les tests unitaires et les tests d’intégration. Ces tests automatisés nécessitent un environnement isolé afin qu’ils ne soient pas affectés par les utilisateurs ou toute autre modification apportée dans les données d’application.

Avec Docker Compose, vous pouvez créer et détruire cet environnement isolé très facilement en quelques commandes à partir de votre invite de commandes ou les scripts, tels que les commandes suivantes :

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a>Déploiements de production

Vous pouvez également utiliser le nouveau message à déployer sur un moteur Docker à distance. Un cas classique consiste à déployer sur une instance unique de l’hôte Docker (comme une machine virtuelle de production ou d’un serveur configuré avec [Machine Docker](https://docs.docker.com/machine/overview/)). Mais cela peut également être un entier [Docker Swarm](https://docs.docker.com/swarm/overview/) de cluster, car les clusters sont également compatibles avec les fichiers compose.yml de docker.

Si vous utilisez n’importe quel autre orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), vous devrez peut-être ajouter le programme d’installation et les métadonnées des paramètres de configuration telles que celles dans docker-compose.yml, mais dans le format requis par l’autres orchestrator.

Dans tous les cas, de composer docker est un outil et les métadonnées un format pratique pour le flux de travail de développement, de test et de production, bien que le flux de travail de production peut-être varier l’orchestrateur que vous utilisez.

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>L’utilisation de plusieurs docker-composer des fichiers pour gérer plusieurs environnements

Lorsque vous ciblez différents environnements, vous devez utiliser plusieurs composer des fichiers. Cela vous permet de créer plusieurs variantes de configuration en fonction de l’environnement.

#### <a name="overriding-the-base-docker-compose-file"></a>Remplacement du fichier de base docker-compose

Vous pouvez utiliser un fichier unique docker-compose.yml comme dans les exemples simplifiées indiqué dans les sections précédentes. Toutefois, qui n’est pas recommandé pour la plupart des applications.

Par défaut, le nouveau message lit deux fichiers, un compose.yml de docker et un fichier docker-compose.override.yml facultatif. Comme indiqué dans la Figure 8 à 11, lorsque vous utilisez Visual Studio et l’activation de la prise en charge de Docker, Visual Studio crée également les fichiers ainsi que des fichiers supplémentaires utilisées pour le débogage.

![](./media/image12.png)

**Figure 8-11**. docker-composer des fichiers dans Visual Studio 2017

Vous pouvez modifier les fichiers docker-compose avec n’importe quel éditeur, telles que Visual Studio Code ou Sublime et exécuter l’application avec la composition de docker jusqu'à la commande.

Par convention, le fichier docker-compose.yml contient la configuration de base et d’autres paramètres statiques. Cela signifie que la configuration du service ne doit pas changer en fonction de l’environnement de déploiement que vous ciblez.

Le fichier compose.override.yml de docker, comme son nom l’indique, contient les paramètres de configuration qui remplacent la configuration de base, telles que configuration dépend de l’environnement de déploiement. Vous pouvez avoir plusieurs fichiers de substitution avec des noms différents également. Les fichiers de remplacement contiennent généralement des informations supplémentaires requises par l’application, mais il est spécifique à un environnement ou à un déploiement.

#### <a name="targeting-multiple-environments"></a>Ciblage de plusieurs environnements

Un cas d’utilisation classique est lorsque vous définissez plusieurs composer des fichiers afin de vous pouvez cibler plusieurs environnements, comme la production, de mise en lots, l’élément de configuration ou de développement. Pour prendre en charge de ces différences, vous pouvez fractionner la configuration de votre nouveau message dans plusieurs fichiers, comme indiqué dans la Figure 8-12.

![](./media/image13.png)

**Figure 8-12**. Plusieurs composer docker les fichiers de substitution de valeurs dans le fichier de base de compose.yml de docker

Vous démarrez avec le fichier de base de compose.yml de docker. Ce fichier de base doit contenir les paramètres de configuration de base ou statique qui ne changent pas selon l’environnement. Par exemple, l’eShopOnContainers a le fichier docker-compose.yml suivant en tant que le fichier de base.

```yml
#docker-compose.yml (Base)
version: '2'

services:
  basket.api:
    image: eshop/basket.api
    build:
    context: ./src/Services/Basket/Basket.API
    dockerfile: Dockerfile
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api
    build:
    context: ./src/Services/Catalog/Catalog.API
    dockerfile: Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  identity.api:
    image: eshop/identity.api
    build:
    context: ./src/Services/Identity/Identity.API
    dockerfile: Dockerfile
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    build:
    context: ./src/Services/Ordering/Ordering.API
    dockerfile: Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  webspa:
    image: eshop/webspa
    build:
    context: ./src/Web/WebSPA
    dockerfile: Dockerfile
    depends_on:
      - identity.api
      - basket.api

  webmvc:
    image: eshop/webmvc
    build:
    context: ./src/Web/WebMVC
    dockerfile: Dockerfile
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api

  sql.data:
    image: microsoft/mssql-server-linux
    basket.data:
    image: redis
    expose:
      - "6379"
    rabbitmq:
    image: rabbitmq
    ports:
      - "5672:5672"

  webstatus:
    image: eshop/webstatus
    build:
    context: ./src/Web/WebStatus
    dockerfile: Dockerfile
```

Les valeurs dans le fichier de base de docker-compose.yml ne doivent pas modifier en raison d’environnements de déploiement cible différent.

Par exemple, si vous vous concentrer sur la définition de service webmvc, vous pouvez voir comment ces informations sont quasiment identique, quel que soit l’environnement vous pouvez cibler. Vous avez les informations suivantes :

-   Le nom du service : webmvc.

-   Image personnalisée du conteneur : Shopping/webmvc.

-   La commande pour générer l’image personnalisée de Docker, indiquant les informations à utiliser.

-   Dépendances sur d’autres services, afin de ce conteneur ne démarre pas tant que les autres conteneurs de dépendance ont démarré.

Vous pouvez avoir une configuration supplémentaire, mais le point important est que dans le fichier de base de compose.yml de docker, vous souhaitez simplement définir les informations qui sont communes à plusieurs environnements. Puis dans le docker-compose.override.yml ou des fichiers similaires pour la production ou intermédiaire, vous devez placer la configuration spécifique pour chaque environnement.

En règle générale, les compose.override.yml de docker est utilisé pour votre environnement de développement, comme dans l’exemple suivant d’eShopOnContainers :

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '2'

services:
# Simplified number of services here:
  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:5101
      - ConnectionString=Server=sql.data; Database=Microsoft.eShopOnContainers.Services.CatalogDb; User Id=sa;Password=Pass@word
      - ExternalCatalogBaseUrl=http://localhost:5101
    ports:
      - "5101:5101"

  identity.api:
    environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:5105
    - SpaClient=http://localhost:5104
    - ConnectionStrings__DefaultConnection = Server=sql.data;Database=Microsoft.eShopOnContainers.Service.IdentityDb;User Id=sa;Password=Pass@word
    - MvcClient=http://localhost:5100
    ports:
      - "5105:5105"

  webspa:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:5104
      - CatalogUrl=http://localhost:5101
      - OrderingUrl=http://localhost:5102
      - IdentityUrl=http://localhost:5105
      - BasketUrl=http:// localhost:5103
    ports:
      - "5104:5104"

  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

Dans cet exemple, la configuration de remplacement de développement expose certains ports à l’hôte, qui définit les variables d’environnement avec URL de redirection et spécifie les chaînes de connexion pour l’environnement de développement. Ces paramètres sont tout simplement pour l’environnement de développement.

Lorsque vous exécutez composer docker des (ou lancer à partir de Visual Studio), la commande lit les remplacements automatiquement comme s’il a été fusionner les deux fichiers.

Supposons que vous souhaitez un autre fichier de composition pour l’environnement de production, avec des valeurs de configuration différente. Vous pouvez créer un autre fichier de remplacement, comme suit. (Ce fichier peut être stocké dans un référentiel Git différents ou géré et sécurisé par une autre équipe.)

```yml
#docker-compose.prod.yml (Extended config for PRODUCTION env.)
version: '2'

services:
  # Simplified number of services here:
  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - ASPNETCORE_URLS=http://0.0.0.0:5101
      - ConnectionString=Server=sql.data; Database = Microsoft.eShopOnContainers.Services.CatalogDb; User Id=sa;Password=Prod@Pass
      - ExternalCatalogBaseUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5101
    ports:
      - "5101:5101"

  identity.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - ASPNETCORE_URLS=http://0.0.0.0:5105
      - SpaClient=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5104
      - ConnectionStrings__DefaultConnection = Server=sql.data;Database=Microsoft.eShopOnContainers.Service.IdentityDb;User Id=sa;Password=Pass@word
      - MvcClient=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5100
    ports:
      - "5105:5105"

  webspa:
    environment:
      - ASPNETCORE_ENVIRONMENT= Production
      - ASPNETCORE_URLS=http://0.0.0.0:5104
      - CatalogUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5101
      - OrderingUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5102
      - IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
      - BasketUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5103
    ports:
      - "5104:5104"

  sql.data:
    environment:
      - SA_PASSWORD=Prod@Pass
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

#### <a name="how-to-deploy-with-a-specific-override-file"></a>Comment déployer avec un fichier de remplacement spécifique

Pour utiliser plusieurs fichiers de substitution, ou un fichier de remplacement avec un nom différent, vous pouvez utiliser l’option-f avec la commande docker-composer et spécifiez les fichiers. Composer fusionne les fichiers dans l’ordre qu’ils sont spécifiés sur la ligne de commande. L’exemple suivant montre comment déployer des fichiers de substitution.

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>À l’aide de variables d’environnement dans docker-composer des fichiers

Il est pratique, en particulier dans les environnements de production, pour être en mesure d’obtenir des informations de configuration à partir de variables d’environnement, comme nous l’avons montré dans les exemples précédents. Vous référencez une variable d’environnement dans vos fichiers docker-compose à l’aide de la syntaxe \${MY\_VAR}. La ligne suivante à partir d’un fichier docker-compose.prod.yml montre comment référencer la valeur d’une variable d’environnement.

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

Variables d’environnement sont créés et initialisés de différentes façons, selon votre environnement d’hôte (Linux, Windows, le cluster du Cloud, etc..). Toutefois, une approche pratique consiste à utiliser un fichier .env. Les fichiers docker-compose prend en charge la déclaration des variables d’environnement par défaut dans le fichier .env. Ces valeurs pour les variables d’environnement sont les valeurs par défaut. Mais elles peuvent être remplacées par les valeurs que vous avez pu définir dans chacun de vos environnements (système d’exploitation hôte ou des variables d’environnement à partir de votre cluster). Vous placez ce fichier .env dans le dossier où la composition de docker commande est exécutée à partir de.

L’exemple suivant montre un fichier .env comme le [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) fichier de l’application eShopOnContainers.

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Composer de docker s’attend à chaque ligne dans un fichier au format .env &lt;variable&gt;=&lt;valeur&gt;.

Notez que les valeurs définies dans l’environnement d’exécution toujours remplacent les valeurs définies dans le fichier .env. De la même façon, les valeurs passées via des arguments de ligne de commande également remplacent les valeurs par défaut définies dans le fichier .env.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Vue d’ensemble de Docker composer**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **Plusieurs fichiers de composition**
    [*https://docs.docker.com/compose/extends/\#plusieurs composer des fichiers*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>Construction d’ASP.NET Core Docker images optimisées

Si vous explorez Docker et .NET Core sur des sources sur Internet, vous trouverez les fichiers Dockerfile qui illustrent la simplicité de la création d’une image Docker en copiant la source dans un conteneur. Ces exemples suggèrent que, en utilisant une configuration simple, vous pouvez avoir une image Docker avec l’environnement empaqueté avec votre application. L’exemple suivant montre un fichier Dockerfile simple de manière similaire.

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

Un fichier Dockerfile, comme cela fonctionne. Toutefois, vous pouvez optimiser essentiellement de vos images, en particulier vos images de production.

Dans le conteneur et le modèle de microservices, vous démarrez en permanence les conteneurs. La manière classique d’utilisation de conteneurs ne redémarre pas un conteneur en veille, car le conteneur peut être supprimé. Orchestrators (par exemple, Docker Swarm, Kubernetes, DCOS ou Azure Service Fabric) créent simplement de nouvelles instances d’images. Cela signifie que vous devez optimiser à précompilation de l’application lorsqu’elle est générée pour le processus d’instanciation seront plus rapide. Lorsque le conteneur est démarré, il doit être prêt à s’exécuter. Vous ne devez pas restaurer et compiler au moment de l’exécution, à l’aide de dotnet dotnet et restauration les commandes de génération à partir de l’interface CLI dotnet qui, comme vous le voyez dans nombreuses publications de blog sur .NET Core et Docker.

L’équipe .NET a été effectue un travail important pour rendre le .NET Core et ASP.NET Core une infrastructure optimisées sur le conteneur. Non seulement est-il .NET Core une infrastructure légère avec un faible encombrement mémoire ; l’équipe a le focus sur les performances de démarrage et les produits certaines images Docker optimisées, comme le [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image disponible à l’adresse [Hub Docker](https://hub.docker.com/r/microsoft/aspnetcore/), par opposition à la mise à jour [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) ou [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images. Le [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image fournit la configuration automatique d’aspnetcore\_URL sur le port 80 et le cache de pre-ngend d’assemblys ; ces deux paramètres entraînent le démarrage plus rapide.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Génération d’Images Docker avec ASP.NET Core optimisées**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

### <a name="building-the-application-from-a-build-ci-container"></a>Génération de l’application à partir d’un conteneur de build (CI)

Un autre avantage de Docker est que vous pouvez générer votre application à partir d’un conteneur préconfiguré, comme indiqué dans la Figure 8-13, vous n’avez pas besoin de créer un ordinateur de build ou d’une machine virtuelle pour générer votre application. Vous pouvez utiliser ou que le conteneur de build de test en l’exécutant à votre ordinateur de développement. Mais ce qui est encore plus intéressant est que vous pouvez utiliser le même conteneur de build à partir de votre pipeline de l’élément de configuration (intégration continue).

![](./media/image14.png)

**Figure 8-13**. Composants de création de bits de .NET à partir d’un conteneur

Pour ce scénario, nous fournissons les [aspnetcore/microsoft-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image que vous pouvez utiliser pour compiler et générer des applications de base ASP.NET. La sortie est placée dans une image basée sur la [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, qui est une image optimisée de runtime, comme indiquée précédemment.

L’image de la build aspnetcore contient tout ce dont vous avez besoin pour compiler une application ASP.NET Core, notamment .NET Core, que le Kit de développement ASP.NET, npm, Bower, Gulp, etc..

Nous avons besoin de ces dépendances au moment de la génération. Mais nous ne souhaitez pas effectuer avec l’application pendant l’exécution, car il serait l’image soit trop importante. Dans l’application eShopOnContainers, vous pouvez générer l’application à partir d’un conteneur en exécutant simplement les éléments suivants docker-composent de commande.

```
  docker-compose -f docker-compose.ci.build.yml up
```

Figure 8-14 montre cette commande en cours d’exécution sur la ligne de commande.

![](./media/image15.png)

**Figure 8-14.** Génération de votre application .NET à partir d’un conteneur

Comme vous pouvez le voir, le conteneur est en cours d’exécution est la génération de l’élément de configuration\_1 conteneur. Cela est basée sur l’image de la build aspnetcore afin qu’il peut compiler et générer votre ensemble de l’application à partir de ce conteneur à la place de votre PC. C’est pourquoi en réalité il est génération et la compilation des projets .NET Core dans Linux, car ce conteneur est en cours d’exécution sur l’hôte Docker Linux par défaut.

Le [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) de fichiers pour cette image (partie d’eShopOnContainers) contient le code suivant. Vous pouvez voir qu’il démarre un conteneur de build à l’aide de la [aspnetcore/microsoft-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.

```yml
version: '2'
  services:
    ci-build:
      image: microsoft/aspnetcore-build:1.0-1.1
      volumes:
        - .:/src
      working_dir: /src
      command: /bin/bash -c "pushd ./src/Web/WebSPA && npm rebuild node-sass && pushd ./../../.. && dotnet restore ./eShopOnContainers-ServicesAndWebApps.sln && dotnet publish ./eShopOnContainers-ServicesAndWebApps.sln -c Release -o ./obj/Docker/publish"
```

* En commençant par **.NET Core 2.0**, `dotnet restore` commande s’exécute automatiquement lorsque le `dotnet publish` commande est exécutée.

Une fois que le conteneur de build est en cours d’exécution, il s’exécute la restauration de dotnet du Kit de développement .NET et dotnet publier des commandes sur tous les projets dans la solution pour compiler les bits de .NET. Dans ce cas, étant donné qu’eShopOnContainers a également une SPA basé sur la machine à écrire et angulaire pour le code client, il doit également vérifier les dépendances du JavaScript avec npm, mais cette action n’est pas liée aux bits de .NET.

Le dotnet publier des builds de commande et publie la sortie compilée dans chaque dossier de projet pour le... dossier /obj/docker/Publish, comme indiqué dans la Figure 8-15.

![](./media/image16.png)

**Figure 8-15.** Commande de publier des fichiers binaires générés par le dotnet

#### <a name="creating-the-docker-images-from-the-cli"></a>Création des images Docker à partir de l’interface CLI

Une fois que la sortie de l’application est publiée dans les dossiers connexes (dans chaque projet), l’étape suivante consiste à générer réellement les images Docker. Pour ce faire, vous utilisez la version docker-compose et docker-composez des commandes, comme indiqué dans la Figure 8 à 16.

![](./media/image17.png)

**Figure 8 à 16.** Création d’images Docker et les conteneurs en cours d’exécution

Figure 8-17, vous pouvez voir comment le docker-compose générer la commande s’exécute.

![](./media/image18.png)

**Figure 8-17**. Création d’images Docker avec la docker-composer la commande de génération

La différence entre la docker-compose générer et composer docker des commandes est qui composent docker des builds et les images de démarrage.

Lorsque vous utilisez Visual Studio, toutes ces étapes sont effectuées en coulisse. Visual Studio compile votre application .NET, crée les images Docker et déploie les conteneurs dans l’hôte Docker. Visual Studio offre des fonctionnalités supplémentaires, comme la possibilité de déboguer vos conteneurs en cours d’exécution dans Docker, directement à partir de Visual Studio.

Le takeway globale ici est que vous êtes en mesure de générer votre application de la même façon votre pipeline de l’élément de configuration/CD doit générer, à partir d’un conteneur au lieu d’à partir d’un ordinateur local. Une fois que les images créées, puis vous devez simplement exécuter les images Docker à l’aide de la docker-composer des commandes.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **Création de bits d’un conteneur : configuration de la solution eShopOnContainers dans un environnement Windows CLI (dotnet CLI, Docker CLI et VS Code)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/ 03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-Environment-(dotnet-CLI,-docker-CLI-and-VS-code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))


>[!div class="step-by-step"]
[Précédente] (données-driven-crud-microservice.md) [suivant] (base de données-server-container.md)
