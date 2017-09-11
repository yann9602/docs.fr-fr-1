---
title: "Littéral de Document XML (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
dev_langs:
- VB
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
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
ms.openlocfilehash: 5e173c8bc89f61925c3e6127fb3cac61379aeffa
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="8b84a-102">Littéral de document XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b84a-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="8b84a-103">Littéral représentant un <xref:System.Xml.Linq.XDocument>objet.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="8b84a-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b84a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b84a-104">Syntax</span></span>  
  
```  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="8b84a-105">Composants</span><span class="sxs-lookup"><span data-stu-id="8b84a-105">Parts</span></span>  
  
|<span data-ttu-id="8b84a-106">Terme</span><span class="sxs-lookup"><span data-stu-id="8b84a-106">Term</span></span>|<span data-ttu-id="8b84a-107">Définition</span><span class="sxs-lookup"><span data-stu-id="8b84a-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="8b84a-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8b84a-108">Optional.</span></span> <span data-ttu-id="8b84a-109">Utilise du texte littéral qui déclare l’encodage du document.</span><span class="sxs-lookup"><span data-stu-id="8b84a-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="8b84a-110">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8b84a-110">Optional.</span></span> <span data-ttu-id="8b84a-111">Texte littéral.</span><span class="sxs-lookup"><span data-stu-id="8b84a-111">Literal text.</span></span> <span data-ttu-id="8b84a-112">Doit être « Oui » ou « non ».</span><span class="sxs-lookup"><span data-stu-id="8b84a-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="8b84a-113">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8b84a-113">Optional.</span></span> <span data-ttu-id="8b84a-114">Liste des instructions de traitement XML et de commentaires XML.</span><span class="sxs-lookup"><span data-stu-id="8b84a-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="8b84a-115">Prend le format suivant :</span><span class="sxs-lookup"><span data-stu-id="8b84a-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="8b84a-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="8b84a-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="8b84a-117">Chaque `piComment`peut être une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8b84a-117">Each `piComment`can be one of the following:</span></span><br /><br /><span data-ttu-id="8b84a-118"> -   [Littéral d’Instruction de traitement XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="8b84a-118"> -   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="8b84a-119">-   [Littéral de commentaire XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="8b84a-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="8b84a-120">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8b84a-120">Required.</span></span> <span data-ttu-id="8b84a-121">Élément racine du document.</span><span class="sxs-lookup"><span data-stu-id="8b84a-121">Root element of the document.</span></span> <span data-ttu-id="8b84a-122">Le format est une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8b84a-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="8b84a-123">[Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="8b84a-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="8b84a-124">L’écran expression incorporée, `<%=` `elementExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="8b84a-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="8b84a-125">Le `elementExp` renvoie une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8b84a-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="8b84a-126">Un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="8b84a-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="8b84a-127">Une collection qui contient un <xref:System.Xml.Linq.XElement>objet et n’importe quel nombre de <xref:System.Xml.Linq.XProcessingInstruction>et <xref:System.Xml.Linq.XComment>objets.</xref:System.Xml.Linq.XComment> </xref:System.Xml.Linq.XProcessingInstruction> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="8b84a-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="8b84a-128">Pour plus d’informations, consultez [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8b84a-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="8b84a-129">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8b84a-129">Return Value</span></span>  
 <span data-ttu-id="8b84a-130">Un <xref:System.Xml.Linq.XDocument>objet.</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="8b84a-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b84a-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="8b84a-131">Remarks</span></span>  
 <span data-ttu-id="8b84a-132">Un littéral de document XML est identifié par la déclaration XML au démarrage du littéral.</span><span class="sxs-lookup"><span data-stu-id="8b84a-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="8b84a-133">Bien que chaque littéral de document XML doit avoir exactement un élément XML racine, il peut avoir n’importe quel nombre d’instructions de traitement XML et de commentaires XML.</span><span class="sxs-lookup"><span data-stu-id="8b84a-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="8b84a-134">Un littéral de document XML ne peut pas apparaître dans un élément XML.</span><span class="sxs-lookup"><span data-stu-id="8b84a-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b84a-135">Un littéral XML peut couvrir plusieurs lignes sans utiliser de caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="8b84a-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="8b84a-136">Cela vous permet de copier le contenu d’un document XML et coller directement dans un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programme.</span><span class="sxs-lookup"><span data-stu-id="8b84a-136">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="8b84a-137">Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit le littéral de document XML en appels à la <xref:System.Xml.Linq.XDocument.%23ctor%2A>et <xref:System.Xml.Linq.XDeclaration.%23ctor%2A>constructeurs.</xref:System.Xml.Linq.XDeclaration.%23ctor%2A> </xref:System.Xml.Linq.XDocument.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="8b84a-137">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b84a-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="8b84a-138">Example</span></span>  
 <span data-ttu-id="8b84a-139">L’exemple suivant crée un document XML qui possède une déclaration XML, une instruction de traitement, un commentaire et un élément contenant un autre élément.</span><span class="sxs-lookup"><span data-stu-id="8b84a-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 <span data-ttu-id="8b84a-140">[!code-vb[30 VbXMLSamples](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8b84a-140">[!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b84a-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b84a-141">See Also</span></span>  
 <span data-ttu-id="8b84a-142"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="8b84a-142"><xref:System.Xml.Linq.XElement></span></span>   
 <span data-ttu-id="8b84a-143"><xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="8b84a-143"><xref:System.Xml.Linq.XProcessingInstruction></span></span>   
 <span data-ttu-id="8b84a-144"><xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="8b84a-144"><xref:System.Xml.Linq.XComment></span></span>   
 <span data-ttu-id="8b84a-145"><xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="8b84a-145"><xref:System.Xml.Linq.XDocument></span></span>   
<span data-ttu-id="8b84a-146"> [Littéral d’Instruction de traitement XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md) </span><span class="sxs-lookup"><span data-stu-id="8b84a-146"> [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md) </span></span>  
<span data-ttu-id="8b84a-147"> [Littéraux de commentaires XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span><span class="sxs-lookup"><span data-stu-id="8b84a-147"> [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span></span>  
<span data-ttu-id="8b84a-148"> [Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="8b84a-148"> [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="8b84a-149"> [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="8b84a-149"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="8b84a-150"> [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="8b84a-150"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="8b84a-151"> [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)</span><span class="sxs-lookup"><span data-stu-id="8b84a-151"> [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)</span></span>
