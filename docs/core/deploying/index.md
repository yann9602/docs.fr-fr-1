---
title: "Déploiement d’applications .NET Core │ Microsoft Docs"
description: "Déploiement d’une application .NET Core."
keywords: ".NET, .NET Core, Déploiement .NET Core"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: da7a31a0-8072-4f23-82aa-8a19184cb701
ms.translationtype: Human Translation
ms.sourcegitcommit: 3ffe3909902659a22cb25bac6dc5aaa4f5b9fde2
ms.openlocfilehash: 31503e39d8a96092dbce03c17397e1adfec6421e
ms.contentlocale: fr-fr
ms.lasthandoff: 05/13/2017

---

# <a name="net-core-application-deployment"></a>Déploiement d’applications .NET Core

Vous pouvez créer deux types de déploiement pour les applications .NET Core :

- Déploiement dépendant du framework. Comme son nom l’indique, un déploiement dépendant du framework s’appuie sur la présence d’une version partagée à l’échelle du système de .NET Core sur le système cible. Comme .NET Core est déjà présent, votre application est également portable entre des installations de .NET Core. Votre application contient seulement son propre code et les dépendances tierces qui sont en dehors des bibliothèques .NET Core. Les déploiements dépendant du framework contiennent des fichiers *.dll* qui peuvent être lancés avec [l’utilitaire dotnet](../tools/dotnet.md) à partir de la ligne de commande. Par exemple, `dotnet app.dll` exécute une application nommée `app`.

- Déploiement autonome. Contrairement à un déploiement dépendant du framework, un déploiement autonome ne s’appuie sur la présence d’aucun composant partagé sur le système cible. Tous les composants, notamment les bibliothèques .NET Core et le runtime .NET Core, sont inclus avec l’application et sont isolées des autres applications .NET Core. Les déploiements autonomes incluent un fichier exécutable (comme *app.exe* sur les plateformes Windows pour une application nommée `app`), qui est une version renommée de l’hôte .NET Core spécifique à la plateforme, et un fichier *.dll* (comme *app.dll*), qui est l’application elle-même.

## <a name="framework-dependent-deployments-fdd"></a>Déploiements dépendant du framework

Pour un déploiement dépendant du framework, vous déployez seulement votre application et les dépendances tierces. Vous ne devez pas déployer .NET Core car votre application utilise la version de .NET Core qui est présente sur le système cible. Il s’agit du modèle de déploiement par défaut pour les applications .NET Core.

### <a name="why-create-a-framework-dependent-deployment"></a>Pourquoi créer un déploiement dépendant du framework ?

Un déploiement dépendant du framework présente plusieurs avantages :

- Vous n’avez pas à définir à l’avance les systèmes d’exploitation cible sur lesquels votre application .NET Core s’exécutera. Comme .NET Core utilise un format de fichier PE commun pour les fichiers exécutables et les bibliothèques quel que soit le système d’exploitation, .NET Core peuvent exécuter votre application quel que soit le système d’exploitation sous-jacent. Pour plus d’informations sur le format de fichier PE, consultez [Format de fichier d’assembly .NET](../../standard/assembly-format.md).

- Votre package de déploiement est de petite taille. Vous déployez seulement votre application et ses dépendances, et non pas .NET Core lui-même.

- Plusieurs applications utilisent la même installation de .NET Core, ce qui réduit l’utilisation de l’espace disque et de la mémoire sur les systèmes hôtes.

Il existe également quelques inconvénients :

- Votre application peut s’exécuter seulement si la version de .NET Core que vous ciblez, ou une version ultérieure, est déjà installée sur le système hôte.

- Il est possible que le runtime et les bibliothèques .NET Core changent sans que vous le sachiez dans les versions futures. Dans de rares cas, ceci peut changer le comportement de votre application.

## <a name="self-contained-deployments-scd"></a>Déploiements autonomes

Pour un déploiement autonome, vous déployez votre application et les dépendances tierces requises, ainsi que la version de .NET Core utilisée pour générer l’application. La création d’un déploiement autonome n’inclut pas les [dépendances natives de .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) sur les différentes plateformes (par exemple OpenSSL sur macOS). Ces services doivent donc être présents avant l’exécution de l’application.

### <a name="why-deploy-a-self-contained-deployment"></a>Pourquoi déployer un déploiement autonome ?

Le déploiement d’un déploiement autonome a deux avantages majeurs :

- Vous avez le contrôle exclusif de la version de .NET Core qui est déployée avec votre application. Vous pouvez vous-même assurer toute la maintenance de .NET Core.

- Vous avez la garantie que le système cible peut exécuter votre application .NET Core puisque vous fournissez la version du .NET Core sur laquelle elle est exécutée.

Elle a également plusieurs inconvénients :

- Comme .NET Core est inclus dans votre package de déploiement, vous devez choisir à l’avance les plateformes cibles pour lesquels vous générez des packages de déploiement.

- La taille de votre package de déploiement est relativement importante car vous devez inclure .NET Core ainsi que votre application et ses dépendances tierces.

- Le déploiement de nombreuses applications .NET Core autonomes sur un système peut consommer une quantité significative d’espace disque car chaque application duplique les fichiers de .NET Core.

## <a name="step-by-step-examples"></a>Exemples étape par étape

Pour obtenir des exemples étape par étape de déploiement d’applications .NET Core avec les outils de l’interface CLI, consultez [Déploiement d’applications .NET Core avec des outils CLI](deploy-with-cli.md). Pour obtenir des exemples étape par étape de déploiement d’applications .NET Core avec Visual Studio, consultez [Déploiement d’applications .NET Core avec Visual Studio](deploy-with-vs.md). Chaque rubrique contient des exemples des déploiements suivants :

- Déploiement dépendant du framework
- Déploiement dépendant du framework avec des dépendances tierces
- Déploiement autonome
- Déploiement autonome avec des dépendances tierces

# <a name="see-also"></a>Voir aussi

[Déploiement d’applications .NET Core avec des outils CLI](deploy-with-cli.md)   
[Déploiement d’applications .NET Core avec Visual Studio](deploy-with-vs.md)   
[Packages, métapackages et frameworks](../packages.md)   
[Catalogue d’identificateurs de runtime (RID) .NET Core](../rid-catalog.md)

