---
title: "Ex&#233;cution d&#39;op&#233;rations de cha&#238;nes ind&#233;pendantes de la culture dans des tableaux | Microsoft Docs"
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
  - "tableaux (.NET Framework), opérations de chaînes indépendantes de la culture"
  - "comparer (paramètre)"
  - "opérations de chaînes indépendantes de la culture, dans les tableaux"
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Ex&#233;cution d&#39;op&#233;rations de cha&#238;nes ind&#233;pendantes de la culture dans des tableaux
Les surcharges des méthodes <xref:System.Array.Sort%2A?displayProperty=fullName> et <xref:System.Array.BinarySearch%2A?displayProperty=fullName> exécutent par défaut des tris dépendants de la culture à l'aide de la propriété <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=fullName>.  Les résultats dépendants de la culture retournés par ces méthodes peuvent varier selon la culture, en raison des différences au niveau des ordres de tri.  Pour supprimer cette dépendance à la culture, utilisez l'une des surcharges de cette méthode qui accepte un paramètre `comparer`.  Le paramètre `comparer` indique l'implémentation de <xref:System.Collections.IComparer> à utiliser lors de la comparaison des éléments du tableau.  Pour le paramètre, spécifiez une classe de comparateur indifférent personnalisé qui utilise <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  La rubrique « Utilisation de la classe SortedList » de la rubrique [Exécution d'opérations de chaînes indépendantes de la culture dans des collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) contient un exemple de classe de comparateur indifférent personnalisé.  
  
 **Remarque** Le passage de **CultureInfo.InvariantCulture** à une méthode de comparaison effectue une comparaison indépendante de la culture.  Toutefois, il n'entraîne pas de comparaison non linguistique, par exemple, pour les chemins d'accès de fichier, les clés de Registre et les variables d'environnement.  Il ne prend pas non plus en charge les décisions de sécurité basées sur le résultat de la comparaison.  Pour une comparaison non linguistique ou la prise en charge des décisions de sécurité dépendantes du résultat, l'application doit utiliser une méthode de comparaison qui accepte une valeur <xref:System.StringComparison>.  L'application doit ensuite passer <xref:System.StringComparison>.  
  
## Voir aussi  
 <xref:System.Array.Sort%2A?displayProperty=fullName>   
 <xref:System.Array.BinarySearch%2A?displayProperty=fullName>   
 <xref:System.Collections.IComparer>   
 [Exécution d'opérations de chaînes indépendantes de la culture](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)