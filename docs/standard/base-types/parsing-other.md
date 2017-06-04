---
title: "Analyse d&#39;autres cha&#238;nes dans .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "type de données char, analyser des chaînes"
  - "énumérations (.NET Framework), analyser des chaînes"
  - "types de base, analyser des chaînes"
  - "analyser des chaînes, autres chaînes"
  - "type de données booléen, analyser des chaînes"
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Analyse d&#39;autres cha&#238;nes dans .NET Framework
Vous pouvez non seulement analyser des chaînes numériques et <xref:System.DateTime>, mais également des chaînes qui représentent les types <xref:System.Char>, <xref:System.Boolean> et <xref:System.Enum> dans des types de données.  
  
## Char  
 La méthode d'analyse statique associée au type de données **Char** est utile pour la conversion d'une chaîne qui contient un caractère unique en une valeur Unicode.  L'exemple de code suivant analyse une chaîne en un caractère Unicode.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## Boolean  
 Le type de données **Boolean** contient une méthode **Parse** que vous pouvez utiliser pour convertir une chaîne représentant une valeur booléenne en type **Boolean** réel.  Cette méthode n'est pas sensible à la casse et peut successivement analyser une chaîne contenant "True" ou "False." La méthode **Parse** associée au type **Boolean** peut aussi analyser des chaînes entourées d'espaces blancs.  Si une autre chaîne est passée, un <xref:System.FormatException> est levé.  
  
 L'exemple de code suivant utilise la méthode **Parse** pour convertir une chaîne en valeur booléenne.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## Énumération  
 Vous pouvez utiliser la méthode statique **Parse** pour initialiser un type d'énumération avec la valeur d'une chaîne.  Cette méthode accepte le type d'énumération que vous analysez, la chaîne à analyser et un indicateur Boolean facultatif indiquant si l'analyse est sensible à la casse.  La chaîne que vous analysez peut contenir plusieurs valeurs séparées par des virgules, lesquelles peuvent être précédées ou suivies d'un ou plusieurs espaces vides \(aussi appelés espaces blancs\).  Lorsque la chaîne contient plusieurs valeurs, celle de l'objet retourné est la valeur de toutes les valeurs spécifiées, combinées avec une opération de bits OR.  
  
 L'exemple suivant utilise la méthode **Parse** pour convertir une représentation de chaîne en valeur d'énumération.  L'énumération <xref:System.DayOfWeek> est initialisée à **Thursday** à partir d'une chaîne.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## Voir aussi  
 [Analyse de chaînes](../../../docs/standard/base-types/parsing-strings.md)   
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)   
 [Conversion de type dans le .NET Framework](../../../docs/standard/base-types/type-conversion.md)