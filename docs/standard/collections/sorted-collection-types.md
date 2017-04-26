---
title: "Types de collections triées | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
caps.latest.revision: 16
author: mairaw
ms.author: mairaw
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2ac1552dba8756d033ee02651142476c4a15a485
ms.lasthandoff: 04/18/2017

---
# <a name="sorted-collection-types"></a>Types de collections triées
La classe <xref:System.Collections.SortedList?displayProperty=fullName>, la classe générique <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> et la classe générique <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> sont similaires à la classe <xref:System.Collections.Hashtable> et à la classe générique <xref:System.Collections.Generic.Dictionary%602> dans la mesure où elles implémentent l’interface <xref:System.Collections.IDictionary>, mais elles conservent leurs éléments triés par clé et elles n’ont pas les caractéristiques de récupération et d’insertion O(1) des tables de hachage. Les trois classes ont plusieurs fonctionnalités en commun :  
  
-   Les trois classes implémentent l’interface <xref:System.Collections.IDictionary?displayProperty=fullName>. Les deux classes génériques implémentent également l’interface générique <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>.  
  
-   Chaque élément est une paire clé/valeur utilisée à des fins d’énumération.  
  
    > [!NOTE]
    >  La classe <xref:System.Collections.SortedList> non générique retourne des objets <xref:System.Collections.DictionaryEntry> lorsqu’elle est énumérée, bien que les deux types génériques retournent des objets <xref:System.Collections.Generic.KeyValuePair%602>.  
  
-   Les éléments sont triés selon une implémentation <xref:System.Collections.IComparer?displayProperty=fullName> (pour la classe <xref:System.Collections.SortedList> non générique) ou une implémentation <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> (pour les deux classes génériques).  
  
-   Chaque classe fournit des propriétés qui retournent des collections contenant uniquement les clés ou uniquement les valeurs.  
  
 Le tableau suivant répertorie certaines des différences entre les deux classes de liste triée et la classe <xref:System.Collections.Generic.SortedDictionary%602>.  
  
|Classe non générique <xref:System.Collections.SortedList> et classe générique <xref:System.Collections.Generic.SortedList%602>|Classe générique <xref:System.Collections.Generic.SortedDictionary%602>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Les propriétés qui retournent des clés et des valeurs sont indexées, ce qui permet une récupération indexée efficace.|Aucune récupération indexée.|  
|La récupération est O(log `n`).|La récupération est O(log `n`).|  
|L’insertion et la suppression sont généralement O(`n`). Toutefois, l’insertion est O(1) pour les données qui se trouvent déjà en ordre de tri, de sorte que chaque élément soit ajouté à la fin de la liste. (Cela suppose qu’un redimensionnement n’est pas requis.)|L’insertion et la suppression sont O(log `n`).|  
|Utilise moins de mémoire qu’un <xref:System.Collections.Generic.SortedDictionary%602>.|Utilise plus de mémoire que la classe non générique <xref:System.Collections.SortedList> et la classe générique <xref:System.Collections.Generic.SortedList%602>.|  
  
 Pour les listes triées ou les dictionnaires qui doivent être accessibles simultanément à partir de plusieurs threads, vous pouvez ajouter une logique de tri à une classe qui dérive de <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.  
  
> [!NOTE]
>  Pour les valeurs qui contiennent leurs propres clés (par exemple, des enregistrements d’employés qui contiennent un ID d’employé), vous pouvez créer une collection à clé qui possède certaines caractéristiques d’une liste et certaines caractéristiques d’un dictionnaire en dérivant de la classe générique <xref:System.Collections.ObjectModel.KeyedCollection%602>.  
  
 À compter de [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], la classe <xref:System.Collections.Generic.SortedSet%601> fournit une arborescence auto-équilibrée qui maintient les données en ordre de tri après les insertions, les suppressions et les recherches. Cette classe et la classe <xref:System.Collections.Generic.HashSet%601> class implémentent l’interface <xref:System.Collections.Generic.ISet%601>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.IDictionary?displayProperty=fullName>   
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>   
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>   
 [Types de collections couramment utilisés](../../../docs/standard/collections/commonly-used-collection-types.md)
