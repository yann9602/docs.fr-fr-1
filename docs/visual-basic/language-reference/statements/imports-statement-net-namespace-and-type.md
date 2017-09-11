---
title: Imports, instruction (.NET Namespace et Type) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Imports
- imports
dev_langs:
- VB
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
caps.latest.revision: 40
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
ms.openlocfilehash: af177874c3278efd348b53a2b74b4d49d6628c61
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="bcdb6-102">Imports, instruction (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="bcdb6-102">Imports Statement (.NET Namespace and Type)</span></span>
<span data-ttu-id="bcdb6-103">Permet d’attribuer des noms d’être référencés sans qualification d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-103">Enables type names to be referenced without namespace qualification.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcdb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcdb6-104">Syntax</span></span>  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## <a name="parts"></a><span data-ttu-id="bcdb6-105">Composants</span><span class="sxs-lookup"><span data-stu-id="bcdb6-105">Parts</span></span>  
  
|<span data-ttu-id="bcdb6-106">Terme</span><span class="sxs-lookup"><span data-stu-id="bcdb6-106">Term</span></span>|<span data-ttu-id="bcdb6-107">Définition</span><span class="sxs-lookup"><span data-stu-id="bcdb6-107">Definition</span></span>|  
|---|---|  
|`aliasname`|<span data-ttu-id="bcdb6-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-108">Optional.</span></span> <span data-ttu-id="bcdb6-109">Un *alias d’importation* ou le nom par lequel le code peut faire référence à `namespace` au lieu de la chaîne de qualification complète.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-109">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="bcdb6-110">Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="bcdb6-110">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`namespace`|<span data-ttu-id="bcdb6-111">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-111">Required.</span></span> <span data-ttu-id="bcdb6-112">Le nom qualifié complet de l’espace de noms importé.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-112">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="bcdb6-113">Une chaîne d’espaces de noms imbriquée à n’importe quel niveau.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-113">Can be a string of namespaces nested to any level.</span></span>|  
|`element`|<span data-ttu-id="bcdb6-114">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-114">Optional.</span></span> <span data-ttu-id="bcdb6-115">Le nom d’un élément de programmation déclaré dans l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-115">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="bcdb6-116">Peut être n’importe quel élément conteneur.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-116">Can be any container element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcdb6-117">Notes</span><span class="sxs-lookup"><span data-stu-id="bcdb6-117">Remarks</span></span>  
 <span data-ttu-id="bcdb6-118">La `Imports` instruction permet aux types qui sont contenus dans un espace de noms donné soient référencés directement.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-118">The `Imports`  statement enables types that are contained in a given namespace to be referenced directly.</span></span>  
  
 <span data-ttu-id="bcdb6-119">Vous pouvez fournir un nom d’espace de noms unique ou une chaîne d’espaces de noms imbriqués.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-119">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="bcdb6-120">Chaque espace de noms imbriqué est séparé de l’espace de noms au niveau supérieur suivant par un point (`.`), comme l’illustre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-120">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates.</span></span>  
  
 `Imports System.Collections.Generic`  
  
 <span data-ttu-id="bcdb6-121">Chaque fichier source peut contenir un nombre quelconque de `Imports` instructions.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-121">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="bcdb6-122">Ces derniers doivent respecter les déclarations d’option, telles que la `Option Strict` instruction et elles doivent précéder les déclarations d’élément de programmation, telles que `Module` ou `Class` instructions.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-122">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>  
  
 <span data-ttu-id="bcdb6-123">Vous pouvez utiliser `Imports` uniquement au niveau fichier.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-123">You can use `Imports` only at file level.</span></span> <span data-ttu-id="bcdb6-124">Cela signifie que le contexte de déclaration pour l’importation doit être un fichier source et ne peut pas être un espace de noms, classe, structure, module, interface, procédure ou bloc.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-124">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>  
  
 <span data-ttu-id="bcdb6-125">Notez que la `Imports` instruction ne rend pas les éléments d’autres projets et assemblys disponibles à votre projet.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-125">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="bcdb6-126">L’importation ne prend pas la place de la définition d’une référence.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-126">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="bcdb6-127">Il supprime uniquement la nécessité pour qualifier des noms qui sont déjà disponibles pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-127">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="bcdb6-128">Pour plus d’informations, consultez « Importation d’éléments conteneurs » dans [références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="bcdb6-128">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bcdb6-129">Vous pouvez définir implicite `Imports` les instructions à l’aide de la [Page références, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="bcdb6-129">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="bcdb6-130">Pour plus d’informations, consultez [Comment : ajouter ou supprimer des espaces de noms importés (Visual Basic)](http://msdn.microsoft.com/library/44cebec3-0ea0-47c2-8406-4edeab6a997e).</span><span class="sxs-lookup"><span data-stu-id="bcdb6-130">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](http://msdn.microsoft.com/library/44cebec3-0ea0-47c2-8406-4edeab6a997e).</span></span>  
  
## <a name="import-aliases"></a><span data-ttu-id="bcdb6-131">Alias d’importation</span><span class="sxs-lookup"><span data-stu-id="bcdb6-131">Import Aliases</span></span>  
 <span data-ttu-id="bcdb6-132">Un *alias d’importation* définit l’alias d’espace de noms ou type.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-132">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="bcdb6-133">Alias d’importation sont utiles lorsque vous devez utiliser des éléments portant le même nom sont déclarées dans un ou plusieurs espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-133">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="bcdb6-134">Pour plus d’informations et un exemple, consultez « Qualification d’un nom d’élément » dans [références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="bcdb6-134">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="bcdb6-135">Vous ne devez pas déclarer un membre au niveau du module avec le même nom que `aliasname`.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-135">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="bcdb6-136">Si vous le faites, le compilateur Visual Basic utilise `aliasname` uniquement pour le membre déclaré et ne plus l’identifie comme un alias d’importation.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-136">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>  
  
 <span data-ttu-id="bcdb6-137">Bien que la syntaxe utilisée pour déclarer un alias d’importation est celui utilisée pour importer un préfixe d’espace de noms XML, les résultats sont différents.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-137">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="bcdb6-138">Un alias d’importation peut être utilisé comme expression dans votre code, alors qu’un préfixe d’espace de noms XML peut être utilisé uniquement dans les littéraux XML ou de propriétés d’axe XML comme préfixe pour un élément qualifié ou un nom d’attribut.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-138">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>  
  
### <a name="element-names"></a><span data-ttu-id="bcdb6-139">Noms des éléments</span><span class="sxs-lookup"><span data-stu-id="bcdb6-139">Element Names</span></span>  
 <span data-ttu-id="bcdb6-140">Si vous fournissez `element`, il doit représenter un *élément conteneur*, autrement dit, un élément de programmation qui peut contenir d’autres éléments.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-140">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="bcdb6-141">Éléments conteneurs comprennent des classes, structures, modules, interfaces et énumérations.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-141">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>  
  
 <span data-ttu-id="bcdb6-142">La portée des éléments mis à disposition par une `Imports` instruction varie selon que vous spécifiez `element`.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-142">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="bcdb6-143">Si vous spécifiez uniquement `namespace`, tout unique nommé membres de cet espace de noms et les membres des éléments conteneurs présents dans cet espace de noms, sont disponibles sans qualification.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-143">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="bcdb6-144">Si vous spécifiez les deux `namespace` et `element`, seuls les membres de cet élément sont disponibles sans qualification.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-144">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcdb6-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcdb6-145">Example</span></span>  
 <span data-ttu-id="bcdb6-146">L’exemple suivant retourne tous les dossiers dans le répertoire C:\ à l’aide de la <xref:System.IO.DirectoryInfo>classe.</xref:System.IO.DirectoryInfo></span><span class="sxs-lookup"><span data-stu-id="bcdb6-146">The following example returns all the folders in the C:\ directory by using the <xref:System.IO.DirectoryInfo> class.</span></span>  
  
 <span data-ttu-id="bcdb6-147">Le code n’a pas `Imports` au début du fichier.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-147">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="bcdb6-148">Par conséquent, le `DirectoryInfo`, <xref:System.Text.StringBuilder>, et <xref:Microsoft.VisualBasic.ControlChars.CrLf>les références sont entièrement qualifiées avec les espaces de noms.</xref:Microsoft.VisualBasic.ControlChars.CrLf> </xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="bcdb6-148">Therefore, the `DirectoryInfo`, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>  
  
 <span data-ttu-id="bcdb6-149">[!code-vb[VbVbalrStatements&#152;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bcdb6-149">[!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcdb6-150">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcdb6-150">Example</span></span>  
 <span data-ttu-id="bcdb6-151">L’exemple suivant inclut `Imports` instructions pour les espaces de noms référencés.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-151">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="bcdb6-152">Par conséquent, les types n’ont pas à être entièrement qualifiés avec les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-152">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>  
  
 <span data-ttu-id="bcdb6-153">[!code-vb[VbVbalrStatements&#153;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="bcdb6-153">[!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]</span></span>  
  
 <span data-ttu-id="bcdb6-154">[!code-vb[VbVbalrStatements&#154;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="bcdb6-154">[!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcdb6-155">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcdb6-155">Example</span></span>  
 <span data-ttu-id="bcdb6-156">L’exemple suivant inclut `Imports` instructions qui créent des alias pour les espaces de noms référencés.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-156">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="bcdb6-157">Les types sont qualifiés avec les alias.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-157">The types are qualified with the aliases.</span></span>  
  
 <span data-ttu-id="bcdb6-158">[!code-vb[VbVbalrStatements&#155;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="bcdb6-158">[!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]</span></span>  
  
 <span data-ttu-id="bcdb6-159">[!code-vb[VbVbalrStatements&#156;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="bcdb6-159">[!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcdb6-160">Exemple</span><span class="sxs-lookup"><span data-stu-id="bcdb6-160">Example</span></span>  
 <span data-ttu-id="bcdb6-161">L’exemple suivant inclut `Imports` instructions qui créent des alias pour les types référencés.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-161">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="bcdb6-162">Alias sont utilisés pour spécifier les types.</span><span class="sxs-lookup"><span data-stu-id="bcdb6-162">Aliases are used to specify the types.</span></span>  
  
 <span data-ttu-id="bcdb6-163">[!code-vb[VbVbalrStatements&#157;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="bcdb6-163">[!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]</span></span>  
  
 <span data-ttu-id="bcdb6-164">[!code-vb[VbVbalrStatements&#158;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="bcdb6-164">[!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcdb6-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcdb6-165">See Also</span></span>  
 <span data-ttu-id="bcdb6-166">[Déclaration de Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md) </span><span class="sxs-lookup"><span data-stu-id="bcdb6-166">[Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) </span></span>  
<span data-ttu-id="bcdb6-167"> [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="bcdb6-167"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="bcdb6-168"> [Références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="bcdb6-168"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="bcdb6-169"> [Imports, instruction (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="bcdb6-169"> [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="bcdb6-170"> [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="bcdb6-170"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
