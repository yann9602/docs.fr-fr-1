---
title: "Tableau des formats des résultats numériques (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 16976f5a59bd4eb0eca29553aff87d4fe0b1d247
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="formatting-numeric-results-table-c-reference"></a>Tableau des formats des résultats numériques (référence C#)
Vous pouvez appliquer un format à un résultat numérique à l’aide de la méthode <xref:System.String.Format%2A?displayProperty=fullName>, ou par l’intermédiaire de la méthode <xref:System.Console.Write%2A?displayProperty=fullName> ou `String.Format`, qui appelle <xref:System.Console.WriteLine%2A?displayProperty=fullName>. Le format est spécifié à l’aide de chaînes de format. Le tableau suivant contient les chaînes de format standard prises en charge. La chaîne de format prend la forme suivante : `Axx`, où `A` est le spécificateur de format et `xx` est le spécificateur de précision. Le spécificateur de format contrôle le type de mise en forme appliquée à la valeur numérique, tandis que le spécificateur de précision contrôle le nombre de chiffres significatifs ou de décimales de la sortie formatée. La valeur du spécificateur de précision est comprise entre 0 et 99.  
  
 Pour plus d’informations sur les chaînes de format standard et personnalisées, consultez [Mise en forme des types](../../../standard/base-types/formatting-types.md). Pour plus d'informations sur la méthode `String.Format`, consultez <xref:System.String.Format%2A?displayProperty=fullName>.  
  
|Spécificateur de format|Description|Exemples|Sortie|  
|----------------------|-----------------|--------------|------------|  
|C ou c|Devise|Console.Write("{0:C}", 2.5);<br /><br /> Console.Write("{0:C}", -2.5);|$2.50<br /><br /> ($2.50)|  
|D ou d|Decimal|Console.Write("{0:D5}", 25);|00025|  
|E ou e|Scientifique|Console.Write("{0:E}", 250000);|2.500000E+005|  
|F ou f|Virgule fixe|Console.Write("{0:F2}", 25);<br /><br /> Console.Write("{0:F0}", 25);|25.00<br /><br /> 25|  
|G ou g|Général|Console.Write("{0:G}", 2.5);|2.5|  
|N ou n|Nombre|Console.Write("{0:N}", 2500000);|2,500,000.00|  
|X ou x|Hexadécimal|Console.Write("{0:X}", 250);<br /><br /> Console.Write("{0:X}", 0xffff);|FA<br /><br /> FFFF|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Chaînes de format numériques standard](../../../standard/base-types/standard-numeric-format-strings.md)   
 [Tableaux de référence des types](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [string](../../../csharp/language-reference/keywords/string.md)

