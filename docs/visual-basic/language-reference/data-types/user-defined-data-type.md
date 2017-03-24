---
title: "User-Defined Data Type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "UserDefined"
  - "UDT"
  - "vb.UDT"
  - "User-Defined"
  - "vb.UserDefined"
  - "vb.User-Defined"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "user-defined data types, Visual Basic"
  - "user-defined types"
  - "structures, as user-defined data types"
  - "user-defined types, Visual Basic"
  - "user-defined types, structure declaration"
  - "user-defined types, structures in Visual Basic"
  - "user-defined data types, structure declaration"
  - "data types [Visual Basic], assigning"
  - "Structure statement"
  - "data types [Visual Basic], user-defined"
  - "user-defined data types, structures in Visual Basic"
  - "user-defined data types"
  - "types [Visual Basic], user-defined"
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# User-Defined Data Type
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Stocke les données dans un format que vous définissez.  L'instruction `Structure` définit le format.  
  
 Les versions antérieures de Visual Basic prennent en charge le type défini par l'utilisateur \(TDU\).  La version actuelle développe le TDU en une *structure*.  Une structure est une concaténation d'un ou plusieurs *membres* de divers types de données.  Visual Basic traite une structure comme une unité unique, bien que vous puissiez également accéder à ses membres individuellement.  
  
## Notes  
 Définissez et utilisez un type de données de structure lorsque vous devez combiner divers types de données en une unité unique ou lorsque aucun des types de données élémentaires ne correspond à vos besoins.  
  
 La valeur par défaut d'un type de données de structure se compose de la combinaison des valeurs par défaut de chacun de ses membres.  
  
## Format de déclaration  
 Une déclaration de structure démarre avec [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) et se termine par l'instruction `End` `Structure`.  L'instruction `Structure` fournit le nom de la structure, qui représente également l'identificateur du type de données défini par la structure.  D'autres parties du code peuvent utiliser cet identificateur pour déclarer que les variables, paramètres et valeurs de retour des fonctions appartiennent à ce type de données de structure.  
  
 Les déclarations figurant entre les instructions `Structure` et `End` `Structure` définissent les membres de la structure.  
  
## Niveaux d'accès au membre  
 Vous devez déclarer chaque membre à l'aide d'une instruction [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) ou d'une instruction qui spécifie le niveau d'accès, comme [Public](../../../visual-basic/language-reference/modifiers/public.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md)ou [Private](../../../visual-basic/language-reference/modifiers/private.md).  Si vous utilisez une instruction `Dim`, le niveau d'accès prend par défaut la valeur public.  
  
## Conseils de programmation  
  
-   **Consommation de mémoire.** Comme dans le cas de tous les types de données composites, vous ne pouvez pas calculer en toute sécurité la consommation totale de la mémoire d'une structure en additionnant les allocations de stockage nominal de ses membres.  De plus, il est risqué de supposer que l'ordre de stockage dans la mémoire est identique à l'ordre de déclaration.  Si vous devez contrôler la disposition de stockage d'une structure, vous pouvez appliquer l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> à l'instruction `Structure`.  
  
-   **Considérations sur l'interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, tels que des objets Automation ou COM, gardez à l'esprit que les types définis par l'utilisateur dans d'autres environnements ne sont pas compatibles avec les types de structure Visual Basic.  
  
-   **Extension.** Aucune conversion automatique n'est effectuée à partir ou vers un type de données de structure quelconque.  Vous pouvez définir des opérateurs de conversion sur votre structure à l'aide de [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md) et pouvez déclarer chaque opérateur de conversion comme `Widening` ou `Narrowing`.  
  
-   **Caractères de type.** Les types de données de structure n'ont aucun caractère de type de littéral ou caractère de type d'identificateur.  
  
-   **Type Framework.** Il n'y a aucun type correspondant dans le .NET Framework.  Toutes les structures héritent de la classe .NET Framework <xref:System.ValueType?displayProperty=fullName>, mais aucune structure individuelle ne correspond à <xref:System.ValueType?displayProperty=fullName>.  
  
## Exemple  
 Le paradigme suivant montre le plan de la déclaration d'une structure.  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## Voir aussi  
 <xref:System.ValueType>   
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)