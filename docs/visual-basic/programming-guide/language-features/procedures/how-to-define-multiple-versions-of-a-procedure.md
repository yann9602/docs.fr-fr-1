---
title: "Comment : définir plusieurs versions d'une procédure (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1abeaa6806252005dd3abfab3ff60bafa0c0cef1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="14ff1-102">Comment : définir plusieurs versions d'une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14ff1-102">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>
<span data-ttu-id="14ff1-103">Vous pouvez définir une procédure dans plusieurs versions par *surcharge* elle, à l’aide du même nom mais une liste de paramètres différente pour chaque version.</span><span class="sxs-lookup"><span data-stu-id="14ff1-103">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="14ff1-104">L’objectif de la surcharge consiste à définir de plusieurs versions étroitement liées d’une procédure sans avoir à les différencier par nom.</span><span class="sxs-lookup"><span data-stu-id="14ff1-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="14ff1-105">Pour plus d’informations, consultez [surcharge de procédure](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="14ff1-105">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="14ff1-106">Pour définir plusieurs versions d’une procédure</span><span class="sxs-lookup"><span data-stu-id="14ff1-106">To define multiple versions of a procedure</span></span>  
  
1.  <span data-ttu-id="14ff1-107">Écrire un `Sub` ou `Function` instruction de déclaration pour chaque version de la procédure que vous souhaitez définir.</span><span class="sxs-lookup"><span data-stu-id="14ff1-107">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="14ff1-108">Utilisez le même nom de procédure dans chaque déclaration.</span><span class="sxs-lookup"><span data-stu-id="14ff1-108">Use the same procedure name in every declaration.</span></span>  
  
2.  <span data-ttu-id="14ff1-109">Précéder la `Sub` ou `Function` mot clé dans chaque déclaration avec le [surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md) (mot clé).</span><span class="sxs-lookup"><span data-stu-id="14ff1-109">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="14ff1-110">Vous pouvez omettre `Overloads` dans les déclarations, mais si vous l’incluez dans une des déclarations, vous devez l’inclure dans chaque déclaration.</span><span class="sxs-lookup"><span data-stu-id="14ff1-110">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3.  <span data-ttu-id="14ff1-111">Après chaque instruction de déclaration, écrire du code de procédure pour gérer le cas spécifique où le code appelant fournit des arguments de correspondance de liste de paramètres de cette version.</span><span class="sxs-lookup"><span data-stu-id="14ff1-111">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="14ff1-112">Vous n’avez pas à tester pour quels paramètres le code appelant a fourni.</span><span class="sxs-lookup"><span data-stu-id="14ff1-112">You do not have to test for which parameters the calling code has supplied.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="14ff1-113">transmet le contrôle à la version correspondante de votre procédure.</span><span class="sxs-lookup"><span data-stu-id="14ff1-113"> passes control to the matching version of your procedure.</span></span>  
  
4.  <span data-ttu-id="14ff1-114">Terminez chaque version de la procédure avec le `End Sub` ou `End Function` instruction comme il convient.</span><span class="sxs-lookup"><span data-stu-id="14ff1-114">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14ff1-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="14ff1-115">Example</span></span>  
 <span data-ttu-id="14ff1-116">L’exemple suivant définit un `Sub` procédure pour valider une transaction sur le solde d’un client.</span><span class="sxs-lookup"><span data-stu-id="14ff1-116">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="14ff1-117">Elle utilise le `Overloads` mot clé pour définir deux versions de la procédure qui accepte le client par nom et l’autre par numéro de compte.</span><span class="sxs-lookup"><span data-stu-id="14ff1-117">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 <span data-ttu-id="14ff1-118">Le code appelant peut obtenir l’identification du client selon un `String` ou un `Integer`, puis utilisez la même instruction appelante dans les deux cas.</span><span class="sxs-lookup"><span data-stu-id="14ff1-118">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="14ff1-119">Pour plus d’informations sur l’appel de ces versions de la `post` procédure, consultez [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="14ff1-119">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="14ff1-120">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="14ff1-120">Compiling the Code</span></span>  
 <span data-ttu-id="14ff1-121">Assurez-vous que chacune de vos versions surchargées a le même nom de procédure, mais une autre liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="14ff1-121">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14ff1-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14ff1-122">See Also</span></span>  
 [<span data-ttu-id="14ff1-123">Procédures</span><span class="sxs-lookup"><span data-stu-id="14ff1-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="14ff1-124">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="14ff1-124">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="14ff1-125">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="14ff1-125">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="14ff1-126">Guide pratique : surcharger une procédure qui accepte des paramètres optionnels</span><span class="sxs-lookup"><span data-stu-id="14ff1-126">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="14ff1-127">Guide pratique : surcharger une procédure qui accepte un nombre indéfini de paramètres</span><span class="sxs-lookup"><span data-stu-id="14ff1-127">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="14ff1-128">Considérations sur les surcharges de procédures</span><span class="sxs-lookup"><span data-stu-id="14ff1-128">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="14ff1-129">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="14ff1-129">Overload Resolution</span></span>](./overload-resolution.md)
