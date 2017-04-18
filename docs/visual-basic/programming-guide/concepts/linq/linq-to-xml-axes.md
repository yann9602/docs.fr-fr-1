---
title: Axes LINQ to XML (Visual Basic) | Documents Microsoft
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
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4d6466a78c3a8e9d21e30f2d3cf8a49ed89dafbf
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-axes-visual-basic"></a>Axes LINQ to XML (Visual Basic)
Après avoir créé une arborescence XML ou chargé un document XML dans une arborescence XML, vous pouvez l'interroger pour rechercher des éléments et des attributs et récupérer leurs valeurs.  
  
 Pour pouvoir écrire des requêtes, vous devez comprendre ce que sont les axes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. Il existe deux types de méthodes d’axe : tout d’abord, il existe des méthodes que vous appelez sur un seul <xref:System.Xml.Linq.XElement>objet <xref:System.Xml.Linq.XDocument>objet, ou <xref:System.Xml.Linq.XNode>objet.</xref:System.Xml.Linq.XNode> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> Ces méthodes opèrent sur un seul objet et renvoient une collection de <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, ou <xref:System.Xml.Linq.XNode>objets.</xref:System.Xml.Linq.XNode> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> En second lieu, il y a des méthodes d'extension qui opèrent sur des collections et retournent des collections. Les méthodes d'extension énumèrent la collection source, appellent la méthode d'axe appropriée sur chaque élément dans la collection et concatènent les résultats.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[LINQ to XML Axes présentation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Définit les axes et explique comment les utiliser dans le contexte des requêtes [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].|  
|[Comment : récupérer une Collection d’éléments (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Introduit la <xref:System.Xml.Linq.XContainer.Elements%2A>méthode.</xref:System.Xml.Linq.XContainer.Elements%2A> Cette méthode récupère une collection d’éléments enfants d’un élément.|  
|[Comment : récupérer la valeur d’un élément (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Montre comment obtenir les valeurs d'éléments.|  
|[Comment : filtrer sur des noms d’élément (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Montre comment filtrer les noms d'éléments lors de l'utilisation des axes.|  
|[Comment : chaîner des appels de méthode d’axe (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Montre comment chaîner les appels aux méthodes d'axe.|  
|[Comment : récupérer un seul élément enfant (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Montre comment récupérer un seul élément enfant d’un élément, étant donné le nom d’étiquette de l’élément enfant.|  
|[Comment : récupérer une Collection d’attributs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Introduit la <xref:System.Xml.Linq.XElement.Attributes%2A>méthode.</xref:System.Xml.Linq.XElement.Attributes%2A> Cette méthode récupère les attributs d'un élément.|  
|[Comment : récupérer un seul attribut (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Montre comment récupérer un seul attribut d'un élément, étant donné le nom de l'attribut.|  
|[Comment : récupérer la valeur d’un attribut (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Montre comment obtenir les valeurs d'attributs.|  
|[Comment : récupérer la valeur superficielle d’un élément (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Indique comment récupérer la valeur superficielle d'un élément.|  
|[Axes intégrés au langage en Visual Basic (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|Résume les [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] axes intégrés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)
