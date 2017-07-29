---
title: "public (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- public
- public_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ae19bf9a33a9860a8960cde5dd4402e10418a094
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="public-c-reference"></a>public (référence C#)
Le mot clé `public` est un modificateur d’accès pour les types et les membres de types. L’accès public est le niveau d’accès le plus permissif. Il n’existe pas de restrictions d’accès aux membres publics, comme dans cet exemple :  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 Pour plus d’informations, consultez [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) et [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md).  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, deux classes sont déclarées, `PointTest` et `MainClass`. L’accès aux membres publics `x` et `y` de `PointTest` s’effectue directement à partir de `MainClass`.  
  
 [!code-cs[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 Si vous remplacez le niveau d’accès `public` par [private](../../../csharp/language-reference/keywords/private.md) ou [protected](../../../csharp/language-reference/keywords/protected.md), le message d’erreur suivant s’affiche :  
  
 'PointTest.y' est inaccessible en raison de son niveau de protection.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)

