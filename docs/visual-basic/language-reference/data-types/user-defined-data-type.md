---
title: "Type de données défini par l'utilisateur"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e1876d61a2ce89b04c6e5061b868f0be365639f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="user-defined-data-type"></a>Type de données défini par l'utilisateur
Contient des données dans un format que vous définissez. La `Structure` instruction définit le format.  
  
 Les versions précédentes de Visual Basic prennent en charge le type défini par l’utilisateur (UDT). La version actuelle développe l’UDT pour un *structure*. Une structure est une concaténation d’une ou plusieurs *membres* de différents types de données. Visual Basic traite une structure comme une unité unique, bien que vous pouvez également accéder à ses membres individuellement.  
  
## <a name="remarks"></a>Remarques  
 Définir et utiliser un type de données de structure lorsque vous devez combiner les différents types de données en une seule unité, ou lorsque aucun des types de données élémentaires répond à vos besoins.  
  
 La valeur par défaut d’un type de données de structure se compose de la combinaison des valeurs par défaut de chacun de ses membres.  
  
## <a name="declaration-format"></a>Format de déclaration  
 Une déclaration de structure démarre avec le [instruction Structure](../../../visual-basic/language-reference/statements/structure-statement.md) et se termine par la `End``Structure` instruction. La `Structure` instruction fournit le nom de la structure, ce qui est également l’identificateur du type de données défini par la structure. Autres parties du code peuvent utiliser cet identificateur pour déclarer des variables, paramètres et fonction de retournent des valeurs de type de données de cette structure.  
  
 Les déclarations entre le `Structure` et `End``Structure` instructions définissent les membres de la structure.  
  
## <a name="member-access-levels"></a>Niveaux d’accès de membre  
 Vous devez déclarer chaque membre à l’aide un [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md) ou une instruction qui spécifie le niveau d’accès, tel que [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), ou [privé](../../../visual-basic/language-reference/modifiers/private.md). Si vous utilisez un `Dim` instruction, les valeurs par défaut au niveau de l’accès public.  
  
## <a name="programming-tips"></a>Conseils de programmation  
  
-   **Consommation de mémoire.** Comme avec tous les types de données composites, vous ne peut pas calculer en toute sécurité la consommation totale de la mémoire d’une structure en additionnant les allocations de stockage nominal de ses membres. En outre, vous ne pouvez pas supposer que l’ordre de stockage en mémoire est le même que l’ordre de déclaration. Si vous avez besoin contrôler la disposition de stockage d’une structure, vous pouvez appliquer la <xref:System.Runtime.InteropServices.StructLayoutAttribute> d’attribut à la `Structure` instruction.  
  
-   **Considérations sur l’interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types définis par l’utilisateur dans d’autres environnements ne sont pas compatibles avec Visual Basic types de structure.  
  
-   **Étendues.** Il n’existe aucune conversion automatique vers ou à partir de n’importe quel type de données de structure. Vous pouvez définir des opérateurs de conversion sur votre structure à l’aide de la [Operator, instruction](../../../visual-basic/language-reference/statements/operator-statement.md), et vous pouvez déclarer chaque opérateur de conversion pour être `Widening` ou `Narrowing`.  
  
-   **Caractères de type.** Types de données de structure n’ont aucun caractère de type littéral ou un caractère de type identificateur.  
  
-   **Type .NET Framework.** Il n’existe pas de type correspondant dans le .NET Framework. Toutes les structures héritent de la classe .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, mais aucune structure individuelle ne correspond à <xref:System.ValueType?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemple  
 Le paradigme suivant montre le plan de la déclaration d’une structure.  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ValueType>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [Types de données](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
