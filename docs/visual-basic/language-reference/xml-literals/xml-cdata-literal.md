---
title: "Littéral CDATA XML (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
dev_langs:
- VB
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
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
ms.openlocfilehash: 6bf12a5dd5b24b0a915cb15f41cb8947c33e94b0
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="d9dc9-102">Littéral CDATA XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9dc9-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="d9dc9-103">Littéral représentant un <xref:System.Xml.Linq.XCData>objet.</xref:System.Xml.Linq.XCData></span><span class="sxs-lookup"><span data-stu-id="d9dc9-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9dc9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9dc9-104">Syntax</span></span>  
  
```  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="d9dc9-105">Composants</span><span class="sxs-lookup"><span data-stu-id="d9dc9-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="d9dc9-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-106">Required.</span></span> <span data-ttu-id="d9dc9-107">Indique le début de la section CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="d9dc9-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-108">Required.</span></span> <span data-ttu-id="d9dc9-109">Contenu de texte à afficher dans la section CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="d9dc9-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-110">Required.</span></span> <span data-ttu-id="d9dc9-111">Indique la fin de la section.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9dc9-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d9dc9-112">Return Value</span></span>  
 <span data-ttu-id="d9dc9-113">Un <xref:System.Xml.Linq.XCData>objet.</xref:System.Xml.Linq.XCData></span><span class="sxs-lookup"><span data-stu-id="d9dc9-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9dc9-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="d9dc9-114">Remarks</span></span>  
 <span data-ttu-id="d9dc9-115">Les sections XML CDATA contiennent du texte brut qui doit être inclus, mais non analysé, avec le code XML qui le contient.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="d9dc9-116">Une section CDATA XML peut contenir n’importe quel texte.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="d9dc9-117">Cela inclut les caractères XML réservés.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-117">This includes reserved XML characters.</span></span> <span data-ttu-id="d9dc9-118">La section XML CDATA se termine par la séquence »]] > ».</span><span class="sxs-lookup"><span data-stu-id="d9dc9-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="d9dc9-119">Cela implique les points suivants :</span><span class="sxs-lookup"><span data-stu-id="d9dc9-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="d9dc9-120">Vous ne pouvez pas utiliser une expression incorporée dans un littéral XML CDATA car les délimiteurs d’expression sont des contenus XML CDATA valides.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="d9dc9-121">Les sections XML CDATA ne peuvent pas être imbriquées, parce que `content` ne peut pas contenir la valeur «]] > ».</span><span class="sxs-lookup"><span data-stu-id="d9dc9-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="d9dc9-122">Vous pouvez assigner un littéral XML CDATA à une variable ou l’inclure dans un littéral d’élément XML.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9dc9-123">Un littéral XML peut couvrir plusieurs lignes, mais n’utilise pas de caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="d9dc9-124">Cela vous permet de copier le contenu d’un document XML et coller directement dans un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programme.</span><span class="sxs-lookup"><span data-stu-id="d9dc9-124">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="d9dc9-125">Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit le littéral XML CDATA en un appel à la <xref:System.Xml.Linq.XCData.%23ctor%2A>constructeur.</xref:System.Xml.Linq.XCData.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="d9dc9-125">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9dc9-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="d9dc9-126">Example</span></span>  
 <span data-ttu-id="d9dc9-127">L’exemple suivant crée une section CDATA qui contient le texte « peut contenir des littéraux \<XML > balises ».</span><span class="sxs-lookup"><span data-stu-id="d9dc9-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 <span data-ttu-id="d9dc9-128">[!code-vb[VbXMLSamples n °&23;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d9dc9-128">[!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9dc9-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9dc9-129">See Also</span></span>  
 <span data-ttu-id="d9dc9-130"><xref:System.Xml.Linq.XCData></xref:System.Xml.Linq.XCData></span><span class="sxs-lookup"><span data-stu-id="d9dc9-130"><xref:System.Xml.Linq.XCData></span></span>   
<span data-ttu-id="d9dc9-131"> [Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="d9dc9-131"> [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="d9dc9-132"> [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="d9dc9-132"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="d9dc9-133"> [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="d9dc9-133"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span></span>
