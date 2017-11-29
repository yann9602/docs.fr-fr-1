---
title: "Littéral de document XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 008b5857418a572046797bf061a05f265669d427
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="1d0c5-102">Littéral de document XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d0c5-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="1d0c5-103">Littéral représentant un <xref:System.Xml.Linq.XDocument> objet.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d0c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d0c5-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="1d0c5-105">Composants</span><span class="sxs-lookup"><span data-stu-id="1d0c5-105">Parts</span></span>  
  
|<span data-ttu-id="1d0c5-106">Terme</span><span class="sxs-lookup"><span data-stu-id="1d0c5-106">Term</span></span>|<span data-ttu-id="1d0c5-107">Définition</span><span class="sxs-lookup"><span data-stu-id="1d0c5-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="1d0c5-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-108">Optional.</span></span> <span data-ttu-id="1d0c5-109">Utilise du texte littéral qui déclare l’encodage du document.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="1d0c5-110">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-110">Optional.</span></span> <span data-ttu-id="1d0c5-111">Texte littéral.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-111">Literal text.</span></span> <span data-ttu-id="1d0c5-112">Doit être « Oui » ou « non ».</span><span class="sxs-lookup"><span data-stu-id="1d0c5-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="1d0c5-113">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-113">Optional.</span></span> <span data-ttu-id="1d0c5-114">Liste des instructions de traitement XML et de commentaires XML.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="1d0c5-115">Prend le format suivant :</span><span class="sxs-lookup"><span data-stu-id="1d0c5-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="1d0c5-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="1d0c5-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="1d0c5-117">Chaque `piComment` peut prendre l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="1d0c5-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="1d0c5-118">-   [Littéral d’Instruction de traitement XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="1d0c5-118">-   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="1d0c5-119">-   [Littéral de commentaire XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="1d0c5-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="1d0c5-120">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-120">Required.</span></span> <span data-ttu-id="1d0c5-121">Élément racine du document.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-121">Root element of the document.</span></span> <span data-ttu-id="1d0c5-122">Le format est une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="1d0c5-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="1d0c5-123">[Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="1d0c5-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="1d0c5-124">Expression sous la forme incorporée `<%=` `elementExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="1d0c5-125">Le `elementExp` renvoie l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="1d0c5-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="1d0c5-126">Objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="1d0c5-127">Une collection qui contient un <xref:System.Xml.Linq.XElement> objet et un nombre quelconque de <xref:System.Xml.Linq.XProcessingInstruction> et <xref:System.Xml.Linq.XComment> objets.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="1d0c5-128">Pour plus d’informations, consultez [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1d0c5-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="1d0c5-129">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1d0c5-129">Return Value</span></span>  
 <span data-ttu-id="1d0c5-130">Objet <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d0c5-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="1d0c5-131">Remarks</span></span>  
 <span data-ttu-id="1d0c5-132">Un littéral de document XML est identifié par la déclaration XML au début du littéral.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="1d0c5-133">Bien que chaque littéral de document XML doit avoir exactement un élément XML racine, il peut avoir n’importe quel nombre d’instructions de traitement XML et de commentaires XML.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="1d0c5-134">Un littéral de document XML ne peut pas apparaître dans un élément XML.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d0c5-135">Un littéral XML peut couvrir plusieurs lignes sans utiliser de caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="1d0c5-136">Cela vous permet de copier le contenu d’un document XML et coller directement dans un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programme.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-136">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="1d0c5-137">Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur convertit le littéral de document XML en appels à la <xref:System.Xml.Linq.XDocument.%23ctor%2A> et <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructeurs.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-137">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d0c5-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d0c5-138">Example</span></span>  
 <span data-ttu-id="1d0c5-139">L’exemple suivant crée un document XML qui possède une déclaration XML, une instruction de traitement, un commentaire et un élément qui contient un autre élément.</span><span class="sxs-lookup"><span data-stu-id="1d0c5-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1d0c5-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d0c5-140">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 <xref:System.Xml.Linq.XComment>  
 <xref:System.Xml.Linq.XDocument>  
 [<span data-ttu-id="1d0c5-141">Littéral d’instruction de traitement XML</span><span class="sxs-lookup"><span data-stu-id="1d0c5-141">XML Processing Instruction Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)  
 [<span data-ttu-id="1d0c5-142">Littéraux de commentaires XML</span><span class="sxs-lookup"><span data-stu-id="1d0c5-142">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [<span data-ttu-id="1d0c5-143">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="1d0c5-143">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="1d0c5-144">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="1d0c5-144">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="1d0c5-145">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1d0c5-145">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="1d0c5-146">Expressions incorporées en XML</span><span class="sxs-lookup"><span data-stu-id="1d0c5-146">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
