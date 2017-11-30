---
title: Liste d'attributs (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: adfb980380bb787280715ca0185950657e174eb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="afa06-102">Liste d'attributs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa06-102">Attribute List (Visual Basic)</span></span>
<span data-ttu-id="afa06-103">Spécifie les attributs à appliquer à un élément de programmation déclaré.</span><span class="sxs-lookup"><span data-stu-id="afa06-103">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="afa06-104">Les attributs multiples sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="afa06-104">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="afa06-105">Voici la syntaxe pour un attribut.</span><span class="sxs-lookup"><span data-stu-id="afa06-105">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afa06-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afa06-106">Syntax</span></span>  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="afa06-107">Composants</span><span class="sxs-lookup"><span data-stu-id="afa06-107">Parts</span></span>  
 `attributemodifier`  
 <span data-ttu-id="afa06-108">Requis pour les attributs appliqués au début d’un fichier source.</span><span class="sxs-lookup"><span data-stu-id="afa06-108">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="afa06-109">Peut être [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) ou [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="afa06-109">Can be [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) or [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md).</span></span>  
  
 `attributename`  
 <span data-ttu-id="afa06-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="afa06-110">Required.</span></span> <span data-ttu-id="afa06-111">Nom de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="afa06-111">Name of the attribute.</span></span>  
  
 `attributearguments`  
 <span data-ttu-id="afa06-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="afa06-112">Optional.</span></span> <span data-ttu-id="afa06-113">Liste des arguments de position pour cet attribut.</span><span class="sxs-lookup"><span data-stu-id="afa06-113">List of positional arguments for this attribute.</span></span> <span data-ttu-id="afa06-114">Plusieurs arguments sont séparés par des virgules.</span><span class="sxs-lookup"><span data-stu-id="afa06-114">Multiple arguments are separated by commas.</span></span>  
  
 `attributeinitializer`  
 <span data-ttu-id="afa06-115">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="afa06-115">Optional.</span></span> <span data-ttu-id="afa06-116">Liste d’initialiseurs de variable ou une propriété pour cet attribut.</span><span class="sxs-lookup"><span data-stu-id="afa06-116">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="afa06-117">Les initialiseurs multiples sont séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="afa06-117">Multiple initializers are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afa06-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="afa06-118">Remarks</span></span>  
 <span data-ttu-id="afa06-119">Vous pouvez appliquer un ou plusieurs attributs à quasiment n’importe quel élément de programmation (types, procédures, propriétés et ainsi de suite).</span><span class="sxs-lookup"><span data-stu-id="afa06-119">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="afa06-120">Les attributs apparaissent dans les métadonnées de votre assembly, et ils peuvent vous aider à annoter votre code ou de spécifier l’utilisation d’un élément de programmation particulier.</span><span class="sxs-lookup"><span data-stu-id="afa06-120">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="afa06-121">Vous pouvez appliquer des attributs définis par Visual Basic et .NET Framework, et vous pouvez définir vos propres attributs.</span><span class="sxs-lookup"><span data-stu-id="afa06-121">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="afa06-122">Pour plus d’informations sur l’utilisation d’attributs, consultez [vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="afa06-122">For more information on when to use attributes, see [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="afa06-123">Pour plus d’informations sur les noms d’attributs, consultez [noms d’élément déclaré](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="afa06-123">For information on attribute names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="afa06-124">Règles</span><span class="sxs-lookup"><span data-stu-id="afa06-124">Rules</span></span>  
  
-   <span data-ttu-id="afa06-125">**Sélection élective.**</span><span class="sxs-lookup"><span data-stu-id="afa06-125">**Placement.**</span></span> <span data-ttu-id="afa06-126">Vous pouvez appliquer des attributs aux éléments de programmation déclarés plus.</span><span class="sxs-lookup"><span data-stu-id="afa06-126">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="afa06-127">Pour appliquer un ou plusieurs attributs, placez un *bloc d’attributs* au début de la déclaration d’élément.</span><span class="sxs-lookup"><span data-stu-id="afa06-127">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="afa06-128">Chaque entrée dans la liste d’attributs Spécifie un attribut que vous souhaitez appliquer, et le modificateur et les arguments que vous utilisez pour cet appel de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="afa06-128">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
-   <span data-ttu-id="afa06-129">**Crochets pointus.**</span><span class="sxs-lookup"><span data-stu-id="afa06-129">**Angle Brackets.**</span></span> <span data-ttu-id="afa06-130">Si vous fournissez une liste d’attributs, vous devez le placer entre crochets pointus («`<`« et »`>`»).</span><span class="sxs-lookup"><span data-stu-id="afa06-130">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
-   <span data-ttu-id="afa06-131">**Partie de la déclaration.**</span><span class="sxs-lookup"><span data-stu-id="afa06-131">**Part of the Declaration.**</span></span> <span data-ttu-id="afa06-132">L’attribut doit faire partie de la déclaration d’élément, pas une instruction séparée.</span><span class="sxs-lookup"><span data-stu-id="afa06-132">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="afa06-133">Vous pouvez utiliser la séquence de continuation de ligne (« `_`») pour étendre l’instruction de déclaration sur plusieurs lignes de code source.</span><span class="sxs-lookup"><span data-stu-id="afa06-133">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
-   <span data-ttu-id="afa06-134">**Modificateurs.**</span><span class="sxs-lookup"><span data-stu-id="afa06-134">**Modifiers.**</span></span> <span data-ttu-id="afa06-135">Un modificateur d’attribut (`Assembly` ou `Module`) est requis sur chaque attribut appliqué à un élément de programmation au début d’un fichier source.</span><span class="sxs-lookup"><span data-stu-id="afa06-135">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="afa06-136">Les modificateurs d’attribut ne sont pas autorisés sur les attributs appliqués à des éléments qui ne sont pas au début d’un fichier source.</span><span class="sxs-lookup"><span data-stu-id="afa06-136">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
-   <span data-ttu-id="afa06-137">**Arguments.**</span><span class="sxs-lookup"><span data-stu-id="afa06-137">**Arguments.**</span></span> <span data-ttu-id="afa06-138">Tous les arguments de position d’un attribut doivent précéder les initialiseurs de variable ou propriété.</span><span class="sxs-lookup"><span data-stu-id="afa06-138">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afa06-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="afa06-139">Example</span></span>  
 <span data-ttu-id="afa06-140">L’exemple suivant applique la <xref:System.Runtime.InteropServices.DllImportAttribute> d’attribut à une définition squelette d’une `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="afa06-140">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <span data-ttu-id="afa06-141"><xref:System.Runtime.InteropServices.DllImportAttribute>Indique que la procédure attribuée représente un point d’entrée dans une bibliothèque de liens dynamiques (DLL) non managée.</span><span class="sxs-lookup"><span data-stu-id="afa06-141"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="afa06-142">L’attribut fournit le nom de la DLL comme argument positionnel et l’autre information comme initialiseurs de variable.</span><span class="sxs-lookup"><span data-stu-id="afa06-142">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa06-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afa06-143">See Also</span></span>  
 [<span data-ttu-id="afa06-144">Assembly</span><span class="sxs-lookup"><span data-stu-id="afa06-144">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [<span data-ttu-id="afa06-145">\<mot clé> du module</span><span class="sxs-lookup"><span data-stu-id="afa06-145">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="afa06-146">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="afa06-146">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="afa06-147">Guide pratique : diviser et combiner des instructions dans le code</span><span class="sxs-lookup"><span data-stu-id="afa06-147">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
