---
title: LINQ to XML pour les utilisateurs XPath (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 91774511-1dca-4f06-ac0b-913746f104fe
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 69109cc8541970695d463e6163bf4d63925ca5bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-xml-for-xpath-users-c"></a>LINQ to XML pour les utilisateurs XPath (C#)
Cet ensemble de rubriques illustre un certain nombre d'expressions XPath et leurs équivalents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Tous les exemples utilisent la fonctionnalité XPath dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] accessible par la méthode d'extension dans <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>. L'exemple exécute à la fois l'expression XPath et l'expression [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Chaque exemple compare ensuite les résultats des deux requêtes et confirme que l'expression XPath est fonctionnellement équivalente à la requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Étant donné que les deux types de requêtes retournent des nœuds de la même arborescence XML, la comparaison des résultats de requêtes est effectuée à l'aide de l'identité référentielle.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Comparaison de XPath et LINQ to XML](../../../../csharp/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|Fournit une vue d'ensemble des similitudes et différences entre XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[Guide pratique pour rechercher un élément enfant (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-child-element-xpath-linq-to-xml.md)|Compare l’axe des éléments enfants XPath à la méthode [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A>.<br /><br /> L'expression XPath associée est : `"DeliveryNotes"`.|  
|[Guide pratique pour rechercher une liste d’éléments enfants (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|Compare l’axe des éléments enfants XPath à l’axe [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A>.<br /><br /> L'expression XPath associée est : `"./*"`|  
|[Guide pratique pour rechercher l’élément racine (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-root-element-xpath-linq-to-xml.md)|Compare comment obtenir l'élément racine avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"/PurchaseOrders"`|  
|[Guide pratique pour rechercher des éléments descendants (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendant-elements-xpath-linq-to-xml.md)|Compare comment obtenir les éléments descendants avec un nom particulier avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"//Name"`|  
|[Guide pratique pour filtrer sur un attribut (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Compare comment obtenir les éléments descendants avec un nom spécifié, et avec un attribut avec une valeur spécifiée avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `".//Address[@Type='Shipping']"`|  
|[Guide pratique pour rechercher des éléments connexes (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-related-elements-xpath-linq-to-xml.md)|Compare comment obtenir un élément en sélectionnant un attribut auquel il est fait référence par la valeur d'un autre élément avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Guide pratique pour rechercher des éléments dans un espace de noms (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-elements-in-a-namespace-xpath-linq-to-xml.md)|Compare l’utilisation de la classe <xref:System.Xml.XmlNamespaceManager> XPath à la propriété [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> de la classe <xref:System.Xml.Linq.XName> pour une utilisation avec des espaces de noms XML.<br /><br /> L'expression XPath associée est : `"./aw:*"`|  
|[Guide pratique pour rechercher les frères précédents (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-preceding-siblings-xpath-linq-to-xml.md)|Compare l'axe `preceding-sibling` XPath à l'axe [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enfant <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>.<br /><br /> L'expression XPath associée est : `"preceding-sibling::*"`|  
|[Guide pratique pour rechercher les descendants d’un élément enfant (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|Compare comment obtenir les éléments descendants d'un élément enfant avec un nom particulier avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"./Paragraph//Text/text()"`|  
|[Guide pratique pour rechercher une union de deux chemins d’emplacements (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-union-of-two-location-paths-xpath-linq-to-xml.md)|Compare l'utilisation de l'opérateur d'union <code>&#124;</code> dans XPath avec l'opérateur de requête standard <xref:System.Linq.Enumerable.Concat%2A> dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : <code>"//Category&#124;//Price"</code>|  
|[Guide pratique pour rechercher des nœuds frères (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-sibling-nodes-xpath-linq-to-xml.md)|Compare comment rechercher tous les frères d'un nœud qui ont un nom spécifique avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. <br /><br /> L'expression XPath associée est : `"../Book"`|  
|[Guide pratique pour rechercher un attribut du parent (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Compare comment naviguer jusqu'à l'élément parent et rechercher un attribut associé à l'aide de XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"../@id"`|  
|[Guide pratique pour rechercher des attributs de frères avec un nom spécifique (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-attributes-of-siblings-with-a-specific-name-xpath-linq-to-xml.md)|Compare comment rechercher des attributs spécifiques des frères du nœud de contexte avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"``../Book/@id``"`|  
|[Guide pratique pour rechercher des éléments avec un attribut spécifique (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml.md)|Compare comment rechercher tous les éléments contenant un attribut spécifique à l'aide de XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. <br /><br /> L'expression XPath associée est : `"./*[@Select]"`|  
|[Guide pratique pour rechercher des éléments enfants en fonction de leur position (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-child-elements-based-on-position-xpath-linq-to-xml.md)|Compare comment rechercher un élément en fonction de sa position relative à l'aide de XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"Test[position() >= 2 and position() <= 4]"`|  
|[Guide pratique pour rechercher le frère précédent (XPath-LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|Compare comment faire rechercher le frère précédent d'un nœud à l'aide de XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.XPath?displayProperty=nameWithType>  
 [Interrogation d’arborescences XML (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)  
 [Traitement des données XML à l’aide du modèle de données XPath](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
