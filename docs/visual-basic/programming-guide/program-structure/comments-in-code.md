---
title: Commentaires dans le code (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cf1aa755c479c73c64951f80ab0b76985507da6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="034c0-102">Commentaires dans le code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="034c0-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="034c0-103">Lorsque vous lisez les exemples de code, vous rencontrez souvent le symbole de commentaire (`'`).</span><span class="sxs-lookup"><span data-stu-id="034c0-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="034c0-104">Ce symbole indique le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur d’ignorer le texte suivant, ou le *commentaire*.</span><span class="sxs-lookup"><span data-stu-id="034c0-104">This symbol tells the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="034c0-105">Les commentaires sont de courtes explications destinées à éclairer ceux qui lisent le code.</span><span class="sxs-lookup"><span data-stu-id="034c0-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="034c0-106">En programmation, il est hautement recommandé de faire précéder toutes les procédures d'un commentaire court qui décrit les caractéristiques fonctionnelles de la procédure (ce qu'elle fait).</span><span class="sxs-lookup"><span data-stu-id="034c0-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="034c0-107">Ceci est utile tant pour l'auteur du code lui-même que pour toute autre personne amenée à consulter le code.</span><span class="sxs-lookup"><span data-stu-id="034c0-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="034c0-108">Vous devez séparer les détails relatifs à l'implémentation (comment la procédure fait ce qu'elle doit faire) des commentaires décrivant les caractéristiques fonctionnelles.</span><span class="sxs-lookup"><span data-stu-id="034c0-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="034c0-109">Si vous fournissez des informations d'implémentation dans la description, n'oubliez pas de les mettre à jour lors de la mise à jour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="034c0-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="034c0-110">Les commentaires peuvent soit suivre une instruction sur la même ligne, soit occuper une ligne entière.</span><span class="sxs-lookup"><span data-stu-id="034c0-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="034c0-111">Ces deux cas sont illustrés par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="034c0-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]  
  
 <span data-ttu-id="034c0-112">Si votre commentaire doit occuper plusieurs lignes, utilisez le symbole de commentaire sur chacune d'elles, comme l'exemple ci-dessous l'illustre.</span><span class="sxs-lookup"><span data-stu-id="034c0-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="034c0-113">Recommandations sur le commentaire</span><span class="sxs-lookup"><span data-stu-id="034c0-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="034c0-114">Le tableau suivant fournit des recommandations générales sur les types de commentaires qui peuvent précéder une section de code.</span><span class="sxs-lookup"><span data-stu-id="034c0-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="034c0-115">Il ne s'agit que de suggestions ; [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] n'impose aucune règle concernant l'ajout de commentaires.</span><span class="sxs-lookup"><span data-stu-id="034c0-115">These are suggestions; [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not enforce rules for adding comments.</span></span> <span data-ttu-id="034c0-116">Procédez de la façon que vous jugez la plus efficace pour vous et toute personne amenée à lire votre code.</span><span class="sxs-lookup"><span data-stu-id="034c0-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="034c0-117">Type de commentaire</span><span class="sxs-lookup"><span data-stu-id="034c0-117">Comment type</span></span>|<span data-ttu-id="034c0-118">Description du commentaire</span><span class="sxs-lookup"><span data-stu-id="034c0-118">Comment description</span></span>|  
|<span data-ttu-id="034c0-119">Objectif</span><span class="sxs-lookup"><span data-stu-id="034c0-119">Purpose</span></span>|<span data-ttu-id="034c0-120">Décrit ce que fait la procédure (et non comment elle le fait)</span><span class="sxs-lookup"><span data-stu-id="034c0-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="034c0-121">Assumptions (Hypothèses)</span><span class="sxs-lookup"><span data-stu-id="034c0-121">Assumptions</span></span>|<span data-ttu-id="034c0-122">Répertorie chaque variable externe, contrôle, fichier ouvert ou autre élément auquel la procédure accède.</span><span class="sxs-lookup"><span data-stu-id="034c0-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="034c0-123">Effects (Effets)</span><span class="sxs-lookup"><span data-stu-id="034c0-123">Effects</span></span>|<span data-ttu-id="034c0-124">Répertorie chaque variable externe, contrôle ou fichier affecté, ainsi que ses effets (uniquement si ce n'est pas évident)</span><span class="sxs-lookup"><span data-stu-id="034c0-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="034c0-125">Inputs (Entrées)</span><span class="sxs-lookup"><span data-stu-id="034c0-125">Inputs</span></span>|<span data-ttu-id="034c0-126">Spécifie l'objectif attaché à l'argument</span><span class="sxs-lookup"><span data-stu-id="034c0-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="034c0-127">Returns (Retours)</span><span class="sxs-lookup"><span data-stu-id="034c0-127">Returns</span></span>|<span data-ttu-id="034c0-128">Explique les valeurs retournées par la procédure.</span><span class="sxs-lookup"><span data-stu-id="034c0-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="034c0-129">N'oubliez pas :</span><span class="sxs-lookup"><span data-stu-id="034c0-129">Remember the following points:</span></span>  
  
-   <span data-ttu-id="034c0-130">Pour chaque déclaration de variable importante, faites précéder d'un commentaire décrivant son utilisation.</span><span class="sxs-lookup"><span data-stu-id="034c0-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
-   <span data-ttu-id="034c0-131">Les noms des variables, contrôles et procédures doivent être suffisamment clairs pour que les commentaires servent uniquement à fournir des détails d'implémentation complexes.</span><span class="sxs-lookup"><span data-stu-id="034c0-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
-   <span data-ttu-id="034c0-132">Vous ne pouvez pas faire suivre une séquence de continuation par un commentaire sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="034c0-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="034c0-133">Vous pouvez ajouter ou supprimer les symboles de commentaires pour un bloc de code en sélectionnant une ou plusieurs lignes de code et en choisissant le **commentaire** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton ")) et **Décommentez** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) des boutons de la **modifier**  barre d’outils.</span><span class="sxs-lookup"><span data-stu-id="034c0-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) and **Uncomment** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="034c0-134">Vous pouvez également ajouter des commentaires à votre code en faisant précéder le texte du mot clé `REM`.</span><span class="sxs-lookup"><span data-stu-id="034c0-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="034c0-135">Toutefois, le `'` symbole et la **commentaire**/**Décommentez** boutons sont plus faciles à utiliser et requiert moins d’espace et mémoire.</span><span class="sxs-lookup"><span data-stu-id="034c0-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="034c0-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="034c0-136">See Also</span></span>  
 [<span data-ttu-id="034c0-137">Documentation de votre Code avec les commentaires XML</span><span class="sxs-lookup"><span data-stu-id="034c0-137">Documenting Your Code With XML Comments</span></span>](http://msdn.microsoft.com/magazine/dd722812.aspx)  
 [<span data-ttu-id="034c0-138">Guide pratique : créer une documentation XML</span><span class="sxs-lookup"><span data-stu-id="034c0-138">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="034c0-139">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="034c0-139">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [<span data-ttu-id="034c0-140">Structure de programme et conventions de codage</span><span class="sxs-lookup"><span data-stu-id="034c0-140">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="034c0-141">REM (instruction)</span><span class="sxs-lookup"><span data-stu-id="034c0-141">REM Statement</span></span>](../../../visual-basic/language-reference/statements/rem-statement.md)
