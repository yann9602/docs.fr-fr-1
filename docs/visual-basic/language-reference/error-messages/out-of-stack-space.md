---
title: "(Visual Basic) d’espace de pile | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
dev_langs:
- VB
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
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
ms.openlocfilehash: 256ef0c7fcb3632e0c13d12737d438225343884f
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="out-of-stack-space-visual-basic"></a><span data-ttu-id="04795-102">Espace de pile insuffisant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04795-102">Out of stack space (Visual Basic)</span></span>
<span data-ttu-id="04795-103">La pile est une zone de mémoire qui augmente ou diminue dynamiquement aux besoins de votre programme en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="04795-103">The stack is a working area of memory that grows and shrinks dynamically with the demands of your executing program.</span></span> <span data-ttu-id="04795-104">Ses limites ont été dépassées.</span><span class="sxs-lookup"><span data-stu-id="04795-104">Its limits have been exceeded.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="04795-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="04795-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="04795-106">Vérifiez que les procédures ne sont pas imbriqués trop profondément.</span><span class="sxs-lookup"><span data-stu-id="04795-106">Check that procedures are not nested too deeply.</span></span>  
  
2.  <span data-ttu-id="04795-107">Assurez-vous que les procédures récursives se terminent correctement.</span><span class="sxs-lookup"><span data-stu-id="04795-107">Make sure recursive procedures terminate properly.</span></span>  
  
3.  <span data-ttu-id="04795-108">Si les variables locales requièrent davantage local variable d’espace disponible, essayez de déclarer des variables au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="04795-108">If local variables require more local variable space than is available, try declaring some variables at the module level.</span></span> <span data-ttu-id="04795-109">Vous pouvez également déclarer toutes les variables dans la procédure statique en faisant précéder le `Property`, `Sub`, ou `Function` mot clé with `Static`.</span><span class="sxs-lookup"><span data-stu-id="04795-109">You can also declare all variables in the procedure static by preceding the `Property`, `Sub`, or `Function` keyword with `Static`.</span></span> <span data-ttu-id="04795-110">Vous pouvez également utiliser la `Static` instruction pour déclarer des variables statiques individuelles au sein de procédures.</span><span class="sxs-lookup"><span data-stu-id="04795-110">Or you can use the `Static` statement to declare individual static variables within procedures.</span></span>  
  
4.  <span data-ttu-id="04795-111">Redéfinir certains de vos chaînes de longueur fixe en tant que chaînes de longueur variable, comme les chaînes de longueur fixe utilisent davantage d’espace pile que les chaînes de longueur variable.</span><span class="sxs-lookup"><span data-stu-id="04795-111">Redefine some of your fixed-length strings as variable-length strings, as fixed-length strings use more stack space than variable-length strings.</span></span> <span data-ttu-id="04795-112">Vous pouvez également définir la chaîne au niveau du module où elle ne requiert aucun espace de pile.</span><span class="sxs-lookup"><span data-stu-id="04795-112">You can also define the string at module level where it requires no stack space.</span></span>  
  
5.  <span data-ttu-id="04795-113">Vérifiez le nombre d’imbriquée `DoEvents` appels de fonctions, à l’aide de la `Calls` boîte de dialogue pour afficher les procédures actives sur la pile.</span><span class="sxs-lookup"><span data-stu-id="04795-113">Check the number of nested `DoEvents` function calls, by using the `Calls` dialog box to view which procedures are active on the stack.</span></span>  
  
6.  <span data-ttu-id="04795-114">Assurez-vous que vous n’avez pas provoqué une « cascade d’événements » en déclenchant un événement qui appelle une procédure d’événement déjà sur la pile.</span><span class="sxs-lookup"><span data-stu-id="04795-114">Make sure you did not cause an "event cascade" by triggering an event that calls an event procedure already on the stack.</span></span> <span data-ttu-id="04795-115">Une cascade d’événements est similaire à un appel de procédure récursive inachevé, mais il est moins évident, puisque l’appel est effectué par [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] plutôt qu’un appel explicit dans le code.</span><span class="sxs-lookup"><span data-stu-id="04795-115">An event cascade is similar to an unterminated recursive procedure call, but it is less obvious, since the call is made by [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] rather than an explicit call in the code.</span></span> <span data-ttu-id="04795-116">Utilisez le `Calls`boîte de dialogue pour afficher les procédures actives sur la pile.</span><span class="sxs-lookup"><span data-stu-id="04795-116">Use the `Calls`dialog box to view which procedures are active on the stack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04795-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04795-117">See Also</span></span>  
 [<span data-ttu-id="04795-118">Fenêtres Mémoire</span><span class="sxs-lookup"><span data-stu-id="04795-118">Memory Windows</span></span>](https://docs.microsoft.com/visualstudio/debugger/memory-windows)
