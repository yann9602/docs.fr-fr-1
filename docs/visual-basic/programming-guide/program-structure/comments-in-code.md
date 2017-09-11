---
title: Commentaires dans le Code (Visual Basic) | Documents Microsoft
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
- Uncomment button
- REM statement
- comments, in code
- comments, Visual Basic code
- Comment button
- buttons, Uncomment
- buttons, Comment
- code comments, Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: 17
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
ms.openlocfilehash: e872c9bb67835573aadcc1016f2c6a98d434201e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="afb55-102">Commentaires dans le code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afb55-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="afb55-103">Lorsque vous lisez les exemples de code, vous rencontrez souvent le symbole de commentaire (`'`).</span><span class="sxs-lookup"><span data-stu-id="afb55-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="afb55-104">Ce symbole indique le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur d’ignorer le texte suivant, ou le *commentaire*.</span><span class="sxs-lookup"><span data-stu-id="afb55-104">This symbol tells the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="afb55-105">Les commentaires sont de courtes explications destinées à éclairer ceux qui lisent le code.</span><span class="sxs-lookup"><span data-stu-id="afb55-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="afb55-106">En programmation, il est hautement recommandé de faire précéder toutes les procédures d'un commentaire court qui décrit les caractéristiques fonctionnelles de la procédure (ce qu'elle fait).</span><span class="sxs-lookup"><span data-stu-id="afb55-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="afb55-107">Ceci est utile tant pour l'auteur du code lui-même que pour toute autre personne amenée à consulter le code.</span><span class="sxs-lookup"><span data-stu-id="afb55-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="afb55-108">Vous devez séparer les détails relatifs à l'implémentation (comment la procédure fait ce qu'elle doit faire) des commentaires décrivant les caractéristiques fonctionnelles.</span><span class="sxs-lookup"><span data-stu-id="afb55-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="afb55-109">Si vous fournissez des informations d'implémentation dans la description, n'oubliez pas de les mettre à jour lors de la mise à jour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="afb55-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="afb55-110">Les commentaires peuvent soit suivre une instruction sur la même ligne, soit occuper une ligne entière.</span><span class="sxs-lookup"><span data-stu-id="afb55-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="afb55-111">Ces deux cas sont illustrés par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="afb55-111">Both are illustrated in the following code.</span></span>  
  
 <span data-ttu-id="afb55-112">[!code-vb[VbVbcnConventions&#16;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="afb55-112">[!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]</span></span>  
  
 <span data-ttu-id="afb55-113">Si votre commentaire doit occuper plusieurs lignes, utilisez le symbole de commentaire sur chacune d'elles, comme l'exemple ci-dessous l'illustre.</span><span class="sxs-lookup"><span data-stu-id="afb55-113">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 <span data-ttu-id="afb55-114">[!code-vb[VbVbcnConventions&#17;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="afb55-114">[!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]</span></span>  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="afb55-115">Recommandations sur le commentaire</span><span class="sxs-lookup"><span data-stu-id="afb55-115">Commenting Guidelines</span></span>  
 <span data-ttu-id="afb55-116">Le tableau suivant fournit des recommandations générales sur les types de commentaires qui peuvent précéder une section de code.</span><span class="sxs-lookup"><span data-stu-id="afb55-116">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="afb55-117">Il ne s'agit que de suggestions ; [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] n'impose aucune règle concernant l'ajout de commentaires.</span><span class="sxs-lookup"><span data-stu-id="afb55-117">These are suggestions; [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] does not enforce rules for adding comments.</span></span> <span data-ttu-id="afb55-118">Procédez de la façon que vous jugez la plus efficace pour vous et toute personne amenée à lire votre code.</span><span class="sxs-lookup"><span data-stu-id="afb55-118">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="afb55-119">Type de commentaire</span><span class="sxs-lookup"><span data-stu-id="afb55-119">Comment type</span></span>|<span data-ttu-id="afb55-120">Description du commentaire</span><span class="sxs-lookup"><span data-stu-id="afb55-120">Comment description</span></span>|  
|<span data-ttu-id="afb55-121">Objectif</span><span class="sxs-lookup"><span data-stu-id="afb55-121">Purpose</span></span>|<span data-ttu-id="afb55-122">Décrit ce que fait la procédure (et non comment elle le fait)</span><span class="sxs-lookup"><span data-stu-id="afb55-122">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="afb55-123">Assumptions (Hypothèses)</span><span class="sxs-lookup"><span data-stu-id="afb55-123">Assumptions</span></span>|<span data-ttu-id="afb55-124">Répertorie chaque variable externe, contrôle, fichier ouvert ou autre élément auquel la procédure accède.</span><span class="sxs-lookup"><span data-stu-id="afb55-124">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="afb55-125">Effects (Effets)</span><span class="sxs-lookup"><span data-stu-id="afb55-125">Effects</span></span>|<span data-ttu-id="afb55-126">Répertorie chaque variable externe, contrôle ou fichier affecté, ainsi que ses effets (uniquement si ce n'est pas évident)</span><span class="sxs-lookup"><span data-stu-id="afb55-126">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="afb55-127">Inputs (Entrées)</span><span class="sxs-lookup"><span data-stu-id="afb55-127">Inputs</span></span>|<span data-ttu-id="afb55-128">Spécifie l'objectif attaché à l'argument</span><span class="sxs-lookup"><span data-stu-id="afb55-128">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="afb55-129">Returns (Retours)</span><span class="sxs-lookup"><span data-stu-id="afb55-129">Returns</span></span>|<span data-ttu-id="afb55-130">Explique les valeurs retournées par la procédure.</span><span class="sxs-lookup"><span data-stu-id="afb55-130">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="afb55-131">N'oubliez pas :</span><span class="sxs-lookup"><span data-stu-id="afb55-131">Remember the following points:</span></span>  
  
-   <span data-ttu-id="afb55-132">Pour chaque déclaration de variable importante, faites précéder d'un commentaire décrivant son utilisation.</span><span class="sxs-lookup"><span data-stu-id="afb55-132">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
-   <span data-ttu-id="afb55-133">Les noms des variables, contrôles et procédures doivent être suffisamment clairs pour que les commentaires servent uniquement à fournir des détails d'implémentation complexes.</span><span class="sxs-lookup"><span data-stu-id="afb55-133">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
-   <span data-ttu-id="afb55-134">Vous ne pouvez pas faire suivre une séquence de continuation par un commentaire sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="afb55-134">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="afb55-135">Vous pouvez ajouter ou supprimer les symboles de commentaires pour un bloc de code en sélectionnant une ou plusieurs lignes de code et en choisissant le **commentaire** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) et **Décommentez** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) des boutons de la **modifier** barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="afb55-135">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) and **Uncomment** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afb55-136">Vous pouvez également ajouter des commentaires à votre code en faisant précéder le texte du mot clé `REM`.</span><span class="sxs-lookup"><span data-stu-id="afb55-136">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="afb55-137">Toutefois, le `'` symbole et la **commentaire**/**Décommentez** boutons sont plus faciles à utiliser et sont moins espace et en mémoire.</span><span class="sxs-lookup"><span data-stu-id="afb55-137">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb55-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afb55-138">See Also</span></span>  
 <span data-ttu-id="afb55-139">[Documentation de votre Code avec des commentaires XML](http://msdn.microsoft.com/magazine/dd722812.aspx) </span><span class="sxs-lookup"><span data-stu-id="afb55-139">[Documenting Your Code With XML Comments](http://msdn.microsoft.com/magazine/dd722812.aspx) </span></span>  
<span data-ttu-id="afb55-140"> [Comment : créer une Documentation XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="afb55-140"> [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md) </span></span>  
<span data-ttu-id="afb55-141"> [Balises de commentaire XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span><span class="sxs-lookup"><span data-stu-id="afb55-141"> [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span></span>  
<span data-ttu-id="afb55-142"> [Structure de programme et Conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="afb55-142"> [Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="afb55-143"> [REM (instruction)](../../../visual-basic/language-reference/statements/rem-statement.md)</span><span class="sxs-lookup"><span data-stu-id="afb55-143"> [REM Statement](../../../visual-basic/language-reference/statements/rem-statement.md)</span></span>
