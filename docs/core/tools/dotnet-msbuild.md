---
title: Commande dotnet-msbuild - CLI .NET Core | Microsoft Docs
description: "La commande dotnet-msbuild fournit l’accès à la ligne de commande MSbuild."
keywords: dotnet-msmsbuild, CLI, commande CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 05/24/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
ms.translationtype: Human Translation
ms.sourcegitcommit: df4b2ddd322e4bd2ebaf444439107e88a983f988
ms.openlocfilehash: 2267ef0b5785959456ea443405b6708a423d00ba
ms.contentlocale: fr-fr
ms.lasthandoff: 05/30/2017

---

<a id="dotnet-msbuild" class="xliff"></a>

# dotnet-msbuild

<a id="name" class="xliff"></a>

## Nom

`dotnet-msbuild` : Génère un projet et l’ensemble de ses dépendances.

<a id="synopsis" class="xliff"></a>

## Résumé

`dotnet msbuild <msbuild_arguments> [-h]`

<a id="description" class="xliff"></a>

## Description

La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.

La commande a les mêmes fonctionnalités que le client de ligne de commande MSBuild existant. Les options sont identiques. Utilisez les [Informations de référence sur la ligne de commande MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference) pour obtenir des informations sur les options disponibles. 

<a id="examples" class="xliff"></a>

## Exemples

Générer un projet et ses dépendances :

`dotnet msbuild`

Générer un projet et ses dépendances à l’aide de la configuration Release :

`dotnet msbuild /p:Configuration=Release`

Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

Consultez la totalité du projet avec toutes les cibles incluses par le kit SDK :

`dotnet msbuild /pp`
