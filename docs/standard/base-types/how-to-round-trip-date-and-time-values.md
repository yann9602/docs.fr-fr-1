---
title: "Comment&#160;: effectuer un aller-retour de valeurs de date et d&#39;heure | Microsoft Docs"
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
  - "aller-retour de valeurs de date et d'heure"
  - "dates (.NET Framework), valeurs aller-retour"
  - "fuseaux horaires (.NET Framework), valeurs de date et d’heure aller-retour"
  - "heure (.NET Framework), valeurs aller-retour"
  - "mise en forme de chaînes (.NET Framework), valeurs aller-retour"
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: effectuer un aller-retour de valeurs de date et d&#39;heure
Dans de nombreuses applications, une valeur de date et d'heure est destinée à identifier clairement un point unique dans le temps.  Cette rubrique indique comment enregistrer et restaurer une valeur <xref:System.DateTime>, une valeur <xref:System.DateTimeOffset> et une valeur de date et d'heure avec des informations de fuseau horaire afin que la valeur restaurée identifie la même heure que la valeur enregistrée.  
  
### Pour effectuer un aller\-retour d'une valeur DateTime  
  
1.  Convertissez la valeur <xref:System.DateTime> en représentation sous forme de chaîne en appelant la méthode <xref:System.DateTime.ToString%28System.String%29?displayProperty=fullName> avec le spécificateur de format "o".  
  
2.  Enregistrez la représentation sous forme de chaîne de la valeur <xref:System.DateTime> dans un fichier ou passez\-la dans un processus, un domaine d'application ou une limite d'ordinateur.  
  
3.  Récupérez la chaîne qui représente la valeur <xref:System.DateTime>.  
  
4.  Appelez la méthode <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=fullName> et passez <xref:System.Globalization.DateTimeStyles?displayProperty=fullName> comme valeur du paramètre `styles`.  
  
 L'exemple suivant montre comment effectuer un aller\-retour d'une valeur <xref:System.DateTime>.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 Lorsque vous effectuez un aller\-retour d'une valeur <xref:System.DateTime>, cette technique conserve l'heure pour toutes les heures locales et universelles.  Par exemple, si une valeur locale <xref:System.DateTime> est stockée sur un système du Pacifique et est restaurée sur un système à la zone d'heure du Centre des États\-Unis, la date et l'heure restaurée sera deux heures une valeur postérieure à l'heure d'origine, qui reflète la différence de temps entre les deux fuseaux horaires.  Toutefois, cette technique n'est pas nécessairement exacte pour les heures non spécifiées.  Toutes les valeurs <xref:System.DateTime> dont la propriété <xref:System.DateTime.Kind%2A> est <xref:System.DateTimeKind> sont traitées comme des heures locales.  Si ce n'est pas le cas, le <xref:System.DateTime> n'identifiera pas le point correct dans le temps.  Vous pouvez contourner cette limitation en associant étroitement une valeur de date et d'heure à son fuseau horaire pour l'enregistrement et la restauration.  
  
### Pour effectuer un aller\-retour d'une valeur DateTimeOffset  
  
1.  Convertissez la valeur <xref:System.DateTimeOffset> en représentation sous forme de chaîne en appelant la méthode <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=fullName> avec le spécificateur de format "o".  
  
2.  Enregistrez la représentation sous forme de chaîne de la valeur <xref:System.DateTimeOffset> dans un fichier ou passez\-la dans un processus, un domaine d'application ou une limite d'ordinateur.  
  
3.  Récupérez la chaîne qui représente la valeur <xref:System.DateTimeOffset>.  
  
4.  Appelez la méthode <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=fullName> et passez <xref:System.Globalization.DateTimeStyles?displayProperty=fullName> comme valeur du paramètre `styles`.  
  
 L'exemple suivant montre comment effectuer un aller\-retour d'une valeur <xref:System.DateTimeOffset>.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 Cette technique identifie toujours clairement une valeur <xref:System.DateTimeOffset> comme point unique dans le temps.  La valeur peut ensuite être convertie en temps universel en appelant la méthode <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=fullName>, ou elle peut être convertie en heure d'un fuseau horaire particulier en appelant la méthode <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=fullName> ou <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=fullName>.  La limitation majeure de cette technique est que l'arithmétique de date et d'heure, lorsqu'elle est effectuée sur une valeur <xref:System.DateTimeOffset> qui représente l'heure d'un fuseau horaire particulier, est susceptible de ne pas produire de résultats exacts pour ce fuseau horaire.  En effet, lorsqu'une valeur <xref:System.DateTimeOffset> est instanciée, elle est dissociée de son fuseau horaire.  Par conséquent, les règles d'ajustement de ce fuseau horaire ne peuvent plus être appliquées lorsque vous effectuez des calculs de date et d'heure.  Vous pouvez contourner ce problème en définissant un type personnalisé qui inclut une valeur de date et d'heure et son fuseau horaire.  
  
### Pour effectuer un aller\-retour d'une valeur de date et d'heure avec son fuseau horaire  
  
1.  Définissez une classe ou une structure avec deux champs.  Le premier champ est un objet <xref:System.DateTime> ou <xref:System.DateTimeOffset>, et le second est un objet <xref:System.TimeZoneInfo>.  L'exemple suivant est une version simple de ce type.  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  Marquez la classe avec l'attribut <xref:System.SerializableAttribute>.  
  
3.  Sérialisez l'objet en utilisant la méthode <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>.  
  
4.  Restaurez l'objet en utilisant la méthode <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>.  
  
5.  Effectuez un cast \(en C\#\) ou convertissez \(en Visual Basic\) l'objet désérialisé en un objet du type approprié.  
  
 L'exemple suivant illustre comment effectuer un aller\-retour d'un objet qui stocke des informations de date et d'heure et des informations de fuseau horaire.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 Cette technique doit toujours refléter clairement le point correct dans le temps avant et après son enregistrement et sa restauration, à condition que l'implémentation de la date et heure et de l'objet de fuseau horaire n'autorise pas la désynchronisation de la valeur de date avec la valeur de fuseau horaire.  
  
## Compilation du code  
 Ces exemples nécessitent :  
  
-   que les espaces de noms suivants soient importés avec des instructions `using` C\# ou des instructions `Imports` [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] :  
  
    -   <xref:System> \(C\# uniquement\).  
  
    -   <xref:System.Globalization?displayProperty=fullName>.  
  
    -   <xref:System.IO?displayProperty=fullName>.  
  
    -   <xref:System.Runtime.Serialization?displayProperty=fullName>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=fullName>.  
  
-   Référence à System.Core.dll.  
  
-   Chaque exemple de code, autre que la classe `DateInTimeZone`, doit être inclus dans une classe ou un module Visual Basic, encapsulé dans des méthodes, et appelé par la méthode `Main`.  
  
## Voir aussi  
 [Exécution d'opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)   
 [Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)   
 [Chaînes de format de date et d'heure standard](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)