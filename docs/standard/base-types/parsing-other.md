---
title: "Analyse d’autres chaînes dans .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: edd48993f50ec8b91ba7941a682d7de9f22aa12e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-other-strings-in-net"></a>Analyse d’autres chaînes dans .NET
En plus de numeric et <xref:System.DateTime> chaînes, vous pouvez également analyser des chaînes qui représentent les types <xref:System.Char>, <xref:System.Boolean>, et <xref:System.Enum> en types de données.  
  
## <a name="char"></a>Char  
 La méthode d’analyse statique associée au type de données **Char** est utile pour la conversion d’une chaîne qui contient un caractère unique en une valeur Unicode. L’exemple de code suivant analyse une chaîne en un caractère Unicode.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Booléen  
 Le **booléenne** type de données contient un **analyser** méthode que vous pouvez utiliser pour convertir une chaîne qui représente une valeur booléenne dans une réelle **booléenne** type. Cette méthode ne respecte pas la casse et peut analyser une chaîne contenant « True » ou « False ». Le **analyser** méthode associée à la **booléenne** type peut aussi analyser des chaînes entourées par des espaces blancs. Si une autre chaîne est passée, un <xref:System.FormatException> est levée.  
  
 Le code suivant exemple utilise le **analyser** méthode pour convertir une chaîne en valeur booléenne.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Énumération  
 Vous pouvez utiliser la méthode **Parse** statique pour initialiser un type d’énumération avec la valeur d’une chaîne. Cette méthode accepte le type d’énumération que vous analysez, la chaîne à analyser et un indicateur booléen facultatif indiquant si l’analyse est sensible à la casse. La chaîne que vous analysez peut contenir plusieurs valeurs séparées par des virgules, lesquelles peuvent être précédées ou suivies d’un ou plusieurs espaces vides (aussi appelés espaces blancs). Quand la chaîne contient plusieurs valeurs, celle de l’objet retourné est la valeur de toutes les valeurs spécifiées, combinées avec une opération OR au niveau du bit.  
  
 L’exemple suivant utilise le **analyser** méthode pour convertir une représentation sous forme de chaîne en une valeur d’énumération. Le <xref:System.DayOfWeek> énumération est initialisée à **jeudi** à partir d’une chaîne.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de chaînes](../../../docs/standard/base-types/parsing-strings.md)  
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)  
 [Conversion de type dans le .NET](../../../docs/standard/base-types/type-conversion.md)
