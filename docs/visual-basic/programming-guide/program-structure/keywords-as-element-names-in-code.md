---
title: "Utilisation des mots clés comme noms d'éléments dans le code (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f410a0eaac0dcc034d406a89ed1d01a8f228a583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="ce448-102">Utilisation des mots clés comme noms d'éléments dans le code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce448-102">Keywords as Element Names in Code (Visual Basic)</span></span>
<span data-ttu-id="ce448-103">N’importe quel élément de programme, par exemple une variable, une classe ou un membre — peut avoir le même nom qu’un mot clé restreint.</span><span class="sxs-lookup"><span data-stu-id="ce448-103">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="ce448-104">Par exemple, vous pouvez créer une variable nommée `Loop`.</span><span class="sxs-lookup"><span data-stu-id="ce448-104">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="ce448-105">Toutefois, pour faire référence à votre version de celui-ci, qui a le même nom que la limitée `Loop` (mot clé), vous devez le faire précéder d’une chaîne de qualification complète ou le placer entre crochets (`[ ]`), comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ce448-105">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 <span data-ttu-id="ce448-106">Si vous ne procédez pas à une de ces, Visual Basic suppose l’utilisation de la fonction intrinsèque `Loop` (mot clé) et génère une erreur, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ce448-106">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="ce448-107">Vous pouvez utiliser des crochets lorsque vous faites référence aux formulaires et contrôles et lors de la déclaration d’une variable ou la définition d’une procédure portant le même nom qu’un mot clé restreint.</span><span class="sxs-lookup"><span data-stu-id="ce448-107">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="ce448-108">Il est facile d’oublier de qualifier des noms ou à inclure des crochets et ainsi d’introduire des erreurs dans votre code et rendre plus difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="ce448-108">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="ce448-109">Pour cette raison, nous vous conseillons pas mots clés restreints comme noms d’éléments de programme.</span><span class="sxs-lookup"><span data-stu-id="ce448-109">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="ce448-110">Toutefois, si une version ultérieure de Visual Basic définit un nouveau mot clé qui entre en conflit avec un nom de contrôle ou un formulaire existant, puis vous pouvez utiliser cette technique lorsque votre code de mise à jour pour fonctionner avec la nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="ce448-110">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ce448-111">Votre programme peut également contenir des noms d’éléments fournis par d’autres assemblys référencés.</span><span class="sxs-lookup"><span data-stu-id="ce448-111">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="ce448-112">Si ces noms en conflit avec les mots clés restreints, puis placer les crochets autour d’elles permet à Visual Basic pour les interpréter comme vos éléments définis.</span><span class="sxs-lookup"><span data-stu-id="ce448-112">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce448-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce448-113">See Also</span></span>  
 [<span data-ttu-id="ce448-114">Conventions d’affectation de noms de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce448-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="ce448-115">Structure de programme et conventions de codage</span><span class="sxs-lookup"><span data-stu-id="ce448-115">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="ce448-116">Mots clés</span><span class="sxs-lookup"><span data-stu-id="ce448-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
