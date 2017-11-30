---
title: Valeurs de retour pour la fonction CStr (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b498c9b1b7916467c96ed2c645c7131192a5e8b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>Valeurs de retour pour la fonction CStr (Visual Basic)
Le tableau suivant décrit les valeurs de retour pour `CStr` pour différents types de données de `expression`.  
  
|Si `expression` est de type|`CStr`Retourne|  
|-----------------------------|--------------------|  
|[Booléen (type de données)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Chaîne contenant « True » ou « False ».|  
|[Date (type de données)](../../../visual-basic/language-reference/data-types/date-data-type.md)|Une chaîne contenant un `Date` valeur (date et heure) dans le format de date courte de votre système.|  
|[Types de données numériques](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|Chaîne représentant le nombre.|  
  
## <a name="cstr-and-date"></a>Date et la fonction CStr  
 Le `Date` type contient toujours des informations de date et heure. À des fins de conversion de type, Visual Basic considère le 1/1/0001 (le 1er janvier de l’année 1) soit un *valeur neutre* pour la date et 00:00:00 (minuit) comme une valeur neutre pour l’heure. `CStr`n’inclut pas de valeurs neutres dans la chaîne résultante. Par exemple, si vous convertissez `#January 1, 0001 9:30:00#` en une chaîne, le résultat est « 9:30:00 AM » ; les informations de date sont supprimées. Toutefois, les informations de date sont toujours présentes dans la version d’origine `Date` valeur et peuvent être récupérées avec des fonctions telles que <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
> [!NOTE]
>  Le `CStr` fonction effectue sa conversion en fonction des paramètres de culture actuels de l’application. Pour obtenir la représentation sous forme de chaîne d’un nombre dans une culture particulière, utilisez le nombre `ToString(IFormatProvider)` (méthode). Par exemple, utilisez <xref:System.Double.ToString%2A?displayProperty=nameWithType> lors de la conversion d’une valeur de type `Double` à un `String`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Booléen (type de données)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [Date (type de données)](../../../visual-basic/language-reference/data-types/date-data-type.md)
