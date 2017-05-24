---
title: Commande dotnet-clean - CLI .NET Core | Microsoft Docs
description: "La commande dotnet-clean nettoie le répertoire actif."
keywords: "dotnet-clean, CLI, commande CLI, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: eff65fa1-bab4-4421-8260-d0a284b690b2
ms.translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: 0bdd8b9ab133ca92e414618412d95d8136d6234a
ms.contentlocale: fr-fr
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-clean"></a>dotnet-clean

## <a name="name"></a>Nom

`dotnet-clean` : Nettoie la sortie d’un projet. 

## <a name="synopsis"></a>Résumé

`dotnet clean [<PROJECT>] [-o|--output] [-f|--framework] [-c|--configuration] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>Description

La commande `dotnet clean` nettoie la sortie de la génération précédente. Comme elle est implémentée en tant que [cible MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-targets), le projet est évalué lorsque la commande est exécutée. Seules les sorties créées lors de la génération sont nettoyées. Les dossiers de sortie intermédiaire (*obj*) et de sortie finale (*bin*) sont tous deux nettoyés.

## <a name="arguments"></a>Arguments

`PROJECT`

Le projet MSBuild à nettoyer. Si vous ne spécifiez pas de fichier projet, MSBuild recherche dans le répertoire de travail actuel un fichier avec une extension se terminant par *proj* et l’utilise.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.

`-o|--output <OUTPUT_DIRECTORY>`

Répertoire dans lequel les sorties générées sont placées. Spécifiez le commutateur `-f|--framework <FRAMEWORK>` avec le commutateur de répertoire de sortie si vous avez spécifié le framework lorsque le projet a été généré.

`-f|--framework <FRAMEWORK>`

Le [framework](../../standard/frameworks.md) spécifié au moment de la génération. Le framework doit être défini dans le [fichier projet](csproj.md). Si vous avez spécifié le framework au moment de la génération, vous devez spécifier le framework lors du nettoyage.

`-c|--configuration <CONFIGURATION>`

Définit la configuration. Si aucune valeur n’est spécifiée, la valeur utilisée par défaut est `Debug`. Cette propriété est uniquement requise lors du nettoyage si vous l’avez spécifiée lors de la génération.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Niveaux autorisés : q[uiet], m[inimal], n[ormal], d[etailed] et diag[nostic].

## <a name="examples"></a>Exemples

Nettoyez une génération par défaut du projet :

`dotnet clean`

Nettoyez un projet généré à l’aide de la configuration Release :

`dotnet clean --configuration Release`

