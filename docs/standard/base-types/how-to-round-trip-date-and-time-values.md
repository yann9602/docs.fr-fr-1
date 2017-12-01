---
title: 'Comment : effectuer un aller-retour de valeurs de date et d''heure'
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
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 515a29e279cfa8fc100e0612fc19df7abc6a3b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a>Comment : effectuer un aller-retour de valeurs de date et d'heure
Dans de nombreuses applications, une valeur de date et d’heure est destinée à identifier clairement un point unique dans le temps. Cette rubrique montre comment enregistrer et restaurer un <xref:System.DateTime> valeur, un <xref:System.DateTimeOffset> valeur et une valeur de date et d’heure avec le temps de zone d’informations afin que la valeur restaurée identifie le même temps que la valeur enregistrée.  
  
### <a name="to-round-trip-a-datetime-value"></a>Pour effectuer un aller-retour d’une valeur DateTime  
  
1.  Convertir le <xref:System.DateTime> valeur à sa représentation sous forme de chaîne en appelant le <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> méthode avec le spécificateur de format « o ».  
  
2.  Enregistrer la représentation sous forme de chaîne de la <xref:System.DateTime> valeur dans un fichier ou passez-la dans un processus, un domaine d’application ou une limite d’ordinateur.  
  
3.  Récupérer la chaîne qui représente le <xref:System.DateTime> valeur.  
  
4.  Appelez le <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> (méthode) et passez <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> comme valeur de le `styles` paramètre.  
  
 L’exemple suivant montre comment effectuer un aller-retour d’une <xref:System.DateTime> valeur.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 Lors de l’aller-retour un <xref:System.DateTime> valeur, cette technique conserve l’heure à tout moment locaux et universels. Par exemple, si une variable locale <xref:System.DateTime> valeur est enregistrée sur un système aux États-Unis. Pacifique (États-Unis) et qu’elle est restaurée sur un système situé dans le fuseau horaire Centre (États-Unis), la date et l’heure restaurées ont deux heures de retard par rapport à l’heure d’origine, ce qui reflète le décalage horaire entre ces deux fuseaux horaires. En revanche, cette technique n’est pas nécessairement exacte pour les heures non spécifiées. Tous les <xref:System.DateTime> dont les valeurs <xref:System.DateTime.Kind%2A> propriété <xref:System.DateTimeKind.Unspecified> sont traités comme s’ils sont locales. Si ce n’est pas le cas, le <xref:System.DateTime> identifiera pas le point correct dans le temps. La solution pour contourner cette limitation consiste à associer étroitement une valeur de date et d’heure avec son fuseau horaire pour l’opération d’enregistrement et de restauration.  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a>Pour effectuer un aller-retour d’une valeur DateTimeOffset  
  
1.  Convertir le <xref:System.DateTimeOffset> valeur à sa représentation sous forme de chaîne en appelant le <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> méthode avec le spécificateur de format « o ».  
  
2.  Enregistrer la représentation sous forme de chaîne de la <xref:System.DateTimeOffset> valeur dans un fichier ou passez-la dans un processus, un domaine d’application ou une limite d’ordinateur.  
  
3.  Récupérer la chaîne qui représente le <xref:System.DateTimeOffset> valeur.  
  
4.  Appelez le <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> (méthode) et passez <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> comme valeur de le `styles` paramètre.  
  
 L’exemple suivant montre comment effectuer un aller-retour d’une <xref:System.DateTimeOffset> valeur.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 Cette technique identifie toujours clairement un <xref:System.DateTimeOffset> valeur comme un point unique dans le temps. La valeur peut ensuite être convertie en temps universel coordonné (UTC), en appelant le <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> (méthode), ou il peut être convertie en heure d’un fuseau horaire particulier en appelant le <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> ou <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> (méthode). La limitation majeure de cette technique est que la date et l’heure arithmétiques, lorsqu’un <xref:System.DateTimeOffset> valeur qui représente l’heure dans un fuseau horaire particulier, peut ne pas produire des résultats précis pour ce fuseau horaire. C’est parce que lorsqu’un <xref:System.DateTimeOffset> valeur est instanciée, il est dissocié de son fuseau horaire. Ainsi, les règles d’ajustement de ce fuseau horaire ne sont plus applicables quand vous effectuez des calculs de date et d’heure. Vous pouvez contourner ce problème en définissant un type personnalisé qui inclut à la fois une valeur de date et heure et son fuseau horaire correspondant.  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Pour effectuer un aller-retour d’une valeur de date et d’heure avec son fuseau horaire  
  
1.  Définissez une classe ou une structure avec deux champs. Le premier champ est un <xref:System.DateTime> ou un <xref:System.DateTimeOffset> objet et le second est un <xref:System.TimeZoneInfo> objet. L’exemple suivant est une version simple d’un tel type.  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  Marquez la classe avec le <xref:System.SerializableAttribute> attribut.  
  
3.  Sérialiser l’objet en utilisant la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> (méthode).  
  
4.  Restaurer l’objet en utilisant la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> (méthode).  
  
5.  Effectuez un cast (en c#) ou convertir (en Visual Basic) l’objet désérialisé en un objet du type approprié.  
  
 L’exemple suivant illustre comment effectuer un aller-retour un objet qui stocke les informations de date et heure et fuseau horaire.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 Cette technique doit toujours refléter clairement le point correct d’exécution à la fois avant et après qu’il est enregistré et restauré, que l’implémentation de l’objet de fuseau horaire et l’heure et date combinée n’autorise pas la valeur de date devenir désynchronisés avec le valeur de fuseau horaire.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Ces exemples nécessitent :  
  
-   Que les espaces de noms suivant importés avec c# `using` instructions ou [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` instructions :  
  
    -   <xref:System>(C# uniquement).  
  
    -   <xref:System.Globalization?displayProperty=nameWithType>.  
  
    -   <xref:System.IO?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.  
  
-   Une référence à System.Core.dll.  
  
-   Chaque exemple de code, autre que le `DateInTimeZone` (classe), doit être inclus dans une classe ou un module Visual Basic, encapsulé dans des méthodes et appelé à partir de la `Main` (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution d’opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [Standard Date and Time Format Strings](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
