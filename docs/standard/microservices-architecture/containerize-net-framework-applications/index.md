---
title: "Migration d’applications .NET Framework monolithiques héritées vers des conteneurs Windows"
description: "Architecture des microservices .NET pour les applications .NET en conteneur | Migration d’applications .NET Framework monolithiques héritées vers des conteneurs Windows"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c88027156b55829f77357c1fdb1aef01a802b88a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="migrating-legacy-monolithic-net-framework-applications-to-windows-containers"></a>Migration d’applications .NET Framework monolithiques héritées vers des conteneurs Windows

*Vous pouvez utiliser les conteneurs Windows pour améliorer les environnements de développement et de test, ainsi que pour déployer des applications qui reposent sur des technologies .NET Framework héritées comme Web* *Forms. L’utilisation de conteneurs pour des applications héritées est appelée scénario « lift-and-shift ».*

Les sections précédentes de ce guide ont défendu une architecture de microservices où les applications métier sont distribuées entre différents conteneurs, chacun exécutant un petit service ciblé. Cet objectif présente de nombreux avantages. Dans tout nouveau développement, cette approche est fortement recommandée. Les applications d’entreprise critiques en tirent également suffisamment parti pour justifier le coût d’une nouvelle architecture et d’une nouvelle implémentation.

Mais cela n’est pas vrai pour toutes les applications. Cela ne signifie pas que ces applications ne peuvent pas être utilisées dans des scénarios de conteneur.

Dans cette section, nous allons examiner une application pour eShopOnContainers, illustrée par la figure 7-1. Cette application est utilisée par les membres de l’équipe de l’entreprise eShopOnContainers pour afficher et modifier le catalogue de produits.

![](./media/image1.png)

**Figure 7-1**. Application ASP.NET Web Forms (technologie héritée) sur un conteneur Windows

Il s’agit d’une application Web Forms qui permet de parcourir et modifier les entrées du catalogue. La dépendance Web Forms signifie que cette application ne s’exécute pas sur .NET Core sauf si elle est réécrite sans Web Forms et qu’elle utilise plutôt ASP.NET Core MVC. Vous allez voir comment il est possible d’exécuter des applications de ce type dans des conteneurs sans apporter de modifications. Vous allez également voir comment apporter des modifications minimales pour fonctionner en mode hybride où certaines fonctionnalités ont été déplacées dans un microservice distinct, alors que la plupart des autres fonctionnalités restent dans l’application monolithique.

## <a name="benefits-of-containerizing-a-monolithic-application"></a>Avantages de la mise en conteneur d’une application monolithique

L’application Catalog.WebForms est disponible dans le dépôt GitHub eShopOnContainers (<https://github.com/dotnet/eShopOnContainers>). Cette application est une application web autonome qui accède à un magasin de données à haute disponibilité. Même dans ce cas, il existe des avantages à l’exécution de l’application dans un conteneur. Vous créez une image de l’application. À partir de là, chaque déploiement s’exécute dans le même environnement. Chaque conteneur utilise la même version du système d’exploitation, a la même version des dépendances installées, utilise le même framework et est généré en utilisant le même processus. Vous pouvez voir l’application chargée dans Visual Studio 2017 dans la figure 7-2.

![](./media/image2.png)

**Figure 7-2**. Application Web Forms de gestion de catalogue dans Visual Studio 2017

De plus, les développeurs peuvent tous exécuter l’application dans cet environnement cohérent. Les problèmes qui n’apparaissent que dans certaines versions sont immédiatement visibles pour les développeurs, au lieu de faire surface dans un environnement de préproduction ou de production. Les différences entre les environnements de développement parmi l’équipe de développement ont moins d’importance une fois que les applications s’exécutent dans des conteneurs.

Enfin, les applications en conteneur ont une courbe de montée en puissance parallèle (scale out) plus plate. Vous avez découvert comment les applications en conteneur activent d’autres conteneurs dans une machine virtuelle ou d’autres conteneurs dans une machine physique. Cela se traduit par une densité plus élevée et moins de ressources nécessaires.

Pour toutes ces raisons, envisagez d’exécuter des applications monolithiques héritées dans un conteneur Docker à l’aide d’une opération « lift-and-shift ». L’expression « lift-and-shift » décrit l’étendue de la tâche : vous *levez* l’ensemble de l’application à partir d’une machine physique ou virtuelle, puis vous la *déplacez* dans un conteneur. Dans les situations idéales, vous n’avez pas besoin d’apporter des modifications au code d’application pour l’exécuter dans un conteneur.

## <a name="possible-migration-paths"></a>Chemins de migration possibles

Comme une application monolithique, l’application Catalog.Webforms est une application web contenant tout le code, y compris les bibliothèques d’accès aux données. La base de données s’exécute sur une machine distincte à haute disponibilité. Cette configuration est simulée dans l’exemple de code à l’aide d’un service de catalogue fictif : vous pouvez exécuter l’application Catalog.WebForms sur ces données fictives pour simuler un scénario « lift-and-shift » pur. Celui-ci montre le chemin de migration le plus simple, où vous déplacez des ressources existantes pour les exécuter dans un conteneur sans apporter du tout de modifications au code. Ce chemin convient aux applications qui sont terminées et qui ont une interaction minimale avec les fonctionnalités que vous déplacez vers des microservices.

Toutefois, le site web eShopOnContainers accède déjà au stockage des données à l’aide de microservices pour différents scénarios. Certaines petites modifications supplémentaires peuvent être apportées à l’éditeur de catalogue pour exploiter le microservice du catalogue au lieu d’accéder au stockage de données de catalogue directement.

Ces modifications montrent le continuum de vos propres applications. Vous pouvez tout faire depuis le déplacement d’une application existante sans modification vers des conteneurs, jusqu’à l’apport de petites modifications qui permettent aux applications existantes d’accéder à certains des microservices en passant par la réécriture complète d’une application pour participer entièrement à une nouvelle architecture de microservice. Le bon chemin dépend à la fois du coût de la migration et des avantages liés à toute migration.

## <a name="application-tour"></a>Présentation de l’application

Vous pouvez charger la solution Catalog.WebForms et exécuter l’application en tant qu’application autonome. Dans cette configuration, au lieu d’une base de données de stockage permanente, l’application utilise un faux service pour retourner des données. L’application utilise Autofac (<https://autofac.org/>) en tant que conteneur d’inversion de contrôle. À l’aide de l’injection de dépendance, vous pouvez configurer l’application pour utiliser les fausses données ou le service de données de catalogue en direct. (Nous allons expliquer plus précisément l’injection de dépendance sous peu.) Le code de démarrage lit un paramètre useFake dans les fichiers web.config et configure le conteneur Autofac pour injecter soit le faux service de données ou le service de catalogue en direct. Si vous exécutez l’application avec la valeur false pour useFake dans le fichier web.config, vous voyez l’application Web Forms afficher les données de catalogue.

La plupart des techniques utilisées dans cette application sont certainement bien connues des personnes qui ont déjà utilisé Web Forms. Toutefois, le microservice du catalogue introduit deux techniques éventuellement nouvelles : l’injection de dépendance, qui a été mentionnée précédemment et l’utilisation de magasins de données asynchrones dans Web Forms.

L’injection de dépendance inverse la stratégie orientée objet typique d’écriture de classes qui allouent toutes les ressources nécessaires. Au lieu de cela, les classes demandent leurs dépendances à un conteneur de service. L’avantage de l’injection de dépendance est que vous pouvez remplacer des services externes par des faux services (fictifs) pour prendre en charge des environnements de test ou autres.

Le conteneur d’injection de dépendance utilise la configuration appSettings de web.config pour contrôler l’utilisation ou non des fausses données de catalogue ou les données en direct du service en cours d’exécution. L’application enregistre un objet HttpModule qui crée le conteneur et inscrit un gestionnaire de demande préliminaire pour injecter des dépendances. Vous pouvez voir que le code dans le fichier Modules/AutoFacHttpModule.cs, qui ressemble à l’exemple suivant :

```cs
private static IContainer CreateContainer()
{
  // Configure AutoFac:
  // Register Containers:

  var settings = WebConfigurationManager.AppSettings;
  var useFake = settings["usefake"];
  bool fake = useFake == "true";
  var builder = new ContainerBuilder();

  if (fake)
  {
    builder.RegisterType<CatalogMockService>()
    .As<ICatalogService>();
  }
  else
  {
    builder.RegisterType<CatalogService>()
    .As<ICatalogService>();
    builder.RegisterType<RequestProvider>()
    .As<IRequestProvider>();
  }

  var container = builder.Build();
  return container;
}

private void InjectDependencies()
{
  if (HttpContext.Current.CurrentHandler is Page page)
  {
    // Get the code-behind class that we may have written
    var pageType = page.GetType().BaseType;

    // Determine if there is a constructor to inject, and grab it
    var ctor = (from c in pageType.GetConstructors()
                where c.GetParameters().Length > 0
                select c).FirstOrDefault();

    if (ctor != null)
    {
      // Resolve the parameters for the constructor
      var args = (from parm in ctor.GetParameters()
                  select Container.Resolve(parm.ParameterType))
                  .ToArray();

      // Execute the constructor method with the arguments resolved
      ctor.Invoke(page, args);
    }

    // Use the Autofac method to inject any
    // properties that can be filled by Autofac
    Container.InjectProperties(page);
  }
}
```

Les pages de l’application (Default.aspx.cs et EditPage.aspx.cs) définissent des constructeurs qui acceptent ces dépendances. Notez que le constructeur par défaut est toujours présent et accessible. L’infrastructure a besoin du code suivant.

```cs
protected _Default() { }

public _Default(ICatalogService catalog) => this.catalog = catalog;
```

Les API de catalogue sont toutes des méthodes asynchrones. Web Forms les prend désormais en charge pour tous les contrôles de données. L’application Catalog.WebForms utilise la liaison de modèle pour les pages de liste et de modification ; les contrôles inclus dans les pages définissent les propriétés SelectMethod, UpdateMethod, InsertMethod et DeleteMethod qui spécifient des opérations asynchrones retournant des tâches. Les contrôles Web Forms comprennent à quel moment les méthodes liées à un contrôle sont asynchrones. La seule restriction que vous rencontrez lors de l’utilisation de méthodes select asynchrones est que la pagination n’est pas prise en charge. La signature de la pagination nécessite un paramètre de sortie alors que les méthodes asynchrones ne peuvent pas avoir de paramètres de sortie. Cette même technique est utilisée dans d’autres pages qui exigent des données du service de catalogue.

La configuration par défaut de l’application Web Forms de catalogue utilise une implémentation fictive du service catalog.api. Cette implémentation fictive utilise un jeu de données codées en dur pour ses données, ce qui simplifie certaines tâches en supprimant la dépendance vis-à-vis du service catalog.api dans les environnements de développement.

## <a name="lifting-and-shifting"></a>Scénarios « lift-and-shift »

Visual Studio offre une excellent prise en charge de la mise en conteneur d’une application. Vous cliquez avec le bouton droit sur le nœud du projet, puis vous sélectionnez **Ajouter** et **Prise en charge de Docker**. Le modèle de projet Docker ajoute un nouveau projet à la solution appelée **docker-compose**. Le projet contient les composants Docker qui constituent (ou génèrent) les images dont vous avez besoin, puis commence à exécuter les conteneurs nécessaires, comme indiqué dans la figure 7-3.

Dans les scénarios « lift-and-shift »les plus simples, l’application est le seul service que vous utilisez pour l’application Web Forms. Le modèle change également votre projet de démarrage pour pointer vers le projet **docker-compose**. Appuyez maintenant sur Ctrl+F5 ou F5 pour créer l’image Docker et lancer le conteneur Docker.

![](./media/image3.png)

**Figure 7-3**. Projet **docker-compose** dans la solution Web Forms

Avant d’exécuter la solution, vous devez vérifier que vous configurez Docker pour utiliser des conteneurs Windows. Pour ce faire, vous cliquez avec le bouton droit sur l’icône Docker située dans la barre des tâches Windows, puis vous sélectionnez **Basculer vers les conteneurs Windows**, comme illustré dans la figure 7-4.

![](./media/image4.png)

**Figure 7-4**. Basculer vers les conteneurs Windows à partir de l’icône Docker située dans la barre des tâches Windows

Si l’élément de menu indique **Basculer vers les conteneurs Linux**, vous exécutez déjà Docker avec des conteneurs Windows.

L’exécution de la solution redémarre l’hôte Docker. Pendant la génération, vous générez l’application et l’image Docker du projet Web Forms. Cette opération prend beaucoup de temps la première fois. En effet, le processus de génération extrait l’image Windows Server de base et l’image supplémentaire pour ASP.NET. Les cycles de génération et d’exécution suivants sont beaucoup plus rapides.

Jetons un œil sur les fichiers ajoutés par le modèle de projet Docker. Ce dernier a créé plusieurs fichiers pour vous. Visual Studio utilise ces fichiers pour créer l’image Docker et lancer un conteneur. Vous pouvez utiliser les mêmes fichiers à partir de l’interface CLI pour exécuter des commandes Docker manuellement.

L’exemple de Dockerfile suivant montre les paramètres de base pour la génération d’une image Docker basée sur l’image Windows ASP.NET qui exécute un site ASP.NET.

```
FROM microsoft/aspnet

ARG source

WORKDIR /inetpub/wwwroot

COPY ${source:-obj/Docker/publish} .
```

Ce Dockerfile ressemble de près à ceux créés pour l’exécution d’une application ASP.NET Core dans des conteneurs Linux. Toutefois, il existe des différences importantes. La principale différence est que l’image de base est microsoft/aspnet, à savoir l’image Windows Server actuelle qui inclut le .NET Framework. Les autres différences ont trait aux répertoires copiés à partir de votre répertoire source.

Les autres fichiers du projet **docker-compose** correspondent aux composants Docker nécessaires pour générer et configurer les conteneurs. Visual Studio place les divers fichiers docker-compose.yml sous un nœud unique pour mettre en évidence leur mode d’utilisation. Le fichier docker-compose de base contient les directives communes à toutes les configurations. Le fichier docker-compose.override.yml contient des variables d’environnement et les remplacements associés d’une configuration de développeur. Les variantes avec .vs.debug et .vs.release fournissent des paramètres d’environnement qui permettent à Visual Studio de s’attacher au conteneur en cours d’exécution et de le gérer.

Alors que l’intégration de Visual Studio fait partie de l’ajout de la prise en charge de Docker à votre solution, vous pouvez aussi générer et exécuter des commandes à partir de la ligne de commande, en utilisant la commande docker-compose up, comme vous l’avez vu dans les sections précédentes.

## <a name="getting-data-from-the-existing-catalog-net-core-microservice"></a>Obtention de données à partir du microservice .NET Core du catalogue existant

Vous pouvez configurer l’application Web Forms pour qu’elle utilise le microservice du catalogue eShopOnContainers afin d’obtenir des données au lieu d’utiliser des données fictives. Pour cela, vous modifiez le fichier web.config et définissez la valeur de la clé useFake sur false. Le conteneur d’injection de dépendance utilise la classe qui accède au microservice du catalogue en direct au lieu de la classe qui retourne les données codées en dur. Aucune autre modification de code n’est nécessaire.

L’accès au service de catalogue en direct exige la mise à jour du projet **docker-compose** pour créer l’image du service de catalogue et lancer le conteneur du service de catalogue. Docker CE pour Windows prend à la fois en charge les conteneurs Linux et les conteneurs Windows, mais pas en même temps. Pour exécuter le microservice du catalogue, vous devez générer une image qui exécute le microservice du catalogue par-dessus un conteneur basé sur Windows. Cette approche exige un autre Dockerfile pour le projet de microservices que vous avez vu dans les sections précédentes. Le fichier Dockerfile.windows contient les paramètres de configuration requis pour générer l’image de conteneur de l’API de catalogue afin qu’elle s’exécute sur un conteneur Windows, par exemple, pour utiliser une image Docker Windows Nano.

Le microservice du catalogue s’appuie sur la base de données SQL Server. Par conséquent, vous devez aussi utiliser une image Docker SQL Server basée sur Windows.

Après ces modifications, le projet docker-compose fait plus de choses pour démarrer l’application. Le projet démarre maintenant le serveur SQL Server à l’aide de l’image SQL Server basée sur Windows. Il démarre le microservice du catalogue dans un conteneur Windows. Et il démarre également le conteneur de l’éditeur de catalogue Web Forms, également dans un conteneur Windows. Si une des images a besoin d’être générée, les images sont d’abord créées.

## <a name="development-and-production-environments"></a>Environnements de développement et de production

Il existe quelques différences entre la configuration de développement et une configuration de production. Dans l’environnement de développement, vous exécutez l’application Web Forms, le microservice du catalogue et SQL Server dans des conteneurs Windows, dans le cadre du même hôte Docker. Dans les sections précédentes, nous avons mentionné les images SQL Server déployées dans le même hôte Docker que les autres services .NET Core sur un hôte Docker Linux. L’avantage d’exécuter les multiples microservices dans le même hôte (ou cluster) Docker est qu’il y a moins de communication réseau et que la communication entre les conteneurs a une latence plus faible.

Dans l’environnement de développement, vous devez exécuter tous les conteneurs dans le même système d’exploitation. Docker CE pour Windows ne prend pas en charge l’exécution de conteneurs Windows et Linux en même temps. En production, vous pouvez décider si vous souhaitez exécuter le microservice du catalogue dans un conteneur Windows dans un seul hôte (ou cluster) Docker, ou si vous voulez que l’application Web Forms communique avec une instance du microservice du catalogue en cours d’exécution dans un conteneur Linux dans un autre hôte Docker. Cette décision dépend de la façon dont vous voulez optimiser la latence du réseau. Dans la plupart des cas, il est souhaitable que les microservices dont dépendent vos applications s’exécutent dans le même hôte (ou essaim) Docker pour faciliter le déploiement et réduire la latence de communication. Dans ces configurations, les seules communications coûteuses ont lieu entre les instances de microservice et les serveurs à haute disponibilité pour le stockage des données persistantes.

>[!div class="step-by-step"]
[Précédent] (../net-core-single-containers-linux-windows-server-hosts/index.md) [Next] (../multi-container-microservice-net-applications/index.md)
