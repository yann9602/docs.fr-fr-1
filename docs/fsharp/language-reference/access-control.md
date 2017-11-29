---
title: "Contrôle d'accès (F#)"
description: "Découvrez comment contrôler l’accès aux éléments de programmation, tels que les types, méthodes et fonctions, dans le langage de programmation F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 955b06fe-d1cd-431d-8db6-93e83b697453
ms.openlocfilehash: a02e20a585a0456577901f2762a0eeb0e3ecd2f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="access-control"></a>Contrôle d'accès

*Contrôle d’accès* fait référence à la déclaration de clients qui peuvent utiliser certains éléments de programme, telles que les types, méthodes et fonctions.


## <a name="basics-of-access-control"></a>Principes de base du contrôle d’accès
En F #, les spécificateurs de contrôle de l’accès `public`, `internal`, et `private` peut être appliqué à des modules, des types, des méthodes, des définitions de valeur, des fonctions, des propriétés et des champs explicites.


- `public`Indique que l’entité est accessible par tous les appelants.

- `internal`Indique que l’entité est accessible uniquement à partir du même assembly.

- `private`Indique que l’entité est accessible uniquement à partir de type ou le module englobant.


>[!NOTE] 
Le spécificateur d’accès `protected` n’est pas utilisé en F #, bien qu’il soit acceptable si vous utilisez des types créés dans les langages qui prennent en charge `protected` accès. Par conséquent, si vous substituez une méthode protégée, votre méthode reste accessible uniquement au sein de la classe et ses descendants.

En général, le spécificateur est placé devant le nom de l’entité, sauf lorsqu’un `mutable` ou `inline` spécificateur est utilisé, qui apparaît après le spécificateur de contrôle d’accès.

Si aucun spécificateur d’accès n’est utilisé, la valeur par défaut est `public`, à l’exception de `let` liaisons dans un type, qui sont toujours `private` au type.

En F #, les signatures constituent un autre mécanisme pour contrôler l’accès aux éléments de programme F #. Les signatures ne sont pas requises pour le contrôle d’accès. Pour plus d’informations, consultez [Signatures](signatures.md).


## <a name="rules-for-access-control"></a>Règles de contrôle d’accès
Contrôle d’accès est soumis aux règles suivantes :


- Les déclarations d’héritage (autrement dit, l’utilisation de `inherit` pour spécifier une classe de base pour une classe), déclarations d’interface (c'est-à-dire spécifier qu’une classe implémente une interface) et d’abstraire les membres ont toujours la même accessibilité que le type englobant. Par conséquent, un spécificateur de contrôle d’accès ne peut pas être utilisé sur ces constructions.

- Les cas individuels dans une union discriminée ne peuvent pas avoir leurs propres modificateurs de contrôle d’accès distinctes du type d’union.

- Les champs individuels d’un type d’enregistrement ne peut pas avoir leurs propres modificateurs de contrôle d’accès distinctes à partir du type d’enregistrement.


## <a name="example"></a>Exemple
Le code suivant illustre l’utilisation de spécificateurs de contrôle d’accès. Il existe deux fichiers dans le projet, `Module1.fs` et `Module2.fs`. Chaque fichier est implicitement un module. Par conséquent, il y a deux modules `Module1` et `Module2`. Un type privé et un type interne sont définis dans `Module1`. Le type privé ne sont pas accessibles à partir de `Module2`, mais le type interne.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]
    
Le code suivant teste l’accessibilité des types créés dans `Module1.fs`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]
    
## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](index.md)

[Signatures](signatures.md)
