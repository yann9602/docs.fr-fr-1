---
title: "Introduction aux littéraux XML dans Visual Basic2 | Documents Microsoft"
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
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 391dd14f971f91d4d128841a7ebd24981266846a
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Introduction aux littéraux XML en Visual Basic
Cette section fournit des informations sur la création d'arborescences XML en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 Pour plus d’informations sur les résultats de requêtes LINQ comme contenu pour une arborescence XML, consultez [Construction fonctionnelle (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).  
  
 Pour plus d’informations sur les littéraux XML en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], consultez [vue d’ensemble de LINQ to XML dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).  
  
## <a name="creating-xml-trees"></a>Création d’arborescences XML  
 L’exemple suivant montre comment créer un <xref:System.Xml.Linq.XElement>, dans ce cas `contacts`:</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### <a name="creating-an-xelement-with-simple-content"></a>Création d'un XElement avec du contenu simple  
 Vous pouvez créer un <xref:System.Xml.Linq.XElement>qui contient du contenu simple, comme suit :</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>Création d'un élément vide  
 Vous pouvez créer un vide <xref:System.Xml.Linq.XElement>, comme suit :</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>Utilisation d'expressions incorporées  
 L'une des caractéristiques importantes des littéraux XML est qu'ils autorisent la présence d'expressions incorporées. Les expressions incorporées vous permettent d’évaluer une expression et d’insérer les résultats de l’expression dans l’arborescence XML. Si l’expression correspond à un type de <xref:System.Xml.Linq.XElement>, un élément est inséré dans l’arborescence.</xref:System.Xml.Linq.XElement> Si l’expression correspond à un type de <xref:System.Xml.Linq.XAttribute>, un attribut est inséré dans l’arborescence.</xref:System.Xml.Linq.XAttribute> Vous pouvez insérer des éléments et des attributs dans l’arborescence uniquement où ils sont valides.  
  
 Il est important de noter que seule une expression unique peut aller dans une expression incorporée. Vous ne pouvez pas incorporer plusieurs instructions. Si une expression s'étend au-delà d'une seule ligne, vous devez utiliser le caractère de continuation de ligne.  
  
 Si vous utilisez une expression incorporée pour ajouter des nœuds (y compris des éléments) et des attributs existants à une nouvelle arborescence XML et si les nœuds existants sont déjà apparentés, les nœuds sont clonés. Les nœuds nouvellement clonés sont attachés à la nouvelle arborescence XML. Si les nœuds existants ne sont pas apparentés, ils sont simplement attachés à la nouvelle arborescence XML. Ceci est illustré dans le dernier exemple de cette rubrique.  
  
 L'exemple suivant utilise une expression incorporée pour insérer un élément dans l'arborescence :  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a>Utilisation d'expressions incorporées pour le contenu  
 Vous pouvez utiliser une expression incorporée pour fournir le contenu d'un élément :  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>Utilisation d'une requête LINQ dans une expression incorporée  
 Vous pouvez utiliser les résultats d'une requête LINQ pour le contenu d'un élément :  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a>Utilisation d'expressions incorporées pour des noms de nœuds  
 Vous pouvez également utiliser des expressions incorporées pour calculer des noms d'attributs, des valeurs d'attributs, des noms d'éléments et des valeurs d'éléments :  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a>Clonage et attachement  
 Comme mentionné précédemment, si vous utilisez une expression incorporée pour ajouter des nœuds (y compris des éléments) et des attributs existants à une nouvelle arborescence XML et que les nœuds existants sont déjà apparentés, les nœuds sont clonés et les nœuds nouvellement clonés sont attachés à la nouvelle arborescence XML. Si les nœuds existants ne sont pas apparentés, ils sont simplement attachés à la nouvelle arborescence XML.  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 Cet exemple génère la sortie suivante :  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)