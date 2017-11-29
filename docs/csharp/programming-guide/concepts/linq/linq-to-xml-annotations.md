---
title: Annotations LINQ to XML3
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eadbc55ac6188fa3634745bf8bb222f07675a308
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-annotations"></a>Annotations LINQ to XML
Les annotations dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vous permettent d’associer n’importe quel objet arbitraire de n’importe quel type arbitraire à n’importe quel composant XML dans une arborescence XML.  
  
 Pour ajouter une annotation à un composant XML, tel qu'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, vous appelez la méthode <xref:System.Xml.Linq.XObject.AddAnnotation%2A>. Vous pouvez récupérer des annotations par type.  
  
 Notez que les annotations ne font pas partie du jeu d'informations XML ; elles ne sont pas sérialisées ou désérialisées.  
  
## <a name="methods"></a>Méthodes  
 Vous pouvez utiliser les méthodes suivantes lorsque vous travaillez avec des annotations :  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Ajoute un objet à la liste d'annotation de <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Obtient le premier objet annotation du type spécifié de <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Obtient une collection d'annotations du type spécifié pour un objet <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Supprime les annotations du type spécifié d’un objet <xref:System.Xml.Linq.XObject>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation LINQ to XML avancée (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
