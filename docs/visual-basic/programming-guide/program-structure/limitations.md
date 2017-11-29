---
title: "Restrictions liées à Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 97a2e162b9f1a673fbe805a5d2ef1421cd423a4f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-limitations"></a><span data-ttu-id="e1728-102">Restrictions liées à Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1728-102">Visual Basic Limitations</span></span>
<span data-ttu-id="e1728-103">Les versions antérieures de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] appliquée à des limites dans le code, comme la longueur des noms de variables, le nombre de variables autorisé dans les modules et la taille du module.</span><span class="sxs-lookup"><span data-stu-id="e1728-103">Earlier versions of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="e1728-104">Dans Visual Basic .NET, ces restrictions ont été allégées, ce qui vous donne une plus grande liberté d’écriture et d’organisation de votre code.</span><span class="sxs-lookup"><span data-stu-id="e1728-104">In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="e1728-105">Les limites physiques sont dépendants plus sur l’exécution de mémoire que sur les considérations relatives à la compilation.</span><span class="sxs-lookup"><span data-stu-id="e1728-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="e1728-106">Si vous utilisez des pratiques de programmation prudentes et divisez de grandes applications en plusieurs classes et les modules, il est peu de risque de rencontrer une interne [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] limitation.</span><span class="sxs-lookup"><span data-stu-id="e1728-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] limitation.</span></span>  
  
 <span data-ttu-id="e1728-107">Voici quelques limitations que vous pouvez rencontrer dans les cas extrêmes :</span><span class="sxs-lookup"><span data-stu-id="e1728-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
-   <span data-ttu-id="e1728-108">**Longueur du nom.**</span><span class="sxs-lookup"><span data-stu-id="e1728-108">**Name Length.**</span></span> <span data-ttu-id="e1728-109">Il existe un nombre maximal de caractères pour le nom de chaque élément de programmation déclaré.</span><span class="sxs-lookup"><span data-stu-id="e1728-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="e1728-110">Cette valeur maximale s’applique à une chaîne de qualification entière si le nom de l’élément est qualifié.</span><span class="sxs-lookup"><span data-stu-id="e1728-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="e1728-111">Consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="e1728-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   <span data-ttu-id="e1728-112">**Longueur de ligne.**</span><span class="sxs-lookup"><span data-stu-id="e1728-112">**Line Length.**</span></span> <span data-ttu-id="e1728-113">Il existe un maximum de 65 535 caractères dans une ligne physique de code source.</span><span class="sxs-lookup"><span data-stu-id="e1728-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="e1728-114">La ligne de code source logique peut être plus longue si vous utilisez des caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="e1728-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="e1728-115">Consultez [Comment : diviser et combiner des instructions dans le Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="e1728-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
-   <span data-ttu-id="e1728-116">**Dimensions du tableau.**</span><span class="sxs-lookup"><span data-stu-id="e1728-116">**Array Dimensions.**</span></span> <span data-ttu-id="e1728-117">Il existe un nombre maximal de dimensions, que vous pouvez déclarer un tableau.</span><span class="sxs-lookup"><span data-stu-id="e1728-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="e1728-118">Cela limite le nombre d’index que vous pouvez utiliser pour spécifier un élément de tableau.</span><span class="sxs-lookup"><span data-stu-id="e1728-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="e1728-119">Consultez [en Visual Basic, les Dimensions de tableau](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="e1728-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
-   <span data-ttu-id="e1728-120">**Longueur de chaîne.**</span><span class="sxs-lookup"><span data-stu-id="e1728-120">**String Length.**</span></span> <span data-ttu-id="e1728-121">Il existe un nombre maximal de caractères Unicode que vous pouvez stocker dans une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="e1728-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="e1728-122">Consultez [Type de données chaîne](../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e1728-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
-   <span data-ttu-id="e1728-123">**Longueur de chaîne d’environnement.**</span><span class="sxs-lookup"><span data-stu-id="e1728-123">**Environment String Length.**</span></span> <span data-ttu-id="e1728-124">Il existe un maximum de 32768 caractères pour toute chaîne d’environnement utilisée comme argument de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e1728-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="e1728-125">Il s’agit d’une limitation sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="e1728-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1728-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1728-126">See Also</span></span>  
 [<span data-ttu-id="e1728-127">Structure de programme et conventions de codage</span><span class="sxs-lookup"><span data-stu-id="e1728-127">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="e1728-128">Conventions d’affectation de noms de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1728-128">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
