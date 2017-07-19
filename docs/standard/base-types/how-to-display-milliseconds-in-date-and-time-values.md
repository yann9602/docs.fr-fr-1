---
title: "Comment&#160;: afficher les&#160;millisecondes&#160;dans les valeurs de date et d&#39;heure | Microsoft Docs"
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
  - "dates (.NET Framework), millisecondes"
  - "DateTime.ToString (méthode)"
  - "afficher les données de date et d'heure"
  - "millisecondes (.NET Framework)"
  - "heure (.NET Framework), millisecondes"
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: afficher les&#160;millisecondes&#160;dans les valeurs de date et d&#39;heure
Les méthodes de date et d'heure par défaut, telles que <xref:System.DateTime.ToString?displayProperty=fullName>, incluent les heures, minutes et secondes d'une valeur d'heure, mais excluent son composant « millisecondes ».  Cette rubrique indique comment inclure le composant « millisecondes » d'une date\/heure dans des chaînes de date et d'heure mises en forme.  
  
### Pour afficher le composant « millisecondes » d'une valeur DateTime  
  
1.  Si vous utilisez la représentation sous forme de chaîne d'une date, convertissez\-la en une valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset> à l'aide de la méthode statique <xref:System.DateTime.Parse%28System.String%29?displayProperty=fullName> ou <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=fullName>.  
  
2.  Pour extraire la représentation sous forme de chaîne du composant « millisecondes » d'une heure, appelez la méthode <xref:System.DateTime.ToString%28System.String%29?displayProperty=fullName> ou <xref:System.DateTimeOffset.ToString%2A> de la valeur de date et d'heure et passez le modèle de format personnalisé `fff` ou `FFF` seul ou avec d'autres spécificateurs de format personnalisés comme paramètre `format`.  
  
## Exemple  
 L'exemple affiche le composant « millisecondes » des valeurs <xref:System.DateTime> et <xref:System.DateTimeOffset> sur la console, seul et dans une chaîne de date et d'heure plus longue.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 Le modèle de format `fff` inclut tous les zéros de fin dans la valeur en millisecondes.  Le modèle de format `FFF` les supprime.  La différence est illustrée dans l'exemple suivant.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 Lorsque vous définissez un spécificateur de format personnalisé complet qui inclut le composant « milliseconde » d'une date\/heure, il se peut que le format codé en dur défini ne corresponde pas à la disposition des éléments d'heure dans la culture actuelle de l'application.  Dans ce cas, il est conseillé de récupérer l'un des modèles d'affichage de date et d'heure définis par l'objet <xref:System.Globalization.DateTimeFormatInfo> de la culture actuelle et d'y inclure les millisecondes.  L'exemple illustre également cette approche.  Il récupère le modèle de date et d'heure complet de la culture actuelle à partir de la propriété <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=fullName>, puis insère le modèle personnalisé `.ffff` après son deuxième modèle.  Notez que l'exemple utilise une expression régulière permettant d'effectuer cette opération dans un seul appel de méthode.  
  
 Vous pouvez également utiliser un spécificateur de format personnalisé pour afficher une partie fractionnaire de secondes autre que les millisecondes.  Par exemple, le spécificateur de format personnalisé `f` ou `F` affiche les dixièmes de seconde, `ff` ou `FF` affiche les centièmes de seconde et `ffff` ou `FFFF` affiche les dix millièmes de seconde.  Les parties fractionnaires d'une milliseconde sont tronquées au lieu d'être arrondies dans la chaîne retournée.  Ces spécificateurs de format sont utilisés dans l'exemple suivant.  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  Il est possible d'afficher des unités fractionnaires de seconde très petites, telles que les dix ou cent millièmes de seconde.  Toutefois, ces valeurs ne sont pas toujours explicites.  La précision des valeurs de date et d'heure dépend de la résolution de l'horloge système.  Dans les systèmes d'exploitation Windows NT 3.5 et versions ultérieures, ainsi que dans [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], la résolution de l'horloge est d'environ 10\-15 millisecondes.  
  
## Compilation du code  
 Compilez le code sur la ligne de commande à l'aide de csc.exe ou vb.exe.  Pour compiler le code dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], placez\-le dans un modèle de projet d'application console.  
  
## Voir aussi  
 <xref:System.Globalization.DateTimeFormatInfo>   
 [Chaînes de format de date et d'heure personnalisées](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)