---
title: "Comment : incorporer des Expressions dans des littéraux XML (Visual Basic) | Documents Microsoft"
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
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: 16
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
ms.openlocfilehash: e4f086b06575cb8300bd65d450cda6b9893bb692
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="f7f91-102">Comment : incorporer des expressions dans des littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7f91-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="f7f91-103">Vous pouvez combiner des littéraux XML avec des expressions incorporées pour créer un document XML, fragment ou élément qui contient le contenu créé au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f7f91-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="f7f91-104">Les exemples suivants montrent comment utiliser des expressions incorporées pour remplir le contenu de l’élément, les attributs et les noms d’élément en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f7f91-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="f7f91-105">La syntaxe pour une expression incorporée est `<%=` `exp` `%>`, qui est la même syntaxe que [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] utilise.</span><span class="sxs-lookup"><span data-stu-id="f7f91-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] uses.</span></span> <span data-ttu-id="f7f91-106">Pour plus d’informations, consultez [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f7f91-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="f7f91-107">Vous pouvez également utiliser le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] API pour créer des [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objets.</span><span class="sxs-lookup"><span data-stu-id="f7f91-107">You can also use the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] APIs to create [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objects.</span></span> <span data-ttu-id="f7f91-108">Pour plus d’informations, consultez <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="f7f91-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="f7f91-109">Procédures</span><span class="sxs-lookup"><span data-stu-id="f7f91-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="f7f91-110">Pour insérer du texte en tant que contenu de l’élément</span><span class="sxs-lookup"><span data-stu-id="f7f91-110">To insert text as element content</span></span>  
  
-   <span data-ttu-id="f7f91-111">L’exemple suivant montre comment insérer le texte contenu dans le `contactName` variable entre les éléments de nom d’ouverture et de fermeture.</span><span class="sxs-lookup"><span data-stu-id="f7f91-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     <span data-ttu-id="f7f91-112">[!code-vb[VbXMLSamples n °&39;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f7f91-112">[!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]</span></span>  
  
     <span data-ttu-id="f7f91-113">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f7f91-113">This example produces the following output:</span></span>  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="f7f91-114">Pour insérer du texte comme valeur d’attribut</span><span class="sxs-lookup"><span data-stu-id="f7f91-114">To insert text as an attribute value</span></span>  
  
-   <span data-ttu-id="f7f91-115">L’exemple suivant montre comment insérer le texte contenu dans le `phoneType` variable comme valeur de la `type` attribut.</span><span class="sxs-lookup"><span data-stu-id="f7f91-115">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     <span data-ttu-id="f7f91-116">[!code-vb[VbXMLSamples numéro&40;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f7f91-116">[!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]</span></span>  
  
     <span data-ttu-id="f7f91-117">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f7f91-117">This example produces the following output:</span></span>  
  
    ```  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="f7f91-118">Pour insérer du texte pour un nom d’élément</span><span class="sxs-lookup"><span data-stu-id="f7f91-118">To insert text for an element name</span></span>  
  
-   <span data-ttu-id="f7f91-119">L’exemple suivant montre comment insérer le texte contenu dans le `elementName` variable en tant que le nom d’un élément.</span><span class="sxs-lookup"><span data-stu-id="f7f91-119">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="f7f91-120">Lorsque vous créez des éléments à l’aide de cette technique, vous devez les fermer avec la \</ > balise.</span><span class="sxs-lookup"><span data-stu-id="f7f91-120">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     <span data-ttu-id="f7f91-121">[!code-vb[# VbXMLSamples&41;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="f7f91-121">[!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]</span></span>  
  
     <span data-ttu-id="f7f91-122">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f7f91-122">This example produces the following output:</span></span>  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f7f91-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7f91-123">See Also</span></span>  
 <span data-ttu-id="f7f91-124">[Comment : créer des littéraux XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md) </span><span class="sxs-lookup"><span data-stu-id="f7f91-124">[How to: Create XML Literals](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md) </span></span>  
<span data-ttu-id="f7f91-125"> [Expressions incorporées en XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span><span class="sxs-lookup"><span data-stu-id="f7f91-125"> [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span></span>  
<span data-ttu-id="f7f91-126"> [Création de code XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="f7f91-126"> [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="f7f91-127"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span><span class="sxs-lookup"><span data-stu-id="f7f91-127"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span></span>
