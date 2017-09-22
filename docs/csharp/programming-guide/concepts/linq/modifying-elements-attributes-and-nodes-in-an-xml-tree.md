---
title: "Modification d’éléments, d’attributs et de nœuds dans une arborescence XML3"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 432587324fbd3560da924c7516a743e623a38b1e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>Modification d’éléments, d’attributs et de nœuds dans une arborescence XML
Le tableau suivant résume les méthodes et propriétés que vous pouvez utiliser pour modifier un élément, ses éléments enfants ou ses attributs.  
  
 Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XElement>.  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Remplace un élément par du code XML analysé.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Supprime tout le contenu (nœuds enfants et attributs) d'un élément.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Supprime les attributs d'un élément.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Remplace tout le contenu (nœuds enfants et attributs) d'un élément.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Remplace les attributs d'un élément.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Définit la valeur d'un attribut. Crée l'attribut s'il n'existe pas. Si la valeur est définie à `null`, supprime l'attribut.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Définit la valeur d'un élément enfant. Crée l'élément s'il n'existe pas. Si la valeur est définie à `null`, supprime l'élément.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Remplace le contenu (nœuds enfants) d'un élément par le texte spécifié.|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Définit la valeur d'un élément.|  
  
 Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XAttribute>.  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Définit la valeur d'un attribut.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Définit la valeur d'un attribut.|  
  
 Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XNode> (y compris un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Remplace un nœud par du nouveau contenu.|  
  
 Les méthodes suivantes modifient un objet <xref:System.Xml.Linq.XContainer> (un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Remplace les nœuds enfants par du nouveau contenu.|  
  
## <a name="see-also"></a>Voir aussi  
 [Modification d’arborescences XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

