---
title: LINQ to XML pour les utilisateurs XPath (Visual Basic) | Documents Microsoft
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
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 376e7d67edf1719dc1a020974b38e3600831d660
ms.lasthandoff: 03/13/2017


---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>LINQ to XML pour les utilisateurs XPath (Visual Basic)
Cet ensemble de rubriques illustre un certain nombre d'expressions XPath et leurs équivalents [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Tous les exemples utilisent la fonctionnalité XPath dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] qui est mis à disposition par les méthodes d’extension dans <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</xref:System.Xml.XPath.Extensions?displayProperty=fullName> L'exemple exécute à la fois l'expression XPath et l'expression [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. Chaque exemple compare ensuite les résultats des deux requêtes et confirme que l'expression XPath est fonctionnellement équivalente à la requête [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. Étant donné que les deux types de requêtes retournent des nœuds de la même arborescence XML, la comparaison des résultats de requêtes est effectuée à l'aide de l'identité référentielle.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Comparaison de XPath et LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|Fournit une vue d'ensemble des similitudes et différences entre XPath et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].|  
|[Comment : rechercher un élément enfant (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|Compare l’axe des éléments enfants XPath à la [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XContainer.Element%2A>méthode.</xref:System.Xml.Linq.XContainer.Element%2A><br /><br /> L'expression XPath associée est : `"DeliveryNotes"`.|  
|[Comment : rechercher une liste d’éléments enfants (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|Compare l’axe des éléments enfants XPath à la [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A>axe.</xref:System.Xml.Linq.XContainer.Elements%2A><br /><br /> L'expression XPath associée est : `"./*"`|  
|[Comment : rechercher l’élément racine (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md)|Compare comment obtenir l'élément racine avec XPath et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> L'expression XPath associée est : `"/PurchaseOrders"`|  
|[Comment : rechercher des éléments descendants (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md)|Compare comment obtenir les éléments descendants avec un nom particulier avec XPath et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> L'expression XPath associée est : `"//Name"`|  
|[Comment : filtrer sur un attribut (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Compare comment obtenir les éléments descendants avec un nom spécifié, et avec un attribut avec une valeur spécifiée avec XPath et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> L'expression XPath associée est : `".//Address[@Type='Shipping']"`|  
|[Comment : rechercher des éléments connexes (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|Compare comment obtenir un élément en sélectionnant un attribut auquel il est fait référence par la valeur d'un autre élément avec XPath et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> L'expression XPath associée est : `".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Comment : rechercher des éléments dans un Namespace (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace.md)|Compare l’utilisation de l’expression XPath <xref:System.Xml.XmlNamespaceManager>classe avec la [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] <xref:System.Xml.Linq.XName.Namespace%2A>Propriétés de la <xref:System.Xml.Linq.XName>classe pour travailler avec des espaces de noms XML.</xref:System.Xml.Linq.XName> </xref:System.Xml.Linq.XName.Namespace%2A> </xref:System.Xml.XmlNamespaceManager><br /><br /> L'expression XPath associée est : `"./aw:*"`|  
|[Comment : rechercher les frères (XPath-LINQ to XML) précédents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md)|Compare l’expression XPath `preceding-sibling` axe pour le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] enfant <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName>axe.</xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName><br /><br /> L'expression XPath associée est : `"preceding-sibling::*"`|  
|[Comment : rechercher les Descendants d’un élément enfant (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|Compare comment obtenir les éléments descendants d'un élément enfant avec un nom particulier avec XPath et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> L'expression XPath associée est : `"./Paragraph//Text/text()"`|  
|[Comment : rechercher une Union de deux chemins d’emplacements (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath.md)|Compare l’utilisation de l’opérateur d’union, `&#124;`, dans XPath avec le <xref:System.Linq.Enumerable.Concat%2A>opérateur de requête standard dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</xref:System.Linq.Enumerable.Concat%2A><br /><br /> L'expression XPath associée est : `"//Category&#124;//Price"`|  
|[Comment : rechercher des nœuds frères (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|Compare comment rechercher tous les frères d'un nœud qui ont un nom spécifique avec XPath et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. <br /><br /> L'expression XPath associée est : `"../Book"`|  
|[Comment : rechercher un attribut du Parent (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Compare comment naviguer jusqu'à l'élément parent et rechercher un attribut associé à l'aide de XPath et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> L'expression XPath associée est : `"../@id"`|  
|[Comment : rechercher des attributs de frères avec un nom spécifique (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name.md)|Compare comment rechercher des attributs spécifiques des frères du nœud de contexte avec XPath et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> L'expression XPath associée est : `"``../Book/@id``"`|  
|[Comment : rechercher des éléments avec un attribut spécifique (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute.md)|Compare comment rechercher tous les éléments contenant un attribut spécifique à l'aide de XPath et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]. <br /><br /> L'expression XPath associée est : `"./*[@Select]"`|  
|[Comment : rechercher des éléments enfants en fonction de la Position (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position.md)|Compare comment rechercher un élément en fonction de sa position relative à l'aide de XPath et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> L'expression XPath associée est : `"Test[position() >= 2 and position() <= 4]"`|  
|[Comment : rechercher le frère précédent (XPath-LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|Compare comment faire rechercher le frère précédent d'un nœud à l'aide de XPath et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].<br /><br /> L'expression XPath associée est : `"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.XPath?displayProperty=fullName></xref:System.Xml.XPath?displayProperty=fullName>   
 [Interrogation d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)   
 [Traitement des données XML à l’aide du modèle de données XPath](http://msdn.microsoft.com/library/536c6fce-1453-4654-9c72-bca54d47e081)
