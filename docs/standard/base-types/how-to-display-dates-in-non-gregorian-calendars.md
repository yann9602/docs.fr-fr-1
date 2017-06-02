---
title: "Comment&#160;: afficher des dates dans des calendriers non gr&#233;goriens | Microsoft Docs"
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
  - "mise en forme (.NET Framework), dates"
  - "dates (.NET Framework), mettre en forme"
  - "calendriers (.NET Framework), afficher des dates"
  - "afficher les données de date et d'heure"
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: afficher des dates dans des calendriers non gr&#233;goriens
Les types <xref:System.DateTime> et <xref:System.DateTimeOffset> utilisent le calendrier grégorien comme calendrier par défaut.  Par conséquent, lorsque vous appelez la méthode `ToString` d'une valeur de date et d'heure, la représentation sous forme de chaîne de ces date et heure est affichée dans le calendrier grégorien, même si elles ont été créées à l'aide d'un autre calendrier.  L'exemple suivant illustre deux méthodes différentes qui permettent de créer une valeur de date et d'heure avec le calendrier persan et de l'afficher dans le calendrier grégorien lorsque la méthode <xref:System.DateTime.ToString%2A> est appelée.  Cet exemple reflète deux techniques souvent utilisées, mais incorrectes, pour afficher la date dans un calendrier particulier.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Vous pouvez afficher la date dans un calendrier particulier en faisant appel à deux techniques différentes.  Avec la première, le calendrier doit être défini par défaut pour une culture particulière, tandis qu'avec  la seconde, n'importe quel calendrier peut être utilisé.  
  
### Pour afficher la date pour le calendrier par défaut d'une culture  
  
1.  Instanciez un objet de calendrier dérivé de la classe <xref:System.Globalization.Calendar> qui représente le calendrier à utiliser.  
  
2.  Instanciez un objet <xref:System.Globalization.CultureInfo> qui représente la culture dont la mise en forme sera utilisée pour afficher la date.  
  
3.  Appelez la méthode <xref:System.Array.Exists%2A?displayProperty=fullName> pour déterminer si l'objet de calendrier est membre du tableau retourné par la propriété <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=fullName>.  Cela indique que le calendrier peut servir de calendrier par défaut pour l'objet <xref:System.Globalization.CultureInfo>.  S'il n'est pas membre du tableau, suivez les instructions de la section « Pour afficher la date dans un calendrier quelconque ».  
  
4.  Assignez l'objet de calendrier à la propriété <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> de l'objet <xref:System.Globalization.DateTimeFormatInfo> retourné par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=fullName>.  
  
    > [!NOTE]
    >  La classe <xref:System.Globalization.CultureInfo> possède également une propriété <xref:System.Globalization.CultureInfo.Calendar%2A>.  Toutefois, comme elle est constante et en lecture seule, elle ne change pas pour refléter le nouveau calendrier par défaut assigné à la propriété <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=fullName>.  
  
5.  Appelez la méthode <xref:System.DateTime.ToString%2A> ou <xref:System.DateTime.ToString%2A> et passez\-lui l'objet <xref:System.Globalization.CultureInfo> dont le calendrier par défaut a été modifié à l'étape précédente.  
  
### Pour afficher la date dans un calendrier quelconque  
  
1.  Instanciez un objet de calendrier dérivé de la classe <xref:System.Globalization.Calendar> qui représente le calendrier à utiliser.  
  
2.  Déterminez les éléments de date et d'heure qui doivent apparaître dans la représentation sous forme de chaîne de la valeur de date et d'heure.  
  
3.  Pour chaque élément de date et d'heure que vous souhaitez afficher, appelez la méthode `Get` de l'objet de calendrier.  Les méthodes disponibles sont les suivantes :  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A> pour afficher l'année dans le calendrier approprié.  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A> pour afficher le mois dans le calendrier approprié.  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A> pour afficher le jour du mois dans le calendrier approprié.  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A> pour afficher l'heure du jour dans le calendrier approprié.  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A> pour afficher les minutes de l'heure dans le calendrier approprié.  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A> pour afficher les secondes de la minute dans le calendrier approprié.  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A> pour afficher les millisecondes de la seconde dans le calendrier approprié.  
  
## Exemple  
 L'exemple affiche une date à l'aide de deux calendriers différents :  le calendrier Hijri défini comme calendrier par défaut pour la culture ar\-JO et le calendrier persan qui n'est pas pris en charge comme calendrier facultatif par la culture fa\-IR.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Chaque objet <xref:System.Globalization.CultureInfo> peut prendre en charge un ou plusieurs calendriers, indiqués par la propriété <xref:System.Globalization.CultureInfo.OptionalCalendars%2A>.  L'un d'eux est désigné comme calendrier par défaut de la culture et est retourné par la propriété <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=fullName> en lecture seule.  Il est possible de désigner un autre calendrier facultatif comme calendrier par défaut en assignant un objet <xref:System.Globalization.Calendar> représentant ce calendrier à la propriété <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=fullName> retournée par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=fullName>.  Toutefois, certains calendriers, tels que le calendrier persan représenté par la classe <xref:System.Globalization.PersianCalendar>, ne peuvent pas être utilisés comme calendriers facultatifs, quelle que soit la culture.  
  
 L'exemple définit une classe utilitaire de calendrier réutilisable `CalendarUtility` pour gérer de nombreux détails de la génération de la représentation d'une date sous forme de chaîne à l'aide d'un calendrier particulier.  La classe `CalendarUtility` possède les membres suivants :  
  
-   Un constructeur paramétré dont le paramètre unique est un objet <xref:System.Globalization.Calendar> dans lequel une date sera représentée.  Il est assigné à un champ privé de la classe.  
  
-   `CalendarExists`, méthode privée qui retourne une valeur booléenne indiquant si le calendrier représenté par l'objet `CalendarUtility` est pris en charge par l'objet <xref:System.Globalization.CultureInfo> passé à la méthode comme paramètre.  La méthode encapsule un appel à la méthode <xref:System.Array.Exists%2A?displayProperty=fullName> à laquelle le tableau <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=fullName> est passé.  
  
-   `HasSameName`, méthode privée assignée au délégué <xref:System.Predicate%601> passé comme paramètre à la méthode <xref:System.Array.Exists%2A?displayProperty=fullName>.  Chaque membre du tableau est passé à la méthode jusqu'à ce que cette dernière retourne la valeur `true`.  La méthode détermine si le nom d'un calendrier facultatif est identique à celui du calendrier représenté par l'objet `CalendarUtility`.  
  
-   `DisplayDate`, méthode publique surchargée à laquelle deux paramètres sont passés : une valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset> à exprimer dans le calendrier représenté par l'objet `CalendarUtility` et la culture dont les règles de mise en forme seront utilisées.  Le comportement adopté pour retourner la représentation d'une date sous forme de chaîne varie selon que le calendrier cible est pris en charge ou non par la culture dont les règles de mise en forme seront utilisées.  
  
 La valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset> est généralement exprimée sous la forme d'une date grégorienne, quel que soit le calendrier utilisé pour la créer.  En effet, les types <xref:System.DateTime> et <xref:System.DateTimeOffset> ne conservent aucune information de calendrier.  En interne, cela correspond au nombre de graduations qui se sont écoulées depuis le 1er janvier 0001, à minuit.  L'interprétation de ce nombre dépend du calendrier.  Pour la plupart des cultures, le calendrier par défaut est le calendrier grégorien.  
  
## Compilation du code  
 Cet exemple requiert une référence à System.Core.dll.  
  
 Compilez le code sur la ligne de commande à l'aide de csc.exe ou vb.exe.  Pour compiler le code dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], placez\-le dans un modèle de projet d'application console.  
  
## Voir aussi  
 [Exécution d'opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)