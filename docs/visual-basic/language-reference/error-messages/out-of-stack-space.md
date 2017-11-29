---
title: Espace de pile insuffisant (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3959c24aa4e95204e156a9863ef0ce237af1fcda
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="e8985-102">Espace de pile insuffisant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8985-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="e8985-103">La pile est une zone de travail de la mémoire augmente et se réduit dynamiquement aux demandes de votre programme en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e8985-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="e8985-104">Ses limites ont été dépassées.</span><span class="sxs-lookup"><span data-stu-id="e8985-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e8985-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e8985-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="e8985-106">Vérifiez que les procédures ne sont pas imbriquées trop profondément.</span><span class="sxs-lookup"><span data-stu-id="e8985-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="e8985-107">Assurez-vous que les procédures récursives se terminent correctement.</span><span class="sxs-lookup"><span data-stu-id="e8985-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="e8985-108">Si les variables locales requièrent davantage d’espace de variable locale qu’il n’est disponible, essayez de déclarer des variables au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="e8985-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="e8985-109">Vous pouvez également déclarer toutes les variables dans la procédure statique en faisant précéder le `Property`, `Sub`, ou `Function` mot clé with `Static`.</span><span class="sxs-lookup"><span data-stu-id="e8985-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="e8985-110">Vous pouvez également utiliser la `Static` instruction pour déclarer des variables statiques individuelles au sein de procédures.</span><span class="sxs-lookup"><span data-stu-id="e8985-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="e8985-111">Redéfinissez certaines de vos chaînes de longueur fixe en tant que chaînes de longueur variable, comme les chaînes de longueur fixe utilisent davantage d’espace de pile que les chaînes de longueur variable.</span><span class="sxs-lookup"><span data-stu-id="e8985-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="e8985-112">Vous pouvez également définir la chaîne au niveau du module où elle ne requiert aucun espace de pile.</span><span class="sxs-lookup"><span data-stu-id="e8985-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="e8985-113">Vérifiez le nombre d’imbriquée `DoEvents` appels de fonctions, à l’aide de la `Calls` boîte de dialogue pour afficher les procédures actives sur la pile.</span><span class="sxs-lookup"><span data-stu-id="e8985-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="e8985-114">Assurez-vous que vous n’avez pas provoqué une « cascade d’événements » en déclenchant un événement qui appelle une procédure événementielle déjà sur la pile.</span><span class="sxs-lookup"><span data-stu-id="e8985-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="e8985-115">Une cascade d’événements est similaire à un appel de procédure récursive inachevé, mais il est moins évidente, étant donné que l’appel est effectué par [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] au lieu d’un appel explicite dans le code.</span><span class="sxs-lookup"><span data-stu-id="e8985-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rather than an explicit call in the code.</span></span> <span data-ttu-id="e8985-116">Utilisez le `Calls` boîte de dialogue pour afficher les procédures actives sur la pile.</span><span class="sxs-lookup"><span data-stu-id="e8985-116">Use the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8985-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8985-117">See Also</span></span>  
 [<span data-ttu-id="e8985-118">Fenêtres Mémoire</span><span class="sxs-lookup"><span data-stu-id="e8985-118">Memory Windows</span></span>](/visualstudio/debugger/memory-windows)
