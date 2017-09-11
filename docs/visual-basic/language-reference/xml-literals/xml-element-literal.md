---
title: "Littéral d’élément XML (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralElement
dev_langs:
- VB
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: 32
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
ms.openlocfilehash: d5cf769a1e3f668652d1eb4551058deba38a8acf
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="b6f33-102">Littéral d'élément XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6f33-102">XML Element Literal (Visual Basic)</span></span>
<span data-ttu-id="b6f33-103">Un littéral qui représente une <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b6f33-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6f33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6f33-104">Syntax</span></span>  
  
```  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a><span data-ttu-id="b6f33-105">Composants</span><span class="sxs-lookup"><span data-stu-id="b6f33-105">Parts</span></span>  
  
-   `<`  
  
     <span data-ttu-id="b6f33-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b6f33-106">Required.</span></span> <span data-ttu-id="b6f33-107">Ouvre la balise d’élément initiale.</span><span class="sxs-lookup"><span data-stu-id="b6f33-107">Opens the starting element tag.</span></span>  
  
-   `name`  
  
     <span data-ttu-id="b6f33-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b6f33-108">Required.</span></span> <span data-ttu-id="b6f33-109">Nom de l'élément.</span><span class="sxs-lookup"><span data-stu-id="b6f33-109">Name of the element.</span></span> <span data-ttu-id="b6f33-110">Le format est une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b6f33-110">The format is one of the following:</span></span>  
  
    -   <span data-ttu-id="b6f33-111">Texte littéral pour le nom de l’élément, sous la forme [`ePrefix``:`]`eName`, où :</span><span class="sxs-lookup"><span data-stu-id="b6f33-111">Literal text for the element name, of the form [`ePrefix``:`]`eName`, where:</span></span>  
  
        |<span data-ttu-id="b6f33-112">Élément</span><span class="sxs-lookup"><span data-stu-id="b6f33-112">Part</span></span>|<span data-ttu-id="b6f33-113">Description</span><span class="sxs-lookup"><span data-stu-id="b6f33-113">Description</span></span>|  
        |---|---|  
        |`ePrefix`|<span data-ttu-id="b6f33-114">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b6f33-114">Optional.</span></span> <span data-ttu-id="b6f33-115">Préfixe d’espace de noms XML de l’élément.</span><span class="sxs-lookup"><span data-stu-id="b6f33-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="b6f33-116">Doit être un espace de noms XML global est défini avec un `Imports` instruction dans le fichier ou au niveau du projet, ou un espace de noms XML local défini dans cet élément ou un élément parent.</span><span class="sxs-lookup"><span data-stu-id="b6f33-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`eName`|<span data-ttu-id="b6f33-117">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b6f33-117">Required.</span></span> <span data-ttu-id="b6f33-118">Nom de l'élément.</span><span class="sxs-lookup"><span data-stu-id="b6f33-118">Name of the element.</span></span> <span data-ttu-id="b6f33-119">Le format est une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b6f33-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="b6f33-120">-Texte littéral.</span><span class="sxs-lookup"><span data-stu-id="b6f33-120">-   Literal text.</span></span> <span data-ttu-id="b6f33-121">Consultez la page [nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b6f33-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="b6f33-122">-L’écran expression incorporée, `<%=` e`NameExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="b6f33-122">-   Embedded expression of the form `<%=` e`NameExp` `%>`.</span></span> <span data-ttu-id="b6f33-123">Le type de `eNameExp` doit être `String` ou un type qui est implicitement convertible en <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="b6f33-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
  
    -   <span data-ttu-id="b6f33-124">L’écran expression incorporée, `<%=` `nameExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="b6f33-124">Embedded expression of the form `<%=` `nameExp` `%>`.</span></span> <span data-ttu-id="b6f33-125">Le type de `nameExp` doit être `String` ou un type implicitement convertible en <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="b6f33-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="b6f33-126">Une expression incorporée n’est pas autorisée dans une balise de fermeture d’un élément.</span><span class="sxs-lookup"><span data-stu-id="b6f33-126">An embedded expression is not allowed in a closing tag of an element.</span></span>  
  
-   `attributeList`  
  
     <span data-ttu-id="b6f33-127">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b6f33-127">Optional.</span></span> <span data-ttu-id="b6f33-128">Liste d’attributs déclarée dans le littéral.</span><span class="sxs-lookup"><span data-stu-id="b6f33-128">List of attributes declared in the literal.</span></span>  
  
     `attribute [ attribute ... ]`  
  
     <span data-ttu-id="b6f33-129">Chaque `attribute` possède l’une des syntaxes suivantes :</span><span class="sxs-lookup"><span data-stu-id="b6f33-129">Each `attribute` has one of the following syntaxes:</span></span>  
  
    -   <span data-ttu-id="b6f33-130">Affectation, sous la forme de l’attribut [`aPrefix``:`]`aName``=``aValue`, où :</span><span class="sxs-lookup"><span data-stu-id="b6f33-130">Attribute assignment, of the form [`aPrefix``:`]`aName``=``aValue`, where:</span></span>  
  
        |<span data-ttu-id="b6f33-131">Élément</span><span class="sxs-lookup"><span data-stu-id="b6f33-131">Part</span></span>|<span data-ttu-id="b6f33-132">Description</span><span class="sxs-lookup"><span data-stu-id="b6f33-132">Description</span></span>|  
        |---|---|  
        |`aPrefix`|<span data-ttu-id="b6f33-133">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b6f33-133">Optional.</span></span> <span data-ttu-id="b6f33-134">Préfixe d’espace de noms XML pour l’attribut.</span><span class="sxs-lookup"><span data-stu-id="b6f33-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="b6f33-135">Doit être un espace de noms XML global est défini avec un `Imports` instruction ou un espace de noms XML local défini dans cet élément ou un élément parent.</span><span class="sxs-lookup"><span data-stu-id="b6f33-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`aName`|<span data-ttu-id="b6f33-136">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b6f33-136">Required.</span></span> <span data-ttu-id="b6f33-137">Nom de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="b6f33-137">Name of the attribute.</span></span> <span data-ttu-id="b6f33-138">Le format est une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b6f33-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="b6f33-139">-Texte littéral.</span><span class="sxs-lookup"><span data-stu-id="b6f33-139">-   Literal text.</span></span> <span data-ttu-id="b6f33-140">Consultez la page [nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b6f33-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="b6f33-141">-L’écran expression incorporée, `<%=` `aNameExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="b6f33-141">-   Embedded expression of the form `<%=` `aNameExp` `%>`.</span></span> <span data-ttu-id="b6f33-142">Le type de `aNameExp` doit être `String` ou un type qui est implicitement convertible en <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="b6f33-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
        |`aValue`|<span data-ttu-id="b6f33-143">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b6f33-143">Optional.</span></span> <span data-ttu-id="b6f33-144">Valeur de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="b6f33-144">Value of the attribute.</span></span> <span data-ttu-id="b6f33-145">Le format est une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b6f33-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="b6f33-146">-Texte littéral, entouré guillemets.</span><span class="sxs-lookup"><span data-stu-id="b6f33-146">-   Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="b6f33-147">-L’écran expression incorporée, `<%=` `aValueExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="b6f33-147">-   Embedded expression of the form `<%=` `aValueExp` `%>`.</span></span> <span data-ttu-id="b6f33-148">N’importe quel type est autorisé.</span><span class="sxs-lookup"><span data-stu-id="b6f33-148">Any type is allowed.</span></span>|  
  
    -   <span data-ttu-id="b6f33-149">L’écran expression incorporée, `<%=` `aExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="b6f33-149">Embedded expression of the form `<%=` `aExp` `%>`.</span></span>  
  
-   `/>`  
  
     <span data-ttu-id="b6f33-150">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b6f33-150">Optional.</span></span> <span data-ttu-id="b6f33-151">Indique que l’élément est un élément vide, sans contenu.</span><span class="sxs-lookup"><span data-stu-id="b6f33-151">Indicates that the element is an empty element, without content.</span></span>  
  
-   `>`  
  
     <span data-ttu-id="b6f33-152">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b6f33-152">Required.</span></span> <span data-ttu-id="b6f33-153">Met fin à la balise d’élément initiale ou vide.</span><span class="sxs-lookup"><span data-stu-id="b6f33-153">Ends the beginning or empty element tag.</span></span>  
  
-   `elementContents`  
  
     <span data-ttu-id="b6f33-154">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b6f33-154">Optional.</span></span> <span data-ttu-id="b6f33-155">Contenu de l’élément.</span><span class="sxs-lookup"><span data-stu-id="b6f33-155">Content of the element.</span></span>  
  
     `content [ content ... ]`  
  
     <span data-ttu-id="b6f33-156">Chaque `content` peut être une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b6f33-156">Each `content` can be one of the following:</span></span>  
  
    -   <span data-ttu-id="b6f33-157">Texte littéral.</span><span class="sxs-lookup"><span data-stu-id="b6f33-157">Literal text.</span></span> <span data-ttu-id="b6f33-158">Tout l’espace blanc dans `elementContents` devient significatif si du texte littéral est.</span><span class="sxs-lookup"><span data-stu-id="b6f33-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>  
  
    -   <span data-ttu-id="b6f33-159">L’écran expression incorporée, `<%=` `contentExp` `%>`.</span><span class="sxs-lookup"><span data-stu-id="b6f33-159">Embedded expression of the form `<%=` `contentExp` `%>`.</span></span>  
  
    -   <span data-ttu-id="b6f33-160">Littéral d’élément XML.</span><span class="sxs-lookup"><span data-stu-id="b6f33-160">XML element literal.</span></span>  
  
    -   <span data-ttu-id="b6f33-161">Littéral de commentaire XML.</span><span class="sxs-lookup"><span data-stu-id="b6f33-161">XML comment literal.</span></span> <span data-ttu-id="b6f33-162">Consultez la page [littéral de commentaire XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span><span class="sxs-lookup"><span data-stu-id="b6f33-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>  
  
    -   <span data-ttu-id="b6f33-163">Instruction de traitement XML littérale.</span><span class="sxs-lookup"><span data-stu-id="b6f33-163">XML processing instruction literal.</span></span> <span data-ttu-id="b6f33-164">Consultez la page [littéral d’Instruction de traitement XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span><span class="sxs-lookup"><span data-stu-id="b6f33-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>  
  
    -   <span data-ttu-id="b6f33-165">Littéral XML CDATA.</span><span class="sxs-lookup"><span data-stu-id="b6f33-165">XML CDATA literal.</span></span> <span data-ttu-id="b6f33-166">Consultez la page [littéral CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span><span class="sxs-lookup"><span data-stu-id="b6f33-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>  
  
-   <span data-ttu-id="b6f33-167">`</`[`name`]`>`</span><span class="sxs-lookup"><span data-stu-id="b6f33-167">`</`[`name`]`>`</span></span>  
  
     <span data-ttu-id="b6f33-168">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b6f33-168">Optional.</span></span> <span data-ttu-id="b6f33-169">Représente la balise de fermeture de l’élément.</span><span class="sxs-lookup"><span data-stu-id="b6f33-169">Represents the closing tag for the element.</span></span> <span data-ttu-id="b6f33-170">Le paramètre facultatif `name` paramètre n’est pas autorisé lorsqu’il est le résultat d’une expression incorporée.</span><span class="sxs-lookup"><span data-stu-id="b6f33-170">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6f33-171">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b6f33-171">Return Value</span></span>  
 <span data-ttu-id="b6f33-172">Un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b6f33-172">An <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6f33-173">Remarques</span><span class="sxs-lookup"><span data-stu-id="b6f33-173">Remarks</span></span>  
 <span data-ttu-id="b6f33-174">Vous pouvez utiliser la syntaxe de littéral d’élément XML pour créer <xref:System.Xml.Linq.XElement>objets dans votre code.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b6f33-174">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6f33-175">Un littéral XML peut couvrir plusieurs lignes sans utiliser de caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="b6f33-175">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="b6f33-176">Cette fonctionnalité vous permet de copier le contenu d’un document XML et coller directement dans un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programme.</span><span class="sxs-lookup"><span data-stu-id="b6f33-176">This feature enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="b6f33-177">Les expressions incorporées du formulaire `<%=` `exp` `%>` vous permettent d’ajouter des informations dynamiques à un littéral d’élément XML.</span><span class="sxs-lookup"><span data-stu-id="b6f33-177">Embedded expressions of the form `<%=` `exp` `%>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="b6f33-178">Pour plus d’informations, consultez [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b6f33-178">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="b6f33-179">Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit le littéral d’élément XML en appels à la <xref:System.Xml.Linq.XElement.%23ctor%2A>constructeur et, si nécessaire, le <xref:System.Xml.Linq.XAttribute.%23ctor%2A>constructeur.</xref:System.Xml.Linq.XAttribute.%23ctor%2A> </xref:System.Xml.Linq.XElement.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="b6f33-179">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="b6f33-180">Espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="b6f33-180">XML Namespaces</span></span>  
 <span data-ttu-id="b6f33-181">Préfixes d’espace de noms XML sont utiles lorsque vous devez créer des littéraux XML avec des éléments à partir de l’espace de noms plusieurs fois dans le code.</span><span class="sxs-lookup"><span data-stu-id="b6f33-181">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="b6f33-182">Vous pouvez utiliser les préfixes d’espace de noms XML globaux, que vous définissez à l’aide de la `Imports` instruction, ou les préfixes locaux, que vous définissez à l’aide de la `xmlns:``xmlPrefix`= «`xmlNamespace`» la syntaxe d’attribut.</span><span class="sxs-lookup"><span data-stu-id="b6f33-182">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:``xmlPrefix`="`xmlNamespace`" attribute syntax.</span></span> <span data-ttu-id="b6f33-183">Pour plus d’informations, consultez [l’instruction Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="b6f33-183">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
 <span data-ttu-id="b6f33-184">Conformément aux règles de portée pour les espaces de noms XML, les préfixes locaux sont prioritaires sur les préfixes globaux.</span><span class="sxs-lookup"><span data-stu-id="b6f33-184">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="b6f33-185">Toutefois, si un littéral XML définit un espace de noms XML, cet espace de noms n’est pas disponible pour les expressions qui apparaissent dans une expression incorporée.</span><span class="sxs-lookup"><span data-stu-id="b6f33-185">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="b6f33-186">L’expression incorporée peut accéder uniquement l’espace de noms XML global.</span><span class="sxs-lookup"><span data-stu-id="b6f33-186">The embedded expression can access only the global XML namespace.</span></span>  
  
 <span data-ttu-id="b6f33-187">Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit chaque espace de noms XML global utilisé par un littéral XML dans une définition d’espace de noms locale dans le code généré.</span><span class="sxs-lookup"><span data-stu-id="b6f33-187">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="b6f33-188">Espaces de noms XML globaux qui ne sont pas utilisés n’apparaissent pas dans le code généré.</span><span class="sxs-lookup"><span data-stu-id="b6f33-188">Global XML namespaces that are not used do not appear in the generated code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6f33-189">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6f33-189">Example</span></span>  
 <span data-ttu-id="b6f33-190">L’exemple suivant montre comment créer un élément XML simple qui a deux éléments vides imbriqués.</span><span class="sxs-lookup"><span data-stu-id="b6f33-190">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>  
  
 <span data-ttu-id="b6f33-191">[!code-vb[VbXMLSamples&#20;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6f33-191">[!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]</span></span>  
  
 <span data-ttu-id="b6f33-192">L’exemple affiche le texte suivant.</span><span class="sxs-lookup"><span data-stu-id="b6f33-192">The example displays the following text.</span></span> <span data-ttu-id="b6f33-193">Notez que le littéral conserve la structure des éléments vides.</span><span class="sxs-lookup"><span data-stu-id="b6f33-193">Notice that the literal preserves the structure of the empty elements.</span></span>  
  
```  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a><span data-ttu-id="b6f33-194">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6f33-194">Example</span></span>  
 <span data-ttu-id="b6f33-195">L’exemple suivant montre comment utiliser des expressions incorporées pour nommer un élément et de créer des attributs.</span><span class="sxs-lookup"><span data-stu-id="b6f33-195">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>  
  
 <span data-ttu-id="b6f33-196">[!code-vb[VbXMLSamples n °&21;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6f33-196">[!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]</span></span>  
  
 <span data-ttu-id="b6f33-197">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="b6f33-197">This code displays the following text:</span></span>  
  
```  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a><span data-ttu-id="b6f33-198">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6f33-198">Example</span></span>  
 <span data-ttu-id="b6f33-199">L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="b6f33-199">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="b6f33-200">Ensuite, il utilise le préfixe d’espace de noms pour créer un littéral XML et affiche le formulaire final de l’élément.</span><span class="sxs-lookup"><span data-stu-id="b6f33-200">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>  
  
 <span data-ttu-id="b6f33-201">[!code-vb[VbXMLSamples&#22;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6f33-201">[!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]</span></span>  
  
 <span data-ttu-id="b6f33-202">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="b6f33-202">This code displays the following text:</span></span>  
  
```  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="b6f33-203">Notez que le compilateur a converti le préfixe d’espace de noms XML global en une définition de préfixe pour l’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="b6f33-203">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="b6f33-204">Le \<ns:middle > élément redéfinit le préfixe d’espace de noms XML pour le \<ns:inner1 > élément.</span><span class="sxs-lookup"><span data-stu-id="b6f33-204">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="b6f33-205">Toutefois, le \<ns:inner2 > élément utilise l’espace de noms défini par le `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="b6f33-205">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6f33-206">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6f33-206">See Also</span></span>  
 <span data-ttu-id="b6f33-207"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="b6f33-207"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="b6f33-208"> [Nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="b6f33-208"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md) </span></span>  
<span data-ttu-id="b6f33-209"> [Littéraux de commentaires XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span><span class="sxs-lookup"><span data-stu-id="b6f33-209"> [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span></span>  
<span data-ttu-id="b6f33-210"> [Littéral CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md) </span><span class="sxs-lookup"><span data-stu-id="b6f33-210"> [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md) </span></span>  
<span data-ttu-id="b6f33-211"> [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="b6f33-211"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="b6f33-212"> [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="b6f33-212"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="b6f33-213"> [Expressions incorporées en XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span><span class="sxs-lookup"><span data-stu-id="b6f33-213"> [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span></span>  
<span data-ttu-id="b6f33-214"> [Imports (instruction) (espace de noms XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)</span><span class="sxs-lookup"><span data-stu-id="b6f33-214"> [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)</span></span>
