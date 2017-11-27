---
title: "Comment : modifier des littéraux XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdc60542477d15f4fe9dd85dae4c9a918e695740
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-xml-literals-visual-basic"></a><span data-ttu-id="c311b-102">Comment : modifier des littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c311b-102">How to: Modify XML Literals (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="c311b-103">Fournit des moyens pratiques de modifier des littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="c311b-103"> provides convenient ways to modify XML literals.</span></span> <span data-ttu-id="c311b-104">Vous pouvez ajouter ou supprimer des éléments et attributs, et vous pouvez également remplacer un élément existant par un élément XML.</span><span class="sxs-lookup"><span data-stu-id="c311b-104">You can add or delete elements and attributes, and you can also replace an existing element with a new XML element.</span></span> <span data-ttu-id="c311b-105">Cette rubrique fournit plusieurs exemples de modification d’un littéral XML existant.</span><span class="sxs-lookup"><span data-stu-id="c311b-105">This topic provides several examples of how to modify an existing XML literal.</span></span>  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a><span data-ttu-id="c311b-106">Pour modifier la valeur d’un littéral XML</span><span class="sxs-lookup"><span data-stu-id="c311b-106">To modify the value of an XML literal</span></span>  
  
1.  <span data-ttu-id="c311b-107">Pour modifier la valeur d’un littéral XML, obtenir une référence au document XML littéral et définissez le `Value` propriété la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="c311b-107">To modify the value of an XML literal, obtain a reference to the XML literal and set the `Value` property to the desired value.</span></span>  
  
     <span data-ttu-id="c311b-108">L’exemple de code suivant met à jour la valeur de tous les \<prix > éléments dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="c311b-108">The following code example updates the value of all the \<Price> elements in an XML document.</span></span>  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     <span data-ttu-id="c311b-109">La commande suivante montre l’exemple de source XML et XML modifié à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="c311b-109">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
    >  <span data-ttu-id="c311b-110">Le `Value` propriété fait référence au premier élément XML dans une collection.</span><span class="sxs-lookup"><span data-stu-id="c311b-110">The `Value` property refers to the first XML element in a collection.</span></span> <span data-ttu-id="c311b-111">S’il existe plus d’un élément qui porte le même nom dans une collection, définissant la `Value` propriété affecte uniquement le premier élément dans la collection.</span><span class="sxs-lookup"><span data-stu-id="c311b-111">If there is more than one element that has the same name in a collection, setting the `Value` property affects only the first element in the collection.</span></span>  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a><span data-ttu-id="c311b-112">Pour ajouter un attribut à un littéral XML</span><span class="sxs-lookup"><span data-stu-id="c311b-112">To add an attribute to an XML literal</span></span>  
  
1.  <span data-ttu-id="c311b-113">Pour ajouter un attribut à un littéral XML, d’abord obtenir une référence au littéral XML.</span><span class="sxs-lookup"><span data-stu-id="c311b-113">To add an attribute to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="c311b-114">Vous pouvez ensuite ajouter un attribut en ajoutant une nouvelle propriété d’axe d’attribut XML.</span><span class="sxs-lookup"><span data-stu-id="c311b-114">You can then add an attribute by adding a new XML attribute axis property.</span></span> <span data-ttu-id="c311b-115">Vous pouvez également ajouter un nouveau <xref:System.Xml.Linq.XAttribute> objet au littéral à l’aide de XML le <xref:System.Xml.Linq.XContainer.Add%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c311b-115">You can also add a new <xref:System.Xml.Linq.XAttribute> object to the XML literal by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="c311b-116">L’exemple suivant montre les deux options.</span><span class="sxs-lookup"><span data-stu-id="c311b-116">The following example shows both options.</span></span>  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     <span data-ttu-id="c311b-117">La commande suivante montre l’exemple de source XML et XML modifié à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="c311b-117">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
     <span data-ttu-id="c311b-118">Pour plus d’informations sur les propriétés d’axe XML attribut, consultez [propriété axe d’attribut XML](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span><span class="sxs-lookup"><span data-stu-id="c311b-118">For more information about XML attribute axis properties, see [XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md).</span></span>  
  
### <a name="to-add-an-element-to-an-xml-literal"></a><span data-ttu-id="c311b-119">Pour ajouter un élément à un littéral XML</span><span class="sxs-lookup"><span data-stu-id="c311b-119">To add an element to an XML literal</span></span>  
  
1.  <span data-ttu-id="c311b-120">Pour ajouter un élément à un littéral XML, d’abord obtenir une référence au littéral XML.</span><span class="sxs-lookup"><span data-stu-id="c311b-120">To add an element to an XML literal, first obtain a reference to the XML literal.</span></span> <span data-ttu-id="c311b-121">Vous pouvez ensuite ajouter un nouveau <xref:System.Xml.Linq.XElement> objet comme dernier sous-élément de l’élément à l’aide de la <xref:System.Xml.Linq.XContainer.Add%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c311b-121">You can then add a new <xref:System.Xml.Linq.XElement> object as the last sub-element of the element by using the <xref:System.Xml.Linq.XContainer.Add%2A> method.</span></span> <span data-ttu-id="c311b-122">Vous pouvez ajouter un nouveau <xref:System.Xml.Linq.XElement> objet en tant que premier sous-élément à l’aide de la <xref:System.Xml.Linq.XContainer.AddFirst%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c311b-122">You can add a new <xref:System.Xml.Linq.XElement> object as the first sub-element by using the <xref:System.Xml.Linq.XContainer.AddFirst%2A> method.</span></span>  
  
     <span data-ttu-id="c311b-123">Pour ajouter un nouvel élément dans un emplacement spécifique par rapport aux autres sous-éléments, d’abord obtenir une référence à un sous-élément adjacent.</span><span class="sxs-lookup"><span data-stu-id="c311b-123">To add a new element in a specific location relative to other sub-elements, first obtain a reference to an adjacent sub-element.</span></span> <span data-ttu-id="c311b-124">Vous pouvez ensuite ajouter le nouveau <xref:System.Xml.Linq.XElement> objet avant le sous-élément adjacent à l’aide de la <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c311b-124">You can then add the new <xref:System.Xml.Linq.XElement> object before the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> method.</span></span> <span data-ttu-id="c311b-125">Vous pouvez également ajouter le nouveau <xref:System.Xml.Linq.XElement> objet après le sous-élément adjacent à l’aide de la <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c311b-125">You can also add the new <xref:System.Xml.Linq.XElement> object after the adjacent sub-element by using the <xref:System.Xml.Linq.XNode.AddAfterSelf%2A> method.</span></span>  
  
     <span data-ttu-id="c311b-126">L’exemple suivant montre des exemples de chacune de ces techniques.</span><span class="sxs-lookup"><span data-stu-id="c311b-126">The following example shows examples of each of these techniques.</span></span>  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     <span data-ttu-id="c311b-127">La commande suivante montre l’exemple de source XML et XML modifié à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="c311b-127">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a><span data-ttu-id="c311b-128">Pour supprimer un élément ou attribut d’un littéral XML</span><span class="sxs-lookup"><span data-stu-id="c311b-128">To remove an element or attribute from an XML literal</span></span>  
  
1.  <span data-ttu-id="c311b-129">Pour supprimer un élément ou un attribut d’un littéral XML, obtenez une référence à l’élément ou un attribut et un appel de la `Remove` méthode, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="c311b-129">To remove an element or an attribute from an XML literal, obtain a reference to the element or attribute and call the `Remove` method, as shown in the following example.</span></span>  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     <span data-ttu-id="c311b-130">La commande suivante montre l’exemple de source XML et XML modifié à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="c311b-130">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
     <span data-ttu-id="c311b-131">Pour supprimer tous les éléments ou attributs d’un littéral XML, obtenez une référence au littéral XML et appelez le <xref:System.Xml.Linq.XElement.RemoveAll%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="c311b-131">To remove all elements or attributes from an XML literal, obtain a reference to the XML literal and call the <xref:System.Xml.Linq.XElement.RemoveAll%2A> method.</span></span>  
  
### <a name="to-modify-an-xml-literal"></a><span data-ttu-id="c311b-132">Pour modifier un littéral XML</span><span class="sxs-lookup"><span data-stu-id="c311b-132">To modify an XML literal</span></span>  
  
1.  <span data-ttu-id="c311b-133">Pour modifier le nom d’un élément XML, d’abord obtenir une référence à l’élément.</span><span class="sxs-lookup"><span data-stu-id="c311b-133">To change the name of an XML element, first obtain a reference to the element.</span></span> <span data-ttu-id="c311b-134">Vous pouvez ensuite créer un nouveau <xref:System.Xml.Linq.XElement> objet qui dispose d’un nouveau nom et passer le nouvel <xref:System.Xml.Linq.XElement> de l’objet à la <xref:System.Xml.Linq.XNode.ReplaceWith%2A> méthode existants <xref:System.Xml.Linq.XElement> objet.</span><span class="sxs-lookup"><span data-stu-id="c311b-134">You can then create a new <xref:System.Xml.Linq.XElement> object that has a new name and pass the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XNode.ReplaceWith%2A> method of the existing <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     <span data-ttu-id="c311b-135">Si l’élément que vous remplacez possède des sous-éléments qui doivent être conservés, définissez la valeur de la nouvelle <xref:System.Xml.Linq.XElement> de l’objet à le <xref:System.Xml.Linq.XContainer.Nodes%2A> la propriété de l’élément existant.</span><span class="sxs-lookup"><span data-stu-id="c311b-135">If the element that you are replacing has sub-elements that must be preserved, set the value of the new <xref:System.Xml.Linq.XElement> object to the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the existing element.</span></span> <span data-ttu-id="c311b-136">La valeur du nouvel élément est ainsi définie pour le code XML interne de l’élément existant.</span><span class="sxs-lookup"><span data-stu-id="c311b-136">This will set the value of the new element to the inner XML of the existing element.</span></span> <span data-ttu-id="c311b-137">Sinon, vous pouvez définir la valeur du nouvel élément à la `Value` la propriété de l’élément existant.</span><span class="sxs-lookup"><span data-stu-id="c311b-137">Otherwise, you can set the value of the new element to the `Value` property of the existing element.</span></span>  
  
     <span data-ttu-id="c311b-138">L’exemple de code suivant remplace tous les \<Description > éléments avec une \<abstraite > élément.</span><span class="sxs-lookup"><span data-stu-id="c311b-138">The following code example replaces all \<Description> elements with an \<Abstract> element.</span></span> <span data-ttu-id="c311b-139">Le contenu de la \<Description > élément est conservé dans le nouvel \<abstraite > élément à l’aide de la <xref:System.Xml.Linq.XContainer.Nodes%2A> propriété de la \<Description > <xref:System.Xml.Linq.XElement> objet.</span><span class="sxs-lookup"><span data-stu-id="c311b-139">The content of the \<Description> element is preserved in the new \<Abstract> element by using the <xref:System.Xml.Linq.XContainer.Nodes%2A> property of the \<Description> <xref:System.Xml.Linq.XElement> object.</span></span>  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     <span data-ttu-id="c311b-140">La commande suivante montre l’exemple de source XML et XML modifié à partir de cet exemple de code.</span><span class="sxs-lookup"><span data-stu-id="c311b-140">The following shows sample source XML and modified XML from this code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c311b-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c311b-141">See Also</span></span>  
 [<span data-ttu-id="c311b-142">Manipulation de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c311b-142">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [<span data-ttu-id="c311b-143">XML</span><span class="sxs-lookup"><span data-stu-id="c311b-143">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="c311b-144">Guide pratique : charger du code XML à partir d’un fichier, d’une chaîne ou d’un flux</span><span class="sxs-lookup"><span data-stu-id="c311b-144">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [<span data-ttu-id="c311b-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="c311b-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="c311b-146">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c311b-146">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
