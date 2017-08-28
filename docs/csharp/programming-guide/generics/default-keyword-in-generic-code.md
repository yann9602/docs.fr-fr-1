---
title: "Mot clé default dans le code générique (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
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
ms.openlocfilehash: b5f5995b720d377717a5fff8a5e7e6e2196c612c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="default-keyword-in-generic-code-c-programming-guide"></a>Mot clé default dans le code générique (Guide de programmation C#)
Dans les classes et méthodes génériques se pose le problème de savoir comment assigner une valeur par défaut à un type paramétrable T quand vous ne connaissez pas les éléments suivants à l’avance :  
  
-   si T sera un type référence ou un type valeur ;  
  
-   si T est un type valeur, s’il s’agira d’une valeur numérique ou d’un struct.  
  
 Avec une variable t d’un type paramétrable T, l’instruction t = null est valide uniquement si T est un type référence et t = 0 fonctionne seulement pour les types valeur numériques, mais pas pour les structs. La solution est d’utiliser le mot clé `default`, qui retournera la valeur null pour les types référence et zéro pour les types valeur numériques. Pour les structs, il retournera chaque membre du struct initialisé à zéro ou null, selon s’il s’agit de types valeur ou référence. Pour les types valeur Nullable, la valeur par défaut retourne <xref:System.Nullable%601?displayProperty=fullName>, initialisé comme tout struct.  
  
 L’exemple suivant de la classe `GenericList<T>` montre comment utiliser le mot clé `default`. Pour plus d’informations, consultez [Introduction aux génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md).  
  
 [!code-cs[csProgGuideGenerics#41](../../../csharp/programming-guide/generics/codesnippet/CSharp/default-keyword-in-generic-code_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Generic>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Génériques](../../../csharp/programming-guide/generics/index.md)   
 [Méthodes génériques](../../../csharp/programming-guide/generics/generic-methods.md)   
 [Génériques](~/docs/standard/generics/index.md)

