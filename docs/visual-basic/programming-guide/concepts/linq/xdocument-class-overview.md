---
title: "Vue d’ensemble de la classe XDocument (Visual Basic) | Documents Microsoft"
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
ms.assetid: 45cb7e71-196a-47da-bfe9-7a5589db1eed
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3f51808a64d51fb354159df1a7323ad2fc26eedc
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="xdocument-class-overview-visual-basic"></a><span data-ttu-id="41c65-102">Vue d’ensemble de la classe XDocument (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41c65-102">XDocument Class Overview (Visual Basic)</span></span>
<span data-ttu-id="41c65-103">Cette rubrique présente la <xref:System.Xml.Linq.XDocument>classe.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="41c65-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="41c65-104">Vue d'ensemble de la classe XDocument</span><span class="sxs-lookup"><span data-stu-id="41c65-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="41c65-105">La <xref:System.Xml.Linq.XDocument>classe contient les informations nécessaires à un document XML valide.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="41c65-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="41c65-106">Cela inclut une déclaration XML, des instructions de traitement et des commentaires.</span><span class="sxs-lookup"><span data-stu-id="41c65-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="41c65-107">Notez que vous devez uniquement créer des <xref:System.Xml.Linq.XDocument>objets, si vous avez besoin de la fonctionnalité spécifique fournie par la <xref:System.Xml.Linq.XDocument>classe.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="41c65-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="41c65-108">Dans de nombreux cas, vous pouvez travailler directement avec <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="41c65-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="41c65-109">Travailler directement avec <xref:System.Xml.Linq.XElement>est un modèle de programmation plus simple.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="41c65-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="41c65-110"><xref:System.Xml.Linq.XDocument>dérive de <xref:System.Xml.Linq.XContainer>.</xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="41c65-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="41c65-111">Par conséquent, il peut contenir des nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="41c65-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="41c65-112">Toutefois, <xref:System.Xml.Linq.XDocument>les objets peuvent avoir qu’un seul enfant <xref:System.Xml.Linq.XElement>nœud.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="41c65-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="41c65-113">Cela reflète la norme XML selon laquelle il ne doit y avoir qu'un seul élément racine dans un document XML.</span><span class="sxs-lookup"><span data-stu-id="41c65-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="41c65-114">Composants de XDocument</span><span class="sxs-lookup"><span data-stu-id="41c65-114">Components of XDocument</span></span>  
 <span data-ttu-id="41c65-115">Un <xref:System.Xml.Linq.XDocument>peut contenir les éléments suivants :</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="41c65-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
-   <span data-ttu-id="41c65-116">Un <xref:System.Xml.Linq.XDeclaration>objet.</xref:System.Xml.Linq.XDeclaration></span><span class="sxs-lookup"><span data-stu-id="41c65-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="41c65-117"><xref:System.Xml.Linq.XDeclaration>permet de spécifier les parties pertinentes d’une déclaration XML : la version XML, l’encodage du document, et si le document XML est autonome.</xref:System.Xml.Linq.XDeclaration></span><span class="sxs-lookup"><span data-stu-id="41c65-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
-   <span data-ttu-id="41c65-118">Un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="41c65-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="41c65-119">Il s'agit du nœud racine du document XML.</span><span class="sxs-lookup"><span data-stu-id="41c65-119">This is the root node of the XML document.</span></span>  
  
-   <span data-ttu-id="41c65-120">Un nombre quelconque de <xref:System.Xml.Linq.XProcessingInstruction>objets.</xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="41c65-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="41c65-121">Une instruction de traitement communique des informations à une application qui traite le code XML.</span><span class="sxs-lookup"><span data-stu-id="41c65-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
-   <span data-ttu-id="41c65-122">Un nombre quelconque de <xref:System.Xml.Linq.XComment>objets.</xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="41c65-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="41c65-123">Les commentaires seront des frères de l'élément racine.</span><span class="sxs-lookup"><span data-stu-id="41c65-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="41c65-124">Le <xref:System.Xml.Linq.XComment>objet ne peut pas être le premier argument de la liste, car il n’est pas valide pour un document XML démarrer avec un commentaire.</xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="41c65-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
-   <span data-ttu-id="41c65-125">Un <xref:System.Xml.Linq.XDocumentType>pour le DTD.</xref:System.Xml.Linq.XDocumentType></span><span class="sxs-lookup"><span data-stu-id="41c65-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="41c65-126">Lorsque vous sérialisez un <xref:System.Xml.Linq.XDocument>, même si `XDocument.Declaration` est `null`, la sortie aura une déclaration XML si le writer a `Writer.Settings.OmitXmlDeclaration` la valeur `false` (la valeur par défaut).</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="41c65-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="41c65-127">Par défaut, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] définit la version à « 1.0 » l'encodage à « utf-8 ».</span><span class="sxs-lookup"><span data-stu-id="41c65-127">By default, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="41c65-128">Utilisation de XElement sans XDocument</span><span class="sxs-lookup"><span data-stu-id="41c65-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="41c65-129">Comme mentionné précédemment, la <xref:System.Xml.Linq.XElement>classe est la classe principale dans le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] interface de programmation.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="41c65-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] programming interface.</span></span> <span data-ttu-id="41c65-130">Dans de nombreux cas, votre application ne nécessitera pas la création d'un document.</span><span class="sxs-lookup"><span data-stu-id="41c65-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="41c65-131">À l’aide de la <xref:System.Xml.Linq.XElement>(classe), vous pouvez créer une arborescence XML, ajouter d’autres arborescences XML, modifiez l’arborescence XML et enregistrez celui-ci.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="41c65-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="41c65-132">Utilisation de XDocument</span><span class="sxs-lookup"><span data-stu-id="41c65-132">Using XDocument</span></span>  
 <span data-ttu-id="41c65-133">Pour construire un <xref:System.Xml.Linq.XDocument>, utilisez la construction fonctionnelle, comme pour construire des <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="41c65-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="41c65-134">Le code suivant crée un <xref:System.Xml.Linq.XDocument>objet et ses objets contenus associés.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="41c65-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```vb  
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>  
                       <!--This is a comment.-->  
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
                       <Pubs>  
                           <Book>  
                               <Title>Artifacts of Roman Civilization</Title>  
                               <Author>Moreno, Jordao</Author>  
                           </Book>  
                           <Book>  
                               <Title>Midieval Tools and Implements</Title>  
                               <Author>Gazit, Inbar</Author>  
                           </Book>  
                       </Pubs>  
                       <!--This is another comment.-->  
doc.Save("test.xml")  
```  
  
 <span data-ttu-id="41c65-135">Lorsque vous examinez le fichier test.xml, vous obtenez la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="41c65-135">When you examine the file test.xml, you get the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a><span data-ttu-id="41c65-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41c65-136">See Also</span></span>  
 [<span data-ttu-id="41c65-137">LINQ to XML programmation présentation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41c65-137">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
