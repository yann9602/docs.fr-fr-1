---
title: "Les Expressions incorporées en XML (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
dev_langs:
- VB
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
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
ms.openlocfilehash: d24a49f2fa6fd66fe6e4c7724bd4298d65fb7a59
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="9354d-102">Expressions incorporées en XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9354d-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="9354d-103">Expressions incorporées permettent de créer des littéraux XML qui contiennent des expressions évaluées au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9354d-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="9354d-104">La syntaxe pour une expression incorporée est `<%=` `expression` `%>`, qui est la même que la syntaxe utilisée dans [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)].</span><span class="sxs-lookup"><span data-stu-id="9354d-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)].</span></span>  
  
 <span data-ttu-id="9354d-105">Par exemple, vous pouvez créer un élément XML littérale, combinant des expressions incorporées au contenu de texte littéral.</span><span class="sxs-lookup"><span data-stu-id="9354d-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 <span data-ttu-id="9354d-106">[!code-vb[27 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9354d-106">[!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]</span></span>  
  
 <span data-ttu-id="9354d-107">Si `isbnNumber` contient l’entier 12345 et `modifiedDate` contient la date 3/5/2006, lorsque ce code s’exécute, la valeur de `book` est :</span><span class="sxs-lookup"><span data-stu-id="9354d-107">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="9354d-108">Validation et l’emplacement d’Expression incorporée</span><span class="sxs-lookup"><span data-stu-id="9354d-108">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="9354d-109">Expressions incorporées peuvent apparaître uniquement à certains emplacements dans des expressions littérales XML.</span><span class="sxs-lookup"><span data-stu-id="9354d-109">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="9354d-110">Les contrôles d’emplacement expression les types de l’expression peuvent retourner et comment `Nothing` est gérée.</span><span class="sxs-lookup"><span data-stu-id="9354d-110">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="9354d-111">Le tableau suivant décrit les emplacements autorisés et les types d’expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="9354d-111">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="9354d-112">Emplacement dans le littéral</span><span class="sxs-lookup"><span data-stu-id="9354d-112">Location in literal</span></span>|<span data-ttu-id="9354d-113">Type d’expression</span><span class="sxs-lookup"><span data-stu-id="9354d-113">Type of expression</span></span>|<span data-ttu-id="9354d-114">Gestion des`Nothing`</span><span class="sxs-lookup"><span data-stu-id="9354d-114">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="9354d-115">Nom d’élément XML</span><span class="sxs-lookup"><span data-stu-id="9354d-115">XML element name</span></span>|<span data-ttu-id="9354d-116"><xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="9354d-116"><xref:System.Xml.Linq.XName></span></span>|<span data-ttu-id="9354d-117">Erreur</span><span class="sxs-lookup"><span data-stu-id="9354d-117">Error</span></span>|  
|<span data-ttu-id="9354d-118">Contenu d’élément XML</span><span class="sxs-lookup"><span data-stu-id="9354d-118">XML element content</span></span>|<span data-ttu-id="9354d-119">`Object`ou un tableau de`Object`</span><span class="sxs-lookup"><span data-stu-id="9354d-119">`Object` or array of `Object`</span></span>|<span data-ttu-id="9354d-120">Ignoré</span><span class="sxs-lookup"><span data-stu-id="9354d-120">Ignored</span></span>|  
|<span data-ttu-id="9354d-121">Nom d’attribut élément XML</span><span class="sxs-lookup"><span data-stu-id="9354d-121">XML element attribute name</span></span>|<span data-ttu-id="9354d-122"><xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="9354d-122"><xref:System.Xml.Linq.XName></span></span>|<span data-ttu-id="9354d-123">Erreur, sauf si la valeur d’attribut est également`Nothing`</span><span class="sxs-lookup"><span data-stu-id="9354d-123">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="9354d-124">Valeur d’attribut élément XML</span><span class="sxs-lookup"><span data-stu-id="9354d-124">XML element attribute value</span></span>|`Object`|<span data-ttu-id="9354d-125">Déclaration attribute ignorée</span><span class="sxs-lookup"><span data-stu-id="9354d-125">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="9354d-126">Attribut d’élément XML</span><span class="sxs-lookup"><span data-stu-id="9354d-126">XML element attribute</span></span>|<span data-ttu-id="9354d-127"><xref:System.Xml.Linq.XAttribute>ou une collection de<xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="9354d-127"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="9354d-128">Ignoré</span><span class="sxs-lookup"><span data-stu-id="9354d-128">Ignored</span></span>|  
|<span data-ttu-id="9354d-129">Élément racine du document XML</span><span class="sxs-lookup"><span data-stu-id="9354d-129">XML document root element</span></span>|<span data-ttu-id="9354d-130"><xref:System.Xml.Linq.XElement>ou une collection d’un <xref:System.Xml.Linq.XElement>objet et un nombre arbitraire <xref:System.Xml.Linq.XProcessingInstruction> <xref:System.Xml.Linq.XComment>d’objets</xref:System.Xml.Linq.XComment> et</xref:System.Xml.Linq.XProcessingInstruction> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="9354d-130"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="9354d-131">Ignoré</span><span class="sxs-lookup"><span data-stu-id="9354d-131">Ignored</span></span>|  
  
-   <span data-ttu-id="9354d-132">Exemple d’expression incorporée dans un nom d’élément XML :</span><span class="sxs-lookup"><span data-stu-id="9354d-132">Example of an embedded expression in an XML element name:</span></span>  
  
     <span data-ttu-id="9354d-133">[!code-vb[VbXMLSamples n°&32;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="9354d-133">[!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]</span></span>  
  
-   <span data-ttu-id="9354d-134">Exemple d’expression incorporée dans le contenu d’un élément XML :</span><span class="sxs-lookup"><span data-stu-id="9354d-134">Example of an embedded expression in the content of an XML element:</span></span>  
  
     <span data-ttu-id="9354d-135">[!code-vb[VbXMLSamples&#33;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="9354d-135">[!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]</span></span>  
  
-   <span data-ttu-id="9354d-136">Exemple d’expression incorporée dans un nom d’attribut XML élément :</span><span class="sxs-lookup"><span data-stu-id="9354d-136">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     <span data-ttu-id="9354d-137">[!code-vb[VbXMLSamples&#34;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="9354d-137">[!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]</span></span>  
  
-   <span data-ttu-id="9354d-138">Exemple d’expression incorporée dans la valeur d’un attribut d’élément XML :</span><span class="sxs-lookup"><span data-stu-id="9354d-138">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     <span data-ttu-id="9354d-139">[!code-vb[VbXMLSamples&#35;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="9354d-139">[!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]</span></span>  
  
-   <span data-ttu-id="9354d-140">Exemple d’expression incorporée dans un attribut d’élément XML :</span><span class="sxs-lookup"><span data-stu-id="9354d-140">Example of an embedded expression in an XML element attribute:</span></span>  
  
     <span data-ttu-id="9354d-141">[!code-vb[VbXMLSamples n °&36;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="9354d-141">[!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]</span></span>  
  
-   <span data-ttu-id="9354d-142">Exemple d’expression incorporée dans un élément racine du document XML :</span><span class="sxs-lookup"><span data-stu-id="9354d-142">Example of an embedded expression in an XML document root element:</span></span>  
  
     <span data-ttu-id="9354d-143">[!code-vb[VbXMLSamples&#37;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="9354d-143">[!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]</span></span>  
  
 <span data-ttu-id="9354d-144">Si vous activez `Option Strict`, le compilateur vérifie que le type de chaque expression incorporée s’étend au type requis.</span><span class="sxs-lookup"><span data-stu-id="9354d-144">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="9354d-145">La seule exception concerne l’élément racine d’un document XML, qui est vérifié lorsque le code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="9354d-145">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="9354d-146">Si vous compilez sans `Option Strict`, vous pouvez incorporer des expressions de type `Object` et leur type est vérifié au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9354d-146">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="9354d-147">Dans les emplacements où le contenu est facultatif, les expressions incorporées qui contiennent `Nothing` sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="9354d-147">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="9354d-148">Cela signifie que vous n’avez pas à ce contenu d’élément, les valeurs d’attribut, et les éléments de tableau ne sont pas `Nothing` avant d’utiliser un littéral XML.</span><span class="sxs-lookup"><span data-stu-id="9354d-148">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="9354d-149">Requis de valeurs, telles que les noms d’élément et d’attribut, ne peuvent pas être `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="9354d-149">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="9354d-150">Pour plus d’informations sur l’utilisation d’une expression incorporée dans un type particulier de littéral, consultez [littéral de Document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span><span class="sxs-lookup"><span data-stu-id="9354d-150">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="9354d-151">Règles de portée</span><span class="sxs-lookup"><span data-stu-id="9354d-151">Scoping Rules</span></span>  
 <span data-ttu-id="9354d-152">Le compilateur convertit chaque littéral XML en un appel de constructeur pour le type de littéral approprié.</span><span class="sxs-lookup"><span data-stu-id="9354d-152">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="9354d-153">Le contenu littéral et les expressions incorporées dans un littéral XML sont passées comme arguments au constructeur.</span><span class="sxs-lookup"><span data-stu-id="9354d-153">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="9354d-154">Cela signifie que tous les [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] les éléments de programmation disponibles pour un littéral XML sont également disponibles pour ses expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="9354d-154">This means that all [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="9354d-155">Dans un littéral XML, vous pouvez accéder à l’espace de noms XML préfixes déclarés avec la `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="9354d-155">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="9354d-156">Vous pouvez déclarer un nouveau préfixe d’espace de noms XML ou masquer un préfixe d’espace de noms XML existant dans un élément à l’aide de la `xmlns` attribut.</span><span class="sxs-lookup"><span data-stu-id="9354d-156">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="9354d-157">Le nouvel espace de noms est disponible pour les nœuds enfants de cet élément, mais pas pour les littéraux XML des expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="9354d-157">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9354d-158">Lorsque vous déclarez un préfixe d’espace de noms XML à l’aide de la `xmlns` attribut d’espace de noms, la valeur d’attribut doit être une chaîne constante.</span><span class="sxs-lookup"><span data-stu-id="9354d-158">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="9354d-159">À cet égard, à l’aide de la `xmlns` attribut ressemble à l’aide de la `Imports` instruction pour déclarer un espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="9354d-159">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="9354d-160">Vous ne pouvez pas utiliser une expression incorporée pour spécifier la valeur d’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="9354d-160">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9354d-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9354d-161">See Also</span></span>  
 <span data-ttu-id="9354d-162">[Création de code XML en Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="9354d-162">[Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="9354d-163"> [Littéral de Document XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span><span class="sxs-lookup"><span data-stu-id="9354d-163"> [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span></span>  
<span data-ttu-id="9354d-164"> [Littéral d’élément XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="9354d-164"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="9354d-165"> [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="9354d-165"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="9354d-166"> [Instruction Imports (espace de noms et type .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="9354d-166"> [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="9354d-167"> [Vue d’ensemble des littéraux XML](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)</span><span class="sxs-lookup"><span data-stu-id="9354d-167"> [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)</span></span>
