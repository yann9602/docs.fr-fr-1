---
title: "Vue d’ensemble de la classe XElement (Visual Basic) | Documents Microsoft"
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
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
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
ms.openlocfilehash: 4b46f3cb5e0d59105fbc31424a0408c3421d9cac
ms.lasthandoff: 03/13/2017

---
# <a name="xelement-class-overview-visual-basic"></a>Vue d’ensemble de la classe XElement (Visual Basic)
La <xref:System.Xml.Linq.XElement>classe est une des classes fondamentales dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</xref:System.Xml.Linq.XElement> Elle représente un élément XML. Vous pouvez utiliser cette classe pour créer des éléments, modifier le contenu de l'élément, ajouter, modifier ou supprimer des éléments enfants, ajouter des attributs à un élément ou sérialiser le contenu d'un élément sous forme textuelle. Vous pouvez également interagir avec d’autres classes dans <xref:System.Xml?displayProperty=fullName>, tel que <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>et <xref:System.Xml.Xsl.XslCompiledTransform>.</xref:System.Xml.Xsl.XslCompiledTransform> </xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> </xref:System.Xml?displayProperty=fullName>  
  
## <a name="xelement-functionality"></a>Fonctionnalité de XElement  
 Cette rubrique décrit les fonctionnalités fournies par la <xref:System.Xml.Linq.XElement>classe.</xref:System.Xml.Linq.XElement>  
  
### <a name="constructing-xml-trees"></a>Construction d'arborescences XML  
 Vous pouvez construire des arborescences XML de diverses façons, notamment les suivantes :  
  
-   Vous pouvez construire une arborescence XML dans du code. Pour plus d’informations, consultez [création d’arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
-   Vous pouvez analyser les données XML provenant de diverses sources, y compris un <xref:System.IO.TextReader>, fichiers texte, ou une adresse Web (URL).</xref:System.IO.TextReader> Pour plus d’informations, consultez [l’analyse de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).  
  
-   Vous pouvez utiliser un <xref:System.Xml.XmlReader>pour remplir l’arborescence.</xref:System.Xml.XmlReader> Pour plus d’informations, consultez <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</xref:System.Xml.Linq.XNode.ReadFrom%2A>  
  
-   Si vous avez un module qui peut écrire du contenu dans une <xref:System.Xml.XmlWriter>, vous pouvez utiliser la <xref:System.Xml.Linq.XContainer.CreateWriter%2A>méthode pour créer un writer, passer ce dernier au module, puis utiliser le contenu qui est écrite dans le <xref:System.Xml.XmlWriter>pour remplir l’arborescence XML.</xref:System.Xml.XmlWriter> </xref:System.Xml.Linq.XContainer.CreateWriter%2A> </xref:System.Xml.XmlWriter>  
  
 Toutefois, la manière la plus courante de créer une arborescence XML est la suivante :  
  
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
  
 Une autre technique de création d’une arborescence XML très courante implique l’utilisation des résultats d’une [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requête pour remplir une arborescence XML, comme illustré dans l’exemple suivant :  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a>Sérialisation d'arborescences XML  
 Vous pouvez sérialiser l’arborescence XML vers un <xref:System.IO.File>, un <xref:System.IO.TextWriter>, ou un <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File>  
  
 Pour plus d’informations, consultez [sérialiser des arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>Récupération de données XML par le biais de méthodes d'axe  
 Vous pouvez utiliser des méthodes d'axe pour récupérer des attributs, des éléments enfants, des éléments descendants et des éléments ancêtres. Les requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] opèrent sur les méthodes d'axe et offrent plusieurs moyens flexibles et puissants de parcourir et de traiter une arborescence XML.  
  
 Pour plus d’informations, consultez [Axes LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).  
  
### <a name="querying-xml-trees"></a>Interrogation d’arborescences XML  
 Vous pouvez écrire [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requêtes qui extraient des données à partir d’une arborescence XML.  
  
 Pour plus d’informations, consultez [interroger des arborescences XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).  
  
### <a name="modifying-xml-trees"></a>Modification d’arborescences XML  
 Vous pouvez modifier un élément de différentes façons, y compris modifier son contenu ou ses attributs. Vous pouvez également supprimer un élément de son parent.  
  
 Pour plus d’informations, consultez [modification d’arborescences XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).  
  
## <a name="see-also"></a>Voir aussi  
 [LINQ to XML programmation présentation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
