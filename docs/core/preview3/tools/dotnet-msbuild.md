---
title: Commande dotnet-msbuild | Microsoft Docs
description: "La commande dotnet-msbuild fournit l’accès à la ligne de commande MSbuild."
keywords: dotnet-msmsbuild, CLI, commande CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 10/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: 06d4210e5dff97d3e96efff8ae8e84efc27fb7d2
ms.lasthandoff: 01/21/2017

---

#<a name="dotnet-msbuild"></a>dotnet-msbuild

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>Nom 
dotnet-msbuild : Génère un projet et l’ensemble de ses dépendances.

## <a name="synopsis"></a>Résumé

`dotnet msbuild <msbuild_arguments>`

## <a name="description"></a>Description
La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel 

La commande a les mêmes fonctionnalités que le client de ligne de commande MSBuild existant. Les options sont identiques. Vous pouvez utiliser les [Informations de référence sur la ligne de commande MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) pour vous familiariser avec les options. 

## <a name="examples"></a>Exemples

Générer un projet et ses dépendances :

`dotnet msbuild`

Générer un projet et ses dépendances à l’aide de la configuration Release :

`dotnet msbuild /p:Configuration=Release`

Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

