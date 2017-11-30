---
title: "Comment : créer des littéraux XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce1bf763529b436158c2d74811c4938182166f92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="de217-102">Comment : créer des littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de217-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="de217-103">Vous pouvez créer un document, fragment ou élément XML directement dans le code à l’aide d’un littéral XML.</span><span class="sxs-lookup"><span data-stu-id="de217-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="de217-104">Les exemples de cette rubrique montrent comment créer un élément XML qui comporte trois éléments enfants et comment créer un document XML.</span><span class="sxs-lookup"><span data-stu-id="de217-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="de217-105">Vous pouvez également utiliser le [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API pour créer des [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objets.</span><span class="sxs-lookup"><span data-stu-id="de217-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="de217-106">Pour plus d'informations, consultez <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="de217-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="de217-107">Pour créer un élément XML</span><span class="sxs-lookup"><span data-stu-id="de217-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="de217-108">Créer l’élément XML inline en utilisant la syntaxe de littéral XML, qui est identique à la syntaxe XML.</span><span class="sxs-lookup"><span data-stu-id="de217-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     <span data-ttu-id="de217-109">Exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="de217-109">Run the code.</span></span> <span data-ttu-id="de217-110">La sortie de ce code est :</span><span class="sxs-lookup"><span data-stu-id="de217-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="de217-111">Pour créer un document XML</span><span class="sxs-lookup"><span data-stu-id="de217-111">To create an XML document</span></span>  
  
-   <span data-ttu-id="de217-112">Créer le document XML inline.</span><span class="sxs-lookup"><span data-stu-id="de217-112">Create the XML document inline.</span></span> <span data-ttu-id="de217-113">Le code suivant crée un document XML qui a une syntaxe de littéral, une déclaration XML, une instruction de traitement, un commentaire et un élément qui contient un autre élément.</span><span class="sxs-lookup"><span data-stu-id="de217-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     <span data-ttu-id="de217-114">Exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="de217-114">Run the code.</span></span> <span data-ttu-id="de217-115">La sortie de ce code est :</span><span class="sxs-lookup"><span data-stu-id="de217-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="de217-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de217-116">See Also</span></span>  
 [<span data-ttu-id="de217-117">XML</span><span class="sxs-lookup"><span data-stu-id="de217-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="de217-118">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="de217-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="de217-119">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="de217-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="de217-120">Littéral de document XML</span><span class="sxs-lookup"><span data-stu-id="de217-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
