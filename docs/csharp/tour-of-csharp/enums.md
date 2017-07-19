---
title: "Enums C# - Visite guidée du langage C# | Microsoft Docs"
description: "Découvrir les enums, constantes nommées discrètes en C#"
keywords: .NET, csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 7faba1cc-6ea9-4a19-adb9-0335e4b132e5
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: b317f399fcbb5c1e91976defba3532bf5533b539
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
    
<a id="enums" class="xliff"></a>

# Énumérations

Un ***type enum*** est un type valeur distinct avec un ensemble de constantes nommées. Vous définissez les enums lorsque vous devez définir un type qui peut avoir un ensemble de valeurs discrètes. Ils utilisent un des types entier comme stockage sous-jacent. Ils apportent une signification sémantique aux valeurs discrètes.

L’exemple suivant déclare et utilise un type `enum` nommé `Color` avec trois valeurs de constante, `Red`, `Green` et `Blue`.

[!code-csharp[EnumExample](../../../samples/snippets/csharp/tour/enums/Program.cs#L3-L36)]

Chaque type `enum` a un type intégral appelé ***type sous-jacent*** de type `enum`. Un type `enum` qui ne déclare pas explicitement un type sous-jacent a un type sous-jacent de `int`. Le format de stockage d’un type `enum` et la plage de valeurs possibles du type sont déterminés par son type sous-jacent. L’ensemble de valeurs qu’un type `enum` peut prendre n’est pas limité par ses membres `enum`. En particulier, n’importe quelle valeur du type sous-jacent d’une `enum` peut être castée en type `enum`, et une valeur valide distincte de ce type `enum`.

L’exemple suivant déclare un type `enum` nommé `Alignment` avec un type sous-jacent de `sbyte`.

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L38-L43)]

Comme le montre l’exemple précédent, une déclaration de membre `enum` peut inclure une expression constante qui spécifie la valeur du membre. La valeur de constante pour chaque membre `enum` doit être dans la plage du type sous-jacent de l’ `enum`. Lorsqu’une déclaration de membre `enum` ne spécifie pas explicitement une valeur, le membre reçoit la valeur zéro (s’il est le premier membre dans le type `enum`) ou la valeur du membre `enum` précédent dans le texte plus un.

Les valeurs `Enum` peuvent être converties en valeurs intégrales et inversement à l’aide des casts de type. Exemple :

[!code-csharp[EnumStorage](../../../samples/snippets/csharp/tour/enums/Program.cs#L49-L50)]

La valeur par défaut de n’importe quel type `enum` est la valeur intégrale de zéro convertie en type `enum`. Dans les cas où les variables sont initialisées automatiquement à une valeur par défaut, il s’agit de la valeur donnée aux variables des types `enum`. Afin que la valeur par défaut d’un type `enum` soit disponible, le littéral `0` convertit implicitement en n’importe quel type `enum`. Ce qui suit est donc autorisé.

[!code-csharp[EnumZero](../../../samples/snippets/csharp/tour/enums/Program.cs#L58-L58)]

>[!div class="step-by-step"]
[Précédent](interfaces.md)
[Suivant](delegates.md)

