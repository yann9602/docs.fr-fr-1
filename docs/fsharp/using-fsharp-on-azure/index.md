---
title: Utilisation de F# dans Azure
description: "Guide à l’aide des services Azure avec F #"
keywords: Azure, cloud, visual f#, f#, programmation fonctionnelle, .NET, .NET Core
author: sylvanc
ms.author: phcart
ms.date: 09/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: FAD4D11E-703A-42D4-9F72-893D9E0F569B
ms.openlocfilehash: 636604b1a0b645f13ac20d7ed85bde9abae3f9f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-f-on-azure"></a>Utilisation de F# dans Azure

F# est un excellent langage pour la programmation dans le cloud. Fréquemment utilisé pour écrire des applications web, des services cloud et des microservices hébergés dans le cloud, il permet aussi de traiter des données scalables.

Vous trouverez dans les sections suivantes des ressources expliquant comment utiliser de nombreux services Azure avec F#.

> [!NOTE]
> Si un service Azure particulier ne figure pas dans cette documentation, consultez la documentation Azure Functions ou .NET pour ce service. Certains services Azure sont indépendants du langage et ne nécessitent aucune documentation spécifique au langage. Ces services ne sont pas listés ici.

## <a name="using-azure-virtual-machines-with-f"></a>À l’aide de Machines virtuelles avec F # #

Azure prend en charge un large éventail de configurations de machine virtuelle. Pour plus d’informations, consultez [Machines virtuelles Linux et Azure](https://azure.microsoft.com/services/virtual-machines/).

Pour installer F# sur une machine virtuelle pour exécution, compilation et/ou création de scripts, consultez [Utilisation de F# sur Linux](http://fsharp.org/use/linux) et [Utilisation de F# sur Windows](http://fsharp.org/use/windows).


## <a name="using-azure-functions-with-f"></a>À l’aide de fonctions Azure avec F # #

[Azure Functions](https://azure.microsoft.com/services/functions/) est une solution qui vous permet d’exécuter facilement de petits blocs de code, ou « fonctions », dans le cloud. Écrivez simplement le code nécessaire pour résoudre le problème qui se pose, sans vous soucier d’une application dans son intégralité ni de l’infrastructure pour l’exécuter. Les fonctions sont connectées à des événements dans le stockage Azure et à d’autres ressources hébergées dans le cloud. Les données sont acheminées aux fonctions F# par le biais d’arguments de fonction. Vous pouvez utiliser le langage de développement de votre choix, Azure se chargeant de la mise à l’échelle en fonction des besoins.

Azure Functions, qui prend en charge F# comme langage de première classe, exécute le code F# de manière efficace, réactive et scalable. Pour obtenir une documentation de référence sur l’utilisation de F# avec Azure Functions, consultez [Informations de référence pour les développeurs F# sur Azure Functions](/azure/azure-functions/functions-reference-fsharp).

Autres ressources relatives à l’utilisation d’Azure Functions et de F# :

* [Montée en puissance des fonctions Azure en F # à l’aide de Suave](http://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)
* [Comment créer une fonction Azure en F #](https://mnie.github.io/2016-09-08-AzureFunctions/)
* [Utilisation du fournisseur de Type Azure avec des fonctions Azure](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>L’utilisation du stockage Azure avec F # #

Stockage Azure est une couche de base de services de stockage pour les applications modernes qui s’appuient sur la durabilité, la disponibilité et la scalabilité afin de répondre aux besoins de leurs clients. En appliquant les techniques décrites dans les articles suivants, vous pouvez faire interagir les programmes F# directement avec les services de stockage Azure.

* [Bien démarrer avec le stockage Blob Azure en F#](blob-storage.md)
* [Bien démarrer avec le stockage Fichier Azure en F#](file-storage.md)
* [Bien démarrer avec le stockage File d’attente Azure en F#](queue-storage.md)
* [Bien démarrer avec le stockage Table Azure en F#](table-storage.md)

Vous pouvez aussi utiliser Stockage Azure conjointement avec Azure Functions en remplaçant les appels d’API explicites par une configuration déclarative. Pour obtenir des exemples d’utilisation de F#, consultez [Déclencheurs et liaisons Azure Functions pour Stockage Azure](/azure/azure-functions/functions-bindings-storage).

## <a name="using-azure-app-service-with-f"></a>À l’aide du Service d’applications Azure avec F # #

[Azure App Service](https://azure.microsoft.com/services/app-service/) est une plateforme cloud qui permet de générer des applications web et mobiles performantes qui se connectent aux données en tout lieu, dans le cloud ou localement.

* [Exemple d’API web Azure F#](https://github.com/fsprojects/azure-webapi-example)
* [Hébergement de F# dans une application web sur Azure](https://github.com/isaacabraham/fsharp-demonstrator)

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a>Utilisation d’Apache Spark avec F# avec Azure HDInsight

[Apache Spark pour Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) est une infrastructure de traitement open source qui exécute des applications d’analytique des données à grande échelle. Azure vous permet de déployer Apache Spark de manière simple et rentable. Développez votre application Spark en F# à l’aide de [Mobius](https://github.com/Microsoft/Mobius), API .NET pour Spark.

* [Implémentation d’applications Spark en F# à l’aide de Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)
* [Exemples d’applications Spark F# à l’aide de Mobius](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)

## <a name="using-azure-documentdb-with-f"></a>À l’aide d’Azure DocumentDB avec F # #

[Azure DocumentDB](https://azure.microsoft.com/services/documentdb/) est un service NoSQL pour les applications hautement disponibles et distribuées globalement.

Vous pouvez utiliser Azure DocumentDB avec F# de deux manières :

1. Soit en créant des fonctions Azure Functions en F# qui réagissent aux changements dans les collections DocumentDB ou qui provoquent de tels changements. Consultez [Déclencheurs Azure Functions pour DocumentDB](/azure/azure-functions/functions-bindings-documentdb).
2. Soit en utilisant le [SDK .NET pour Azure](/azure/documentdb/documentdb-get-started-quickstart). Notez que ces exemples sont en C#.

## <a name="using-azure-event-hubs-with-f"></a>À l’aide de concentrateurs d’événements Azure avec F # #

[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) assure l’ingestion de la télémétrie à l’échelle du cloud à partir de sites web, d’applications et d’appareils.

Vous pouvez utiliser Azure DocumentDB avec F# de deux manières :

1. Soit en créant des fonctions Azure Functions en F# qui sont déclenchées par des événements. Consultez [Déclencheurs Azure Functions pour Event Hubs](/azure/azure-functions/functions-bindings-event-hubs).
2. Soit en utilisant le [SDK .NET pour Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted). Notez que ces exemples sont en C#.

## <a name="using-azure-notification-hubs-with-f"></a>À l’aide de concentrateurs de Notification Azure avec F # #

[Azure Notification Hubs](/azure/notification-hubs/) est une infrastructure Push multiplateforme avec montée en charge qui vous permet d’envoyer des notifications Push de n’importe quel backend (dans le cloud ou localement) vers toute plateforme mobile.

Vous pouvez utiliser Azure Notification Hubs avec F# de deux manières :

1. Soit en créant des fonctions Azure Functions en F# qui envoient les résultats à un hub de notification. Consultez [Déclencheurs de sortie Azure Function pour Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs).
2. Soit en utilisant le [SDK .NET pour Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/). Notez que ces exemples sont en C#.


## <a name="implementing-webhooks-on-azure-with-f"></a>Implémentation de WebHooks sur Azure avec F # #

Un [Webhook](https://en.wikipedia.org/wiki/Webhook) est un rappel déclenché au moyen d’une requête web. Les Webhooks sont utilisés par des sites tels que GitHub pour signaler des événements. 

Vous pouvez implémenter des Webhooks en F# et les héberger sur Azure par le biais d’une [fonction Azure Functions en F# avec une liaison Webhook](/azure/azure-functions/functions-bindings-http-webhook).

## <a name="using-webjobs-with-f"></a>À l’aide des tâches Web avec F # #

Les [Webjobs](/azure/app-service-web/web-sites-create-web-jobs) sont des programmes que vous pouvez exécuter dans votre application web App Service de trois façons : à la demande, en continu ou selon une planification.

[Exemple de Webjob en F# ](https://github.com/andredublin/fsharp-azure-webjob)

## <a name="implementing-timers-on-azure-with-f"></a>Implémentation des minuteries sur Azure avec F # #

Les déclencheurs de minuterie appellent des fonctions selon une planification ou de manière ponctuelle ou périodique.

Vous pouvez implémenter des minuteries en F# et les héberger sur Azure par le biais d’une [fonction Azure Functions en F# avec un déclencheur de minuterie](/azure/azure-functions/functions-bindings-timer).

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>Déploiement et gestion des ressources Azure avec des scripts F# #

Vous pouvez déployer et gérer des machines virtuelles Azure par programmation à partir de scripts F# à l’aide de packages et d’API Microsoft.Azure.Management. Par exemple, consultez [Bien démarrer avec les bibliothèques de gestion pour .NET](https://msdn.microsoft.com/library/dn722415.aspx) et [Utilisation d’Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).

De même, vous pouvez déployer et gérer d’autres ressources Azure à partir de scripts F# à l’aide des mêmes composants. Par exemple, vous pouvez créer des comptes de stockage, déployer Azure Cloud Services, créer des instances d’Azure DocumentDB et gérer Azure Notifcation Hubs par programmation à partir de scripts F#.

Il est généralement inutile d’utiliser des scripts F# pour déployer et gérer des ressources. Par exemple, vous pouvez déployer des ressources Azure directement à partir de descriptions de modèles JSON paramétrables. Consultez [Modèles Azure Resource Manager](/azure/azure-resource-manager/resource-manager-template-best-practices), en particulier les exemples fournis tels que les [modèles de démarrage rapide Azure](https://azure.microsoft.com/documentation/templates/).

## <a name="other-resources"></a>Autres ressources

* [Documentation complète sur tous les services Azure](/azure/)
