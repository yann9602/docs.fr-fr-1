---
title: "La relation entre les fonctionnalités de langage et les types de bibliothèque | Documents Microsoft"
description: "Fonctionnalités de langage souvent se baser sur les types de bibliothèque pour l’implémentation. Comprendre cette relation."
keywords: "Conception du langage c#, bibliothèque standard"
author: billwagner
ms.author: wiwagn
ms.date: 07/20/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 93fd26a72743fcf45df3904cb8d0c787d8a228a8
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="relationships-between-language-features-and-library-types"></a>Relations entre les fonctionnalités de langage et les types de bibliothèque

La définition du langage c# nécessite une bibliothèque standard pour que certains types et certains membres accessibles sur ces types. Le compilateur génère du code qui utilise ces types requis et des membres pour de nombreuses fonctionnalités de langue différente. Lorsque cela est nécessaire, il existe des packages NuGet qui contiennent les types nécessaires pour les versions plus récentes de la langue lors de l’écriture de code pour les environnements où les types ou les membres n'ont pas encore été déployés.

Cette dépendance sur les fonctionnalités de bibliothèque standard fait partie du langage c# depuis sa première version. Dans cette version, les exemples inclus :

* <xref:System.Exception>-utilisé pour toutes les exceptions générées par le compilateur.
* <xref:System.String>-C# `string` type est un synonyme de <xref:System.String>.
* <xref:System.Int32>-synonyme de `int`.

Cette première version était simple : le compilateur et la bibliothèque standard fournis ensemble, et il n’a qu’une seule version de chaque.

Les versions ultérieures de c# ont parfois ajoutés les nouveaux types ou membres aux dépendances. Exemples : <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> et <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>. C# 7.0 Cela continue en ajoutant une dépendance sur <xref:System.ValueTuple> pour implémenter le [tuples](../tuples.md) fonctionnalité de langage.

L’équipe de conception de langage fonctionne pour réduire la surface d’exposition des types et membres nécessaires dans une bibliothèque standard conforme. Cet objectif est évalué par rapport à une nouvelle conception où les nouvelles fonctionnalités de bibliothèque sont incorporées en toute transparence dans la langue. Il y aura nouvelles fonctionnalités dans les versions ultérieures du langage c# qui nécessitent des nouveaux types et membres dans une bibliothèque standard. Il est important de comprendre comment gérer ces dépendances dans votre travail.

## <a name="managing-your-dependencies"></a>La gestion de vos dépendances

Les outils du compilateur c# sont maintenant découplés du cycle de version des bibliothèques .NET sur les plateformes prises en charge. En fait, les bibliothèques .NET différentes ont des différents cycles de publication : relesed comme une mise à jour de Windows, le .NET Framework sur Windows .NET Core est fourni sur une planification séparée et les versions Xamarin de livraison de mises à jour de bibliothèque avec les outils Xamarin pour chaque plateforme cible.

La plupart du temps, vous ne remarquerez ces modifications. Toutefois, lorsque vous travaillez avec une version plus récente de la langue qui requiert des fonctionnalités non encore dans les bibliothèques .NET sur cette plateforme, vous devez référencer les packages NuGet pour fournir ces nouveaux types.
Comme les plateformes que votre application prend en charge est mis à jour avec les nouvelles installations d’infrastructure, vous pouvez supprimer la référence supplémentaire.

Cette séparation signifie que vous pouvez utiliser les nouvelles fonctionnalités de langage même lorsque vous ciblez des ordinateurs qui ne disposent pas de l’infrastructure correspondante.
