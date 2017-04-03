---
title: Annotations LINQ to XML | Microsoft Docs
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
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 13718f509eee46853020cfe1dd27ee85437d2e6d
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-annotations"></a>Annotations LINQ to XML
Les annotations dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] vous permettent d’associer n’importe quel objet arbitraire de n’importe quel type arbitraire à n’importe quel composant XML dans une arborescence XML.  
  
 Pour ajouter une annotation à un composant XML, comme <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, vous appelez la méthode <xref:System.Xml.Linq.XObject.AddAnnotation%2A>. Vous pouvez récupérer des annotations par type.  
  
 Notez que les annotations ne font pas partie du jeu d'informations XML ; elles ne sont pas sérialisées ou désérialisées.  
  
## <a name="methods"></a>Méthodes  
 Vous pouvez utiliser les méthodes suivantes lorsque vous travaillez avec des annotations :  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Ajoute un objet à la liste d’annotations d’un <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Obtient le premier objet annotation du type spécifié auprès d’un <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Obtient une collection d’annotations du type spécifié pour un <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Supprime les annotations du type spécifié dans un <xref:System.Xml.Linq.XObject>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation LINQ to XML avancée (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
