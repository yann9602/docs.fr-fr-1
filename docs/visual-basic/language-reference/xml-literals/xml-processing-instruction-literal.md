---
title: "Littéral d’Instruction (Visual Basic) de traitement XML | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralProcessingInstruction
dev_langs:
- VB
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
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
ms.openlocfilehash: 2ae976530ed3028677a1fef39db92265591df530
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="f8a22-102">Littéral d'instruction de traitement XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8a22-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="f8a22-103">Littéral représentant un <xref:System.Xml.Linq.XProcessingInstruction>objet.</xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="f8a22-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8a22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8a22-104">Syntax</span></span>  
  
```  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="f8a22-105">Composants</span><span class="sxs-lookup"><span data-stu-id="f8a22-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="f8a22-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f8a22-106">Required.</span></span> <span data-ttu-id="f8a22-107">Indique le début de l’instruction de traitement XML littéral.</span><span class="sxs-lookup"><span data-stu-id="f8a22-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="f8a22-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f8a22-108">Required.</span></span> <span data-ttu-id="f8a22-109">Nom indiquant l’application les cibles d’instruction de traitement.</span><span class="sxs-lookup"><span data-stu-id="f8a22-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="f8a22-110">Ne peut pas commencer par « xml » ou « XML ».</span><span class="sxs-lookup"><span data-stu-id="f8a22-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="f8a22-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f8a22-111">Optional.</span></span> <span data-ttu-id="f8a22-112">Chaîne indiquant la manière dont l’application ciblée par `piName` doit traiter le document XML.</span><span class="sxs-lookup"><span data-stu-id="f8a22-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="f8a22-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f8a22-113">Required.</span></span> <span data-ttu-id="f8a22-114">Indique la fin de l’instruction de traitement.</span><span class="sxs-lookup"><span data-stu-id="f8a22-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8a22-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f8a22-115">Return Value</span></span>  
 <span data-ttu-id="f8a22-116">Un <xref:System.Xml.Linq.XProcessingInstruction>objet.</xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="f8a22-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8a22-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="f8a22-117">Remarks</span></span>  
 <span data-ttu-id="f8a22-118">Littéraux d’instruction de traitement XML indiquent la manière dont les applications doivent traiter un document XML.</span><span class="sxs-lookup"><span data-stu-id="f8a22-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="f8a22-119">Lorsqu’une application charge un document XML, l’application peut vérifier les instructions de traitement XML pour déterminer comment traiter le document.</span><span class="sxs-lookup"><span data-stu-id="f8a22-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="f8a22-120">L’application interprète la signification de `piName` et `piData`.</span><span class="sxs-lookup"><span data-stu-id="f8a22-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="f8a22-121">Le littéral de document XML utilise la syntaxe est semblable à celle de l’instruction de traitement XML.</span><span class="sxs-lookup"><span data-stu-id="f8a22-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="f8a22-122">Pour plus d’informations, consultez [littéral de Document XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span><span class="sxs-lookup"><span data-stu-id="f8a22-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8a22-123">Le `piName` élément ne peut pas commencer par les chaînes « xml » ou « XML », parce que la spécification XML 1.0 réserve ces identificateurs.</span><span class="sxs-lookup"><span data-stu-id="f8a22-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="f8a22-124">Vous pouvez assigner un littéral d’instruction de traitement XML à une variable ou l’inclure dans un littéral de document XML.</span><span class="sxs-lookup"><span data-stu-id="f8a22-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8a22-125">Un littéral XML peut couvrir plusieurs lignes sans avoir besoin de caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="f8a22-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="f8a22-126">Cela vous permet de copier le contenu d’un document XML et coller directement dans un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programme.</span><span class="sxs-lookup"><span data-stu-id="f8a22-126">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="f8a22-127">Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit le littéral d’instruction de traitement XML en un appel à la <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>constructeur.</xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="f8a22-127">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8a22-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="f8a22-128">Example</span></span>  
 <span data-ttu-id="f8a22-129">L’exemple suivant crée une instruction de traitement identifiant une feuille de style pour un document XML.</span><span class="sxs-lookup"><span data-stu-id="f8a22-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 <span data-ttu-id="f8a22-130">[!code-vb[VbXMLSamples&#28;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f8a22-130">[!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8a22-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8a22-131">See Also</span></span>  
 <span data-ttu-id="f8a22-132"><xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="f8a22-132"><xref:System.Xml.Linq.XProcessingInstruction></span></span>   
<span data-ttu-id="f8a22-133"> [Littéral de Document XML](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span><span class="sxs-lookup"><span data-stu-id="f8a22-133"> [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span></span>  
<span data-ttu-id="f8a22-134"> [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="f8a22-134"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="f8a22-135"> [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="f8a22-135"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span></span>
