---
title: "Comment : afficher des dates dans des calendriers non grégoriens"
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
- formatting [.NET Framework], dates
- dates [.NET Framework], formatting
- calendars [.NET Framework], displaying dates
- displaying date and time data
ms.assetid: ed324eff-4aff-4a76-b6c0-04e6c0d8f5a9
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a79860091e549dcf4eaa7090947f9506eceb6119
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-display-dates-in-non-gregorian-calendars"></a>Comment : afficher des dates dans des calendriers non grégoriens
Le <xref:System.DateTime> et <xref:System.DateTimeOffset> types utilisent le calendrier grégorien comme calendrier par défaut. Cela signifie que l’appel de la méthode `ToString` d’une valeur de date et d’heure affiche la représentation sous forme de chaîne de la date et de l’heure dans le calendrier grégorien, même si ces date et heure ont été créées à l’aide d’un autre calendrier. Ceci est illustré dans l’exemple suivant, qui utilise deux façons de créer une valeur de date et d’heure avec le calendrier persan, mais affiche ces valeurs de date et d’heure dans le calendrier grégorien lorsqu’il appelle le <xref:System.DateTime.ToString%2A> (méthode). Cet exemple reflète deux techniques couramment utilisées, mais incorrectes, pour l’affichage de la date dans un calendrier particulier.  
  
 [!code-csharp[Formatting.HowTo.Calendar#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#1)]
 [!code-vb[Formatting.HowTo.Calendar#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#1)]  
  
 Deux techniques différentes peuvent être utilisées pour afficher la date dans un calendrier particulier. La première nécessite que le calendrier soit le calendrier par défaut pour une culture particulière. La seconde est utilisable avec n’importe quel calendrier.  
  
### <a name="to-display-the-date-for-a-cultures-default-calendar"></a>Pour afficher la date pour le calendrier par défaut d’une culture  
  
1.  Instancier un objet de calendrier dérivé de la <xref:System.Globalization.Calendar> classe qui représente le calendrier à utiliser.  
  
2.  Instancier une <xref:System.Globalization.CultureInfo> objet représentant la culture dont la mise en forme sera utilisée pour afficher la date.  
  
3.  Appelez le <xref:System.Array.Exists%2A?displayProperty=nameWithType> méthode pour déterminer si l’objet de calendrier est membre du tableau retourné par la <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> propriété. Cela indique que le calendrier peut servir le calendrier par défaut pour le <xref:System.Globalization.CultureInfo> objet. S’il n’est pas membre du tableau, suivez les instructions de la section « Pour afficher la date dans un calendrier ».  
  
4.  Assignez l’objet de calendrier à la <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A> propriété de la <xref:System.Globalization.DateTimeFormatInfo> objet retourné par la <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> propriété.  
  
    > [!NOTE]
    >  Le <xref:System.Globalization.CultureInfo> classe a également un <xref:System.Globalization.CultureInfo.Calendar%2A> propriété. Toutefois, il est en lecture seule et constante ; Il ne change pas pour refléter le nouveau calendrier par défaut affecté à la <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> propriété.  
  
5.  Appelez le <xref:System.DateTime.ToString%2A> ou <xref:System.DateTime.ToString%2A> (méthode) et lui passer le <xref:System.Globalization.CultureInfo> objet dont le calendrier par défaut a été modifié à l’étape précédente.  
  
### <a name="to-display-the-date-in-any-calendar"></a>Pour afficher la date dans un calendrier  
  
1.  Instancier un objet de calendrier dérivé de la <xref:System.Globalization.Calendar> classe qui représente le calendrier à utiliser.  
  
2.  Déterminez les éléments de date et d’heure qui doivent apparaître dans la représentation sous forme de chaîne de la valeur de date et d’heure.  
  
3.  Pour chaque élément de date et d’heure que vous souhaitez afficher, appelez l’objet de calendrier `Get`... . Les méthodes suivantes sont disponibles :  
  
    -   <xref:System.Globalization.Calendar.GetYear%2A>, pour afficher l’année dans le calendrier approprié.  
  
    -   <xref:System.Globalization.Calendar.GetMonth%2A>, pour afficher le mois dans le calendrier approprié.  
  
    -   <xref:System.Globalization.Calendar.GetDayOfMonth%2A>, pour afficher le numéro du jour du mois dans le calendrier approprié.  
  
    -   <xref:System.Globalization.Calendar.GetHour%2A>, pour afficher l’heure du jour dans le calendrier approprié.  
  
    -   <xref:System.Globalization.Calendar.GetMinute%2A>, pour afficher les minutes de l’heure dans le calendrier approprié.  
  
    -   <xref:System.Globalization.Calendar.GetSecond%2A>, pour afficher les secondes de la minute dans le calendrier approprié.  
  
    -   <xref:System.Globalization.Calendar.GetMilliseconds%2A>, pour afficher les millisecondes de la seconde dans le calendrier approprié.  
  
## <a name="example"></a>Exemple  
 L’exemple affiche une date à l’aide de deux calendriers différents. Il affiche la date après avoir défini le calendrier hégirien comme calendrier par défaut pour la culture ar-JO et affiche la date à l’aide du calendrier persan, qui n’est pas pris en charge comme calendrier facultatif par la culture fa-IR.  
  
 [!code-csharp[Formatting.HowTo.Calendar#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Calendar/cs/Calendar1.cs#2)]
 [!code-vb[Formatting.HowTo.Calendar#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Calendar/vb/Calendar1.vb#2)]  
  
 Chaque <xref:System.Globalization.CultureInfo> objet peut prendre en charge un ou plusieurs calendriers sont indiquées par le <xref:System.Globalization.CultureInfo.OptionalCalendars%2A> propriété. Un de ces est désigné comme calendrier par défaut de la culture et est retourné par la lecture seule <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> propriété. Un autre calendrier facultatif peut être désigné comme la valeur par défaut en attribuant un <xref:System.Globalization.Calendar> objet qui représente ce calendrier à la <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> propriété retournée par le <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> propriété. Toutefois, certains calendriers, tels que le calendrier persan représenté par la <xref:System.Globalization.PersianCalendar> de classe, ne servent pas comme des calendriers facultatifs pour n’importe quelle culture.  
  
 L’exemple définit une classe utilitaire de calendrier réutilisable, `CalendarUtility`, pour gérer de nombreux détails de la génération de la représentation sous forme de chaîne d’une date à l’aide d’un calendrier particulier. La classe `CalendarUtility` possède les membres suivants :  
  
-   Un constructeur paramétrable dont le paramètre unique est un <xref:System.Globalization.Calendar> objet dans lequel la date doit être représenté. Il est assigné à un champ privé de la classe.  
  
-   `CalendarExists`, une méthode privée qui retourne une valeur booléenne qui indique si le calendrier est représenté par le `CalendarUtility` objet est pris en charge par le <xref:System.Globalization.CultureInfo> objet qui est passé à la méthode en tant que paramètre. La méthode encapsule un appel à la <xref:System.Array.Exists%2A?displayProperty=nameWithType> méthode, auquel il transmet le <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> tableau.  
  
-   `HasSameName`, une méthode privée assignée à la <xref:System.Predicate%601> délégué qui est passé en tant que paramètre à la <xref:System.Array.Exists%2A?displayProperty=nameWithType> (méthode). Chaque membre du tableau est passé à la méthode jusqu’à ce qu’elle retourne `true`. La méthode détermine si le nom d’un calendrier facultatif est identique à celui du calendrier représenté par l’objet `CalendarUtility`.  
  
-   `DisplayDate`, une méthode publique surchargée qui est passée de deux paramètres : soit un <xref:System.DateTime> ou <xref:System.DateTimeOffset> valeur pour exprimer dans le calendrier représenté par le `CalendarUtility` objet et la culture dont les règles de mise en forme doivent être utilisées. La façon dont elle retourne la représentation sous forme de chaîne d’une date varie selon que le calendrier cible est pris en charge ou non par la culture dont les règles de mise en forme doivent être utilisées.  
  
 Quel que soit le calendrier utilisé pour créer un <xref:System.DateTime> ou <xref:System.DateTimeOffset> valeur dans cet exemple, que valeur est généralement exprimée comme une date du calendrier grégorien. C’est parce que le <xref:System.DateTime> et <xref:System.DateTimeOffset> types ne conservent pas les informations relatives au calendrier. En interne, elles sont représentées comme nombre de graduations qui se sont écoulées depuis le 1er janvier 0001 à minuit. L’interprétation de ce nombre dépend du calendrier. Pour la plupart des cultures, le calendrier par défaut est le calendrier grégorien.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple requiert une référence à System.Core.dll.  
  
 Compiler le code à la ligne de commande à l’aide de csc.exe ou vb.exe. Pour compiler le code dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], placez-le dans un modèle de projet application console.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)
