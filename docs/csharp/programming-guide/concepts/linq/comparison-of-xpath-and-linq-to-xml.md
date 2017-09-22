---
title: Comparaison de XPath et LINQ to XML2
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
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a0b24eeeb79651f69178fa4e9c2e4a3359434556
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Comparaison de XPath et LINQ to XML
XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] offrent certaines fonctionnalités similaires. Tous deux peuvent être utilisés pour interroger une arborescence XML et retourner des résultats tels qu'une collection d'élément, une collection d'attributs, une collection de nœuds ou la valeur d'un élément ou attribut. Il existe toutefois certaines différences.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>Différences entre XPath et LINQ to XML  
 XPath n'autorise pas la projection de nouveaux types. Il ne peut retourner que des collections de nœuds à partir de l'arborescence, tandis que [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] peut exécuter une requête et projeter un graphique d'objet ou une arborescence XML dans une nouvelle forme. Les requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] englobent beaucoup plus de fonctionnalités et sont beaucoup plus puissantes que les expressions XPath.  
  
 Les expressions XPath existent de manière isolée dans une chaîne. Le compilateur C# ne peut pas contribuer à l’analyse de l’expression XPath au moment de la compilation. En revanche, c’est lui qui analyse et compile les requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Le compilateur est capable d'intercepter de nombreuses erreurs de requête.  
  
 Les résultats XPath ne sont pas fortement typés. Dans certaines circonstances, le résultat de l'évaluation d'une expression XPath est un objet et il incombe au développeur de déterminer le type correct et de convertir le résultat si nécessaire. En revanche, les projections à partir d'une requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sont fortement typées.  
  
## <a name="result-ordering"></a>Ordonnancement des résultats  
 La Recommandation XPath 1.0 stipule qu'une collection qui est le résultat de l'évaluation d'une expression XPath n'est pas ordonnée.  
  
 Toutefois, lors de l'itération d'une collection retournée par une méthode d'axe XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], les nœuds de la collection sont retournés dans l'ordre du document. Cela est valable même lors de l'accès à des axes XPath où les prédicats sont exprimés dans l'ordre inverse du document, par exemple `preceding` et `preceding-sibling`.  
  
 Par contraste, la plupart des axes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] retournent les collections dans l'ordre du document, mais deux d'entre eux, <xref:System.Xml.Linq.XNode.Ancestors%2A> et <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, retournent les collections dans l'ordre inverse du document. Le tableau suivant énumère les axes et indique l'ordre de collection pour chacun d'eux :  
  
|Axe LINQ to XML|Classement|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Ordre du document|  
|XContainer.Descendants|Ordre du document|  
|XContainer.Elements|Ordre du document|  
|XContainer.Nodes|Ordre du document|  
|XContainer.NodesAfterSelf|Ordre du document|  
|XContainer.NodesBeforeSelf|Ordre du document|  
|XElement.AncestorsAndSelf|Ordre inverse du document|  
|XElement.Attributes|Ordre du document|  
|XElement.DescendantNodesAndSelf|Ordre du document|  
|XElement.DescendantsAndSelf|Ordre du document|  
|XNode.Ancestors|Ordre inverse du document|  
|XNode.ElementsAfterSelf|Ordre du document|  
|XNode.ElementsBeforeSelf|Ordre du document|  
|XNode.NodesAfterSelf|Ordre du document|  
|XNode.NodesBeforeSelf|Ordre du document|  
  
## <a name="positional-predicates"></a>Prédicats de position  
 Dans une expression XPath, les prédicats de position sont exprimés dans l'ordre du document pour de nombreux axes, mais dans l'ordre inverse du document pour les axes inversés, qui sont `preceding`, `preceding-sibling`, `ancestor` et `ancestor-or-self`. Par exemple, l'expression XPath `preceding-sibling::*[1]` retourne le frère qui précède. C'est le cas même si le jeu de résultats final est présenté dans l'ordre du document.  
  
 Par contraste, tous les prédicats de position dans LINQ to XML sont toujours exprimés dans l'ordre de l'axe. Par exemple, `anElement.ElementsBeforeSelf().ToList()[0]` retourne le premier élément enfant du parent de l'élément interrogé, mais pas l'enfant qui précède. Autre exemple : `anElement.Ancestors().ToList()[0]` retourne l'élément parent.  
  
 Notez que l'approche ci-dessus matérialise l'intégralité de la collection. Il ne s'agit pas de la méthode la plus efficace pour écrire cette requête. Elle a été écrite de cette façon afin d'illustrer le comportement des prédicats de position. Une méthode plus appropriée pour écrire la même requête consiste à utiliser la méthode <xref:System.Linq.Enumerable.First%2A>, comme suit : `anElement.ElementsBeforeSelf().First()`.  
  
 Si vous souhaitez rechercher l'élément qui précède dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous devez écrire l'expression suivante :  
  
 `ElementsBeforeSelf().Last()`  
  
## <a name="performance-differences"></a>Différences en matière de performances  
 Les requêtes XPath qui utilisent la fonctionnalité XPath dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] présentent des performances inférieures à celles des requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="comparison-of-composition"></a>Comparaison de la composition  
 La composition d'une requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est quelque peu parallèle à celle d'une expression XPath, bien qu'elle soit très différente en termes de syntaxe.  
  
 Par exemple, si vous avez un élément dans une variable nommée `customers` et que vous souhaitez trouver un élément petit-enfant `CompanyName` sous tous les éléments enfants nommés `Customer`, vous devez écrire une expression XPath comme suit :  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName");  
```  
  
 La requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] équivalente est la suivante :  
  
```csharp  
customers.Element("Customer").Elements("CompanyName");  
```  
  
 Il existe des parallèles similaires pour chacun des axes XPath.  
  
|Axe XPath|Axe LINQ to XML|  
|----------------|----------------------|  
|enfant (l'axe par défaut)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Parent (..)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|axe des attributs (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|axe des ancêtres|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|axe ancestor-or-self|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|axe des descendants (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|descendant-or-self|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|frère suivant|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|frère précédent|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|suivant|Aucun équivalent direct.|  
|précédent|Aucun équivalent direct.|  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to XML pour les utilisateurs XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)

