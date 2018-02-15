---
title: "Processus de développement pour Azure"
description: "Architecture des Applications Web avec ASP.NET Core et Azure | Processus de développement pour Azure"
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 576a717cbdcb8cf465e8cb7b4898df1df7447aa7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="development-process-for-azure"></a>Processus de développement pour Azure

> _« Avec le cloud, particuliers et petites entreprises peuvent aligner leurs doigts et configurer instantanément les services d’entreprise. »_  
> _- Roy Stephan_

 ## <a name="vision"></a>Vision

> *Développer des applications ASP .NET Core bien conçues comme vous le souhaitez, à l’aide de Visual Studio ou l’interface CLI dotnet et Visual Studio Code ou éditeur de votre choix.*

## <a name="development-environment-for-aspnet-core-apps"></a>Environnement de développement pour les applications ASP.NET Core

### <a name="development-tools-choices-ide-or-editor"></a>Choix d’outils de développement : IDE ou éditeur

Si vous préférez un IDE complet et puissant ou un éditeur léger et agile, Microsoft a vous couvert lors du développement d’applications de base de ASP.NET.

**Visual Studio 2017.** Si vous utilisez *Visual Studio 2017* vous pouvez générer ASP.NET Core des applications, que vous avez le *.NET Core le développement multiplateforme* installé la charge de travail. Figure 10-1 indique la charge de travail requis dans la boîte de dialogue de programme d’installation de Visual Studio 2017.

![](./media/image10-1.png)

**Figure 10-1.** Installation de la charge de travail .NET Core dans Visual Studio 2017.

[Télécharger Visual Studio 2017](https://www.visualstudio.com/downloads/)

**Visual Studio Code et dotnet CLI** (les outils multiplateformes pour Mac, Linux et Windows). Si vous préférez un éditeur léger et inter-plateformes prenant en charge de n’importe quel langage de développement, vous pouvez utiliser Microsoft Visual Studio Code et l’interface CLI dotnet. Ces produits fournissent une expérience simple et robuste qui simplifie le flux de travail du développeur. En outre, Visual Studio Code prend en charge des extensions pour C\# et développement web, fournissant intellisense et les tâches de raccourcis dans l’éditeur.

[Télécharger le Kit de développement logiciel de .NET Core](https://www.microsoft.com/net/download/core)

[Télécharger Visual Studio Code](https://code.visualstudio.com/download)



## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Flux de travail de développement pour les applications hébergés par Azure ASP.NET Core

Le cycle de vie de développement d’application commence à partir de l’ordinateur de chaque développeur, l’application à l’aide de leur langue par défaut et le tester localement de codage. Les développeurs peuvent choisir leur système de contrôle de source par défaut et peuvent configurer l’intégration continue (CI) et/ou de remise/déploiement continu (CD) à l’aide d’un serveur de builds ou en fonction des fonctionnalités intégrées de Azure.

Pour commencer à développer une application ASP.NET Core à l’aide de l’élément de configuration/CD, vous pouvez utiliser Visual Studio Team Services ou de votre organisation possède de Team Foundation Server (TFS).

### <a name="initial-setup"></a>Programme d’installation initiale

Pour créer un pipeline de mise en production pour votre application, vous devez disposer de votre code d’application dans le contrôle de code source. Configurer un référentiel local et le connecter à un référentiel distant dans un projet d’équipe. Suivez ces instructions :

-   [Partager votre code avec Git et Visual Studio](https://www.visualstudio.com/docs/git/share-your-code-in-git-vs) ou

-   [Partager votre code avec TFVC et Visual Studio](https://www.visualstudio.com/docs/tfvc/share-your-code-in-tfvc-vs)

Créer un Service d’application Azure où vous allez déployer votre application. Créer une application Web en accédant au panneau des Services d’application sur le portail Azure. Cliquez sur + Ajouter, sélectionnez le modèle d’application Web, cliquez sur Créer et fournir un nom et autres détails. L’application web est accessible à partir de {nom}. azurewebsites.net.

![AzureWebApp](./media/image10-2.png)

**Figure 10-2.** Création d’une application Azure App Service Web dans le portail Azure.

Votre processus de génération de l’élément de configuration effectue une génération automatique chaque fois que le nouveau code est validé dans le référentiel de contrôle de code source du projet. Cela vous donne des informations immédiates que le code est généré (et, dans l’idéal, réussit les tests automatisés) et peuvent potentiellement être déployés. Cette version de l’élément de configuration génère un site web artefact de package de déploiement et le publier pour la consommation par votre processus de CD.

[Définir votre processus de génération de l’élément de configuration](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#ci)

Veillez à activer l’intégration continue pour le système sera en file d’attente une build chaque fois qu’une personne de votre équipe valide le nouveau code. La génération de test et vérifier qu’il produit un site web déployer le package comme l’un de ses artefacts.

Lorsqu’une build terminée, votre processus de CD déploie les résultats de la génération de l’élément de configuration à votre application web Azure. Pour configurer cela, vous créez et configurez un *version*, laquelle sera déployez votre service d’application Azure.

[Définir votre processus de mise en production du CD](https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure#cd)

Une fois votre pipeline de l’élément de configuration/CD est configuré, vous pouvez simplement mettre à jour votre application web et les valider sur le contrôle de code source pour les déployer.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Flux de travail pour développer des applications hébergés par Azure ASP.NET Core

Une fois que vous avez configuré votre compte Azure et votre processus de l’élément de configuration/CD, le développement d’applications de Azure hébergé ASP.NET Core est simple. Voici les étapes de base généralement lors de la création d’une application ASP.NET Core, hébergée dans Azure App Service comme une application Web, comme illustré dans la Figure 10-3.

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**Figure 10-3.** Flux de travail pas à pas pour la création d’applications ASP.NET Core et leur hébergement dans Azure

#### <a name="step-1-local-dev-environment-inner-loop"></a>Étape 1. Boucle interne des environnement de développement local

Développement de votre application ASP.NET Core pour le déploiement vers Azure n’est pas différente de développement de votre application dans le cas contraire. Utiliser l’environnement de développement local que vous êtes à l’aise avec, que ce soit Visual Studio 2017 ou l’interface CLI dotnet et Code de Visual Studio ou votre éditeur favori. Vous pouvez écrire du code, exécuter et déboguer vos modifications, exécuter des tests automatisés et rendre les validations locales pour le contrôle de code source jusqu'à ce que vous êtes prêt à transmettre vos modifications à votre référentiel de contrôle de source partagée.

#### <a name="step-2-application-code-repository"></a>Étape 2. Référentiel de Code d’application

Chaque fois que vous êtes prêt à partager votre code avec votre équipe, vous devez orienter vos modifications à partir de votre référentiel local source vers le référentiel de partage de code source de votre équipe. Si vous avez déjà utilisé dans une branche personnalisée, cette étape implique généralement la fusion de votre code partagé à une branche (par exemple au moyen d’un [requête de tirage](https://www.visualstudio.com/docs/git/pull-requests)).

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Étape 3. Serveur de builds : L’intégration continue. Package de build, de Test,

Une nouvelle build est déclenchée sur le serveur de builds chaque fois qu’une nouvelle validation est effectuée dans le référentiel de code d’application partagée. Dans le cadre du processus de l’élément de configuration, cette build doit entièrement compiler l’application et exécuter des tests automatisés pour vérifier que tout fonctionne comme prévu. Le résultat final du processus de l’élément de configuration doit être une version de package de l’application web, prête pour le déploiement.

#### <a name="step-4-build-server-continuous-delivery"></a>Étape 4. Serveur de builds : Livraison continue

Une fois une build comme a réussi, le processus de CD prennent en charge les artefacts de build générés. Cela inclut un site web déployer le package. Le serveur de builds déployez ce package du Service d’applications Azure, en remplaçant tout service existant par celui qui vient d’être créé. En général, cette étape vise un environnement intermédiaire, mais certaines applications déploiement directement à la production via un processus de CD.

#### <a name="step-5-azure-app-service-web-app"></a>Étape 5. Service d’applications Azure. Application Web.

Une fois déployé, l’application ASP.NET Core s’exécute dans le contexte d’une application Azure App Service Web. Cette application Web peut être surveillée et davantage configurés à l’aide du portail Azure.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>Étape 6. Surveillance de la production et de Diagnostics

Pendant l’exécution de l’application Web, vous pouvez surveiller l’intégrité de l’application et collecter des données de comportement d’utilisateur et de diagnostic. Application Insights est inclus dans Visual Studio et offre une instrumentation automatique pour les applications ASP.NET. Il peut vous fournir plus d’informations sur l’utilisation, des exceptions, les demandes, performances et des journaux.

## <a name="references"></a>Références

**Générer et déployer votre application ASP.NET Core vers Azure**  
<https://www.visualstudio.com/docs/build/apps/aspnet/aspnetcore-to-azure>


>[!div class="step-by-step"]
[Précédente] (test-asp-net-core-mvc-apps.md) [suivant] (azure-hosting-recommendations-for-asp-net-web-apps.md)
