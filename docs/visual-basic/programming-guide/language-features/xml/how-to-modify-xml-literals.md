---
title: "Comment : modifier des littéraux XML (Visual Basic) | Documents Microsoft"
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
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9c21ded9fdd8f49b469b9a712be304c0d4cabb8c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="25983-102">Comment : modifier des littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25983-102">How to: Modify XML Literals (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="25983-103">offre des moyens pratiques de modifier des littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="25983-103"> provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="25983-104">Vous pouvez ajouter ou supprimer des éléments et attributs, et vous pouvez également remplacer un élément existant avec un élément XML.</span><span class="sxs-lookup"><span data-stu-id="25983-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="25983-105">Cette rubrique fournit plusieurs exemples de modification d’un littéral XML existant.</span><span class="sxs-lookup"><span data-stu-id="25983-105">This topic provides several examples of how to modify an existing XML literal.</span></span>  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="25983-106">Pour modifier la valeur d’un littéral XML</span><span class="sxs-lookup"><span data-stu-id="25983-106">To modify the value of an XML literal</span></span>  
  
1.  <span data-ttu-id="25983-107">Pour modifier la valeur d’un littéral XML, obtenir une référence au document XML littérale et définissez le `Value` propriété à la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="25983-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>  
  
     <span data-ttu-id="25983-108">L’exemple de code suivant met à jour la valeur de tous les \<prix > éléments dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="25983-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>  
  
     <span data-ttu-id="25983-109">[!code-vb[VbXmlSamples2 n °&4;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="25983-109">[!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]</span></span>  
  
     <span data-ttu-id="25983-110">Ce qui suit illustre l’exemple de source XML et XML modifié à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="25983-110">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
    >  <span data-ttu-id="25983-111">Le `Value` propriété fait référence au premier élément XML d’une collection.</span><span class="sxs-lookup"><span data-stu-id="25983-111">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="25983-112">S’il existe plus d’un élément qui a le même nom dans une collection, définissant le `Value` propriété affecte uniquement le premier élément dans la collection.</span><span class="sxs-lookup"><span data-stu-id="25983-112">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="25983-113">Pour ajouter un attribut à un littéral XML</span><span class="sxs-lookup"><span data-stu-id="25983-113">To add an attribute to an XML literal</span></span>  
  
1.  <span data-ttu-id="25983-114">Pour ajouter un attribut à un littéral XML, tout d’abord obtenir une référence au littéral XML.</span><span class="sxs-lookup"><span data-stu-id="25983-114">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="25983-115">Vous pouvez ensuite ajouter un attribut en ajoutant une nouvelle propriété d’axe d’attribut XML.</span><span class="sxs-lookup"><span data-stu-id="25983-115">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="25983-116">Vous pouvez également ajouter un nouveau <xref:System.Xml.Linq.XAttribute>objet au XML littéral à l’aide de la <xref:System.Xml.Linq.XContainer.Add%2A>méthode.</xref:System.Xml.Linq.XContainer.Add%2A> </xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="25983-116">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="25983-117">L’exemple suivant montre les deux options.</span><span class="sxs-lookup"><span data-stu-id="25983-117">The following example shows both options.</span></span>  
  
     <span data-ttu-id="25983-118">[!code-vb[VbXmlSamples2 n °&5;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="25983-118">[!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]</span></span>  
  
     <span data-ttu-id="25983-119">Ce qui suit illustre l’exemple de source XML et XML modifié à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="25983-119">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
     <span data-ttu-id="25983-120">Pour plus d’informations sur les propriétés d’axe XML attribut, consultez [propriété d’axe d’attribut XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="25983-120">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>  
  
### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="25983-121">Pour ajouter un élément à un littéral XML</span><span class="sxs-lookup"><span data-stu-id="25983-121">To add an element to an XML literal</span></span>  
  
1.  <span data-ttu-id="25983-122">Pour ajouter un élément à un littéral XML, tout d’abord obtenir une référence au littéral XML.</span><span class="sxs-lookup"><span data-stu-id="25983-122">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="25983-123">Vous pouvez ensuite ajouter un nouveau <xref:System.Xml.Linq.XElement>objet comme dernier sous-élément de l’élément à l’aide de la <xref:System.Xml.Linq.XContainer.Add%2A>méthode.</xref:System.Xml.Linq.XContainer.Add%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="25983-123">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="25983-124">Vous pouvez ajouter un nouveau <xref:System.Xml.Linq.XElement>objet en tant que premier sous-élément à l’aide de la <xref:System.Xml.Linq.XContainer.AddFirst%2A>méthode.</xref:System.Xml.Linq.XContainer.AddFirst%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="25983-124">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>  
  
     <span data-ttu-id="25983-125">Pour ajouter un nouvel élément dans un emplacement spécifique par rapport à d’autres sous-éléments, tout d’abord obtenir une référence à un sous-élément adjacent.</span><span class="sxs-lookup"><span data-stu-id="25983-125">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="25983-126">Vous pouvez ensuite ajouter le nouveau <xref:System.Xml.Linq.XElement>objet avant le sous-élément adjacent à l’aide de la <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>méthode.</xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="25983-126">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="25983-127">Vous pouvez également ajouter le nouveau <xref:System.Xml.Linq.XElement>objet après le sous-élément adjacent à l’aide de la <xref:System.Xml.Linq.XNode.AddAfterSelf%2A>méthode.</xref:System.Xml.Linq.XNode.AddAfterSelf%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="25983-127">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>  
  
     <span data-ttu-id="25983-128">L’exemple suivant montre des exemples de chacune de ces techniques.</span><span class="sxs-lookup"><span data-stu-id="25983-128">The following example shows examples of each of these techniques.</span></span>  
  
     <span data-ttu-id="25983-129">[!code-vb[VbXmlSamples2 n °&6;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="25983-129">[!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]</span></span>  
  
     <span data-ttu-id="25983-130">Ce qui suit illustre l’exemple de source XML et XML modifié à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="25983-130">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="25983-131">Pour supprimer un élément ou attribut d’un littéral XML</span><span class="sxs-lookup"><span data-stu-id="25983-131">To remove an element or attribute from an XML literal</span></span>  
  
1.  <span data-ttu-id="25983-132">Pour supprimer un élément ou un attribut d’un littéral XML, obtenez une référence à l’élément ou attribut et l’appel de la `Remove` méthode, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="25983-132">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>  
  
     <span data-ttu-id="25983-133">[!code-vb[VbXmlSamples&#2;7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="25983-133">[!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]</span></span>  
  
     <span data-ttu-id="25983-134">Ce qui suit illustre l’exemple de source XML et XML modifié à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="25983-134">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
      </Book></Catalog>  
    ```  
  
     <span data-ttu-id="25983-135">Pour supprimer tous les éléments ou attributs d’un littéral XML, obtenez une référence au littéral XML et appelez le <xref:System.Xml.Linq.XElement.RemoveAll%2A>méthode.</xref:System.Xml.Linq.XElement.RemoveAll%2A></span><span class="sxs-lookup"><span data-stu-id="25983-135">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>  
  
### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="25983-136">Pour modifier un littéral XML</span><span class="sxs-lookup"><span data-stu-id="25983-136">To modify an XML literal</span></span>  
  
1.  <span data-ttu-id="25983-137">Pour modifier le nom d’un élément XML, tout d’abord obtenir une référence à l’élément.</span><span class="sxs-lookup"><span data-stu-id="25983-137">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="25983-138">Vous pouvez ensuite créer un nouveau <xref:System.Xml.Linq.XElement>qui possède un nouveau nom et passer le nouvel objet <xref:System.Xml.Linq.XElement>de l’objet à le <xref:System.Xml.Linq.XNode.ReplaceWith%2A>méthode existants <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XNode.ReplaceWith%2A> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="25983-138">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="25983-139">Si l’élément que vous remplacez possède des sous-éléments devant être conservés, définissez la valeur de la nouvelle <xref:System.Xml.Linq.XElement>de l’objet à le <xref:System.Xml.Linq.XContainer.Nodes%2A>la propriété de l’élément existant.</xref:System.Xml.Linq.XContainer.Nodes%2A> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="25983-139">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="25983-140">Cela définit la valeur du nouvel élément au XML interne de l’élément existant.</span><span class="sxs-lookup"><span data-stu-id="25983-140">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="25983-141">Sinon, vous pouvez définir la valeur du nouvel élément à la `Value` propriété de l’élément existant.</span><span class="sxs-lookup"><span data-stu-id="25983-141">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>  
  
     <span data-ttu-id="25983-142">L’exemple de code suivant remplace tous les \<Description > éléments avec une \<abstraite > élément.</span><span class="sxs-lookup"><span data-stu-id="25983-142">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="25983-143">Le contenu de la \<Description > élément est conservé dans le nouvel \<abstraite > élément à l’aide de la <xref:System.Xml.Linq.XContainer.Nodes%2A>propriété de la \<Description > <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer.Nodes%2A></span><span class="sxs-lookup"><span data-stu-id="25983-143">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="25983-144">[!code-vb[VbXmlSamples2 n °&8;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="25983-144">[!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]</span></span>  
  
     <span data-ttu-id="25983-145">Ce qui suit illustre l’exemple de source XML et XML modifié à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="25983-145">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
        <MSRP>44.95</MSRP>    <Abstract>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Abstract>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <MSRP>45.95</MSRP>    <Abstract>  
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
  
## <a name="see-also"></a><span data-ttu-id="25983-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25983-146">See Also</span></span>  
 <span data-ttu-id="25983-147">[Manipulation de XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="25983-147">[Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span></span>  
<span data-ttu-id="25983-148"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="25983-148"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="25983-149"> [Comment : charger du code XML à partir d’un fichier, une chaîne ou un flux de données](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span><span class="sxs-lookup"><span data-stu-id="25983-149"> [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span></span>  
<span data-ttu-id="25983-150"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="25983-150"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="25983-151"> [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="25983-151"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
