---
title: "Restrictions liées à Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- limits
- limitations, Visual Basic
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: 14
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
ms.openlocfilehash: a3bd551ade2f0c55cd943cfbd353b09dfede4063
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="visual-basic-limitations"></a><span data-ttu-id="c0515-102">Restrictions liées à Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c0515-102">Visual Basic Limitations</span></span>
<span data-ttu-id="c0515-103">Les versions antérieures de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] appliquée limites dans le code, telles que la longueur des noms de variables, le nombre de variables autorisé dans les modules et la taille du module.</span><span class="sxs-lookup"><span data-stu-id="c0515-103">Earlier versions of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size.</span></span> <span data-ttu-id="c0515-104">Dans [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)], ces restrictions ont été allégées, ce qui vous donne une plus grande liberté d’écriture et d’organisation de votre code.</span><span class="sxs-lookup"><span data-stu-id="c0515-104">In [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)], these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.</span></span>  
  
 <span data-ttu-id="c0515-105">Les limites physiques dépendent les plus sur l’exécution de mémoire que sur les considérations relatives à la compilation.</span><span class="sxs-lookup"><span data-stu-id="c0515-105">Physical limits are dependent more on run-time memory than on compile-time considerations.</span></span> <span data-ttu-id="c0515-106">Si vous utilisez des pratiques de programmation prudentes et divisez de grandes applications en plusieurs classes et modules, il existe très peu de risque de rencontrer interne [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] limitation.</span><span class="sxs-lookup"><span data-stu-id="c0515-106">If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] limitation.</span></span>  
  
 <span data-ttu-id="c0515-107">Voici quelques limitations que vous pouvez rencontrer dans les cas extrêmes :</span><span class="sxs-lookup"><span data-stu-id="c0515-107">The following are some limitations that you might encounter in extreme cases:</span></span>  
  
-   <span data-ttu-id="c0515-108">**Longueur du nom.**</span><span class="sxs-lookup"><span data-stu-id="c0515-108">**Name Length.**</span></span> <span data-ttu-id="c0515-109">Il est un nombre maximal de caractères pour le nom de chaque élément de programmation déclaré.</span><span class="sxs-lookup"><span data-stu-id="c0515-109">There is a maximum number of characters for the name of every declared programming element.</span></span> <span data-ttu-id="c0515-110">Cette limite s’applique à une chaîne de qualification entière si le nom de l’élément est qualifié.</span><span class="sxs-lookup"><span data-stu-id="c0515-110">This maximum applies to an entire qualification string if the element name is qualified.</span></span> <span data-ttu-id="c0515-111">Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="c0515-111">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   <span data-ttu-id="c0515-112">**Longueur de ligne.**</span><span class="sxs-lookup"><span data-stu-id="c0515-112">**Line Length.**</span></span> <span data-ttu-id="c0515-113">Il existe un maximum de 65 535 caractères dans une ligne physique de code source.</span><span class="sxs-lookup"><span data-stu-id="c0515-113">There is a maximum of 65535 characters in a physical line of source code.</span></span> <span data-ttu-id="c0515-114">La ligne de code source logique peut être plus longue si vous utilisez des caractères de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="c0515-114">The logical source code line can be longer if you use line continuation characters.</span></span> <span data-ttu-id="c0515-115">Consultez la page [Comment : diviser et combiner des instructions dans le Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="c0515-115">See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
-   <span data-ttu-id="c0515-116">**Dimensions du tableau.**</span><span class="sxs-lookup"><span data-stu-id="c0515-116">**Array Dimensions.**</span></span> <span data-ttu-id="c0515-117">Il existe un nombre maximal de dimensions, que vous pouvez déclarer un tableau.</span><span class="sxs-lookup"><span data-stu-id="c0515-117">There is a maximum number of dimensions you can declare for an array.</span></span> <span data-ttu-id="c0515-118">Cela limite le nombre d’index vous permet de spécifier un élément de tableau.</span><span class="sxs-lookup"><span data-stu-id="c0515-118">This limits how many indexes you can use to specify an array element.</span></span> <span data-ttu-id="c0515-119">Consultez la page [en Visual Basic, les Dimensions de tableau](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span><span class="sxs-lookup"><span data-stu-id="c0515-119">See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).</span></span>  
  
-   <span data-ttu-id="c0515-120">**Longueur de chaîne.**</span><span class="sxs-lookup"><span data-stu-id="c0515-120">**String Length.**</span></span> <span data-ttu-id="c0515-121">Il existe un nombre maximal de caractères Unicode que vous pouvez stocker dans une chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="c0515-121">There is a maximum number of Unicode characters you can store in a single string.</span></span> <span data-ttu-id="c0515-122">Consultez la page [Type de données chaîne](../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="c0515-122">See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
-   <span data-ttu-id="c0515-123">**Longueur de chaîne d’environnement.**</span><span class="sxs-lookup"><span data-stu-id="c0515-123">**Environment String Length.**</span></span> <span data-ttu-id="c0515-124">Il existe un maximum de 32768 caractères de n’importe quel environnement la chaîne utilisée comme argument de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c0515-124">There is a maximum of 32768 characters for any environment string used as a command-line argument.</span></span> <span data-ttu-id="c0515-125">Il s’agit d’une limitation sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="c0515-125">This is a limitation on all platforms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0515-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0515-126">See Also</span></span>  
 <span data-ttu-id="c0515-127">[Structure de programme et Conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="c0515-127">[Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="c0515-128"> [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)</span><span class="sxs-lookup"><span data-stu-id="c0515-128"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)</span></span>
