---
title: "Types (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
caps.latest.revision: 13
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
ms.openlocfilehash: 2816a5dd86e71641198a340b3a72094dffc93bdf
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="types-c-reference"></a>Types (référence C#)
Le système de types C# comporte les catégories suivantes :  
  
-   [Types valeur](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [Types référence](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 Les variables de types valeur stockent des données alors que les variables de types référence stockent les références aux données réelles. Les types référence sont également considérés comme des objets. Les types pointeur ne peuvent être utilisés qu’en mode [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
 Il est possible de convertir un type valeur en type référence, puis de revenir en type valeur, en effectuant une conversion [boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md). Vous ne pouvez pas convertir un type référence en type valeur, sauf s’il s’agit d’un type valeur boxed.  
  
 Cette section présente également [void](../../../csharp/language-reference/keywords/void.md).  
  
 Les types valeur sont également Nullable, ce qui signifie qu’ils peuvent stocker un état de non-valeur supplémentaire. Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Tableaux de référence des types](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [Types](../../../csharp/programming-guide/types/index.md)

