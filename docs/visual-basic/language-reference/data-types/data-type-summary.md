---
title: "Liste des types de données (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Boolean data type [Visual Basic], supported types in Visual Basic
- storage [Visual Basic], order of storage
- data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], supported types in Visual Basic
- notation [Visual Basic], scientific
- memory requirements, data types
- user-defined data types [Visual Basic], Visual Basic
- Date data type [Visual Basic], Visual Basic
- Visual Basic, data types
- storage [Visual Basic], allocation
- Integer data type [Visual Basic], Visual Basic data types
- storage [Visual Basic], space
- Variant data types [Visual Basic], supported types in Visual Basic
- Char data type [Visual Basic], Visual Basic data types
- intrinsic data types [Visual Basic]
- memory consumption [Visual Basic], data types
- single-precision numbers
- data types [Visual Basic], order of storage
- Long data type [Visual Basic], supported types in Visual Basic
- String data type [Visual Basic], Visual Basic data types
- storage order, data types
- StructLayoutAttribute class, Visual Basic data type storage
- scientific notation
- Double data type [Visual Basic], Visual Basic data types
- Byte data type [Visual Basic], Visual Basic data types
- Object data type [Visual Basic], supported types in Visual Basic
- data types [Visual Basic], storage allocation
- double-precision numbers
- data types [Visual Basic], summary
- dates [Visual Basic], data types
- strings [Visual Basic], data types
- memory consumption
- storage order, controlling in Visual Basic
- data types [Visual Basic], memory requirements
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f69a112718eed7bb7baaff9bdffd110865c21081
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="data-type-summary-visual-basic"></a>Liste des types de données (Visual Basic)
Le tableau suivant montre les types de données Visual Basic, leurs types du common language runtime prise en charge, leur allocation de stockage nominal et leur plage de valeurs.  
  
|Type Visual Basic|Structure de type Common language runtime|Allocation de stockage nominal|Plage de valeurs|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|Dépend de la mise en œuvre de la plateforme|`True` ou `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 octet|0 à 255 (non signé)|  
|[Char](../../../visual-basic/language-reference/data-types/char-data-type.md) (caractère unique)|<xref:System.Char>|2 octets|0 à 65 535 (non signé)|  
|[Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 octets|0:00:00 (minuit) le 1er janvier 0001 à 23:59:59 le 31 décembre 9999|  
|[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 octets|0 à +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9... E + 28) <sup>†</sup> sans aucune virgule décimale ; 0 à +/-7,9228162514264337593543950335 avec 28 chiffres à droite du séparateur décimal ;<br /><br /> plus petit un nombre différent de zéro est +/-0,0000000000000000000000000001 (+/-1E-28) <sup>†</sup>|  
|[Double](../../../visual-basic/language-reference/data-types/double-data-type.md) (à virgule flottante double précision)|<xref:System.Double>|8 octets|-1, 79769313486231570E + 308 à - 4, 94065645841246544E-324 <sup>†</sup> pour les valeurs négatives ;<br /><br /> 4, 94065645841246544E-324 à 1, 79769313486231570E + 308 <sup>†</sup> pour les valeurs positives|  
|[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 octets|2,147,483,648 et 2 147 483 647 (signé)|  
|[Long](../../../visual-basic/language-reference/data-types/long-data-type.md) (entier long)|<xref:System.Int64>|8 octets|-9,223,372,036,854,775,808 à 9,223,372,036,854,775,807 (9.2... E + 18 <sup>†</sup>) (signé)|  
|[Objet](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object>(classe)|4 octets sur une plateforme 32 bits<br /><br /> 8 octets sur une plateforme 64 bits|N’importe quel type peut être stocké dans une variable de type`Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 octet|-128 à 127 (signé)|  
|[Short](../../../visual-basic/language-reference/data-types/short-data-type.md) (entier court)|<xref:System.Int16>|2 octets|-32 768 à 32 767 (signé)|  
|[Seul](../../../visual-basic/language-reference/data-types/single-data-type.md) (à virgule flottante simple précision)|<xref:System.Single>|4 octets|-3,4028235E + 38 à - 1, 401298E-45 <sup>†</sup> pour les valeurs négatives ;<br /><br /> 1, 401298E-45 et 3,4028235E + 38 <sup>†</sup> pour les valeurs positives|  
|[Chaîne](../../../visual-basic/language-reference/data-types/string-data-type.md) (de longueur variable)|<xref:System.String>(classe)|Dépend de la mise en œuvre de la plateforme|0 à environ 2 milliards de caractères Unicode|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 octets|0 à 4 294 967 295 (non signé)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 octets|0 et 18,446,744,073,709,551,615 (1.8... E + 19 <sup>†</sup>) (non signé)|  
|[Défini par l’utilisateur](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) (structure)|(hérite de <xref:System.ValueType>)|Dépend de la mise en œuvre de la plateforme|Chaque membre de la structure a une plage déterminée par son type de données et indépendante des plages des autres membres|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 octets|0 à 65 535 (non signé)|  
  
 <sup>†</sup> Dans *la notation scientifique*, « E » fait référence à une puissance de 10. Par 3.56E + 2 3.56 x 10<sup>2</sup> ou 356 et 3.56E-2 signifie 3.56 / 10<sup>2</sup> ou 0.0356.  
  
> [!NOTE]
>  Pour les chaînes contenant du texte, utilisez la <xref:Microsoft.VisualBasic.Strings.StrConv%2A> fonction convertir à partir d’un format de texte à un autre.  
  
 Outre la spécification d’un type de données dans une instruction de déclaration, vous pouvez forcer le type de données de certains éléments de programmation à l’aide d’un caractère de type. Consultez [caractères de Type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Consommation de mémoire  
 Lorsque vous déclarez un type de données élémentaire, il n’est pas possible de supposer que sa consommation de mémoire est identique à son allocation de stockage nominal. Il s’agit en raison de considérations suivantes :  
  
-   **Affectation de stockage.** Le common language runtime peut assigner le stockage basé sur les caractéristiques actuelles de la plateforme sur laquelle votre application s’exécute. Si la mémoire est presque plein, il peut pack vos éléments déclarés aussi près que possible. Dans d’autres cas, il peut s’aligner leurs adresses mémoire sur les limites matérielles naturelles pour optimiser les performances.  
  
-   **Largeur de la plateforme.** Affectation de stockage sur une plateforme 64 bits est différente de l’affectation sur une plateforme 32 bits.  
  
### <a name="composite-data-types"></a>Types de données composites  
 Les mêmes considérations s’appliquent à chaque membre d’un type de données composite, comme une structure ou un tableau. Vous ne pouvez pas compter simplement additionner les allocations de stockage nominal des membres du type. En outre, il existe d’autres considérations, telles que les éléments suivants :  
  
-   **Coûts.** Certains types composites ont des besoins en mémoire supplémentaires. Par exemple, un tableau utilise davantage de mémoire pour le tableau lui-même, mais également pour chaque dimension. Sur une plateforme 32 bits, cette surcharge est actuellement de 12 octets plus de 8 octets pour chaque dimension. Sur une plateforme 64 bits, cette exigence est doublée.  
  
-   **Disposition de stockage.** Vous ne pouvez pas sans risque supposer que l’ordre de stockage en mémoire est le même que l’ordre de déclaration. Vous ne pouvez pas même hypothèses sur Alignement des octets, par exemple une limite de 2 octets ou 4 octets. Si vous définissez une classe ou une structure et que vous avez besoin de contrôler la disposition de stockage de ses membres, vous pouvez appliquer la <xref:System.Runtime.InteropServices.StructLayoutAttribute> d’attribut à la classe ou structure.  
  
### <a name="object-overhead"></a>Surcharge de l’objet  
 Un `Object` qui fait référence à des données élémentaires ou composites de type utilise 4 octets en plus des données contenues dans le type de données.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Strings.StrConv%2A>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Caractères de type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
