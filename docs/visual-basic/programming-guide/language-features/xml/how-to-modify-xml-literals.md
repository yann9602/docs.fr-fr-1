---
title: "How to: Modify XML Literals (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML axis [Visual Basic], Value"
  - "XML literals [Visual Basic]"
  - "XML literals [Visual Basic], modifying"
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Modify XML Literals (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] offre des moyens pratiques de modifier des littéraux XML.  Vous pouvez ajouter ou supprimer des éléments et des attributs ; vous pouvez également remplacer un élément existant par un nouvel élément XML.  Cette rubrique fournit plusieurs exemples de modification d'un littéral XML existant.  
  
### Pour modifier la valeur d'un littéral XML  
  
1.  Pour modifier la valeur d'un littéral XML, obtenez une référence au littéral XML et affectez à la propriété `Value` la valeur désirée.  
  
     L'exemple de code suivant met à jour la valeur de tous les éléments \<Price\> dans un document XML.  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     Voici des exemples de XML source et de XML modifié issus de cet exemple de code.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>47.20</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>48.25</Price>  
      </Book>  
    </Catalog>  
    ```  
  
    > [!NOTE]
    >  La propriété `Value` fait référence au premier élément XML d'une collection.  Si plusieurs éléments possèdent le même nom dans une collection, la définition de la propriété `Value` affecte uniquement le premier élément de la collection.  
  
### Pour ajouter un attribut à un littéral XML  
  
1.  Pour ajouter un attribut à un littéral XML, obtenez d'abord une référence au littéral XML.  Vous pouvez ensuite ajouter un attribut en ajoutant une nouvelle propriété d'axe d'attribut XML.  Vous pouvez également ajouter un nouvel objet <xref:System.Xml.Linq.XAttribute> au littéral XML en utilisant la méthode <xref:System.Xml.Linq.XContainer.Add%2A>.  L'exemple suivant présente les deux options.  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     Voici des exemples de XML source et de XML modifié issus de cet exemple de code.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
    ```  
  
     Pour plus d'informations sur les propriétés d'axe d'attribut XML, consultez [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).  
  
### Pour ajouter un élément à un littéral XML  
  
1.  Pour ajouter un élément à un littéral XML, obtenez d'abord une référence au littéral XML.  Vous pouvez ensuite ajouter un nouvel objet <xref:System.Xml.Linq.XElement> comme dernier sous\-élément de l'élément à l'aide de la méthode <xref:System.Xml.Linq.XContainer.Add%2A>.  Vous pouvez ajouter un nouvel objet <xref:System.Xml.Linq.XElement> comme premier sous\-élément à l'aide de la méthode <xref:System.Xml.Linq.XContainer.AddFirst%2A>.  
  
     Pour ajouter un nouvel élément dans un emplacement spécifique relatif à d'autres sous\-éléments, obtenez d'abord une référence à un sous\-élément adjacent.  Vous pouvez ensuite ajouter le nouvel objet <xref:System.Xml.Linq.XElement> avant le sous\-élément adjacent à l'aide de la méthode <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>.  Vous pouvez également ajouter ensuite le nouvel objet <xref:System.Xml.Linq.XElement> après le sous\-élément adjacent à l'aide de la méthode <xref:System.Xml.Linq.XNode.AddAfterSelf%2A>.  
  
     L'exemple suivant présente des exemples de chacune de ces techniques.  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     Voici des exemples de XML source et de XML modifié issus de cet exemple de code.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331">  
        <Publisher>Microsoft Press</Publisher>  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
        <PublishDate>2005-2-14</PublishDate>  
      </Book>  
      <Book id="bk999"></Book>  
    </Catalog>  
    ```  
  
### Pour supprimer un élément ou un attribut d'un littéral XML  
  
1.  Pour supprimer un élément ou un attribut d'un littéral XML, obtenez une référence à l'élément ou à l'attribut et appelez la méthode `Remove`, comme illustré dans l'exemple suivant.  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     Voici des exemples de XML source et de XML modifié issus de cet exemple de code.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
      <Book id="bk999"></Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book> </Catalog>  
    ```  
  
     Pour supprimer tous les éléments ou attributs d'un littéral XML, obtenez une référence au littéral XML et appelez la méthode <xref:System.Xml.Linq.XElement.RemoveAll%2A>.  
  
### Pour modifier un littéral XML  
  
1.  Pour modifier le nom d'un élément XML, obtenez d'abord une référence à l'élément.  Vous pouvez ensuite créer un nouvel objet <xref:System.Xml.Linq.XElement> qui possède un nouveau nom et passer le nouvel objet <xref:System.Xml.Linq.XElement> à la méthode <xref:System.Xml.Linq.XNode.ReplaceWith%2A> de l'objet <xref:System.Xml.Linq.XElement> existant.  
  
     Si l'élément que vous remplacez possède des sous\-éléments devant être conservés, affectez au nouvel objet <xref:System.Xml.Linq.XElement> la valeur de la propriété <xref:System.Xml.Linq.XContainer.Nodes%2A> de l'élément existant.  Cela affectera au nouvel élément la valeur du code XML interne de l'élément existant.  Sinon, vous pouvez affecter au nouvel élément la valeur de la propriété `Value` de l'élément existant.  
  
     L'exemple de code suivant remplace tous les éléments \<Description\> par un élément \<Abstract\>.  Le contenu de l'élément \<Description\> est conservé dans le nouvel élément \<Abstract\> à l'aide de la propriété <xref:System.Xml.Linq.XContainer.Nodes%2A> de l'objet <xref:System.Xml.Linq.XElement> \<Description\>.  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     Voici des exemples de XML source et de XML modifié issus de cet exemple de code.  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
        <Description>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Description>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
        <Description>  
          Get the expert insights, practical code samples, and best  
          practices you need to advance your expertise with   
          <technology>Visual Basic .NET</technology>.   
          Learn how to create faster, more reliable applications  
          based on professional, pragmatic guidance by today's top  
          <audience>developers</audience>.  
        </Description>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <MSRP>44.95</MSRP>     <Abstract>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Abstract>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <MSRP>45.95</MSRP>     <Abstract>  
          Get the expert insights, practical code samples, and best  
          practices you need to advance your expertise with   
          <technology>Visual Basic .NET</technology>.   
          Learn how to create faster, more reliable applications  
          based on professional, pragmatic guidance by today's top  
          <audience>developers</audience>.  
        </Abstract>  
      </Book>  
    </Catalog>  
    ```  
  
## Voir aussi  
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)