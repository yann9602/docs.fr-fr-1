---
title: "Comment : définir plusieurs Versions d’une procédure (Visual Basic) | Documents Microsoft"
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
- procedures, defining
- Visual Basic code, procedures
- procedures, overloading
- procedures, multiple versions
- procedure overloading, multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
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
ms.openlocfilehash: f4296ba3a78316b70011bcca18f7071716f3c90d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="feb53-102">Comment : définir plusieurs versions d'une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="feb53-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="feb53-103">Vous pouvez définir une procédure dans plusieurs versions en *surcharge* il, en utilisant le même nom mais une liste de paramètres différente pour chaque version.</span><span class="sxs-lookup"><span data-stu-id="feb53-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="feb53-104">L’objectif de la surcharge consiste à définir plusieurs versions étroitement liées d’une procédure sans avoir à les différencier par nom.</span><span class="sxs-lookup"><span data-stu-id="feb53-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="feb53-105">Pour plus d’informations, consultez [surcharge de procédure](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="feb53-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="feb53-106">Pour définir plusieurs versions d’une procédure</span><span class="sxs-lookup"><span data-stu-id="feb53-106">To define multiple versions of a procedure</span></span>  
  
1.  <span data-ttu-id="feb53-107">Écrire un `Sub` ou `Function` instruction de déclaration pour chaque version de la procédure que vous souhaitez définir.</span><span class="sxs-lookup"><span data-stu-id="feb53-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="feb53-108">Utilisez le même nom de procédure dans chaque déclaration.</span><span class="sxs-lookup"><span data-stu-id="feb53-108">Use the same procedure name in every declaration.</span></span>  
  
2.  <span data-ttu-id="feb53-109">Faites précéder le `Sub` ou `Function` (mot clé) dans chaque déclaration le [surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md) (mot clé).</span><span class="sxs-lookup"><span data-stu-id="feb53-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="feb53-110">Vous pouvez omettre `Overloads` dans les déclarations, mais si vous l’incluez dans une des déclarations, vous devez l’inclure dans toutes les déclarations.</span><span class="sxs-lookup"><span data-stu-id="feb53-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3.  <span data-ttu-id="feb53-111">Après chaque instruction de déclaration, écrivez le code de procédure pour gérer le cas où le code appelant fournit les arguments qui correspondent à liste de paramètres de cette version.</span><span class="sxs-lookup"><span data-stu-id="feb53-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="feb53-112">Vous n’avez pas à tester pour quels paramètres le code appelant a fourni.</span><span class="sxs-lookup"><span data-stu-id="feb53-112">You do not have to test for which parameters the calling code has supplied.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="feb53-113">passe le contrôle à la version correspondante de votre procédure.</span><span class="sxs-lookup"><span data-stu-id="feb53-113"> passes control to the matching version of your procedure.</span></span>  
  
4.  <span data-ttu-id="feb53-114">Terminez chaque version de la procédure avec le `End Sub` ou `End Function` instruction comme il convient.</span><span class="sxs-lookup"><span data-stu-id="feb53-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feb53-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="feb53-115">Example</span></span>  
 <span data-ttu-id="feb53-116">L’exemple suivant définit un `Sub` procédure pour publier une transaction relative au solde d’un client.</span><span class="sxs-lookup"><span data-stu-id="feb53-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="feb53-117">Il utilise le `Overloads` (mot clé) pour définir deux versions de la procédure, un qui accepte le client par nom et l’autre par numéro de compte.</span><span class="sxs-lookup"><span data-stu-id="feb53-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 <span data-ttu-id="feb53-118">[!code-vb[VbVbcnProcedures&#72;](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="feb53-118">[!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]</span></span>  
  
 <span data-ttu-id="feb53-119">Le code appelant peut obtenir l’identification du client selon un `String` ou `Integer`, puis utilisez la même instruction appelante dans les deux cas.</span><span class="sxs-lookup"><span data-stu-id="feb53-119">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="feb53-120">Pour plus d’informations sur l’appel de ces versions de la `post` procédure, consultez la page [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="feb53-120">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="feb53-121">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="feb53-121">Compiling the Code</span></span>  
 <span data-ttu-id="feb53-122">Assurez-vous que chacun de vos versions surchargées a le même nom de procédure, mais une liste de paramètres différente.</span><span class="sxs-lookup"><span data-stu-id="feb53-122">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb53-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="feb53-123">See Also</span></span>  
 <span data-ttu-id="feb53-124">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="feb53-124">[Procedures](./index.md) </span></span>  
<span data-ttu-id="feb53-125"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="feb53-125"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="feb53-126"> [Procédures de dépannage](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="feb53-126"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="feb53-127"> [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="feb53-127"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="feb53-128"> [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="feb53-128"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="feb53-129"> [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="feb53-129"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="feb53-130"> [Résolution de surcharge](./overload-resolution.md)</span><span class="sxs-lookup"><span data-stu-id="feb53-130"> [Overload Resolution](./overload-resolution.md)</span></span>
