---
title: "Analyse des cha&#238;nes de date et d&#39;heure dans .NET Framework | Microsoft Docs"
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
  - "types de base, analyser des chaînes"
  - "chaînes date et heure"
  - "DateTime (objet)"
  - "énumérations (.NET Framework), analyser des chaînes"
  - "ParseExact (méthode)"
  - "analyser des chaînes, chaînes date et heure"
  - "chaînes heure"
ms.assetid: 43bae51e-9b1d-41a6-a187-772c0d096d90
caps.latest.revision: 24
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 24
---
# Analyse des cha&#238;nes de date et d&#39;heure dans .NET Framework
Les méthodes d'analyse convertissent la représentation sous forme de chaîne d'une date et heure en un objet <xref:System.DateTime> équivalent.  Les méthodes <xref:System.DateTime.Parse%2A> et <xref:System.DateTime.TryParse%2A> convertissent l'une des nombreuses représentations communes de date et heure.  Les méthodes <xref:System.DateTime.ParseExact%2A> et <xref:System.DateTime.TryParseExact%2A> convertissent une représentation sous forme de chaîne conforme au modèle spécifié par une chaîne de format de date et d'heure. \(Consultez les rubriques sur les [chaînes de format de date et d'heure standard](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) et les [chaînes de format de date et d'heure personnalisées](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).\)  
  
 L'analyse est influencée par les propriétés d'un fournisseur de format qui donne des informations telles que les chaînes utilisées pour les séparateurs de date et d'heure, et les noms de mois, jours et ères.  Le fournisseur de format est l'objet <xref:System.Globalization.DateTimeFormatInfo> en cours qui est fourni implicitement par la culture du thread en cours ou explicitement par le paramètre <xref:System.IFormatProvider> d'une méthode d'analyse.  Pour le paramètre <xref:System.IFormatProvider>, spécifiez un objet <xref:System.Globalization.CultureInfo> qui représente une culture, ou un objet <xref:System.Globalization.DateTimeFormatInfo>.  
  
 La représentation sous forme de chaîne d'une date à analyser doit inclure le mois et au moins un jour ou une année.  La représentation d'une heure sous forme de chaîne doit inclure l'heure et au moins les minutes ou l'indicateur AM\/PM.  Toutefois, si possible, l'analyse fournit des valeurs par défaut pour les composants omis.  Une date manquante a comme valeur par défaut la date du jour, une année manquante a comme valeur par défaut l'année en cours, un jour manquant du mois a comme valeur par défaut le premier jour du mois, et une heure manquante a comme valeur par défaut minuit.  
  
 Si la représentation sous forme de chaîne spécifie uniquement une heure, l'analyse retourne un objet <xref:System.DateTime> avec les propriétés <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A> et <xref:System.DateTime.Day%2A> définies sur les valeurs correspondantes de la propriété <xref:System.DateTime.Today%2A>.  Toutefois, si la constante <xref:System.Globalization.DateTimeStyles> est spécifiée dans la méthode d'analyse, les propriétés d'année, mois et jour résultantes ont la valeur `1`.  
  
 Outre le composant de date et d'heure, la représentation sous forme de chaîne d'une date et d'une heure peut inclure un offset qui indique le décalage horaire par rapport au temps universel coordonné \(UTC, Coordinated Universal Time\).  Par exemple, la chaîne "2\/14\/2007 5:32:00 \-7: 00" définit une heure qui est sept heures plus tôt que l'heure UTC.  Si la représentation d'une heure sous forme de chaîne n'inclut pas d'offset, l'analyse retourne un objet <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> a la valeur <xref:System.DateTimeKind?displayProperty=fullName>.  Si un offset est spécifié, l'analyse retourne un objet <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> a la valeur <xref:System.DateTimeKind> et dont la valeur est ajustée en fonction du fuseau horaire local de votre ordinateur.  Vous pouvez modifier ce comportement en utilisant une constante <xref:System.Globalization.DateTimeStyles> avec la méthode d'analyse.  
  
 Le fournisseur de format est également utilisé pour interpréter une date numérique ambiguë.  Par exemple, il n'est pas évident de savoir quels composants de la date représentée par la chaîne "02\/03\/04" correspondent au mois, au jour et à l'année.  Dans ce cas, les composants sont interprétés d'après l'ordre des formats de date similaires dans le fournisseur de format.  
  
## Parse  
 L'exemple de code suivant illustre l'utilisation de la méthode **Parse** pour convertir une chaîne en **DateTime**.  Cet exemple fait appel à la culture associée au thread en cours pour effectuer à l'analyse.  Si l'objet <xref:System.Globalization.CultureInfo> associé à la culture actuelle ne peut analyser la chaîne d'entrée, une exception <xref:System.FormatException> est levée.  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 Vous pouvez également spécifier un objet **CultureInfo** qui prend la valeur d'une des cultures qu'il a définies ou spécifier l'un des objets <xref:System.Globalization.DateTimeFormatInfo> standard retournés par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=fullName>.  L'exemple de code suivant utilise un fournisseur de format pour analyser une chaîne en allemand dans **DateTime**.  Un **CultureInfo** représentant la culture de\-DE est défini et passé avec la chaîne analysée pour assurer l'analyse réussie de cette chaîne particulière.  Ceci exclut tous les paramètres contenus dans **CurrentCulture** de **CurrentThread**.  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 Toutefois, bien que vous puissiez utiliser les surcharges de la méthode <xref:System.DateTime.Parse%2A> pour spécifier des fournisseurs de format personnalisé, la méthode ne prend pas en charge l'utilisation de fournisseurs de format non standard.  Pour analyser une date et une heure exprimées dans un format non standard, faites plutôt appel à la méthode <xref:System.DateTime.ParseExact%2A>.  
  
 L'exemple de code suivant utilise l'énumération <xref:System.Globalization.DateTimeStyles> pour indiquer que les informations de date et d'heure actuelles ne doivent pas être ajoutées à **DateTime** pour les champs que la chaîne ne définit pas.  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## ParseExact  
 La méthode <xref:System.DateTime.ParseExact%2A?displayProperty=fullName> convertit une chaîne conforme à un modèle de chaîne spécifié en objet **DateTime**.  Lorsqu'une chaîne dans un format autre que celui spécifié est passée à cette méthode, une <xref:System.FormatException> est renvoyée.  Vous pouvez spécifier un des spécificateurs de format standard de date et d'heure ou une combinaison limitée de spécificateurs de format personnalisé de date et d'heure.  En utilisant les spécificateurs de format personnalisés, il vous est possible de construire une chaîne de reconnaissance personnalisée.  Pour obtenir une explication des spécificateurs, consultez les rubriques relatives aux [chaînes de format de date et d'heure standard](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) et aux [chaînes de format de date et d'heure personnalisées](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).  
  
 Chaque surcharge de la méthode <xref:System.DateTime.ParseExact%2A> a également un paramètre <xref:System.IFormatProvider> qui fournit généralement des informations spécifiques à la culture sur la mise en forme de la chaîne.  En général, cet objet <xref:System.IFormatProvider> est un objet <xref:System.Globalization.CultureInfo> qui représente une culture standard ou un objet <xref:System.Globalization.DateTimeFormatInfo> qui est retourné par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=fullName>.  Toutefois, contrairement aux autres fonctions d'analyse de date et d'heure, cette méthode prend également en charge <xref:System.IFormatProvider> qui définit un format de date et d'heure non standard.  
  
 Dans l'exemple de code suivant, la méthode **ParseExact** reçoit un objet chaîne à analyser, puis spécificateur de format, puis un objet **CultureInfo**.  Cette méthode **ParseExact** peut uniquement analyser des chaînes qui exhibent le format de date longue dans la culture en\-US.  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## Voir aussi  
 [Analyse de chaînes](../../../docs/standard/base-types/parsing-strings.md)   
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)   
 [Conversion de type dans le .NET Framework](../../../docs/standard/base-types/type-conversion.md)