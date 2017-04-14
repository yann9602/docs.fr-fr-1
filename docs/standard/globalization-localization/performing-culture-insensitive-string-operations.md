---
title: "Ex&#233;cution d&#39;op&#233;rations de cha&#238;nes ind&#233;pendantes de la culture | Microsoft Docs"
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
  - "mappages de casse"
  - "mappages de casse personnalisés"
  - "culture, règles de tri personnalisées"
  - "règles de tri personnalisées"
  - "opérations de chaînes indépendantes de la culture, options d’exécution"
  - "culture, mappages de casse personnalisés"
  - "opérations de chaînes indépendantes de la culture, surcharges de méthode"
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Ex&#233;cution d&#39;op&#233;rations de cha&#238;nes ind&#233;pendantes de la culture
La plupart des méthodes .NET Framework qui effectuent par défaut des opérations de chaînes dépendantes de la culture fournissent des surcharges de méthode qui vous permettent de spécifier explicitement la culture à utiliser en passant un paramètre  <xref:System.Globalization.CultureInfo>.  Ces surcharges vous permettent d'éliminer les différences culturelles des règles de tri et des mappages de casse et garantissent des résultats indépendants de la culture.  
  
 Cette section contient les rubriques suivantes qui montrent comment effectuer des opérations de chaînes indépendantes de la culture à l'aide des méthodes du .NET Framework dépendantes de la culture par défaut.  
  
## Dans cette section  
 [Exécution de comparaisons de chaînes indépendantes de la culture](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 Décrit comment utiliser les <xref:System.String.Compare%2A?displayProperty=fullName> et méthodes <xref:System.String.CompareTo%2A?displayProperty=fullName> pour exécuter des comparaisons de chaînes indépendantes de la culture.  
  
 [Exécution de changements de casse indépendants de la culture](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 Décrit comment utiliser les méthodes <xref:System.String.ToUpper%2A?displayProperty=fullName>, <xref:System.String.ToLower%2A?displayProperty=fullName>, <xref:System.Char.ToUpper%2A?displayProperty=fullName>et <xref:System.Char.ToLower%2A?displayProperty=fullName> pour exécuter des changements de casse indépendants de la culture.  
  
 [Exécution d'opérations de chaînes indépendantes de la culture dans des collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 Explique comment utiliser la [classe CaseInsensitiveComparer](frlrfSystemCollectionsCaseInsensitiveComparerClassTopic), la classe <xref:System.Collections.CaseInsensitiveHashCodeProvider>, la [classe SortedList](frlrfSystemCollectionsSortedListClassTopic), la [méthode ArrayList.Sort](https://msdn.microsoft.com/en-us/library/system.collections.arraylist.sort.aspx) et la [méthode CollectionsUtil.CreateCaseInsensitiveHashtable](frlrfSystemCollectionsSpecializedCollectionsUtilClassCreateCaseInsensitiveHashtableTopic) pour effectuer des opérations indépendantes de la culture dans des collections.  
  
 [Exécution d'opérations de chaînes indépendantes de la culture dans des tableaux](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 Décrit comment utiliser les méthodes <xref:System.Array.Sort%2A?displayProperty=fullName> et <xref:System.Array.BinarySearch%2A?displayProperty=fullName> pour exécuter des comparaisons indépendantes de la culture dans des tableaux.  
  
## Rubriques connexes  
 [Opérations de chaînes indépendantes de la culture](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Explique pourquoi vous devez tenir compte de la culture lorsque vous effectuez des opérations de chaînes et contient des instructions qui vous indiquent quand vous pouvez effectuer des opérations dépendantes de la culture et des opérations indépendantes de la culture.