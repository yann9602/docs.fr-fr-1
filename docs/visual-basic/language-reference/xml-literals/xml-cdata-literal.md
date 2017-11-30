---
title: "Littéral CDATA XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 906fd2494dd952c08088b9b7e38dba4505780481
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="cea03-102">Littéral CDATA XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cea03-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="cea03-103">Littéral représentant un <xref:System.Xml.Linq.XCData> objet.</span><span class="sxs-lookup"><span data-stu-id="cea03-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cea03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cea03-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="cea03-105">Composants</span><span class="sxs-lookup"><span data-stu-id="cea03-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="cea03-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="cea03-106">Required.</span></span> <span data-ttu-id="cea03-107">Indique le début de la section CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="cea03-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="cea03-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="cea03-108">Required.</span></span> <span data-ttu-id="cea03-109">Contenu de texte s’affichent dans la section CDATA XML.</span><span class="sxs-lookup"><span data-stu-id="cea03-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="cea03-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="cea03-110">Required.</span></span> <span data-ttu-id="cea03-111">Indique la fin de la section.</span><span class="sxs-lookup"><span data-stu-id="cea03-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cea03-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cea03-112">Return Value</span></span>  
 <span data-ttu-id="cea03-113">Objet <xref:System.Xml.Linq.XCData>.</span><span class="sxs-lookup"><span data-stu-id="cea03-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cea03-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="cea03-114">Remarks</span></span>  
 <span data-ttu-id="cea03-115">Les sections XML CDATA contiennent du texte brut qui doit être inclus, mais non analysé, avec le code XML qui le contient.</span><span class="sxs-lookup"><span data-stu-id="cea03-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="cea03-116">Une section CDATA XML peut contenir n’importe quel texte.</span><span class="sxs-lookup"><span data-stu-id="cea03-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="cea03-117">Cela inclut les caractères XML réservés.</span><span class="sxs-lookup"><span data-stu-id="cea03-117">This includes reserved XML characters.</span></span> <span data-ttu-id="cea03-118">La section CDATA XML se termine par la séquence «]] > ».</span><span class="sxs-lookup"><span data-stu-id="cea03-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="cea03-119">Cela implique les points suivants :</span><span class="sxs-lookup"><span data-stu-id="cea03-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="cea03-120">Vous ne pouvez pas utiliser une expression incorporée dans un littéral XML CDATA, car les délimiteurs d’expression sont contenus XML CDATA valides.</span><span class="sxs-lookup"><span data-stu-id="cea03-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="cea03-121">Les sections XML CDATA ne peuvent pas être imbriquées, parce que `content` ne peut pas contenir la valeur «]] > ».</span><span class="sxs-lookup"><span data-stu-id="cea03-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="cea03-122">Vous pouvez assigner un littéral XML CDATA à une variable ou l’inclure dans un littéral d’élément XML.</span><span class="sxs-lookup"><span data-stu-id="cea03-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cea03-123">Un littéral XML peut couvrir plusieurs lignes, mais n’utilise pas de caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="cea03-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="cea03-124">Cela vous permet de copier le contenu d’un document XML et coller directement dans un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programme.</span><span class="sxs-lookup"><span data-stu-id="cea03-124">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="cea03-125">Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur convertit le littéral XML CDATA à un appel à la <xref:System.Xml.Linq.XCData.%23ctor%2A> constructeur.</span><span class="sxs-lookup"><span data-stu-id="cea03-125">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cea03-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="cea03-126">Example</span></span>  
 <span data-ttu-id="cea03-127">L’exemple suivant crée une section CDATA qui contient le texte « peut contenir des littéraux \<XML > balises ».</span><span class="sxs-lookup"><span data-stu-id="cea03-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cea03-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cea03-128">See Also</span></span>  
 <xref:System.Xml.Linq.XCData>  
 [<span data-ttu-id="cea03-129">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="cea03-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="cea03-130">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="cea03-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="cea03-131">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cea03-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
