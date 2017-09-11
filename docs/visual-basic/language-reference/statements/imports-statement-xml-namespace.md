---
title: Imports, instruction (XML Namespace) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ImportsXmlns
dev_langs:
- VB
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
caps.latest.revision: 18
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
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: 66ac2bd947328dab9df812709525b43fb27145ac
ms.contentlocale: fr-fr
ms.lasthandoff: 06/01/2017

---
# <a name="imports-statement-xml-namespace"></a><span data-ttu-id="7c232-102">Imports, instruction (espace de noms XML)</span><span class="sxs-lookup"><span data-stu-id="7c232-102">Imports Statement (XML Namespace)</span></span>
<span data-ttu-id="7c232-103">Importe des préfixes d’espace de noms XML pour une utilisation dans les littéraux XML et les propriétés d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="7c232-103">Imports XML namespace prefixes for use in XML literals and XML axis properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c232-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c232-104">Syntax</span></span>  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a><span data-ttu-id="7c232-105">Composants</span><span class="sxs-lookup"><span data-stu-id="7c232-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="7c232-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7c232-106">Optional.</span></span> <span data-ttu-id="7c232-107">La chaîne en XML ainsi que les attributs et les éléments peuvent faire référence à `xmlNamespaceName`.</span><span class="sxs-lookup"><span data-stu-id="7c232-107">The string by which XML elements and attributes can refer to `xmlNamespaceName`.</span></span> <span data-ttu-id="7c232-108">Si aucune `xmlNamespacePrefix` est fourni, l’espace de noms XML importé est l’espace de noms XML par défaut.</span><span class="sxs-lookup"><span data-stu-id="7c232-108">If no `xmlNamespacePrefix` is supplied, the imported XML namespace is the default XML namespace.</span></span> <span data-ttu-id="7c232-109">Doit être un identificateur XML valide.</span><span class="sxs-lookup"><span data-stu-id="7c232-109">Must be a valid XML identifier.</span></span> <span data-ttu-id="7c232-110">Pour plus d’informations, consultez [les attributs et les noms des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="7c232-110">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>  
  
 `xmlNamespaceName`  
 <span data-ttu-id="7c232-111">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7c232-111">Required.</span></span> <span data-ttu-id="7c232-112">La chaîne qui identifie l’espace de noms XML en cours d’importation.</span><span class="sxs-lookup"><span data-stu-id="7c232-112">The string identifying the XML namespace being imported.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c232-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="7c232-113">Remarks</span></span>  
 <span data-ttu-id="7c232-114">Vous pouvez utiliser la `Imports` instruction afin de définir des espaces de noms XML global que vous pouvez utiliser avec les littéraux XML et les propriétés d’axe XML, ou comme paramètres passés à la `GetXmlNamespace` opérateur.</span><span class="sxs-lookup"><span data-stu-id="7c232-114">You can use the `Imports` statement to define global XML namespaces that you can use with XML literals and XML axis properties, or as parameters passed to the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="7c232-115">(Pour plus d’informations sur l’utilisation de la `Imports` pour importer un alias utilisable lorsque des noms de type sont utilisés dans votre code, consultez [Imports, instruction (.NET Namespace et Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) La syntaxe de déclaration d’espace de noms XML à l’aide de la `Imports` instruction est identique à la syntaxe utilisée dans XML.</span><span class="sxs-lookup"><span data-stu-id="7c232-115">(For information about using the `Imports` statement to import an alias that can be used where type names are used in your code, see [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) The syntax for declaring an XML namespace by using the `Imports` statement is identical to the syntax used in XML.</span></span> <span data-ttu-id="7c232-116">Par conséquent, vous pouvez copier une déclaration d’espace de noms à partir d’un fichier XML et l’utiliser dans un `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="7c232-116">Therefore, you can copy a namespace declaration from an XML file and use it in an `Imports` statement.</span></span>  
  
 <span data-ttu-id="7c232-117">Préfixes d’espace de noms XML sont utiles lorsque vous souhaitez créer à plusieurs reprises des éléments XML qui sont dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7c232-117">XML namespace prefixes are useful when you want to repeatedly create XML elements that are from the same namespace.</span></span> <span data-ttu-id="7c232-118">Le préfixe d’espace de noms XML déclaré avec le `Imports` instruction est globale en ce sens qu’il est disponible à tout le code dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="7c232-118">The XML namespace prefix declared with the `Imports` statement is global in the sense that it is available to all code in the file.</span></span> <span data-ttu-id="7c232-119">Vous pouvez l’utiliser lorsque vous créez des littéraux d’éléments XML et lorsque vous accédez aux propriétés d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="7c232-119">You can use it when you create XML element literals and when you access XML axis properties.</span></span> <span data-ttu-id="7c232-120">Pour plus d’informations, consultez [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) et [propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).</span><span class="sxs-lookup"><span data-stu-id="7c232-120">For more information, see [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) and [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).</span></span>  
  
 <span data-ttu-id="7c232-121">Si vous définissez un espace de noms XML global sans préfixe d’espace de noms (par exemple, `Imports <xmlns="http://SomeNameSpace>"`), cet espace de noms est considéré comme l’espace de noms XML par défaut.</span><span class="sxs-lookup"><span data-stu-id="7c232-121">If you define a global XML namespace without a namespace prefix (for example, `Imports <xmlns="http://SomeNameSpace>"`), that namespace is considered the default XML namespace.</span></span> <span data-ttu-id="7c232-122">L’espace de noms XML par défaut est utilisé pour les littéraux d’éléments XML ou les propriétés d’axe d’attribut XML qui ne spécifient pas explicitement un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7c232-122">The default XML namespace is used for any XML element literals or XML attribute axis properties that do not explicitly specify a namespace.</span></span> <span data-ttu-id="7c232-123">L’espace de noms par défaut est également utilisé si l’espace de noms spécifié est l’espace de noms vide (autrement dit, `xmlns=""`).</span><span class="sxs-lookup"><span data-stu-id="7c232-123">The default namespace is also used if the specified namespace is the empty namespace (that is, `xmlns=""`).</span></span> <span data-ttu-id="7c232-124">L’espace de noms XML par défaut ne s’applique pas aux attributs XML dans les littéraux XML ou aux propriétés d’axe d’attribut XML qui n’ont pas un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7c232-124">The default XML namespace does not apply to XML attributes in XML literals or to XML attribute axis properties that do not have a namespace.</span></span>  
  
 <span data-ttu-id="7c232-125">Espaces de noms XML définis dans un littéral XML, appelés *des espaces de noms XML local*, sont prioritaires sur les espaces de noms XML sont définies par la `Imports` instruction comme globale.</span><span class="sxs-lookup"><span data-stu-id="7c232-125">XML namespaces that are defined in an XML literal, which are called *local XML namespaces*, take precedence over XML namespaces that are defined by the `Imports` statement as global.</span></span> <span data-ttu-id="7c232-126">Espaces de noms XML sont définies par la `Imports` instruction sont prioritaires sur les espaces de noms XML importés pour un projet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7c232-126">XML namespaces that are defined by the `Imports` statement take precedence over XML namespaces imported for a Visual Basic project.</span></span> <span data-ttu-id="7c232-127">Si un littéral XML définit un espace de noms XML, cet espace de noms local ne s’applique pas aux expressions incorporées.</span><span class="sxs-lookup"><span data-stu-id="7c232-127">If an XML literal defines an XML namespace, that local namespace does not apply to embedded expressions.</span></span>  
  
 <span data-ttu-id="7c232-128">Espaces de noms XML globaux suivent les mêmes règles de portée et de définition que les espaces de noms .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c232-128">Global XML namespaces follow the same scoping and definition rules as .NET Framework namespaces.</span></span> <span data-ttu-id="7c232-129">Par conséquent, vous pouvez inclure un `Imports` instruction pour définir un espace de noms XML global partout où vous pouvez importer un espace de noms .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c232-129">As a result, you can include an `Imports` statement to define a global XML namespace anywhere you can import a .NET Framework namespace.</span></span> <span data-ttu-id="7c232-130">Cela inclut les fichiers de code et les espaces de noms importés au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="7c232-130">This includes both code files and project-level imported namespaces.</span></span> <span data-ttu-id="7c232-131">Pour plus d’informations sur les espaces de noms importés au niveau du projet, consultez [Page références, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7c232-131">For information about project-level imported namespaces, see [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="7c232-132">Chaque fichier source peut contenir un nombre quelconque de `Imports` instructions.</span><span class="sxs-lookup"><span data-stu-id="7c232-132">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="7c232-133">Ces derniers doivent respecter les déclarations d’option, telles que la `Option Strict` instruction et doivent précéder les déclarations d’élément de programmation, tel que `Module` ou `Class` instructions.</span><span class="sxs-lookup"><span data-stu-id="7c232-133">These must follow option declarations, such as the `Option Strict` statement, and they must precede programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c232-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="7c232-134">Example</span></span>  
 <span data-ttu-id="7c232-135">L’exemple suivant importe un espace de noms XML par défaut et un espace de noms XML identifié par le préfixe `ns`.</span><span class="sxs-lookup"><span data-stu-id="7c232-135">The following example imports a default XML namespace and an XML namespace identified with the prefix `ns`.</span></span> <span data-ttu-id="7c232-136">Il crée ensuite des littéraux XML qui utilisent les deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="7c232-136">It then creates XML literals that use both namespaces.</span></span>  
  
 <span data-ttu-id="7c232-137">[!code-vb[VbXMLSamples n °&45;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7c232-137">[!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]</span></span>  
  
 <span data-ttu-id="7c232-138">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="7c232-138">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a><span data-ttu-id="7c232-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="7c232-139">Example</span></span>  
 <span data-ttu-id="7c232-140">L’exemple suivant importe le préfixe d’espace de noms XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="7c232-140">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="7c232-141">Il crée ensuite un littéral XML qui utilise le préfixe d’espace de noms et affiche le formulaire final de l’élément.</span><span class="sxs-lookup"><span data-stu-id="7c232-141">It then creates an XML literal that uses the namespace prefix and displays the element's final form.</span></span>  
  
 <span data-ttu-id="7c232-142">[!code-vb[VbXMLSamples&#22;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7c232-142">[!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]</span></span>  
  
 <span data-ttu-id="7c232-143">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="7c232-143">This code displays the following text:</span></span>  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="7c232-144">Notez que le compilateur a converti le préfixe d’espace de noms XML à partir d’un préfixe global à une définition de préfixe local.</span><span class="sxs-lookup"><span data-stu-id="7c232-144">Notice that the compiler converted the XML namespace prefix from a global prefix to a local prefix definition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c232-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="7c232-145">Example</span></span>  
 <span data-ttu-id="7c232-146">L’exemple suivant importe le préfixe d’espace de noms XML `ns`.</span><span class="sxs-lookup"><span data-stu-id="7c232-146">The following example imports the XML namespace prefix `ns`.</span></span> <span data-ttu-id="7c232-147">Il utilise ensuite le préfixe de l'espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="7c232-147">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 <span data-ttu-id="7c232-148">[!code-vb[VbXMLSamples n °&19;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="7c232-148">[!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]</span></span>  
  
 <span data-ttu-id="7c232-149">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="7c232-149">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="7c232-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c232-150">See Also</span></span>  
 <span data-ttu-id="7c232-151">[Littéral d’élément XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="7c232-151">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="7c232-152"> [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="7c232-152"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="7c232-153"> [Nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="7c232-153"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md) </span></span>  
<span data-ttu-id="7c232-154"> [GetXmlNamespace (opérateur)](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)</span><span class="sxs-lookup"><span data-stu-id="7c232-154"> [GetXmlNamespace Operator](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)</span></span>
