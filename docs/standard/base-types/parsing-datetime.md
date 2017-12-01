---
title: "Analyse des chaînes de date et d'heure dans .NET Framework"
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
helpviewer_keywords:
- parsing strings, date and time strings
- date and time strings
- ParseExact method
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- DateTime object
- time strings
ms.assetid: 43bae51e-9b1d-41a6-a187-772c0d096d90
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1beceb2b2d32c500e73cd7786c480fcd84c3001c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-date-and-time-strings-in-net"></a>L’analyse des chaînes de Date et heure dans .NET
Méthodes d’analyse convertissent la représentation sous forme de chaîne d’une date et une heure en un équivalent <xref:System.DateTime> objet. Le <xref:System.DateTime.Parse%2A> et <xref:System.DateTime.TryParse%2A> méthodes convertissent l’une des nombreuses représentations communes d’une date et une heure. Le <xref:System.DateTime.ParseExact%2A> et <xref:System.DateTime.TryParseExact%2A> méthodes convertissent une représentation sous forme de chaîne conforme au modèle spécifié par une chaîne de format de date et d’heure. (Consultez les rubriques sur les [chaînes de format de date et d’heure standard](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) et les [chaînes de format de date et d’heure personnalisées](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).)  
  
 L’analyse est influencée par les propriétés d’un fournisseur de format qui donne des informations telles que les chaînes utilisées pour les séparateurs de date et d’heure, et les noms de mois, jours et ères. Le fournisseur de format est en cours <xref:System.Globalization.DateTimeFormatInfo> objet, qui est fourni implicitement par la culture actuelle du thread ou explicitement par le <xref:System.IFormatProvider> paramètre d’une méthode d’analyse. Pour le <xref:System.IFormatProvider> paramètre, spécifiez un <xref:System.Globalization.CultureInfo> objet, qui représente une culture, ou un <xref:System.Globalization.DateTimeFormatInfo> objet.  
  
 La représentation sous forme de chaîne d’une date à analyser doit inclure le mois et au moins un jour ou une année. La représentation d’une heure sous forme de chaîne doit inclure l’heure et au moins les minutes ou l’indicateur AM/PM. Toutefois, si possible, l’analyse fournit des valeurs par défaut pour les composants omis. Une date manquante a comme valeur par défaut la date du jour, une année manquante a comme valeur par défaut l’année en cours, un jour manquant du mois a comme valeur par défaut le premier jour du mois, et une heure manquante a comme valeur par défaut minuit.  
  
 Si la représentation sous forme de chaîne spécifie uniquement une heure, l’analyse retourne un <xref:System.DateTime> de l’objet avec son <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, et <xref:System.DateTime.Day%2A> propriétés définies sur les valeurs correspondantes de la <xref:System.DateTime.Today%2A> propriété. Toutefois, si le <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> constante est spécifiée dans la méthode d’analyse, qui en résulte année, mois, et les propriétés de jour sont définies sur la valeur `1`.  
  
 Outre le composant de date et d’heure, la représentation sous forme de chaîne d’une date et d’une heure peut inclure un offset qui indique le décalage horaire par rapport au temps universel coordonné (UTC, Coordinated Universal Time). Par exemple, la chaîne « 2/14/2007 5:32:00 -7:00 » définit une heure qui est sept heures plus tôt que l’heure UTC. Si un décalage est omis à partir de la représentation sous forme de chaîne d’une heure, l’analyse retourne un <xref:System.DateTime> de l’objet avec son <xref:System.DateTime.Kind%2A> propriété <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Si un offset est spécifié, l’analyse retourne un <xref:System.DateTime> de l’objet avec son <xref:System.DateTime.Kind%2A> propriété <xref:System.DateTimeKind.Local> et sa valeur est ajustée pour le fuseau horaire local de votre ordinateur. Vous pouvez modifier ce comportement en utilisant un <xref:System.Globalization.DateTimeStyles> constante avec la méthode d’analyse.  
  
 Le fournisseur de format est également utilisé pour interpréter une date numérique ambiguë. Par exemple, il n’est pas évident de savoir quels composants de la date représentée par la chaîne « 02/03/04 » correspondent au mois, au jour et à l’année. Dans ce cas, les composants sont interprétés d’après l’ordre des formats de date similaires dans le fournisseur de format.  
  
## <a name="parse"></a>Parse  
 L’exemple de code suivant illustre l’utilisation de la **analyser** méthode pour convertir une chaîne en un **DateTime**. Cet exemple fait appel à la culture associée au thread actuel pour effectuer l’analyse. Si le <xref:System.Globalization.CultureInfo> associé actuel culture ne peut pas analyser la chaîne d’entrée, un <xref:System.FormatException> est levée.  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 Vous pouvez également spécifier un **CultureInfo** défini sur l’une des cultures définies par cet objet, ou vous pouvez spécifier l’une de la norme <xref:System.Globalization.DateTimeFormatInfo> objets retournés par le <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> propriété. L’exemple de code suivant utilise un fournisseur de format pour analyser une chaîne en allemand dans une **DateTime**. A **CultureInfo** représentant la culture fr-fr est défini et passé avec la chaîne analysée pour assurer l’analyse réussie de cette chaîne particulière. Cela exclut dans le **CurrentCulture** de la **CurrentThread**.  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 Toutefois, vous pouvez utiliser les surcharges de la <xref:System.DateTime.Parse%2A> méthode pour spécifier des fournisseurs de format personnalisé, la méthode ne prend pas en charge l’utilisation de fournisseurs de format non standard. Pour analyser une date et heure exprimées dans un format non standard, utilisez la <xref:System.DateTime.ParseExact%2A> méthode à la place.  
  
 Le code suivant exemple utilise le <xref:System.Globalization.DateTimeStyles> énumération pour spécifier que les informations de date et l’heure actuelles ne doivent pas être ajoutées à la **DateTime** pour les champs qui ne définit pas de la chaîne.  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## <a name="parseexact"></a>ParseExact  
 Le <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> méthode convertit une chaîne qui est conforme à un modèle de chaîne spécifiée à un **DateTime** objet. Lorsqu’une chaîne qui n’est pas sous la forme spécifiée est passée à cette méthode, un <xref:System.FormatException> est levée. Vous pouvez spécifier un des spécificateurs de format standard de date et d’heure ou une combinaison limitée de spécificateurs de format personnalisé de date et d’heure. En utilisant les spécificateurs de format personnalisé, vous pouvez construire une chaîne de reconnaissance personnalisée. Pour obtenir une explication des spécificateurs, consultez les rubriques relatives aux [chaînes de format de date et d’heure standard](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) et aux [chaînes de format de date et d’heure personnalisées](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).  
  
 Chaque surcharge de la <xref:System.DateTime.ParseExact%2A> méthode présente également un <xref:System.IFormatProvider> paramètre qui fournit généralement des informations sur la mise en forme propres à la culture de la chaîne. En règle générale, cela <xref:System.IFormatProvider> objet est un <xref:System.Globalization.CultureInfo> objet qui représente une culture standard ou un <xref:System.Globalization.DateTimeFormatInfo> objet qui est retourné par la <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> propriété. Toutefois, contrairement à d’autres date et heure fonctions d’analyse, cette méthode prend également en charge un <xref:System.IFormatProvider> qui définit une date non standard et le format d’heure.  
  
 Dans l’exemple de code suivant, le **ParseExact** méthode est passée à un objet chaîne à analyser, suivi d’un spécificateur de format, suivi d’un **CultureInfo** objet. Cela **ParseExact** méthode peut uniquement analyser des chaînes qui présentent le modèle de date longue dans la culture en-US.  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de chaînes](../../../docs/standard/base-types/parsing-strings.md)  
 [Mise en forme des types](../../../docs/standard/base-types/formatting-types.md)  
 [Conversion de type dans .NET](../../../docs/standard/base-types/type-conversion.md)
