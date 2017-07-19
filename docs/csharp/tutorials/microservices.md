---
title: "Microservices hébergés dans Docker, C# | Microsoft Docs"
description: "Apprenez à créer des services principaux ASP.NET qui s’exécutent dans des conteneurs Docker"
keywords: .NET, .NET Core, Docker, C#, ASP.NET, Microservice
author: BillWagner
ms.author: wiwagn
ms.date: 02/03/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: csharp
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.translationtype: Human Translation
ms.sourcegitcommit: b64eb0d8f1778a4834ecce5d2ced71e0741dbff3
ms.openlocfilehash: 40d81a161e6be06a32fb559b70a4e7eeca41e4da
ms.contentlocale: fr-fr
ms.lasthandoff: 05/27/2017

---

<a id="microservices-hosted-in-docker" class="xliff"></a>

# Microservices hébergés dans Docker

<a id="introduction" class="xliff"></a>

## Introduction

Ce didacticiel détaille les tâches nécessaires pour générer et déployer un microservice ASP.NET Core dans un conteneur Docker. Au cours de ce didacticiel, vous apprendrez à :

* Générer une application ASP.NET Core à l’aide de Yeoman
* Guide de création d’un environnement de développement Docker
* Créer une image Docker basée sur une image existante.
* Déployer votre service dans un conteneur Docker.

Au passage, vous verrez également certaines fonctionnalités du langage C# :

* Conversion des objets C# en charges utiles JSON.
* Création d’objets de transfert de données immuables
* Traitement des demandes HTTP entrantes et création de la réponse HTTP
* Guide pratique de travail avec les types valeur Nuallable

Vous pouvez [afficher ou télécharger l’exemple d’application](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/WeatherMicroservice) de cette rubrique. Pour obtenir des instructions de téléchargement, consultez [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

<a id="why-docker" class="xliff"></a>

### Pourquoi Docker ?

Docker facilite la création d’images de machine standard pour héberger vos services dans un centre de données ou dans le cloud public. Docker vous permet de configurer l’image et de la répliquer en fonction des besoins pour mettre à l’échelle l’installation de votre application.

Tout le code de ce didacticiel fonctionne dans n’importe quel environnement .NET Core.
Les tâches supplémentaires pour une installation Docker fonctionneront pour une application ASP.NET Core. 

<a id="prerequisites" class="xliff"></a>

## Conditions préalables
Vous devez configurer votre ordinateur pour exécuter .NET Core. Vous trouverez les instructions d’installation sur la page de [.NET Core](https://www.microsoft.com/net/core).
Vous pouvez exécuter cette application sur Windows, Ubuntu Linux, Mac OS ou dans un conteneur Docker. Vous devez installer l’éditeur de code de votre choix. Les descriptions ci-dessous utilisent [Visual Studio Code](https://code.visualstudio.com/), un éditeur open source et multiplateforme. Cependant, vous pouvez utiliser les outils avec lesquels vous êtes le plus à l’aise.

Vous devez également installer le moteur Docker. Consultez la [page d’installation de Docker](http://www.docker.com/products/docker) pour obtenir des instructions pour votre plateforme.
Docker peut être installé dans de nombreuses distributions Linux, Mac OS ou Windows. La page mentionnée ci-dessus contient des sections pour chacune des installations disponibles.

La plupart des composants à installer le sont par un gestionnaire de package. Si vous disposez du gestionnaire de packages de node.js `npm` installé, vous pouvez ignorer cette étape. Sinon, installez la dernière version de NodeJs à partir de [nodejs.org](https://nodejs.org), ce qui installe le gestionnaire de packages npm. 

À ce stade, vous devrez installer un certain nombre d’outils de ligne de commande qui prennent en charge le développement avec ASP.NET Core. Les modèles de ligne de commande utilisent Yeoman, Bower, Grunt et Gulp. Si vous les avez déjà installés, c’est parfait, sinon saisissez ce qui suit dans votre interpréteur de commandes préféré :

`npm install -g yo bower grunt-cli gulp`

L’option `-g` indique qu’il s’agit d’une installation globale, et que ces outils sont disponibles à l’échelle du système. (Une installation locale définit la portée du package sur un projet unique). Une fois que vous avez installé les outils de base, vous devez installer les générateurs de modèle yeoman ASP.NET :

`npm install -g generator-aspnet`

<a id="create-the-application" class="xliff"></a>

## Création de l’application

Maintenant que vous avez installé tous les outils, créez une nouvelle application asp.net. Pour utiliser le générateur de ligne de commande, exécutez la commande yeoman suivante dans votre interpréteur de commandes préféré :

`yo aspnet`

Cette commande vous invite à sélectionner le type d’application que vous souhaitez créer. Pour ce microservice, vous souhaitez obtenir l’application web la plus simple et légère possible, sélectionnez donc « Application Web vide ». Le modèle vous demandera un nom. Sélectionnez « WeatherMicroservice ». 

Le modèle crée huit fichiers pour vous :

* Un .gitignore personnalisé pour les applications ASP.NET Core.
* Un fichier Startup.cs. Cela contient la base de l’application.
* Un fichier Program.cs. Cela contient le point d’entrée de l’application.
* Un fichier WeatherMicroservice.csproj. Il s’agit du fichier de génération de l’application.
* Un Dockerfile. Ce script crée une image Docker pour l’application.
* Un README.md. Il contient des liens vers d’autres ressources de base d’ASP.NET.
* Un fichier web.config. Les informations de configuration de base s’y trouvent.
* Un fichier runtimeconfig.template.json. Il contient les paramètres de débogage utilisés par l’EDI.

Vous pouvez maintenant exécuter l’application générée par le modèle. Vous pouvez le faire à l’aide d’une série d’outils en ligne de commande. La commande `dotnet` exécute les outils nécessaires pour le développement .NET. Chaque verbe exécute une commande différente

La première étape consiste à restaurer toutes les dépendances :

```console
dotnet restore
```

La restauration Dotnet utilise le gestionnaire de packages NuGet pour installer tous les packages dans le répertoire de l’application. Il génère également un fichier project.json.lock. Ce fichier contient des informations sur chaque package référencé. Après la restauration de toutes les dépendances, vous générez l’application :

```console
dotnet build
```

Et une fois que vous générez l’application, vous l’exécutez à partir de la ligne de commande :

```console
dotnet run
```

La configuration par défaut écoute le port http://localhost:5000. Vous pouvez ouvrir un navigateur et accéder à cette page pour voir un « Hello World! » « Operation Not Found! ».

<a id="anatomy-of-an-aspnet-core-application" class="xliff"></a>

### Anatomie d’une application ASP.NET Core

Maintenant que vous avez créé l’application, nous allons voir comment cette fonctionnalité est implémentée. Deux des fichiers générés sont particulièrement intéressants à ce stade : project.json et Startup.cs. 

Project.json qui contient des informations sur le projet. Ces deux nœuds, que vous utiliserez souvent, sont des « dépendances » et des « frameworks ». Le nœud de dépendances répertorie tous les packages qui sont nécessaires pour cette application.
À ce stade, il s’agit d’un petit nœud, qui ne nécessite que les packages qui exécutent le serveur Web.

Le nœud « frameworks » spécifie les versions et les configurations du .NET Framework qui va exécuter cette application.

L’application est implémentée dans Startup.cs. Ce fichier contient la classe de démarrage.

Les deux méthodes sont appelées par l’infrastructure ASP.NET Core pour configurer et exécuter l’application. La méthode `ConfigureServices` décrit les services qui sont nécessaires pour cette application. Vous créez un microservice épuré, vous n’avez donc pas besoin de configurer de dépendances. La méthode `Configure` configure les gestionnaires pour les requêtes HTTP entrantes. Le modèle génère un gestionnaire simple qui répond à une demande dont le texte est « Hello World! ».

<a id="build-a-microservice" class="xliff"></a>

## Créer un microservice

Le service que vous vous apprêtez à générer fournira des rapports météorologiques depuis n’importe où dans le monde. Dans une application de production, vous appelleriez un service pour récupérer des données météorologiques. Pour notre exemple, nous allons générer des prévisions météorologiques aléatoires. 

Il existe un certain nombre de tâches que vous devez effectuer pour implémenter notre service météo aléatoire :

* Analyser la requête entrante pour lire la latitude et la longitude.
* Générer des données de prévision aléatoires.
* Convertir ces données de prévision aléatoires d’objets C# en paquets JSON.
* Définir l’en-tête de réponse pour indiquer que votre service renvoie JSON.
* Écrivez la réponse.

Les sections suivantes décrivent chacune de ces étapes.

<a id="parsing-the-query-string" class="xliff"></a>

### Analyse de la chaîne de requête.

Vous commencerez par analyser la chaîne de requête. Le service acceptera les arguments 'lat' et 'longs' sur la chaîne de requête dans ce formulaire :

`http://localhost:5000/?lat=-35.55&long=-12.35`  

Toutes les modifications que vous devez apporter se trouvent dans l’expression lambda définie comme argument de `app.Run` dans votre classe de démarrage.

L’argument de l’expression lambda est le `HttpContext` pour la demande. Une de ses propriétés est l’objet `Request`. L’objet `Request` a une propriété `Query` qui contient un dictionnaire de toutes les valeurs dans la chaîne de requête pour la demande. La première addition consiste à rechercher les valeurs de latitude et longitude :

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString " lit les variables à partir de la chaîne de requête")]

Les valeurs du dictionnaire de requêtes sont de type `StringValue`. Ce type peut contenir une collection de chaînes. Pour votre service météo, chaque valeur est une chaîne unique. C’est pourquoi il y a un appel à `FirstOrDefault()` dans le code ci-dessus. 

Ensuite, vous devez convertir les chaînes en valeurs de type double. La méthode que vous allez utiliser pour convertir la chaîne en double est `double.TryParse()` :

```csharp
bool TryParse(string s, out double result);
```

Cette méthode s’appuie sur les paramètres de sortie de C# pour indiquer si la chaîne d’entrée peut être convertie en double. Si la chaîne constitue une représentation valide pour un double, la méthode retourne true et l’argument `result` contient la valeur. Si la chaîne ne représente pas une valeur double valide, la méthode retourne false.

Vous pouvez adapter cette API à l’aide d’une *méthode d’extension* qui renvoie un *double Nullable*. Un *type de valeur Nullable* est un type qui représente un type de valeur et peut également contenir un une valeur manquante ou Null. Un type Nullable est représenté en ajoutant le caractère `?` à la déclaration de type. 

Les méthodes d’extension sont des méthodes qui sont définies comme des méthodes statiques mais qui, en ajoutant le modificateur `this` sur le premier paramètre, peuvent être appelées comme si elles étaient des membres de cette classe. Les méthodes d’extension peuvent être définies uniquement dans les classes statiques. Voici la définition de la classe contenant la méthode d’extension pour l’analyse :

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "Essayer d’analyser une valeur Nullable")]

L’expression `default(double?)` retourne la valeur par défaut pour le type `double?`. Cette valeur par défaut est la valeur null (ou manquante).

Vous pouvez utiliser cette méthode d’extension pour convertir les arguments de chaîne de requête en type double :

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Utiliser la méthode d’extension TryParse")]

Pour tester facilement le code d’analyse, mettez à jour la réponse pour inclure les valeurs des arguments :

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Écrire la réponse de sortie")]

À ce stade, vous pouvez exécuter l’application web et voir si votre code d’analyse fonctionne. Ajoutez des valeurs à la requête web dans un navigateur, et vous devriez voir les résultats de la mise à jour.

<a id="build-a-random-weather-forecast" class="xliff"></a>

### Générer des prévisions météorologiques aléatoires

La tâche suivante consiste à créer des prévisions météorologiques aléatoires. Commençons avec un conteneur de données qui contient les valeurs que vous souhaiteriez pour les prévisions météorologiques :

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions = new string[]
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HiTemperature { get; }
    public int LoTemperature { get; }
    public int AverageWindSpeed { get; }
    public string Conditions { get; }
}
```

Ensuite, générez un constructeur qui définit de façon aléatoire ces valeurs. Ce constructeur utilise les valeurs de latitude et de longitude pour amorcer le générateur de nombres aléatoires. Cela signifie que la prévision pour un même emplacement est la même. Si vous modifiez les arguments pour la latitude et la longitude, vous obtiendrez une prévision différente (parce que vous démarrez avec une valeur initiale différente.)

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Constructeur de rapport météorologique")]

Vous pouvez maintenant générer des prévisions sur 5 jours dans votre méthode de réponse :

[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Générer un bulletin météorologique aléatoire")]

<a id="build-the-json-response" class="xliff"></a>

### Générez la réponse JSON.

La tâche de code final sur le serveur consiste à convertir le tableau WeatherReport en un paquet JSON, et de renvoyer cela au client. Commençons par créer le paquet JSON. Vous allez ajouter le sérialiseur JSON NewtonSoft à la liste des dépendances. Pour ce faire, utilisez l’interface CLI `dotnet` :

```
dotnet add package Newtonsoft.Json
```

Ensuite, vous pouvez utiliser la classe `JsonConvert` pour écrire l’objet dans une chaîne :

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convertir les objets en JSON")]

Le code ci-dessus convertit l’objet de prévision (une liste d’objets `WeatherForecast`) en un paquet JSON. Une fois que vous avez construit le paquet de réponse, vous définissez le type de contenu `application/json` et écrivez la chaîne.

Maintenant, l’application s’exécute et renvoie des prévisions aléatoires.

<a id="build-a-docker-image" class="xliff"></a>

## Créer une image Docker

La dernière tâche consiste à exécuter l’application dans Docker. Nous allons créer un conteneur Docker qui exécute une image Docker qui représente l’application.

Une ***image Docker*** est un fichier qui définit l’environnement d’exécution de l’application.

Un ***conteneur Docker*** représente une instance en cours d’exécution d’une image Docker.

Par analogie, vous pouvez considérer *l’Image Docker* comme une *classe* et le *conteneur Docker* comme un objet ou une instance de cette classe.  

Le fichier Dockerfile créé par le modèle asp.net prend en charge nos besoins. Attardons-nous sur son contenu.

La première ligne indique l’image source :

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

Docker vous permet de configurer une image d’ordinateur basée sur un modèle source. Cela signifie que vous n’êtes pas obligé de fournir tous les paramètres de la machine lorsque vous démarrez. Il vous suffit de fournir les modifications éventuelles. Les modifications apportées ici serviront à inclure notre application.

Dans ce premier exemple, nous allons utiliser la version `1.1-sdk-msbuild` de l’image dotnet. Il s’agit du moyen le plus simple de créer un environnement Docker. Cette image inclut le composant d’exécution principal dotnet et le kit de développement logiciel dotnet. Cela facilite la mise en route et la création, mais génère aussi une image plus grande.

Les cinq lignes suivantes configurent et génèrent votre application :

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroservice.csproj .
RUN dotnet restore

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

Cela copie le fichier de projet à partir du répertoire actuel sur la machine virtuelle Docker et restaure tous les packages. L’utilisation de l’interface de ligne de commande dotnet signifie que l’image Docker doit inclure le kit de développement logiciel .NET Core. Après cela, le reste de votre application est copié et le la commande dotnet publish génère et crée un package de votre application.

La dernière ligne du fichier exécute l’application :

```
ENTRYPOINT ["dotnet", "out/WeatherMicroservice.dll", "--server.urls", "http://0.0.0.0:5000"]
```

Ce port configuré est référencé dans l’argument `--server.urls` sur `dotnet` sur la dernière ligne du fichier Docker. La commande `ENTRYPOINT` informe Docker des options de commande et de la ligne de commande qui démarrent le service. 

<a id="building-and-running-the-image-in-a-container" class="xliff"></a>

## Génération et exécution de l’image dans un conteneur.

Nous allons créer une image et exécuter le service à l’intérieur d’un conteneur Docker. Nous ne voulons pas que tous les fichiers de votre répertoire local soient copiés dans l’image. Au lieu de cela, nous allons développer l’application dans le conteneur. Vous allez créer un fichier `.dockerignore` pour spécifier les répertoires qui ne sont pas copiés dans l’image. Nous ne souhaitons copier aucune des ressources build. Spécifiez les répertoires build et publish dans le fichier `.dockerignore` :

```
bin/*
obj/*
out/*
```

Vous générez l’image avec la commande docker build. Exécutez la commande suivante à partir du répertoire qui contient votre code.

```console
docker build -t weather-microservice .
```

Cette commande génère l’image de conteneur sur la base de toutes les informations de votre fichier Docker. L’argument `-t` fournit une balise ou un nom pour cette image de conteneur. Dans la ligne de commande ci-dessus, la balise utilisée pour le conteneur Docker est `weather-microservice`. Lorsque cette commande est terminée, vous disposez d’un conteneur prêt à exécuter votre nouveau service. 

Exécutez la commande suivante pour démarrer le conteneur et lancer votre service :

```console
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

L’option `-d` consiste à exécuter le conteneur de façon détachée du terminal actuel. Cela signifie que vous ne verrez pas le résultat de la commande dans votre terminal. L’option `-p` indique le mappage de port entre le service et la machine hôte. Ici, elle indique que toute requête entrante sur le port 80 doit être transférée vers le port 5000 sur le conteneur. 5000 correspond au port sur lequel votre service écoute venant des arguments de ligne de commande spécifiés dans le fichier Docker ci-dessus. L’argument `--name` nomme votre conteneur en cours d’exécution. Il s’agit d’un nom convivial que vous pouvez utiliser pour travailler avec ce conteneur. 

Vous pouvez voir si l’image est en cours d’exécution avec la commande :

```console
docker ps
```

Si votre conteneur est en cours d’exécution, vous verrez une ligne qui répertorie les processus en cours d’exécution. (Il peut s’agir de la seule).

Vous pouvez tester votre service en ouvrant un navigateur et en accédant à localhost et en spécifiant une latitude et une longitude :

```
http://localhost/?lat=35.5&long=40.75
```

<a id="attaching-to-a-running-container" class="xliff"></a>

## Attachement à un conteneur en cours d’exécution

Lorsque vous avez exécuté votre service dans une fenêtre de commande, vous pouvez voir les informations de diagnostic imprimées pour chaque demande. Ces informations ne s’affichent pas lorsque votre conteneur s’exécute en mode détaché. La commande attach de Docker vous permet de vous attacher à un conteneur en cours d’exécution afin de voir les informations du journal.  Exécutez cette commande à partir d’une fenêtre de commande :

```console
docker attach --sig-proxy=false hello-docker
```

L’argument `--sig-proxy=false` signifie que les commandes `Ctrl-C` ne sont pas envoyées au processus de conteneur, mais arrêtent plutôt la commande `docker attach`. Le dernier argument est le nom donné au conteneur dans la commande `docker run`. 

> [!NOTE]
> Vous pouvez également utiliser l’ID de conteneur affecté au Docker pour faire référence à n’importe quel conteneur. Si vous n’avez pas spécifié de nom pour votre conteneur dans `docker run`, vous devez utiliser l’ID de conteneur.

Ouvrez un navigateur et accédez à votre service. Vous verrez les messages de diagnostic dans la fenêtre de commande à partir du conteneur en cours d’exécution attaché.

Appuyez sur `Ctrl-C` pour arrêter le processus d’attachement.

Lorsque vous avez terminé de manipuler votre conteneur, vous pouvez l’arrêter :

```console
docker stop hello-docker
```

Le conteneur et l’image sont toujours disponibles pour vous permettre de redémarrer.  Si vous souhaitez supprimer le conteneur de votre machine, utilisez cette commande :

```console
docker rm hello-docker
```

Si vous souhaitez supprimer des images inutilisées dans votre machine, utilisez cette commande :

```console
docker rmi weather-microservice
```

<a id="conclusion" class="xliff"></a>

## Conclusion 

Dans ce didacticiel, vous avez généré un microservice de base ASP.NET et ajouté quelques fonctionnalités simples.

Vous avez construit une image de conteneur Docker pour ce service et exécuté ce conteneur sur votre machine. Vous avez attaché une fenêtre de terminal au service et vu les messages de diagnostic à partir de votre service.

En chemin, vous avez vu plusieurs fonctionnalités du langage C# en action.

