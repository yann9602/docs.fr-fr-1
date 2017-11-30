---
title: "Types imbriqués (guide de programmation C#)"
ms.date: 07/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab13c68b638062ab89c90dbfc51b51b8d72d3bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types-c-programming-guide"></a>Types imbriqués (guide de programmation C#)
Un type défini dans une [classe](../../../csharp/language-reference/keywords/class.md) ou un [struct](../../../csharp/language-reference/keywords/struct.md) s’appelle un type imbriqué. Exemple :  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
Que le type externe soit une classe ou un struct, les types imbriqués sont par défaut [private](../../../csharp/language-reference/keywords/private.md) ; ils sont accessibles uniquement à partir de leur type conteneur. Dans l’exemple précédent, la classe `Nested` est inaccessible aux types externes. 

Vous pouvez aussi spécifier un [modificateur d’accès](../../language-reference/keywords/access-modifiers.md) pour définir l’accessibilité d’un type imbriqué, comme ceci :

- Imbriqués de types d’un **classe** peut être [public](../../../csharp/language-reference/keywords/public.md), [protégé](../../../csharp/language-reference/keywords/protected.md), [interne](../../../csharp/language-reference/keywords/internal.md), [protégé interne](../../../csharp/language-reference/keywords/protected-internal.md), [privé](../../../csharp/language-reference/keywords/private.md) ou [protégé privé](../../../csharp/language-reference/keywords/private-protected.md). 

   Toutefois, en définissant un `protected`, `protected internal` ou `private protected` imbriqués de classe à l’intérieur un [sealed classe](../../language-reference/keywords/sealed.md) génère l’avertissement du compilateur [CS0628](../../misc/cs0628.md), « nouveau membre protected déclaré dans une classe sealed. »
  
- Les types imbriqués d’un **struct** peuvent être [public](../../../csharp/language-reference/keywords/public.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou [private](../../../csharp/language-reference/keywords/private.md).
  
L’exemple suivant fait passer le type de la classe `Nested` à public :
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 Le type imbriqué (ou interne) peut accéder au type conteneur (ou externe). Pour accéder au type conteneur, passez-le en tant qu’argument au constructeur du type imbriqué. Exemple :  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 Un type imbriqué a accès à tous les membres qui sont accessibles à son type conteneur. Il peut accéder aux membres privés et protégés du type conteneur, y compris à tous les membres protégés hérités.  
  
 Dans la déclaration précédente, le nom complet de classe `Nested` est `Container.Nested`. Il s'agit du nom utilisé pour créer une instance de la classe imbriquée, comme suit :  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)
