---
title: "Types de collections tri&#233;es | Microsoft Docs"
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
  - "collections (.NET Framework), SortedList (type de collection)"
  - "regrouper des données dans des collections, SortedList (type de collection)"
  - "SortedDictionary (type de collection)"
  - "SortedList (classe), regrouper des données dans des collections"
  - "SortedList (type de collection)"
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# Types de collections tri&#233;es
La classe <xref:System.Collections.SortedList?displayProperty=fullName>, la classe générique <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> et la classe générique <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> sont semblables à la classe <xref:System.Collections.Hashtable> et à la classe générique <xref:System.Collections.Generic.Dictionary%602> car elles implémentent l'interface <xref:System.Collections.IDictionary>, mais conservent leurs éléments triés par clé et ne possèdent pas les caractéristiques d'insertion et de récupération O\(1\) des tables de hachage.  Les trois classes possèdent plusieurs fonctionnalités en commun :  
  
-   Les trois classes implémentent toutes l'interface <xref:System.Collections.IDictionary?displayProperty=fullName>.  Les deux classes génériques implémentent également l'interface générique <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>.  
  
-   Chaque élément est une paire clé\/valeur à des fins d'énumération.  
  
    > [!NOTE]
    >  La classe <xref:System.Collections.SortedList> non générique retourne des objets <xref:System.Collections.DictionaryEntry> lorsqu'elle est énumérée, même si les deux types génériques retournent des objets <xref:System.Collections.Generic.KeyValuePair%602>.  
  
-   Les éléments sont triés selon une implémentation d'<xref:System.Collections.IComparer?displayProperty=fullName> \(pour la classe <xref:System.Collections.SortedList> non générique\) ou une implémentation d'<xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> \(pour les deux classes génériques\).  
  
-   Chaque classe fournit des propriétés qui retournent des collections contenant uniquement les clés ou uniquement les valeurs.  
  
 Le tableau suivant répertorie certaines des différences entre les deux classes de liste triée et la classe <xref:System.Collections.Generic.SortedDictionary%602>.  
  
|Classe non générique <xref:System.Collections.SortedList> et classe générique <xref:System.Collections.Generic.SortedList%602>|Classe générique <xref:System.Collections.Generic.SortedDictionary%602>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Les propriétés qui retournent des clés et des valeurs sont indexées, entraînant ainsi une extraction indexée efficace.|Aucune extraction indexée.|  
|L'extraction correspond à O\(log `n`\).|L'extraction correspond à O\(log `n`\).|  
|L'insertion et la suppression correspondent généralement à O\(`n`\) ; toutefois, l'insertion correspond à O\(1\) pour les données qui sont déjà dans l'ordre de tri, afin que chaque élément soit ajouté à la fin de la liste. \(Cela suppose qu'il n'est pas nécessaire d'effectuer un redimensionnement.\)|L'insertion et la suppression correspondent à O \(log `n`\).|  
|Requiert moins de mémoire qu'un <xref:System.Collections.Generic.SortedDictionary%602>.|Requiert plus de mémoire que la classe non générique <xref:System.Collections.SortedList> et la classe générique <xref:System.Collections.Generic.SortedList%602>.|  
  
 Pour les listes ou les dictionnaires triés qui doivent être accessibles simultanément à partir de plusieurs threads, vous pouvez ajouter une logique de tri à une classe qui dérive de <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.  
  
> [!NOTE]
>  Pour les valeurs qui contiennent leurs propres clés \(par exemple, les enregistrements d'employé qui contiennent un numéro d'ID de l'employé\), vous pouvez créer une collection à clé qui possède certaines caractéristiques d'une liste et certaines caractéristiques d'un dictionnaire, en dérivant de la classe générique <xref:System.Collections.ObjectModel.KeyedCollection%602>.  
  
 À partir du [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], la classe <xref:System.Collections.Generic.SortedSet%601> fournit une arborescence autonome qui maintient les données triées dans un certain ordre après les insertions, les suppressions et les recherches.  Cette classe et la classe<xref:System.Collections.Generic.HashSet%601> implémentent l'interface <xref:System.Collections.Generic.ISet%601>.  
  
## Voir aussi  
 <xref:System.Collections.IDictionary?displayProperty=fullName>   
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>   
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>   
 [Types de collections couramment utilisés](../../../docs/standard/collections/commonly-used-collection-types.md)