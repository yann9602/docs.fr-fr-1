---
title: LINQ to XML Annotations2 | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1f2e5bea1cde74548daa1697b6a0a819e3eba3e4
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-annotations"></a>Annotations LINQ to XML
Annotations dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] vous permettent d’associer n’importe quel objet arbitraire de n’importe quel type arbitraire avec n’importe quel composant XML dans une arborescence XML.  
  
 Pour ajouter une annotation à un composant XML, tel qu’un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XAttribute>, vous appelez le <xref:System.Xml.Linq.XObject.AddAnnotation%2A>méthode.</xref:System.Xml.Linq.XObject.AddAnnotation%2A> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> Vous pouvez récupérer des annotations par type.  
  
 Notez que les annotations ne font pas partie du jeu d'informations XML ; elles ne sont pas sérialisées ou désérialisées.  
  
## <a name="methods"></a>Méthodes  
 Vous pouvez utiliser les méthodes suivantes lorsque vous travaillez avec des annotations :  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A></xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Ajoute un objet à la liste d’annotation d’un <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>|  
|<xref:System.Xml.Linq.XObject.Annotation%2A></xref:System.Xml.Linq.XObject.Annotation%2A>|Obtient le premier objet annotation du type spécifié à partir d’un <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>|  
|<xref:System.Xml.Linq.XObject.Annotations%2A></xref:System.Xml.Linq.XObject.Annotations%2A>|Obtient une collection d’annotations du type spécifié pour un <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A></xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Supprime les annotations du type spécifié à partir d’un <xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>|  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to XML (Visual Basic) de la programmation avancée](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
