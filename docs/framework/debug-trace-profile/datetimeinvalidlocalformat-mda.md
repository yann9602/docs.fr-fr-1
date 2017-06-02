---
title: "dateTimeInvalidLocalFormat MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "dates [.NET Framework], formatting"
  - "invalid date time local format"
  - "invalid local formats"
  - "MDAs (managed debugging assistants), invalid local formats"
  - "managed debugging assistants (MDAs), invalid local formats"
  - "dateTimeInvalidLocalFormat MDA"
  - "date formatting"
  - "time formatting"
  - "UTC formatting"
ms.assetid: c4a942bb-2651-4b65-8718-809f892a0659
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# dateTimeInvalidLocalFormat MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `dateTimeInvalidLocalFormat` est activé lorsqu'une instance de <xref:System.DateTime> stockée en temps universel \(UTC, Universal Coordinated Time\) est mise en forme à l'aide d'un format conçu uniquement pour des instances de <xref:System.DateTime> locales.  Cet Assistant Débogage managé n'est pas activé pour les instances de <xref:System.DateTime> par défaut ou non spécifiées.  
  
## Symptôme  
 Une application sérialise manuellement une instance de <xref:System.DateTime> en temps universel à l'aide d'un format local :  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffzzz"));  
```  
  
### Cause  
 Le format « z » pour la méthode <xref:System.DateTime.ToString%2A?displayProperty=fullName> inclut l'offset de fuseau horaire local, par exemple, « \+10: 00 » pour l'heure de Sydney.  Comme tel, il ne produit un résultat significatif que si <xref:System.DateTime> a une valeur locale.  S'il s'agit d'une valeur en heure UTC, <xref:System.DateTime.ToString%2A?displayProperty=fullName> inclut l'offset de fuseau horaire local, mais il n'affiche pas et n'ajuste pas le spécificateur de fuseau horaire.  
  
### Résolution  
 Les instances de <xref:System.DateTime> en temps universel doivent être mises en forme d'une façon qui indique leur format UTC.  Le format recommandé consiste à utiliser un « Z » pour désigner une UTC :  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("yyyy-MM-dd'T'HH:mm:ss.fffffffZ"));  
```  
  
 Il existe également un format « o » qui sérialise <xref:System.DateTime> en utilisant la propriété <xref:System.DateTime.Kind%2A>, laquelle effectue une sérialisation correcte qu'il s'agisse d'une instance locale, en temps universel ou non spécifiée :  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
Serialize(myDateTime.ToString("o"));  
```  
  
## Effet sur le runtime  
 Cet Assistant Débogage managé n'affecte pas le runtime.  
  
## Sortie  
 Il n'y a aucune sortie spéciale résultant de l'activation de cet Assistant Débogage managé. Toutefois, la pile des appels peut être utilisée pour déterminer l'emplacement de l'appel à <xref:System.DateTime.ToString%2A> qui a activé l'Assistant Débogage managé.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <dateTimeInvalidLocalFormat />  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
 Prenons l'exemple d'une application qui sérialise indirectement une valeur <xref:System.DateTime> en temps universel en utilisant la classe <xref:System.Xml.XmlConvert> ou <xref:System.Data.DataSet>, de la manière suivante.  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XMLConvert.ToString(myDateTime);  
```  
  
 Les sérialisations de <xref:System.Xml.XmlConvert> et <xref:System.Data.DataSet> utilisent par défaut des formats locaux pour la sérialisation.  D'autres options sont nécessaires pour sérialiser d'autres types de valeurs <xref:System.DateTime>, tels que le temps universel.  
  
 Pour cet exemple précis, passez `XmlDateTimeSerializationMode.RoundtripKind` à l'appel `ToString` sur `XmlConvert`.  Les données sont sérialisées en heure UTC.  
  
 Lors de l'utilisation d'un <xref:System.Data.DataSet>, affectez <xref:System.Data.DataSetDateTime> à la propriété <xref:System.Data.DataColumn.DateTimeMode%2A> sur l'objet <xref:System.Data.DataColumn>.  
  
```  
DateTime myDateTime = DateTime.UtcNow;  
String serialized = XmlConvert.ToString(myDateTime,   
    XmlDateTimeSerializationMode.RoundtripKind);  
```  
  
## Voir aussi  
 <xref:System.Globalization.DateTimeFormatInfo>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)