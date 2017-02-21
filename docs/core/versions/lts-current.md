---
title: Support de .NET Core | Microsoft Docs
description: "Découvrir les différents supports d’ensembles de versions (LTS et Actuel) pour .NET Core"
keywords: .NET, .NET Core, lts, actuel, fts, support, ensembles de support, suivis de support, cycle de vie, ensembles de versions
author: kendrahavens
ms.author: mairaw
ms.date: 01/30/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: fedc7025-f320-4cba-957b-ef74885f66de
translationtype: Human Translation
ms.sourcegitcommit: 1ef17b16b85c81a0b96bb1712db3734dc67d801d
ms.openlocfilehash: 582a521e6a30b740465890b6cb8c773061a98ea6

---

# <a name="net-core-support"></a>Support de .NET Core

Il s’agit d’une description générale du support de .NET Core.

## <a name="lts-and-current-release-trains"></a>Ensembles de versions LTS et Actuel

Le support de deux ensembles de versions est un concept couramment utilisé dans l’univers du développement logiciel, en particulier pour les projets open source comme .NET Core. .NET Core présente les supports d’ensembles de versions suivants : [LTS (Long Term Support)](https://en.wikipedia.org/wiki/Long-term_support) et Actuel. Au cours de leur cycle de vie, les versions LTS reçoivent des correctifs pour les problèmes importants et la sécurité afin de maintenir leur stabilité. Quant aux versions actuelles, elles accueillent les nouvelles fonctionnalités et autres correctifs de bogues. Du point de vue du support, ces ensembles de versions disposent des attributs du cycle de vie du support suivants.

Pour les versions LTS
* Support pendant trois ans après la date de disponibilité générale d’une version LTS
* Ou support pendant un an après la disponibilité générale d’une version LTS ultérieure

Pour les versions actuelles
* Support pendant la même plage de trois ans que la version LTS parente
* Support pendant trois mois après la disponibilité générale d’une version actuelle ultérieure
* Et support pendant un an après la disponibilité générale d’une version LTS ultérieure

## <a name="versioning"></a>Gestion de version
Les nouvelles versions LTS sont marquées par une augmentation du numéro de version principale. Les versions actuelles ont le même numéro de version principale que l’ensemble LTS correspondant et sont marquées par une augmentation du numéro de version secondaire. Par exemple, 1.0.3 correspond à la version LTS et 1.1.0 à la version actuelle. Des mises à jour des correctifs de bogues apportées à l’un des ensembles augmentent la version corrective. Pour plus d’informations sur le schéma de version, consultez [Gestion de version .NET Core](index.md).

## <a name="what-causes-updates-in-lts-and-current-trains"></a>Pourquoi les ensembles de versions LTS et actuelles sont-ils mis à jour ?
Pour savoir quelles modifications spécifiques, telles que les correctifs de bogues ou l’ajout d’API, entraînent des mises à jour des numéros de version, consultez la section Arbre de décision dans la [documentation sur la gestion de version](index.md). Il n’existe aucune règle d’or permettant d’identifier les modifications qui passent de la branche actuelle à la branche LTS. En général, les mises à jour de sécurité nécessaires et les correctifs qui résolvent un comportement attendu constituent de bonnes raisons de mettre à jour la branche LTS. Nous envisageons également d’assurer le support des systèmes d’exploitation de développeur Desktop récents sur la branche LTS, même si cela n’est peut-être pas toujours possible. Pour vous tenir informé des API, correctifs et systèmes d’exploitation pris en charge dans une certaine version, n’hésitez pas à parcourir les [notes de publication](https://github.com/dotnet/core/tree/master/release-notes) de celle-ci sur GitHub.

### <a name="further-reading"></a>informations supplémentaires
* [Fiche d’information sur le cycle de vie de support .NET Core](https://www.microsoft.com/net/core/support)
* [Versions et systèmes d’exploitation actuellement pris en charge](https://github.com/dotnet/core/blob/master/roadmap.md)


<!--HONumber=Feb17_HO1-->


