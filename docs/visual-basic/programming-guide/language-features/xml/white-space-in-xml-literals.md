---
title: "Espace blanc dans les littéraux XML (Visual Basic) | Documents Microsoft"
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
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
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
ms.openlocfilehash: 4fc3d30a9c71cbd732597c5e3f32bd01eb489a80
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="4207f-102">Espaces blancs dans les littéraux XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4207f-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="4207f-103">Le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur incorpore uniquement les caractères d’espaces blancs significatifs d’un littéral XML, lorsqu’il crée un [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objet.</span><span class="sxs-lookup"><span data-stu-id="4207f-103">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] object.</span></span> <span data-ttu-id="4207f-104">Les espaces blancs non significatifs ne sont pas incorporés.</span><span class="sxs-lookup"><span data-stu-id="4207f-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="4207f-105">Espaces blancs significatifs et non significatifs</span><span class="sxs-lookup"><span data-stu-id="4207f-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="4207f-106">Espaces blancs dans les littéraux XML sont significatifs que dans trois zones :</span><span class="sxs-lookup"><span data-stu-id="4207f-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="4207f-107">Lorsqu’ils sont dans une valeur d’attribut.</span><span class="sxs-lookup"><span data-stu-id="4207f-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="4207f-108">Lorsqu’ils font partie d’un élément contenu de texte et le texte contient également d’autres caractères.</span><span class="sxs-lookup"><span data-stu-id="4207f-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="4207f-109">Lorsqu’ils sont dans une expression incorporée pour le contenu de texte d’un élément.</span><span class="sxs-lookup"><span data-stu-id="4207f-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="4207f-110">Dans le cas contraire, le compilateur traite les caractères d’espace blanc comme insignifiants et ne les inclut pas dans le [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objet du littéral.</span><span class="sxs-lookup"><span data-stu-id="4207f-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="4207f-111">Pour inclure des espaces blancs non significatifs dans un littéral XML, utilisez une expression incorporée contenant un littéral de chaîne avec les espaces blancs.</span><span class="sxs-lookup"><span data-stu-id="4207f-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4207f-112">Si le `xml:space` attribut apparaît dans un élément XML littéral, le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur inclut l’attribut dans le <xref:System.Xml.Linq.XElement>objet, mais l’ajout de cet attribut ne modifie pas la façon dont le compilateur traite l’espace blanc.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="4207f-112">If the `xml:space` attribute appears in an XML element literal, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4207f-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="4207f-113">Examples</span></span>  
 <span data-ttu-id="4207f-114">L’exemple suivant contient deux éléments XML, externes et internes.</span><span class="sxs-lookup"><span data-stu-id="4207f-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="4207f-115">Les deux éléments contiennent un espace blanc dans leur contenu de texte.</span><span class="sxs-lookup"><span data-stu-id="4207f-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="4207f-116">L’espace blanc dans l’élément externe est insignifiant, car elle contient uniquement un espace blanc et un élément XML.</span><span class="sxs-lookup"><span data-stu-id="4207f-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="4207f-117">L’espace blanc dans l’élément interne est significatif, car elle contient un espace blanc et texte.</span><span class="sxs-lookup"><span data-stu-id="4207f-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 <span data-ttu-id="4207f-118">[!code-vb[VbXMLSamples&#29;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4207f-118">[!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]</span></span>  
  
 <span data-ttu-id="4207f-119">Lors de l’exécution, ce code affiche le texte suivant.</span><span class="sxs-lookup"><span data-stu-id="4207f-119">When run, this code displays the following text.</span></span>  
  
```  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4207f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4207f-120">See Also</span></span>  
 [<span data-ttu-id="4207f-121">Création de code XML en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4207f-121">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
