---
title: "Programmation avec des nœuds (Visual Basic) | Documents Microsoft"
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
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 52fb60b95b869a79900f84c2a1a7a6151bb5b58f
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="programming-with-nodes-visual-basic"></a>Programmation avec des nœuds (Visual Basic)
Les développeurs [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] qui doivent écrire des programmes tels qu'un éditeur XML, un système de transformation ou un générateur de rapports doivent souvent écrire des programmes qui fonctionnent à un niveau de granularité plus élevé que les éléments et attributs. Ils doivent souvent travailler au niveau des nœuds, manipuler des nœuds de texte et traiter des instructions et des commentaires. Cette rubrique fournit quelques détails sur la programmation au niveau nœud.  
  
## <a name="node-details"></a>Détails concernant les nœuds  
 Un programmeur travaillant au niveau nœud doit connaître certains détails de programmation.  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a>La propriété parente des nœuds enfants de XDocument a la valeur Null  
 Le <xref:System.Xml.Linq.XObject.Parent%2A>propriété contient le parent <xref:System.Xml.Linq.XElement>, pas le nœud parent.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XObject.Parent%2A> Nœuds enfants de <xref:System.Xml.Linq.XDocument>ne avoir aucun parent <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> Leur parent étant le document, afin que la <xref:System.Xml.Linq.XObject.Parent%2A>propriété de ces nœuds est définie sur null.</xref:System.Xml.Linq.XObject.Parent%2A>  
  
 Cela est illustré par l'exemple suivant :  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a>Des nœuds de texte adjacents sont possibles  
 Dans un certain nombre de modèles de programmation XML, les nœuds de texte adjacents sont toujours fusionnés. On appelle parfois cela la normalisation des nœuds de texte. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] ne normalise pas les nœuds de texte. L'ajout de deux nœuds de texte au même élément entraîne l'existence de nœuds de texte adjacents. Toutefois, si vous ajoutez du contenu spécifié en tant que chaîne plutôt que comme un <xref:System.Xml.Linq.XText>nœud, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] peut fusionner la chaîne avec un nœud de texte adjacents.</xref:System.Xml.Linq.XText>  
  
 Cela est illustré par l'exemple suivant :  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
' This does not add a new text node.  
xmlTree.Add("new content")  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
'// This does add a new, adjacent text node.  
xmlTree.Add(New XText("more text"))  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a>Des nœuds de texte vides sont possibles  
 Dans certains modèles de programmation XML, les nœuds de texte sont assurés de ne pas contenir la chaîne vide. Le raisonnement est qu'un tel nœud de texte n'a aucun impact sur la sérialisation du code XML. Toutefois, pour la même raison que les nœuds de texte adjacents sont possibles, si vous supprimez le texte d'un nœud de texte en lui affectant comme valeur la chaîne vide, le nœud de texte lui-même ne sera pas supprimé.  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a>Un nœud de texte vide a un impact sur la sérialisation  
 Si un élément contient uniquement un nœud de texte enfant vide, il est sérialisé avec la syntaxe de balise longue : `<Child></Child>`. Si un élément ne contient aucun nœud enfant, il est sérialisé avec la syntaxe de balise abrégée : `<Child />`.  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a>Les espaces de noms sont des attributs dans l'arborescence LINQ to XML  
 Bien que les déclarations d'espaces de noms aient une syntaxe identique aux attributs, dans certaines interfaces de programmation (telles que XSLT et XPath) les déclarations d'espaces de noms ne sont pas considérées comme des attributs. Toutefois, dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], espaces de noms sont stockés en tant que <xref:System.Xml.Linq.XAttribute>objets dans l’arborescence XML.</xref:System.Xml.Linq.XAttribute> Si vous itérez au sein des attributs à la recherche d'un élément qui contient une déclaration d'espace de noms, vous verrez la déclaration d'espace de noms comme l'un des éléments dans la collection retournée.  
  
 Le <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A>propriété indique si un attribut est une déclaration d’espace de noms.</xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A>  
  
```vb  
Dim root As XElement = _   
<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>  
For Each att As XAttribute In root.Attributes()  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, _  
                      att.IsNamespaceDeclaration)  
Next  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a>Les méthodes d'axe XPath ne retournent pas les espaces blancs enfants de XDocument  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]permet à des nœuds de texte enfants d’un <xref:System.Xml.Linq.XDocument>, à condition que les nœuds de texte contiennent uniquement des espaces blancs.</xref:System.Xml.Linq.XDocument> Toutefois, le modèle objet XPath n’inclut pas espace blanc comme nœuds enfants d’un document, donc lorsque vous itérez les enfants d’une <xref:System.Xml.Linq.XDocument>à l’aide de la <xref:System.Xml.Linq.XContainer.Nodes%2A>axe, nœuds de texte d’un espace blanc apparaîtront.</xref:System.Xml.Linq.XContainer.Nodes%2A> </xref:System.Xml.Linq.XDocument> Toutefois, lorsque vous itérez via les enfants d’un <xref:System.Xml.Linq.XDocument>à l’aide de méthodes d’axe XPath, nœuds de texte d’un espace blanc n’est retournés.</xref:System.Xml.Linq.XDocument>  
  
```vb  
' Create a document with some white space child nodes of the document.  
Dim root As XDocument = XDocument.Parse( _  
"<?xml version='1.0' encoding='utf-8' standalone='yes'?>" & _  
vbNewLine & "<Root/>" & vbNewLine & "<!--a comment-->" & vbNewLine, _  
LoadOptions.PreserveWhitespace)  
  
' Count the white space child nodes using LINQ to XML.  
Console.WriteLine(root.Nodes().OfType(Of XText)().Count())  
  
' Count the white space child nodes using XPathEvaluate.  
Dim nodes As IEnumerable = CType(root.XPathEvaluate("text()"), IEnumerable)  
Console.WriteLine(nodes.OfType(Of XText)().Count())  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a>Les objets XDeclaration ne sont pas des nœuds  
 Lorsque vous itérez les nœuds enfants d’un <xref:System.Xml.Linq.XDocument>, vous ne verrez pas l’objet de déclaration XML.</xref:System.Xml.Linq.XDocument> Il s'agit d'une propriété du document, et non d'un de ses nœuds enfants.  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to XML (Visual Basic) de la programmation avancée](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

