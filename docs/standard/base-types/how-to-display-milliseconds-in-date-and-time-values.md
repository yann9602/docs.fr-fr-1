---
title: "Comment : afficher les millisecondes dans les valeurs de date et d'heure"
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
- DateTime.ToString method
- displaying date and time data
- time [.NET Framework], milliseconds
- dates [.NET Framework], milliseconds
- milliseconds [.NET Framework]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 260d202eb0a218a6657bc719e36da6f39138e54e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a>Comment : afficher les millisecondes dans les valeurs de date et d'heure
La date par défaut et l’heure de mise en forme des méthodes, telles que <xref:System.DateTime.ToString?displayProperty=nameWithType>, incluent les heures, minutes et secondes d’une valeur d’heure, mais exclut les son composant « millisecondes ». Cette rubrique montre comment inclure le composant « millisecondes » d’une date et d’une heure dans des chaînes de date et d’heure mises en forme.  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a>Pour afficher le composant « millisecondes » d’une valeur DateTime  
  
1.  Si la date est représentée sous forme de chaîne, convertissez-la en une valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset> en utilisant la méthode <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> statique.  
  
2.  Pour extraire la représentation sous forme de chaîne du composant « millisecondes » d’une heure, appelez la valeur date et d’heure <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.ToString%2A> (méthode) et passez le `fff` ou `FFF` modèle de format personnalisé, seul ou avec d’autres format personnalisé les spécificateurs en tant que le `format` paramètre.  
  
## <a name="example"></a>Exemple  
 L’exemple affiche le composant « millisecondes » d’une <xref:System.DateTime> et un <xref:System.DateTimeOffset> sur la console, seule et dans une chaîne de date et d’heure plus longue.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 Le modèle de format `fff` inclut les zéros de fin éventuels dans la valeur en millisecondes. Le modèle de format `FFF` les supprime. L’exemple suivant illustre cette différence.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 Quand vous définissez un spécificateur de format personnalisé complet qui inclut le composant « millisecondes » d’une date et d’une heure, vous pouvez être confronté au problème suivant : le format défini peut être un format codé en dur qui ne correspond pas à la disposition des éléments d’heure dans la culture actuelle de l’application. Une meilleure solution consiste à récupérer une de la date et l’heure des modèles d’affichage définis par la culture actuelle <xref:System.Globalization.DateTimeFormatInfo> de l’objet et modifiez-le pour inclure les millisecondes. L’exemple illustre également cette approche. Il récupère de la culture actuelle complète modèle de date et heure à partir de la <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> propriété, puis insère le modèle personnalisé `.ffff` après son deuxième modèle. Notez que l’exemple utilise une expression régulière pour effectuer cette opération dans un seul appel de méthode.  
  
 Vous pouvez également utiliser un spécificateur de format personnalisé pour afficher une partie fractionnaire des secondes autre que les millisecondes. Par exemple, le spécificateur de format personnalisé `f` ou `F` affiche les dixièmes de seconde, le spécificateur de format personnalisé `ff` ou `FF` affiche les centièmes de seconde, tandis que le spécificateur de format personnalisé `ffff` ou `FFFF` affiche les dix millièmes de seconde. La partie fractionnaire d’une milliseconde est tronquée au lieu d’être arrondie dans la chaîne retournée. Ces spécificateurs de format sont utilisés dans l’exemple suivant.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  Il est possible d’afficher de très petites unités fractionnaires d’une seconde, telles que les dix millièmes de seconde ou les cent millièmes de seconde. Toutefois, ces valeurs peuvent ne pas être significatives. La précision des valeurs de date et d'heure dépend de la résolution de l'horloge système. Sur Windows NT 3.5 et versions ultérieures, et [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] les systèmes d’exploitation, la résolution de l’horloge est environ 10-15 millisecondes.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Compiler le code à la ligne de commande à l’aide de csc.exe ou vb.exe. Pour compiler le code dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], placez-le dans un modèle de projet application console.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [Custom Date and Time Format Strings](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
