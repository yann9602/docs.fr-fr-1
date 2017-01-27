---
title: Commande dotnet-msbuild | SDK .NET Core
description: "La commande dotnet-msmsbuild fournit l’accès à la ligne de commande MSmsbuild"
keywords: dotnet-msmsbuild, CLI, commande CLI, .NET Core
author: mairaw
manager: wpickett
ms.date: 10/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
translationtype: Human Translation
ms.sourcegitcommit: cde9d9577246a9025d646ce2a6d574a18512146e
ms.openlocfilehash: 51a3afdcf591b8147790d78471c6fee63ceb7f2d

---

#<a name="dotnet-msbuild"></a>dotnet-msbuild

## <a name="name"></a>Nom 
dotnet-msbuild : permet de générer un projet et l’ensemble de ses dépendances 

## <a name="synopsis"></a>Résumé

`dotnet msbuild <msbuild_arguments>`

## <a name="description"></a>Description
La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel 

La commande a les mêmes fonctionnalités que le client de ligne de commande MSBuild existant. Les options sont identiques. Vous pouvez utiliser la [documentation existante](https://msdn.microsoft.com/en-us/library/ms164311.aspx) pour vous familiariser avec la référence des commandes. 

## <a name="examples"></a>Exemples

Générer un projet et ses dépendances :

`dotnet msbuild`

Générer un projet et ses dépendances à l’aide de la configuration Release :

`dotnet msbuild /p:Configuration=Release`

Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`



<!--HONumber=Nov16_HO3-->


