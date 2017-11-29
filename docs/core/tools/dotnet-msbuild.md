---
title: Commande dotnet msbuild - Interface CLI .NET Core
description: "La commande dotnet msbuild fournit l’accès à la ligne de commande MSbuild."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 96e4eac528abad2b336a979a98c9be2bee5d17ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nom

`dotnet msbuild` : Génère un projet et l’ensemble de ses dépendances.

## <a name="synopsis"></a>Résumé

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>Description

La commande `dotnet msbuild` permet d’accéder à un outil MSBuild entièrement fonctionnel.

La commande a les mêmes fonctionnalités que le client de ligne de commande MSBuild existant. Les options sont identiques. Utilisez les [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) pour obtenir des informations sur les options disponibles. 

## <a name="examples"></a>Exemples

Générer un projet et ses dépendances :

`dotnet msbuild`

Générer un projet et ses dépendances à l’aide de la configuration Release :

`dotnet msbuild /p:Configuration=Release`

Exécuter la cible de publication et effectuer une publication pour le RID `osx.10.11-x64` :

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

Consultez la totalité du projet avec toutes les cibles incluses par le kit SDK :

`dotnet msbuild /pp`
