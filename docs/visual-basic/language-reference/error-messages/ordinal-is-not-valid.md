---
title: Nombre non valide
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d31d0fba19cc16004c0b56786af30603d0c509ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="362cc-102">Nombre non valide</span><span class="sxs-lookup"><span data-stu-id="362cc-102">Ordinal is not valid</span></span>
<span data-ttu-id="362cc-103">Votre appel à une bibliothèque de liens dynamiques (DLL) indiqué à utiliser un nombre au lieu d’un nom de procédure, à l’aide de la `#num` syntaxe.</span><span class="sxs-lookup"><span data-stu-id="362cc-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="362cc-104">Cette erreur a les causes possibles suivantes :</span><span class="sxs-lookup"><span data-stu-id="362cc-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="362cc-105">Une tentative de convertir le `#num` expression à un nombre a échoué.</span><span class="sxs-lookup"><span data-stu-id="362cc-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="362cc-106">Le `#num` spécifié n’indique pas de fonction dans la DLL.</span><span class="sxs-lookup"><span data-stu-id="362cc-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="362cc-107">Une bibliothèque de types possède une déclaration non valide, ce qui provoque une utilisation interne d’un nombre ordinal non valide.</span><span class="sxs-lookup"><span data-stu-id="362cc-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="362cc-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="362cc-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="362cc-109">Assurez-vous que l’expression représente un nombre valide ou appelez la procédure par nom.</span><span class="sxs-lookup"><span data-stu-id="362cc-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2.  <span data-ttu-id="362cc-110">Assurez-vous que `#num` identifie une fonction valide dans la DLL.</span><span class="sxs-lookup"><span data-stu-id="362cc-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3.  <span data-ttu-id="362cc-111">Isoler la cause du problème en supprimant le code de l’appel de procédure.</span><span class="sxs-lookup"><span data-stu-id="362cc-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="362cc-112">Écrire un `Declare` instruction de la procédure et signalez le problème au fournisseur de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="362cc-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="362cc-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="362cc-113">See Also</span></span>  
 [<span data-ttu-id="362cc-114">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="362cc-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
