---
title: "Tableau des formats des r&#233;sultats num&#233;riques (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "mettre en forme (C#)"
  - "mettre en forme les nombres (C#)"
  - "String.Format (méthode)"
  - "Console.Write (méthode)"
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Tableau des formats des r&#233;sultats num&#233;riques (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous pouvez mettre en forme des résultats numériques à l'aide de la méthode <xref:System.String.Format%2A?displayProperty=fullName>, ou via la méthode <xref:System.Console.Write%2A?displayProperty=fullName> ou <xref:System.Console.WriteLine%2A?displayProperty=fullName>, qui appelle `String.Format`.  Le format est spécifié à l'aide de chaînes de format.  Le tableau suivant répertorie les chaînes de format standard prises en charge.  La chaîne de format prend la forme suivante : `Axx`, où `A` est le spécificateur de format et `xx` le spécificateur de précision.  Le spécificateur de format détermine le format appliqué à la valeur numérique alors que le spécificateur de précision définit le nombre de chiffres significatifs ou de décimales que doit contenir le résultat auquel le format a été appliqué.  La valeur du spécificateur de précision est compris entre 0 et 99.  
  
 Pour plus d'informations sur les chaînes de standard et de mise en forme personnalisée, consultez [Mise en forme des types](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md).  Pour plus d'informations sur la méthode `String.Format`, consultez <xref:System.String.Format%2A?displayProperty=fullName>.  
  
|Spécificateur de format|Description|Exemples|Sortie|  
|-----------------------------|-----------------|--------------|------------|  
|C ou c|Devise|Console.Write\("{0:C}", 2,5\);<br /><br /> Console.Write\("{0:C}", \-2.5\);|$2.50<br /><br /> \($2.50\)|  
|D ou d|Decimal|Console.Write\("{0:D5}", 25\) ;|00025|  
|E ou e|Scientifique|Console.Write\("{0:E}", 250000\) ;|2.500000E\+005|  
|F ou f|Virgule fixe|Console.Write\("{0:F2}", 25\);<br /><br /> Console.Write\("{0:F0}", 25\) ;|25.00<br /><br /> 25|  
|G ou g|Général|Console.Write\("{0:G}", 2.5\) ;|2.5|  
|N ou n|Numéro|Console.Write\("{0:N}", 2500000\) ;|2,500,000.00|  
|X ou x|Hexadécimal|Console.Write\("{0:X}", 250\) ;<br /><br /> Console.Write\("{0:X}", 0xffff\) ;|FA<br /><br /> FFFF|  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Chaînes de format numériques standard](../Topic/Standard%20Numeric%20Format%20Strings.md)   
 [Tableaux de référence des types](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [chaîne](../../../csharp/language-reference/keywords/string.md)