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
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="45ecd-104">Définition de votre application conteneur multiples avec docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="45ecd-104">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="45ecd-105">Dans ce guide, les [docker-compose.yml](https://docs.docker.com/compose/compose-file/) fichier a été introduit dans la section [étape 4. Définir vos services dans docker-compose.yml lors de la création d’une application de Docker conteneur multi](#step4_define_svcs_in_docker_compose_yml).</span><span class="sxs-lookup"><span data-stu-id="45ecd-105">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="45ecd-106">Toutefois, il existe d’autres façons d’utiliser les fichiers docker-compose peine d’Explorer plus en détail.</span><span class="sxs-lookup"><span data-stu-id="45ecd-106">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="45ecd-107">Par exemple, vous pouvez décrire de façon explicite comment vous souhaitez déployer votre application conteneur multiples dans le fichier compose.yml de docker.</span><span class="sxs-lookup"><span data-stu-id="45ecd-107">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="45ecd-108">Si vous le souhaitez, vous pouvez également décrire la manière dont vous vous apprêtez à créer vos images Docker personnalisés.</span><span class="sxs-lookup"><span data-stu-id="45ecd-108">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="45ecd-109">(Les images Docker personnalisé peuvent également être générées avec l’interface CLI de Docker.)</span><span class="sxs-lookup"><span data-stu-id="45ecd-109">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="45ecd-110">En fait, vous définissez chacune des conteneurs que vous souhaitez déployer plus certaines caractéristiques pour chaque déploiement de conteneur.</span><span class="sxs-lookup"><span data-stu-id="45ecd-110">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="45ecd-111">Une fois que vous avez un fichier de description du déploiement de plusieurs conteneurs, vous pouvez déployer la solution dans son intégralité en une seule action orchestrée par le [docker-composer des](https://docs.docker.com/compose/overview/) commande CLI, ou vous pouvez déployer en toute transparence à partir de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="45ecd-111">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="45ecd-112">Dans le cas contraire, vous devez utiliser l’interface CLI de Docker pour déployer un conteneur en conteneur en plusieurs étapes à l’aide de la commande docker run à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="45ecd-112">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="45ecd-113">Par conséquent, chaque service défini dans docker-compose.yml doit spécifier exactement une image ou générer.</span><span class="sxs-lookup"><span data-stu-id="45ecd-113">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="45ecd-114">Autres clés sont facultatifs et sont analogues à leur docker exécuter équivalents de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="45ecd-114">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="45ecd-115">Le code YAML suivant est la définition d’un fichier possible globale mais unique docker-compose.yml pour l’exemple eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="45ecd-115">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="45ecd-116">Cela n’est pas le fichier réel docker-compose eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="45ecd-116">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="45ecd-117">Au lieu de cela, elle est une version simplifiée et consolidée dans un seul fichier, qui n’est pas le meilleur moyen de travailler avec docker-composer des fichiers, comme vous le verrez plus tard.</span><span class="sxs-lookup"><span data-stu-id="45ecd-117">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

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

<span data-ttu-id="45ecd-118">La clé racine de ce fichier est services.</span><span class="sxs-lookup"><span data-stu-id="45ecd-118">The root key in this file is services.</span></span> <span data-ttu-id="45ecd-119">Sous cette clé, vous définissez les services que vous souhaitez déployer et exécuter lorsque vous exécutez le composer docker commande ou lorsque vous déployez à partir de Visual Studio à l’aide de ce fichier compose.yml de docker.</span><span class="sxs-lookup"><span data-stu-id="45ecd-119">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="45ecd-120">Dans ce cas, le fichier compose.yml de docker a plusieurs services définis, comme décrit dans la liste suivante.</span><span class="sxs-lookup"><span data-stu-id="45ecd-120">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="45ecd-121">webmvc conteneur, y compris l’application ASP.NET MVC de base consomme la microservices du côté serveur C\#</span><span class="sxs-lookup"><span data-stu-id="45ecd-121">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="45ecd-122">Catalog.API conteneur, y compris l’API Web de catalogue ASP.NET Core microservice</span><span class="sxs-lookup"><span data-stu-id="45ecd-122">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="45ecd-123">Ordering.API conteneur, y compris le classement l’API Web ASP.NET principale microservice</span><span class="sxs-lookup"><span data-stu-id="45ecd-123">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="45ecd-124">SQL.Data conteneur en cours d’exécution SQL Server pour Linux, contenant les bases de données microservices</span><span class="sxs-lookup"><span data-stu-id="45ecd-124">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="45ecd-125">basket.API conteneur avec l’API Web de panier d’achat ASP.NET Core microservice</span><span class="sxs-lookup"><span data-stu-id="45ecd-125">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="45ecd-126">basket.Data conteneur en cours d’exécution du service de cache REDIS, avec la base de données du panier d’achat comme un cache REDIS</span><span class="sxs-lookup"><span data-stu-id="45ecd-126">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="45ecd-127">Un conteneur d’API du Service Web simple</span><span class="sxs-lookup"><span data-stu-id="45ecd-127">A simple Web Service API container</span></span>

<span data-ttu-id="45ecd-128">En mettant l’accent sur un seul conteneur, le conteneur-microservice catalog.api a une définition simple :</span><span class="sxs-lookup"><span data-stu-id="45ecd-128">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

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

<span data-ttu-id="45ecd-129">Ce service en conteneur dispose de la configuration de base suivante :</span><span class="sxs-lookup"><span data-stu-id="45ecd-129">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="45ecd-130">Il est basé sur l’image eshop/catalog.api personnalisé.</span><span class="sxs-lookup"><span data-stu-id="45ecd-130">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="45ecd-131">Par souci de simplicité, il n’existe aucune build : paramètre dans le fichier de clé.</span><span class="sxs-lookup"><span data-stu-id="45ecd-131">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="45ecd-132">Cela signifie que l’image doit avoir été créé précédemment (avec la génération docker) ou ont été téléchargés (avec la commande d’extraction docker) à partir d’un Registre Docker.</span><span class="sxs-lookup"><span data-stu-id="45ecd-132">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="45ecd-133">Il définit une variable d’environnement nommée ConnectionString avec la chaîne de connexion à utiliser par Entity Framework pour accéder à l’instance de SQL Server qui contient le modèle de données de catalogue.</span><span class="sxs-lookup"><span data-stu-id="45ecd-133">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="45ecd-134">Dans ce cas, le même conteneur de SQL Server contient plusieurs bases de données.</span><span class="sxs-lookup"><span data-stu-id="45ecd-134">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="45ecd-135">Vous devez donc moins de mémoire dans votre ordinateur de développement pour Docker.</span><span class="sxs-lookup"><span data-stu-id="45ecd-135">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="45ecd-136">Toutefois, vous pouvez également déployer un conteneur de SQL Server pour chaque base de données de microservice.</span><span class="sxs-lookup"><span data-stu-id="45ecd-136">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="45ecd-137">Le nom SQL Server est sql.data, qui est le même nom que celui utilisé pour le conteneur qui exécute l’instance de SQL Server pour Linux.</span><span class="sxs-lookup"><span data-stu-id="45ecd-137">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="45ecd-138">Ceci est pratique ; Pour pouvoir utiliser cette résolution de noms (interne à l’hôte Docker) résout l’adresse réseau vous n’avez pas besoin de connaître l’adresse IP interne pour les conteneurs que vous accédez à partir d’autres conteneurs.</span><span class="sxs-lookup"><span data-stu-id="45ecd-138">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="45ecd-139">Étant donné que la chaîne de connexion est définie par une variable d’environnement, vous pouvez définir cette variable via un mécanisme différent et à un autre moment.</span><span class="sxs-lookup"><span data-stu-id="45ecd-139">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="45ecd-140">Par exemple, vous pouvez définir une chaîne de connexion différentes lors du déploiement en production finales hôtes d’ou en procédant à partir de vos pipelines de l’élément de configuration/CD dans VSTS ou votre système DevOps préféré.</span><span class="sxs-lookup"><span data-stu-id="45ecd-140">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in VSTS or your preferred DevOps system.</span></span>

-   <span data-ttu-id="45ecd-141">Il expose le port 80 pour l’accès interne au service catalog.api au sein de l’hôte Docker.</span><span class="sxs-lookup"><span data-stu-id="45ecd-141">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="45ecd-142">L’hôte est actuellement un VM Linux, car il est basé sur une image Docker pour Linux, mais vous pouvez configurer le conteneur à exécuter sur une image Windows à la place.</span><span class="sxs-lookup"><span data-stu-id="45ecd-142">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="45ecd-143">Il transfère l’exposé le port 80 sur le conteneur au port 5101 sur l’ordinateur hôte de Docker (la VM Linux).</span><span class="sxs-lookup"><span data-stu-id="45ecd-143">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="45ecd-144">Il lie le service web pour le service sql.data (l’instance de SQL Server pour Linux de base de données en cours d’exécution dans un conteneur).</span><span class="sxs-lookup"><span data-stu-id="45ecd-144">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="45ecd-145">Lorsque vous spécifiez cette dépendance, le conteneur catalog.api ne démarrera pas tant que le conteneur sql.data a déjà été démarré ; C’est tout d’abord important car catalog.api doit avoir au plus la base de données SQL Server et en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="45ecd-145">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="45ecd-146">Toutefois, ce type de dépendance de conteneur n’est pas suffisant dans de nombreux cas, étant donné que Docker vérifie uniquement au niveau du conteneur.</span><span class="sxs-lookup"><span data-stu-id="45ecd-146">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="45ecd-147">Parfois le service (dans ce cas de SQL Server) peut toujours pas être prêt, il est recommandé d’implémenter la logique de nouvelle tentative avec interruption exponentielle dans votre microservices client.</span><span class="sxs-lookup"><span data-stu-id="45ecd-147">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="45ecd-148">De cette façon, si un conteneur de dépendance n’est pas prêt pour une courte période, l’application sera toujours être résiliente.</span><span class="sxs-lookup"><span data-stu-id="45ecd-148">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="45ecd-149">Il est configuré pour autoriser l’accès aux serveurs externes : extra\_hôtes définition permet d’accéder aux serveurs externes ou des ordinateurs en dehors de l’hôte Docker (autrement dit, en dehors de la valeur par défaut VM Linux qui est un développement Docker en hôte), par exemple un serveur SQL local Instance de serveur sur votre ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="45ecd-149">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="45ecd-150">Il existe également des autres, docker-compose.yml des paramètres plus avancés que nous aborderons dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="45ecd-150">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="45ecd-151">À l’aide de docker-composer des fichiers pour cibler plusieurs environnements</span><span class="sxs-lookup"><span data-stu-id="45ecd-151">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="45ecd-152">Les fichiers de docker-compose.yml sont des fichiers de définition et peuvent être utilisées par plusieurs infrastructures qui comprennent ce format.</span><span class="sxs-lookup"><span data-stu-id="45ecd-152">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="45ecd-153">L’outil plus simple est le docker-composition de commande, mais les autres outils, tels qu’orchestrators (par exemple, Docker Swarm) également comprennent ce fichier.</span><span class="sxs-lookup"><span data-stu-id="45ecd-153">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="45ecd-154">Par conséquent, à l’aide de la commande, vous pouvez cibler les principaux scénarios suivants docker-composer.</span><span class="sxs-lookup"><span data-stu-id="45ecd-154">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="45ecd-155">Environnements de développement</span><span class="sxs-lookup"><span data-stu-id="45ecd-155">Development environments</span></span>

<span data-ttu-id="45ecd-156">Lorsque vous développez des applications, il est important d’être en mesure d’exécuter une application dans un environnement de développement isolé.</span><span class="sxs-lookup"><span data-stu-id="45ecd-156">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="45ecd-157">Vous pouvez utiliser la commande CLI pour créer cet environnement ou utiliser Visual Studio qui docker utilise-composer en coulisse docker-composer.</span><span class="sxs-lookup"><span data-stu-id="45ecd-157">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="45ecd-158">Le fichier docker-compose.yml vous permet de configurer et de documenter les dépendances du service de tous les votre application (autres services, du cache, bases de données, les files d’attente, etc.).</span><span class="sxs-lookup"><span data-stu-id="45ecd-158">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="45ecd-159">À l’aide de la docker-composer des commandes CLI, vous pouvez créer et démarrer un ou plusieurs conteneurs pour chaque dépendance avec une seule commande (docker-composer des).</span><span class="sxs-lookup"><span data-stu-id="45ecd-159">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="45ecd-160">Les fichiers de compose.yml de docker sont interprétés par le moteur Docker les fichiers de configuration, mais servent également à des fichiers de documentation pratique sur la composition de votre application conteneur multiples.</span><span class="sxs-lookup"><span data-stu-id="45ecd-160">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="45ecd-161">Environnements de test</span><span class="sxs-lookup"><span data-stu-id="45ecd-161">Testing environments</span></span>

<span data-ttu-id="45ecd-162">Une partie importante de tout déploiement continu (CD) ou le processus d’intégration continue (CI) sont les tests unitaires et les tests d’intégration.</span><span class="sxs-lookup"><span data-stu-id="45ecd-162">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="45ecd-163">Ces tests automatisés nécessitent un environnement isolé afin qu’ils ne soient pas affectés par les utilisateurs ou toute autre modification apportée dans les données d’application.</span><span class="sxs-lookup"><span data-stu-id="45ecd-163">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="45ecd-164">Avec Docker Compose, vous pouvez créer et détruire cet environnement isolé très facilement en quelques commandes à partir de votre invite de commandes ou les scripts, tels que les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="45ecd-164">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="45ecd-165">Déploiements de production</span><span class="sxs-lookup"><span data-stu-id="45ecd-165">Production deployments</span></span>

<span data-ttu-id="45ecd-166">Vous pouvez également utiliser le nouveau message à déployer sur un moteur Docker à distance.</span><span class="sxs-lookup"><span data-stu-id="45ecd-166">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="45ecd-167">Un cas classique consiste à déployer sur une instance unique de l’hôte Docker (comme une machine virtuelle de production ou d’un serveur configuré avec [Machine Docker](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="45ecd-167">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="45ecd-168">Mais cela peut également être un entier [Docker Swarm](https://docs.docker.com/swarm/overview/) de cluster, car les clusters sont également compatibles avec les fichiers compose.yml de docker.</span><span class="sxs-lookup"><span data-stu-id="45ecd-168">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="45ecd-169">Si vous utilisez n’importe quel autre orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), vous devrez peut-être ajouter le programme d’installation et les métadonnées des paramètres de configuration telles que celles dans docker-compose.yml, mais dans le format requis par l’autres orchestrator.</span><span class="sxs-lookup"><span data-stu-id="45ecd-169">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="45ecd-170">Dans tous les cas, de composer docker est un outil et les métadonnées un format pratique pour le flux de travail de développement, de test et de production, bien que le flux de travail de production peut-être varier l’orchestrateur que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="45ecd-170">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="45ecd-171">L’utilisation de plusieurs docker-composer des fichiers pour gérer plusieurs environnements</span><span class="sxs-lookup"><span data-stu-id="45ecd-171">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="45ecd-172">Lorsque vous ciblez différents environnements, vous devez utiliser plusieurs composer des fichiers.</span><span class="sxs-lookup"><span data-stu-id="45ecd-172">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="45ecd-173">Cela vous permet de créer plusieurs variantes de configuration en fonction de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="45ecd-173">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="45ecd-174">Remplacement du fichier de base docker-compose</span><span class="sxs-lookup"><span data-stu-id="45ecd-174">Overriding the base docker-compose file</span></span>

<span data-ttu-id="45ecd-175">Vous pouvez utiliser un fichier unique docker-compose.yml comme dans les exemples simplifiées indiqué dans les sections précédentes.</span><span class="sxs-lookup"><span data-stu-id="45ecd-175">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="45ecd-176">Toutefois, qui n’est pas recommandé pour la plupart des applications.</span><span class="sxs-lookup"><span data-stu-id="45ecd-176">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="45ecd-177">Par défaut, le nouveau message lit deux fichiers, un compose.yml de docker et un fichier docker-compose.override.yml facultatif.</span><span class="sxs-lookup"><span data-stu-id="45ecd-177">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="45ecd-178">Comme indiqué dans la Figure 8 à 11, lorsque vous utilisez Visual Studio et l’activation de la prise en charge de Docker, Visual Studio crée également les fichiers ainsi que des fichiers supplémentaires utilisées pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="45ecd-178">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates those files plus some additional files used for debugging.</span></span>

![](./media/image12.png)

<span data-ttu-id="45ecd-179">**Figure 8-11**.</span><span class="sxs-lookup"><span data-stu-id="45ecd-179">**Figure 8-11**.</span></span> <span data-ttu-id="45ecd-180">docker-composer des fichiers dans Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="45ecd-180">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="45ecd-181">Vous pouvez modifier les fichiers docker-compose avec n’importe quel éditeur, telles que Visual Studio Code ou Sublime et exécuter l’application avec la composition de docker jusqu'à la commande.</span><span class="sxs-lookup"><span data-stu-id="45ecd-181">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="45ecd-182">Par convention, le fichier docker-compose.yml contient la configuration de base et d’autres paramètres statiques.</span><span class="sxs-lookup"><span data-stu-id="45ecd-182">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="45ecd-183">Cela signifie que la configuration du service ne doit pas changer en fonction de l’environnement de déploiement que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="45ecd-183">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="45ecd-184">Le fichier compose.override.yml de docker, comme son nom l’indique, contient les paramètres de configuration qui remplacent la configuration de base, telles que configuration dépend de l’environnement de déploiement.</span><span class="sxs-lookup"><span data-stu-id="45ecd-184">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="45ecd-185">Vous pouvez avoir plusieurs fichiers de substitution avec des noms différents également.</span><span class="sxs-lookup"><span data-stu-id="45ecd-185">You can have multiple override files with different names also.</span></span> <span data-ttu-id="45ecd-186">Les fichiers de remplacement contiennent généralement des informations supplémentaires requises par l’application, mais il est spécifique à un environnement ou à un déploiement.</span><span class="sxs-lookup"><span data-stu-id="45ecd-186">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="45ecd-187">Ciblage de plusieurs environnements</span><span class="sxs-lookup"><span data-stu-id="45ecd-187">Targeting multiple environments</span></span>

<span data-ttu-id="45ecd-188">Un cas d’utilisation classique est lorsque vous définissez plusieurs composer des fichiers afin de vous pouvez cibler plusieurs environnements, comme la production, de mise en lots, l’élément de configuration ou de développement.</span><span class="sxs-lookup"><span data-stu-id="45ecd-188">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="45ecd-189">Pour prendre en charge de ces différences, vous pouvez fractionner la configuration de votre nouveau message dans plusieurs fichiers, comme indiqué dans la Figure 8-12.</span><span class="sxs-lookup"><span data-stu-id="45ecd-189">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="45ecd-190">**Figure 8-12**.</span><span class="sxs-lookup"><span data-stu-id="45ecd-190">**Figure 8-12**.</span></span> <span data-ttu-id="45ecd-191">Plusieurs composer docker les fichiers de substitution de valeurs dans le fichier de base de compose.yml de docker</span><span class="sxs-lookup"><span data-stu-id="45ecd-191">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="45ecd-192">Vous démarrez avec le fichier de base de compose.yml de docker.</span><span class="sxs-lookup"><span data-stu-id="45ecd-192">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="45ecd-193">Ce fichier de base doit contenir les paramètres de configuration de base ou statique qui ne changent pas selon l’environnement.</span><span class="sxs-lookup"><span data-stu-id="45ecd-193">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="45ecd-194">Par exemple, l’eShopOnContainers a le fichier docker-compose.yml suivant en tant que le fichier de base.</span><span class="sxs-lookup"><span data-stu-id="45ecd-194">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

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

<span data-ttu-id="45ecd-195">Les valeurs dans le fichier de base de docker-compose.yml ne doivent pas modifier en raison d’environnements de déploiement cible différent.</span><span class="sxs-lookup"><span data-stu-id="45ecd-195">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="45ecd-196">Par exemple, si vous vous concentrer sur la définition de service webmvc, vous pouvez voir comment ces informations sont quasiment identique, quel que soit l’environnement vous pouvez cibler.</span><span class="sxs-lookup"><span data-stu-id="45ecd-196">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="45ecd-197">Vous avez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="45ecd-197">You have the following information:</span></span>

-   <span data-ttu-id="45ecd-198">Le nom du service : webmvc.</span><span class="sxs-lookup"><span data-stu-id="45ecd-198">The service name: webmvc.</span></span>

-   <span data-ttu-id="45ecd-199">Image personnalisée du conteneur : Shopping/webmvc.</span><span class="sxs-lookup"><span data-stu-id="45ecd-199">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="45ecd-200">La commande pour générer l’image personnalisée de Docker, indiquant les informations à utiliser.</span><span class="sxs-lookup"><span data-stu-id="45ecd-200">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="45ecd-201">Dépendances sur d’autres services, afin de ce conteneur ne démarre pas tant que les autres conteneurs de dépendance ont démarré.</span><span class="sxs-lookup"><span data-stu-id="45ecd-201">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="45ecd-202">Vous pouvez avoir une configuration supplémentaire, mais le point important est que dans le fichier de base de compose.yml de docker, vous souhaitez simplement définir les informations qui sont communes à plusieurs environnements.</span><span class="sxs-lookup"><span data-stu-id="45ecd-202">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="45ecd-203">Puis dans le docker-compose.override.yml ou des fichiers similaires pour la production ou intermédiaire, vous devez placer la configuration spécifique pour chaque environnement.</span><span class="sxs-lookup"><span data-stu-id="45ecd-203">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="45ecd-204">En règle générale, les compose.override.yml de docker est utilisé pour votre environnement de développement, comme dans l’exemple suivant d’eShopOnContainers :</span><span class="sxs-lookup"><span data-stu-id="45ecd-204">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

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

<span data-ttu-id="45ecd-205">Dans cet exemple, la configuration de remplacement de développement expose certains ports à l’hôte, qui définit les variables d’environnement avec URL de redirection et spécifie les chaînes de connexion pour l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="45ecd-205">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="45ecd-206">Ces paramètres sont tout simplement pour l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="45ecd-206">These settings are all just for the development environment.</span></span>

<span data-ttu-id="45ecd-207">Lorsque vous exécutez composer docker des (ou lancer à partir de Visual Studio), la commande lit les remplacements automatiquement comme s’il a été fusionner les deux fichiers.</span><span class="sxs-lookup"><span data-stu-id="45ecd-207">When you run docker-compose up (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="45ecd-208">Supposons que vous souhaitez un autre fichier de composition pour l’environnement de production, avec des valeurs de configuration différente.</span><span class="sxs-lookup"><span data-stu-id="45ecd-208">Suppose that you want another Compose file for the production environment, with different configuration values.</span></span> <span data-ttu-id="45ecd-209">Vous pouvez créer un autre fichier de remplacement, comme suit.</span><span class="sxs-lookup"><span data-stu-id="45ecd-209">You can create another override file, like the following.</span></span> <span data-ttu-id="45ecd-210">(Ce fichier peut être stocké dans un référentiel Git différents ou géré et sécurisé par une autre équipe.)</span><span class="sxs-lookup"><span data-stu-id="45ecd-210">(This file might be stored in a different Git repo or managed and secured by a different team.)</span></span>

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

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="45ecd-211">Comment déployer avec un fichier de remplacement spécifique</span><span class="sxs-lookup"><span data-stu-id="45ecd-211">How to deploy with a specific override file</span></span>

<span data-ttu-id="45ecd-212">Pour utiliser plusieurs fichiers de substitution, ou un fichier de remplacement avec un nom différent, vous pouvez utiliser l’option-f avec la commande docker-composer et spécifiez les fichiers.</span><span class="sxs-lookup"><span data-stu-id="45ecd-212">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="45ecd-213">Composer fusionne les fichiers dans l’ordre qu’ils sont spécifiés sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="45ecd-213">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="45ecd-214">L’exemple suivant montre comment déployer des fichiers de substitution.</span><span class="sxs-lookup"><span data-stu-id="45ecd-214">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="45ecd-215">À l’aide de variables d’environnement dans docker-composer des fichiers</span><span class="sxs-lookup"><span data-stu-id="45ecd-215">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="45ecd-216">Il est pratique, en particulier dans les environnements de production, pour être en mesure d’obtenir des informations de configuration à partir de variables d’environnement, comme nous l’avons montré dans les exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="45ecd-216">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="45ecd-217">Vous référencez une variable d’environnement dans vos fichiers docker-compose à l’aide de la syntaxe \${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="45ecd-217">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="45ecd-218">La ligne suivante à partir d’un fichier docker-compose.prod.yml montre comment référencer la valeur d’une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="45ecd-218">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="45ecd-219">Variables d’environnement sont créés et initialisés de différentes façons, selon votre environnement d’hôte (Linux, Windows, le cluster du Cloud, etc..).</span><span class="sxs-lookup"><span data-stu-id="45ecd-219">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="45ecd-220">Toutefois, une approche pratique consiste à utiliser un fichier .env.</span><span class="sxs-lookup"><span data-stu-id="45ecd-220">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="45ecd-221">Les fichiers docker-compose prend en charge la déclaration des variables d’environnement par défaut dans le fichier .env.</span><span class="sxs-lookup"><span data-stu-id="45ecd-221">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="45ecd-222">Ces valeurs pour les variables d’environnement sont les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="45ecd-222">These values for the environment variables are the default values.</span></span> <span data-ttu-id="45ecd-223">Mais elles peuvent être remplacées par les valeurs que vous avez pu définir dans chacun de vos environnements (système d’exploitation hôte ou des variables d’environnement à partir de votre cluster).</span><span class="sxs-lookup"><span data-stu-id="45ecd-223">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="45ecd-224">Vous placez ce fichier .env dans le dossier où la composition de docker commande est exécutée à partir de.</span><span class="sxs-lookup"><span data-stu-id="45ecd-224">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="45ecd-225">L’exemple suivant montre un fichier .env comme le [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) fichier de l’application eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="45ecd-225">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="45ecd-226">Composer de docker s’attend à chaque ligne dans un fichier au format .env &lt;variable&gt;=&lt;valeur&gt;.</span><span class="sxs-lookup"><span data-stu-id="45ecd-226">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="45ecd-227">Notez que les valeurs définies dans l’environnement d’exécution toujours remplacent les valeurs définies dans le fichier .env.</span><span class="sxs-lookup"><span data-stu-id="45ecd-227">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="45ecd-228">De la même façon, les valeurs passées via des arguments de ligne de commande également remplacent les valeurs par défaut définies dans le fichier .env.</span><span class="sxs-lookup"><span data-stu-id="45ecd-228">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="45ecd-229">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="45ecd-229">Additional resources</span></span>

-   <span data-ttu-id="45ecd-230">**Vue d’ensemble de Docker composer**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="45ecd-230">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="45ecd-231">**Plusieurs fichiers de composition**
    [*https://docs.docker.com/compose/extends/\#plusieurs composer des fichiers*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="45ecd-231">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="45ecd-232">Construction d’ASP.NET Core Docker images optimisées</span><span class="sxs-lookup"><span data-stu-id="45ecd-232">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="45ecd-233">Si vous explorez Docker et .NET Core sur des sources sur Internet, vous trouverez les fichiers Dockerfile qui illustrent la simplicité de la création d’une image Docker en copiant la source dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="45ecd-233">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="45ecd-234">Ces exemples suggèrent que, en utilisant une configuration simple, vous pouvez avoir une image Docker avec l’environnement empaqueté avec votre application.</span><span class="sxs-lookup"><span data-stu-id="45ecd-234">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="45ecd-235">L’exemple suivant montre un fichier Dockerfile simple de manière similaire.</span><span class="sxs-lookup"><span data-stu-id="45ecd-235">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="45ecd-236">Un fichier Dockerfile, comme cela fonctionne.</span><span class="sxs-lookup"><span data-stu-id="45ecd-236">A Dockerfile like this will work.</span></span> <span data-ttu-id="45ecd-237">Toutefois, vous pouvez optimiser essentiellement de vos images, en particulier vos images de production.</span><span class="sxs-lookup"><span data-stu-id="45ecd-237">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="45ecd-238">Dans le conteneur et le modèle de microservices, vous démarrez en permanence les conteneurs.</span><span class="sxs-lookup"><span data-stu-id="45ecd-238">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="45ecd-239">La manière classique d’utilisation de conteneurs ne redémarre pas un conteneur en veille, car le conteneur peut être supprimé.</span><span class="sxs-lookup"><span data-stu-id="45ecd-239">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="45ecd-240">Orchestrators (par exemple, Docker Swarm, Kubernetes, DCOS ou Azure Service Fabric) créent simplement de nouvelles instances d’images.</span><span class="sxs-lookup"><span data-stu-id="45ecd-240">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="45ecd-241">Cela signifie que vous devez optimiser à précompilation de l’application lorsqu’elle est générée pour le processus d’instanciation seront plus rapide.</span><span class="sxs-lookup"><span data-stu-id="45ecd-241">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="45ecd-242">Lorsque le conteneur est démarré, il doit être prêt à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="45ecd-242">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="45ecd-243">Vous ne devez pas restaurer et compiler au moment de l’exécution, à l’aide de dotnet dotnet et restauration les commandes de génération à partir de l’interface CLI dotnet qui, comme vous le voyez dans nombreuses publications de blog sur .NET Core et Docker.</span><span class="sxs-lookup"><span data-stu-id="45ecd-243">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="45ecd-244">L’équipe .NET a été effectue un travail important pour rendre le .NET Core et ASP.NET Core une infrastructure optimisées sur le conteneur.</span><span class="sxs-lookup"><span data-stu-id="45ecd-244">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="45ecd-245">Non seulement est-il .NET Core une infrastructure légère avec un faible encombrement mémoire ; l’équipe a le focus sur les performances de démarrage et les produits certaines images Docker optimisées, comme le [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image disponible à l’adresse [Hub Docker](https://hub.docker.com/r/microsoft/aspnetcore/), par opposition à la mise à jour [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) ou [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span><span class="sxs-lookup"><span data-stu-id="45ecd-245">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="45ecd-246">Le [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image fournit la configuration automatique d’aspnetcore\_URL sur le port 80 et le cache de pre-ngend d’assemblys ; ces deux paramètres entraînent le démarrage plus rapide.</span><span class="sxs-lookup"><span data-stu-id="45ecd-246">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="45ecd-247">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="45ecd-247">Additional resources</span></span>

-   <span data-ttu-id="45ecd-248">**Génération d’Images Docker avec ASP.NET Core optimisées**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="45ecd-248">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="45ecd-249">Génération de l’application à partir d’un conteneur de build (CI)</span><span class="sxs-lookup"><span data-stu-id="45ecd-249">Building the application from a build (CI) container</span></span>

<span data-ttu-id="45ecd-250">Un autre avantage de Docker est que vous pouvez générer votre application à partir d’un conteneur préconfiguré, comme indiqué dans la Figure 8-13, vous n’avez pas besoin de créer un ordinateur de build ou d’une machine virtuelle pour générer votre application.</span><span class="sxs-lookup"><span data-stu-id="45ecd-250">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="45ecd-251">Vous pouvez utiliser ou que le conteneur de build de test en l’exécutant à votre ordinateur de développement.</span><span class="sxs-lookup"><span data-stu-id="45ecd-251">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="45ecd-252">Mais ce qui est encore plus intéressant est que vous pouvez utiliser le même conteneur de build à partir de votre pipeline de l’élément de configuration (intégration continue).</span><span class="sxs-lookup"><span data-stu-id="45ecd-252">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="45ecd-253">**Figure 8-13**.</span><span class="sxs-lookup"><span data-stu-id="45ecd-253">**Figure 8-13**.</span></span> <span data-ttu-id="45ecd-254">Composants de création de bits de .NET à partir d’un conteneur</span><span class="sxs-lookup"><span data-stu-id="45ecd-254">Components building .NET bits from a container</span></span>

<span data-ttu-id="45ecd-255">Pour ce scénario, nous fournissons les [aspnetcore/microsoft-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image que vous pouvez utiliser pour compiler et générer des applications de base ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="45ecd-255">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="45ecd-256">La sortie est placée dans une image basée sur la [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, qui est une image optimisée de runtime, comme indiquée précédemment.</span><span class="sxs-lookup"><span data-stu-id="45ecd-256">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="45ecd-257">L’image de la build aspnetcore contient tout ce dont vous avez besoin pour compiler une application ASP.NET Core, notamment .NET Core, que le Kit de développement ASP.NET, npm, Bower, Gulp, etc..</span><span class="sxs-lookup"><span data-stu-id="45ecd-257">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="45ecd-258">Nous avons besoin de ces dépendances au moment de la génération.</span><span class="sxs-lookup"><span data-stu-id="45ecd-258">We need these dependencies at build time.</span></span> <span data-ttu-id="45ecd-259">Mais nous ne souhaitez pas effectuer avec l’application pendant l’exécution, car il serait l’image soit trop importante.</span><span class="sxs-lookup"><span data-stu-id="45ecd-259">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="45ecd-260">Dans l’application eShopOnContainers, vous pouvez générer l’application à partir d’un conteneur en exécutant simplement les éléments suivants docker-composent de commande.</span><span class="sxs-lookup"><span data-stu-id="45ecd-260">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="45ecd-261">Figure 8-14 montre cette commande en cours d’exécution sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="45ecd-261">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="45ecd-262">**Figure 8-14.**</span><span class="sxs-lookup"><span data-stu-id="45ecd-262">**Figure 8-14.**</span></span> <span data-ttu-id="45ecd-263">Génération de votre application .NET à partir d’un conteneur</span><span class="sxs-lookup"><span data-stu-id="45ecd-263">Building your .NET application from a container</span></span>

<span data-ttu-id="45ecd-264">Comme vous pouvez le voir, le conteneur est en cours d’exécution est la génération de l’élément de configuration\_1 conteneur.</span><span class="sxs-lookup"><span data-stu-id="45ecd-264">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="45ecd-265">Cela est basée sur l’image de la build aspnetcore afin qu’il peut compiler et générer votre ensemble de l’application à partir de ce conteneur à la place de votre PC.</span><span class="sxs-lookup"><span data-stu-id="45ecd-265">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="45ecd-266">C’est pourquoi en réalité il est génération et la compilation des projets .NET Core dans Linux, car ce conteneur est en cours d’exécution sur l’hôte Docker Linux par défaut.</span><span class="sxs-lookup"><span data-stu-id="45ecd-266">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="45ecd-267">Le [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) de fichiers pour cette image (partie d’eShopOnContainers) contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="45ecd-267">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="45ecd-268">Vous pouvez voir qu’il démarre un conteneur de build à l’aide de la [aspnetcore/microsoft-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span><span class="sxs-lookup"><span data-stu-id="45ecd-268">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

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

* <span data-ttu-id="45ecd-269">En commençant par **.NET Core 2.0**, `dotnet restore` commande s’exécute automatiquement lorsque le `dotnet publish` commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="45ecd-269">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="45ecd-270">Une fois que le conteneur de build est en cours d’exécution, il s’exécute la restauration de dotnet du Kit de développement .NET et dotnet publier des commandes sur tous les projets dans la solution pour compiler les bits de .NET.</span><span class="sxs-lookup"><span data-stu-id="45ecd-270">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="45ecd-271">Dans ce cas, étant donné qu’eShopOnContainers a également une SPA basé sur la machine à écrire et angulaire pour le code client, il doit également vérifier les dépendances du JavaScript avec npm, mais cette action n’est pas liée aux bits de .NET.</span><span class="sxs-lookup"><span data-stu-id="45ecd-271">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="45ecd-272">Le dotnet publier des builds de commande et publie la sortie compilée dans chaque dossier de projet pour le... dossier /obj/docker/Publish, comme indiqué dans la Figure 8-15.</span><span class="sxs-lookup"><span data-stu-id="45ecd-272">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="45ecd-273">**Figure 8-15.**</span><span class="sxs-lookup"><span data-stu-id="45ecd-273">**Figure 8-15.**</span></span> <span data-ttu-id="45ecd-274">Commande de publier des fichiers binaires générés par le dotnet</span><span class="sxs-lookup"><span data-stu-id="45ecd-274">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="45ecd-275">Création des images Docker à partir de l’interface CLI</span><span class="sxs-lookup"><span data-stu-id="45ecd-275">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="45ecd-276">Une fois que la sortie de l’application est publiée dans les dossiers connexes (dans chaque projet), l’étape suivante consiste à générer réellement les images Docker.</span><span class="sxs-lookup"><span data-stu-id="45ecd-276">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="45ecd-277">Pour ce faire, vous utilisez la version docker-compose et docker-composez des commandes, comme indiqué dans la Figure 8 à 16.</span><span class="sxs-lookup"><span data-stu-id="45ecd-277">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="45ecd-278">**Figure 8 à 16.**</span><span class="sxs-lookup"><span data-stu-id="45ecd-278">**Figure 8-16.**</span></span> <span data-ttu-id="45ecd-279">Création d’images Docker et les conteneurs en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="45ecd-279">Building Docker images and running the containers</span></span>

<span data-ttu-id="45ecd-280">Figure 8-17, vous pouvez voir comment le docker-compose générer la commande s’exécute.</span><span class="sxs-lookup"><span data-stu-id="45ecd-280">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="45ecd-281">**Figure 8-17**.</span><span class="sxs-lookup"><span data-stu-id="45ecd-281">**Figure 8-17**.</span></span> <span data-ttu-id="45ecd-282">Création d’images Docker avec la docker-composer la commande de génération</span><span class="sxs-lookup"><span data-stu-id="45ecd-282">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="45ecd-283">La différence entre la docker-compose générer et composer docker des commandes est qui composent docker des builds et les images de démarrage.</span><span class="sxs-lookup"><span data-stu-id="45ecd-283">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="45ecd-284">Lorsque vous utilisez Visual Studio, toutes ces étapes sont effectuées en coulisse.</span><span class="sxs-lookup"><span data-stu-id="45ecd-284">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="45ecd-285">Visual Studio compile votre application .NET, crée les images Docker et déploie les conteneurs dans l’hôte Docker.</span><span class="sxs-lookup"><span data-stu-id="45ecd-285">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="45ecd-286">Visual Studio offre des fonctionnalités supplémentaires, comme la possibilité de déboguer vos conteneurs en cours d’exécution dans Docker, directement à partir de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="45ecd-286">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="45ecd-287">Le takeway globale ici est que vous êtes en mesure de générer votre application de la même façon votre pipeline de l’élément de configuration/CD doit générer, à partir d’un conteneur au lieu d’à partir d’un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="45ecd-287">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="45ecd-288">Une fois que les images créées, puis vous devez simplement exécuter les images Docker à l’aide de la docker-composer des commandes.</span><span class="sxs-lookup"><span data-stu-id="45ecd-288">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="45ecd-289">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="45ecd-289">Additional resources</span></span>

-   <span data-ttu-id="45ecd-290">**Création de bits d’un conteneur : configuration de la solution eShopOnContainers dans un environnement Windows CLI (dotnet CLI, Docker CLI et VS Code)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/ 03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-Environment-(dotnet-CLI,-docker-CLI-and-VS-code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="45ecd-290">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="45ecd-291">[Précédente] (données-driven-crud-microservice.md) [suivant] (base de données-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="45ecd-291">[Previous] (data-driven-crud-microservice.md) [Next] (database-server-container.md)</span></span>
