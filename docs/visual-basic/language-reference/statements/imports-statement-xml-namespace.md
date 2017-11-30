---
title: Imports, instruction (espace de noms XML)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0fe6d37c58ead94f2c03736318209abb67cd6dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="0eebf-102">Imports, instruction (espace de noms XML)</span><span class="sxs-lookup"><span data-stu-id="0eebf-102">Imports Statement (XML Namespace)</span></span>
<span data-ttu-id="0eebf-103">Importe des préfixes d’espace de noms XML pour une utilisation dans les littéraux XML et les propriétés d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="0eebf-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eebf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0eebf-104">Syntax</span></span>  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a><span data-ttu-id="0eebf-105">Composants</span><span class="sxs-lookup"><span data-stu-id="0eebf-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="0eebf-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="0eebf-106">Optional.</span></span> <span data-ttu-id="0eebf-107">La chaîne par laquelle le langage XML éléments et attributs peuvent faire référence à `xmlNamespaceName`.</span><span class="sxs-lookup"><span data-stu-id="0eebf-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="0eebf-108">Si aucun `xmlNamespacePrefix` est fourni, l’espace de noms XML importé est l’espace de noms XML par défaut.</span><span class="sxs-lookup"><span data-stu-id="0eebf-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="0eebf-109">Doit être un identificateur XML valide.</span><span class="sxs-lookup"><span data-stu-id="0eebf-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="0eebf-110">Pour plus d’informations, consultez [les attributs et les noms des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="0eebf-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>  
  
 `xmlNamespaceName`  
 <span data-ttu-id="0eebf-111">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="0eebf-111">Required.</span></span> <span data-ttu-id="0eebf-112">Chaîne identifiant l’espace de noms XML importé.</span><span class="sxs-lookup"><span data-stu-id="0eebf-112">The string identifying the XML namespace being imported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0eebf-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="0eebf-113">Remarks</span></span>  
 <span data-ttu-id="0eebf-114">Vous pouvez utiliser la `Imports` instruction afin de définir des espaces de noms XML global que vous pouvez utiliser avec les littéraux XML et les propriétés d’axe XML, ou comme paramètres passés à la `GetXmlNamespace` opérateur.</span><span class="sxs-lookup"><span data-stu-id="0eebf-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="0eebf-115">(Pour plus d’informations sur l’utilisation de la `Imports` instruction pour importer un alias qui peut être utilisé lorsque des noms de type sont utilisés dans votre code, consultez [Imports, instruction (.NET Namespace et Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) La syntaxe de déclaration d’espace de noms XML à l’aide de la `Imports` instruction est identique à la syntaxe utilisée dans XML.</span><span class="sxs-lookup"><span data-stu-id="0eebf-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="0eebf-116">Par conséquent, vous pouvez copier une déclaration d’espace de noms à partir d’un fichier XML et l’utiliser dans un `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="0eebf-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>  
  
 <span data-ttu-id="0eebf-117">Les préfixes d’espace de noms XML sont utiles lorsque vous souhaitez créer des éléments XML qui sont du même espace de noms à plusieurs reprises.</span><span class="sxs-lookup"><span data-stu-id="0eebf-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="0eebf-118">Le préfixe d’espace de noms XML déclaré avec le `Imports` instruction est globale en ce sens qu’il est disponible à tout le code dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="0eebf-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="0eebf-119">Vous pouvez l’utiliser lorsque vous créez des littéraux d’éléments XML et lorsque vous accédez à des propriétés d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="0eebf-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="0eebf-120">Pour plus d’informations, consultez [XML élément Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et [propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).</span><span class="sxs-lookup"><span data-stu-id="0eebf-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).</span></span>  
  
 <span data-ttu-id="0eebf-121">Si vous définissez un espace de noms XML global sans préfixe d’espace de noms (par exemple, `Imports <xmlns="http://SomeNameSpace>"`), cet espace de noms est considéré comme l’espace de noms XML par défaut.</span><span class="sxs-lookup"><span data-stu-id="0eebf-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="0eebf-122">L’espace de noms XML par défaut est utilisé pour les littéraux d’élément XML ou les propriétés d’axe d’attribut XML qui ne spécifient pas explicitement un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="0eebf-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="0eebf-123">L’espace de noms par défaut est également utilisée si l’espace de noms spécifié est l’espace de noms vide (autrement dit, `xmlns=""`).</span><span class="sxs-lookup"><span data-stu-id="0eebf-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="0eebf-124">L’espace de noms XML par défaut ne s’applique pas aux attributs XML dans les littéraux XML ou aux propriétés d’axe d’attribut XML qui n’ont pas d’un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="0eebf-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>  
  
 <span data-ttu-id="0eebf-125">Espaces de noms XML qui sont définis dans un littéral XML, qui sont appelés *des espaces de noms XML local*, sont prioritaires sur les espaces de noms XML qui sont définis par le `Imports` instruction comme étant global.</span><span class="sxs-lookup"><span data-stu-id="0eebf-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="0eebf-126">Les espaces de noms XML qui sont définis par le `Imports` instruction sont prioritaires sur les espaces de noms XML importé pour un projet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0eebf-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="0eebf-127">Si un littéral XML définit un espace de noms XML, cet espace de noms local ne s’applique pas aux expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="0eebf-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>  
  
 <span data-ttu-id="0eebf-128">Espaces de noms XML globaux suivent les mêmes règles de portée et de définition en tant que les espaces de noms .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0eebf-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="0eebf-129">Par conséquent, vous pouvez inclure une `Imports` instruction afin de définir un espace de noms XML global partout où vous pouvez importer un espace de noms .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0eebf-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="0eebf-130">Cela inclut les fichiers de code et les espaces de noms importés au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="0eebf-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="0eebf-131">Pour plus d’informations sur les espaces de noms importés au niveau du projet, consultez [Page références, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0eebf-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="0eebf-132">Chaque fichier source peut contenir un nombre quelconque de `Imports` instructions.</span><span class="sxs-lookup"><span data-stu-id="0eebf-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="0eebf-133">Ces derniers doivent respecter les déclarations d’option, telles que la `Option Strict` instruction et doivent précéder les déclarations d’élément de programmation, tels que `Module` ou `Class` instructions.</span><span class="sxs-lookup"><span data-stu-id="0eebf-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0eebf-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="0eebf-134">Example</span></span>  
 <span data-ttu-id="0eebf-135">L’exemple suivant importe un espace de noms XML par défaut et un espace de noms XML identifié par le préfixe `ns`.</span><span class="sxs-lookup"><span data-stu-id="0eebf-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="0eebf-136">Il crée ensuite des littéraux XML qui utilisent les deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="0eebf-136">It then creates XML literals that use both namespaces.</span></span>  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 <span data-ttu-id="0eebf-137">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="0eebf-137">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a><span data-ttu-id="0eebf-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="0eebf-138">Example</span></span>  
 <span data-ttu-id="0eebf-139">L’exemple suivant importe le préfixe d’espace de noms XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="0eebf-139">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="0eebf-140">Il crée ensuite un littéral XML qui utilise le préfixe d’espace de noms et affiche la forme finale de l’élément.</span><span class="sxs-lookup"><span data-stu-id="0eebf-140">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 <span data-ttu-id="0eebf-141">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="0eebf-141">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="0eebf-142">Notez que le compilateur a converti le préfixe d’espace de noms XML à partir d’un préfixe global à une définition de préfixe local.</span><span class="sxs-lookup"><span data-stu-id="0eebf-142">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0eebf-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="0eebf-143">Example</span></span>  
 <span data-ttu-id="0eebf-144">L’exemple suivant importe le préfixe d’espace de noms XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="0eebf-144">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="0eebf-145">Il utilise ensuite le préfixe de l'espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="0eebf-145">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 <span data-ttu-id="0eebf-146">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="0eebf-146">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="0eebf-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0eebf-147">See Also</span></span>  
 [<span data-ttu-id="0eebf-148">Littéral d’élément XML</span><span class="sxs-lookup"><span data-stu-id="0eebf-148">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="0eebf-149">Propriétés d’axe XML</span><span class="sxs-lookup"><span data-stu-id="0eebf-149">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="0eebf-150">Nom des attributs et des éléments XML déclarés</span><span class="sxs-lookup"><span data-stu-id="0eebf-150">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [<span data-ttu-id="0eebf-151">GetXmlNamespace (opérateur)</span><span class="sxs-lookup"><span data-stu-id="0eebf-151">GetXmlNamespace Operator</span></span>](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)
