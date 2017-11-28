---
title: Empaquetage de la distribution de .NET Core
description: "Découvrez comment empaqueter, nommer et versionner .NET Core pour la distribution."
keywords: .NET, .NET Core, source, build
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 71b9d722-c5a8-4271-9ce1-d87e7ae2494d
ms.openlocfilehash: 7ff5ed127ad0d4f435c697a8f35b33c7ba3b56ff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="net-core-distribution-packaging"></a>Empaquetage de la distribution de .NET Core

.NET Core est disponible sur de plus en plus de plateformes ; il est donc utile de savoir comment l’empaqueter, le nommer et le versionner. De cette manière, les chargés de maintenance des packages pourront garantir une expérience cohérente quelle que soit la plateforme choisie par les utilisateurs pour exécuter .NET.

## <a name="net-core-components"></a>Composants de .NET Core

.NET Core est constitué de trois parties principales qui doivent être empaquetées :

1. **L’hôte** (également appelé « muxer ») a deux rôles distincts : activer un runtime, afin de lancer une application, et un Kit de développement logiciel (SDK), pour y répartir les commandes. L’hôte est constitué d’un exécutable natif (`dotnet.exe`) et des bibliothèques de stratégies associées (installées dans `host/fxr`). Il est généré à partir du code du référentiel [`dotnet/core-setup`](https://github.com/dotnet/core-setup/). Il n’y a généralement qu’un seul hôte sur un même ordinateur, même s’il ne s’agit pas d’une exigence stricte.
2. **L’infrastructure** est constituée d’un runtime et des bibliothèques gérées associées. Elle peut être installée au sein d’une application, ou sous forme d’infrastructure partagée, située à un emplacement central et réutilisable par plusieurs applications. Il peut y avoir un nombre illimité d’infrastructures partagées installées sur un même ordinateur. Les infrastructures partagées se trouvent sous `shared/Microsoft.NETCore.App/<version>`. L’hôte est restauré par progression d’une version corrective à l’autre. Si une application cible `Microsoft.NETCore.App` 1.0.0 et que seule la version 1.0.4 est présente, l’application est lancée sur cette dernière version.
3. **Le Kit de développement logiciel (SDK)** (également appelé « outils ») est un ensemble d’outils gérés servant à écrire et à générer des applications et des bibliothèques .NET Core. Il inclut l’interface de ligne de commande, MSBuild et les cibles et tâches de génération associées, NuGet, de nouveaux modèles de projet, etc. Il est possible d’avoir plusieurs Kits SDK sur un ordinateur (par exemple, pour générer des projets qui exigent explicitement une version antérieure), mais il est recommandé d’utiliser la dernière version des outils.

## <a name="recommended-package-names"></a>Noms de packages recommandés

L’aide suivante décrit nos recommandations pour les noms de packages. Le chargé de maintenance des packages peut choisir de s’en écarter pour diverses raisons, par exemple, en cas de tradition différente de la distribution spécifiquement ciblée.

### <a name="minimum-package-set"></a>Ensemble minimal du package

* `dotnet-runtime-[major].[minor]` : infrastructure partagée avec la version spécifiée (seule la dernière version corrective pour une combinaison majeure + mineure doit être disponible dans le Gestionnaire de package). **dépendances** : `dotnet-host`
* `dotnet-sdk` : dernière version du Kit SDK. **dépendances** : dernière version de `dotnet-sdk-[major].[minor]`.
* `dotnet-sdk-[major].[minor]` : Kit SDK avec la version spécifiée. La version spécifiée est la version la plus élevée incluse des infrastructures partagées incluses, afin que les utilisateurs puissent facilement associer un Kit SDK à une infrastructure partagée. **dépendances** : `dotnet-host`, une ou plusieurs versions `dotnet-runtime-[major].[minor]` (l’un des runtimes est utilisé par le code du Kit de développement logiciel (SDK) proprement dit, les autres servent aux utilisateurs à des fins de génération et d’exécution).
* `dotnet-host` : dernière version de l’hôte.

#### <a name="preview-versions"></a>Préversions

Les chargés de maintenance des packages peuvent décider d’inclure les préversions de l’infrastructure partagée et du Kit SDK. Elles ne doivent jamais être incluses dans le package `dotnet-sdk` non versionné, mais elles peuvent être publiées en tant que packages versionnés avec un marqueur de préversion supplémentaire ajouté aux sections du nom correspondant à la version majeure et à la version mineure. Par exemple, il peut y avoir un package `dotnet-sdk-2.0-preview-final`.

### <a name="optional-additional-packages"></a>Packages supplémentaires facultatifs

Certains chargés de maintenance peuvent choisir de fournir des packages supplémentaires, notamment :

* `dotnet-lts` : la dernière version avec prise en charge à long terme (LTS) de l’infrastructure partagée. Les [ensembles de versions LTS et « version actuelle »](~/docs/core/versions/lts-current.md) correspondent à différentes cadences de lancement de .NET Core. Les utilisateurs ont la possibilité d’adopter l’ensemble qu’ils souhaitent, selon la fréquence souhaitée de mise à jour. Ce concept étant également lié aux niveaux de prise en charge, il est plus ou moins pertinent en fonction de la distribution concernée.

## <a name="disk-layout"></a>Disposition du disque

Lors de l’installation de packages .NET Core, le positionnement relatif de leur destination cible sur le disque a de l’importance.
L’hôte `dotnet.exe` doit être placé à côté des dossiers `sdk` et `shared` qui contiennent le contenu versionné des packages du Kit SDK `dotnet-sdk` et les packages de l’infrastructure partagée `dotnet-runtime`.

La disposition des fichiers et des répertoires sur le disque, à l’intérieur des packages, est versionnée. Cela signifie que la mise à jour vers la dernière version de `dotnet-runtime` installe la nouvelle version côte à côte avec les versions précédentes, ce qui réduit le risque d’arrêt des applications existantes par la mise à jour du package. Normalement, les mises à jour de package ne suppriment pas les versions précédentes.

## <a name="update-policies"></a>Stratégies de mise à jour

Lorsqu’une opération `update` est effectuée, le comportement de chaque package est le suivant :

* `dotnet-runtime-[major].[minor]` : les nouvelles versions correctives mettent à jour le package, mais les nouvelles versions mineures ou majeures sont des packages distincts.
* `dotnet-sdk` : `update` restaure par progression les versions majeures, mineures et correctives.
* `dotnet-sdk-[major].[minor]` : les nouvelles versions correctives mettent à jour le package, mais les nouvelles versions mineures ou majeures sont des packages distincts.
* `dotnet-lts` : `update` restaure par progression les versions majeures, mineures et correctives.

Cette rubrique a présenté nos recommandations pour l’empaquetage de .NET Core. Cependant, chaque distributeur est libre de choisir quelles versions proposer et quand. Par exemple, un distributeur qui attache plus d’importance à la stabilité qu’au fait d’être à jour peut choisir de publier uniquement les versions qui s’alignent sur l’ensemble de versions LTS.