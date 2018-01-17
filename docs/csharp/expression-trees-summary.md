---
title: "Récapitulatif concernant les arborescences d’expressions"
description: "Récapitule la façon dont vous pouvez utiliser des arborescences d’expressions pour créer des programmes dynamiques qui interprètent du code en tant que données et génèrent de nouvelles fonctionnalités en fonction de ce code."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: d2754493c782c2550a8b0bd0de274cb8100c78af
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="expression-trees-summary"></a>Récapitulatif concernant les arborescences d’expressions

[Précédent -- Traduction d’expressions](expression-trees-translating.md)

Dans cette série, vous avez vu comment utiliser des *arborescences d’expressions* pour créer des programmes dynamiques qui interprètent du code en tant que données et génèrent de nouvelles fonctionnalités en fonction de ce code.

Vous pouvez examiner des arborescences d’expressions pour comprendre l’intention d’un algorithme. Vous pouvez non seulement examiner ce code, mais aussi créer de nouvelles arborescences d’expressions qui représentent des versions modifiées du code d’origine.

Vous pouvez également utiliser des arborescences d’expressions pour examiner un algorithme, et traduire celui-ci dans un autre langage ou environnement. 

## <a name="limitations"></a>Limitations

Certains éléments de langage C# récents ne se traduisent pas correctement en arborescences d’expressions. Les arborescences d’expressions ne peuvent pas contenir d’expressions `await` ou d’expressions lambda `async`. La plupart des fonctionnalités ajoutées dans la version 6 de C# n’apparaissent pas exactement telles qu’écrites dans les arborescences d’expressions. Au lieu de cela, les nouvelles fonctionnalités sont exposées dans les arborescences d’expressions dans la syntaxe antérieure équivalente. Cette limitation n’est peut-être pas aussi importante que vous pourriez le penser. En fait, elle signifie que votre code qui interprète des arborescences d’expressions continuera probablement de fonctionner de la même manière lors de l’introduction de nouvelles fonctionnalités de langage.

Même avec ces limitations, les arborescences d’expressions vous permettent de créer des algorithmes dynamiques qui reposent sur l’interprétation et la modification de code représenté sous la forme d’une structure de données. C’est un outil puissant et l’une des fonctionnalités de l’écosystème .NET qui permet aux bibliothèques enrichies telles qu’Entity Framework d’accomplir leur travail.

