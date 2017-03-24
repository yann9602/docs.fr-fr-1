---
title: "Data Type Summary (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Boolean data type, supported types in Visual Basic"
  - "storage, order of storage"
  - "data types [Visual Basic], Visual Basic"
  - "Single data type, supported types in Visual Basic"
  - "notation, scientific"
  - "memory requirements, data types"
  - "user-defined data types, Visual Basic"
  - "Date data type, Visual Basic"
  - "Visual Basic, data types"
  - "storage, allocation"
  - "Integer data type, Visual Basic data types"
  - "storage, space"
  - "Variant data types, supported types in Visual Basic"
  - "Char data type, Visual Basic data types"
  - "intrinsic data types"
  - "memory consumption, data types"
  - "single-precision numbers"
  - "data types [Visual Basic], order of storage"
  - "Long data type, supported types in Visual Basic"
  - "String data type, Visual Basic data types"
  - "storage order, data types"
  - "StructLayoutAttribute class, Visual Basic data type storage"
  - "scientific notation"
  - "Double data type, Visual Basic data types"
  - "Byte data type, Visual Basic data types"
  - "Object data type, supported types in Visual Basic"
  - "data types [Visual Basic], storage allocation"
  - "double-precision numbers"
  - "data types [Visual Basic], summary"
  - "dates [Visual Basic], data types"
  - "strings [Visual Basic], data types"
  - "memory consumption"
  - "storage order, controlling in Visual Basic"
  - "data types [Visual Basic], memory requirements"
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Data Type Summary (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Le tableau suivant illustre les types de données Visual Basic, leurs types Common Language Runtime pris en charge, leur allocation de stockage nominal et leur plage de valeurs.  
  
|Type Visual Basic|Structure de type Common Language Runtime|Allocation de stockage nominal|Plage de valeurs|  
|-----------------------|-----------------------------------------------|------------------------------------|----------------------|  
|[Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|Dépend de la plateforme d'implémentation|`True` ou `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 octet|0 à 255 \(non signé\)|  
|[Char](../../../visual-basic/language-reference/data-types/char-data-type.md) \(caractère unique\)|<xref:System.Char>|2 octets|0 à 65 535 \(non signé\)|  
|[Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 octets|Du 1er janvier 0001 0:00:00 \(minuit\) au 31 décembre 9999 23:59:59|  
|[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 octets|0 à \+\/\-79 228 162 514 264 337 593 543 950 335 \(\+\/\-7,9...E\+28\) <sup>†</sup> sans virgule décimale ; 0 à \+\/\-7,9228162514264337593543950335 avec 28 décimales après la virgule ;<br /><br /> la plus petite valeur différente de zéro est \+\/\-0,0000000000000000000000000001 \(\+\/\-1E\-28\) <sup>†</sup>|  
|[Double](../../../visual-basic/language-reference/data-types/double-data-type.md) \(nombre à virgule flottante double précision\)|<xref:System.Double>|8 octets|\-1,79769313486231570E\+308 à \-4,94065645841246544E\-324 <sup>†</sup> pour les valeurs négatives ;<br /><br /> 4,94065645841246544E\-324 à 1,79769313486231570E\+308 <sup>†</sup> pour les valeurs positives|  
|[Entier](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 octets|\-2 147 483 648 à 2 147 483 647 \(signé\)|  
|[Long](../../../visual-basic/language-reference/data-types/long-data-type.md) \(entier long\)|<xref:System.Int64>|8 octets|\-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807 \(9,2...E\+18 <sup>†</sup>\) \(signé\)|  
|[Objet](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object> \(classe\)|4 octets sur une plateforme 32 bits<br /><br /> 8 octets sur une plateforme 64 bits|N'importe quel type peut être stocké dans une variable de type `Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 octet|\-128 à 127 \(signé\)|  
|[Short](../../../visual-basic/language-reference/data-types/short-data-type.md) \(entier court\)|<xref:System.Int16>|2 octets|\-32 768 à 32 767 \(signé\)|  
|[Single](../../../visual-basic/language-reference/data-types/single-data-type.md) \(nombre à virgule flottante simple précision\)|<xref:System.Single>|4 octets|\-3,4028235E\+38 à \-1,401298E\-45 <sup>†</sup> pour les valeurs négatives ;<br /><br /> 1,401298E\-45 à 3,4028235E\+38 <sup>†</sup> pour les valeurs positives|  
|[String](../../../visual-basic/language-reference/data-types/string-data-type.md) \(longueur variable\)|<xref:System.String> \(classe\)|Dépend de la plateforme d'implémentation|0 à environ 2 milliards de caractères Unicode|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 octets|0 à 4 294 967 295 \(non signé\)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 octets|0 à 18 446 744 073 709 551 615 \(1,8...E\+19 <sup>†</sup>\) \(non signé\)|  
|[User\-Defined](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) \(structure\)|\(hérite de <xref:System.ValueType>\)|Dépend de la plateforme d'implémentation|Chaque membre de la structure présente une plage déterminée par son type de données et qui est indépendante des plages des autres membres|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 octets|0 à 65 535 \(non signé\)|  
  
 <sup>.</sup> Dans *la notation scientifique*, « E » fait référence à une alimentation de 10.  Par conséquent, 3,56E\+2 équivaut à 3.56 x 10<sup>2</sup> ou 356, et 3,56E\-2 équivaut à 3.56 \/ 10<sup>2</sup> ou 0,0356.  
  
> [!NOTE]
>  Pour les chaînes contenant du texte, utilisez la fonction <xref:Microsoft.VisualBasic.Strings.StrConv%2A> pour effectuer une conversion d'un format de texte à un autre.  
  
 En plus de spécifier un type de données dans une instruction de déclaration, vous pouvez forcer le type de données de certains éléments de programmation à l'aide d'un caractère de type.  Consultez [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## Consommation de mémoire  
 Lorsque vous déclarez un type de données élémentaire, il est risqué de supposer que sa consommation de mémoire est identique à son allocation de stockage nominal.  Cela est dû aux considérations suivantes :  
  
-   **Assignation de stockage.** Le Common Language Runtime peut assigner le stockage en fonction des caractéristiques actuelles de la plateforme sur laquelle s'exécute votre application.  Si la mémoire est presque pleine, il se peut qu'il compresse vos éléments déclarés aussi étroitement que possible.  Dans d'autres cas, il se peut qu'il aligne leurs adresses mémoire sur les limites matérielles naturelles pour optimiser les performances.  
  
-   **Largeur de plateforme.** L'assignation de stockage est différente sur une plateforme 64 bits et sur une plateforme 32 bits.  
  
### Types de données composites  
 Les mêmes considérations s'appliquent à chaque membre d'un type de données composite \(par exemple, une structure ou un tableau\).  Il ne suffit pas d'additionner les allocations de stockage nominal des membres du type.  D'autre part, il existe d'autres considérations, telles que les suivantes :  
  
-   **Charge mémoire.** La configuration requise pour la mémoire est plus importante pour certains types composites.  Par exemple, un tableau utilise davantage de mémoire pour le tableau lui\-même, mais également pour chaque dimension.  Sur une plateforme 32 bits, cette charge mémoire est actuellement de 12 octets, auxquels il convient d'ajouter 8 octets pour chaque dimension.  Sur une plateforme 64 bits, cette configuration requise est doublée.  
  
-   **Disposition de stockage.** Il est risqué de supposer que l'ordre de stockage dans la mémoire est le même que l'ordre de vos déclarations.  Vous ne pouvez même pas faire de suppositions au sujet de l'alignement des octets, tels qu'une limite de 2 octets ou de 4 octets.  Si vous définissez une classe ou une structure et que vous devez contrôler la disposition de stockage de ses membres, vous pouvez appliquer l'attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> à la classe ou à la structure.  
  
### Charge mémoire d'un objet  
 Un `Object` faisant référence à un type de données élémentaire ou composite utilise 4 octets en plus des données contenues dans le type de données.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.StrConv%2A>   
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Résumé de la conversion](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)