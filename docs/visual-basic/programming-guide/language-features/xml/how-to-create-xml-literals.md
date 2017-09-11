---
title: "Comment : créer des littéraux XML (Visual Basic) | Documents Microsoft"
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
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
caps.latest.revision: 17
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
ms.openlocfilehash: 3a7b5dc692317067290b48222ba056d765a449f3
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="cc109-102">Comment : créer des littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc109-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="cc109-103">Vous pouvez créer un document, fragment ou élément XML directement dans le code à l’aide d’un littéral XML.</span><span class="sxs-lookup"><span data-stu-id="cc109-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="cc109-104">Les exemples de cette rubrique montrent comment créer un élément XML qui comporte trois éléments enfants et comment créer un document XML.</span><span class="sxs-lookup"><span data-stu-id="cc109-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="cc109-105">Vous pouvez également utiliser le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API pour créer des [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objets.</span><span class="sxs-lookup"><span data-stu-id="cc109-105">You can also use the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] APIs to create [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objects.</span></span> <span data-ttu-id="cc109-106">Pour plus d’informations, consultez <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="cc109-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="cc109-107">Pour créer un élément XML</span><span class="sxs-lookup"><span data-stu-id="cc109-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="cc109-108">Créer le code XML inline en utilisant la syntaxe de littéral XML, qui est identique à la syntaxe XML.</span><span class="sxs-lookup"><span data-stu-id="cc109-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     <span data-ttu-id="cc109-109">[!code-vb[VbXMLSamples n °&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc109-109">[!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]</span></span>  
  
     <span data-ttu-id="cc109-110">Exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="cc109-110">Run the code.</span></span> <span data-ttu-id="cc109-111">La sortie de ce code est :</span><span class="sxs-lookup"><span data-stu-id="cc109-111">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="cc109-112">Pour créer un document XML</span><span class="sxs-lookup"><span data-stu-id="cc109-112">To create an XML document</span></span>  
  
-   <span data-ttu-id="cc109-113">Créer le document XML inline.</span><span class="sxs-lookup"><span data-stu-id="cc109-113">Create the XML document inline.</span></span> <span data-ttu-id="cc109-114">Le code suivant crée un document XML qui possède la syntaxe littérale, une déclaration XML, une instruction de traitement, un commentaire et un élément contenant un autre élément.</span><span class="sxs-lookup"><span data-stu-id="cc109-114">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     <span data-ttu-id="cc109-115">[!code-vb[30 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="cc109-115">[!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]</span></span>  
  
     <span data-ttu-id="cc109-116">Exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="cc109-116">Run the code.</span></span> <span data-ttu-id="cc109-117">La sortie de ce code est :</span><span class="sxs-lookup"><span data-stu-id="cc109-117">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="cc109-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc109-118">See Also</span></span>  
 <span data-ttu-id="cc109-119">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="cc109-119">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="cc109-120"> [Création de code XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="cc109-120"> [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="cc109-121"> [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="cc109-121"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="cc109-122"> [Littéral de document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)</span><span class="sxs-lookup"><span data-stu-id="cc109-122"> [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)</span></span>
