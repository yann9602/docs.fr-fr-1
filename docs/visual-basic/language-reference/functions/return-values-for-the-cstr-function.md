---
title: "Return Values for the CStr Function (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "times, CStr Function return values"
  - "type conversion"
  - "dates [Visual Basic], CStr Function return values"
  - "CStr function"
  - "strings [Visual Basic], return value"
  - "Date data type, converting"
  - "dates [Visual Basic]"
  - "String data type, converting"
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Return Values for the CStr Function (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le tableau suivant illustre les valeurs de retour de `CStr` pour différents types de données de `expression`.  
  
|Si le type `expression` a la valeur|`CStr` retourne|  
|-----------------------------------------|---------------------|  
|[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Une chaîne contenant les valeurs "True" ou "False".|  
|[Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md)|Une chaîne contenant une valeur `Date` \(date et heure\) dans le format de date courte en vigueur sur votre système.|  
|[Numeric Data Types](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Une chaîne représentant le nombre.|  
  
## CStr et Date  
 Le type `Date` contient toujours des informations sur la date et l'heure.  Dans le cadre de la conversion de type, Visual Basic considère la valeur 1\/1\/0001 \(le 1er janvier de l'année 1\) comme une *valeur neutre* pour la date et 00:00:00 \(minuit\) comme une valeur neutre pour l'heure.  `CStr` n'inclut pas de valeurs neutres dans la chaîne obtenue.  Par exemple, si vous convertissez `#January 1, 0001 9:30:00#` en une chaîne, la chaîne obtenue est "9:30:00 AM" ; les informations relatives à la date sont supprimées.  Toutefois, les informations de date sont toujours présentes dans la valeur `Date` d'origine et peuvent être récupérées à l'aide de fonctions, telles que <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
>  La fonction `CStr` effectue sa conversion en fonction des paramètres de culture actuels de l'application.  Pour obtenir la représentation sous forme de chaîne d'un nombre dans une culture spécifique, utilisez la méthode `ToString(IFormatProvider)` du nombre.  Par exemple, utilisez <xref:System.Double.ToString%2A?displayProperty=fullName> lors de la conversion d'une valeur de type `Double` en `String`.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)   
 [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md)