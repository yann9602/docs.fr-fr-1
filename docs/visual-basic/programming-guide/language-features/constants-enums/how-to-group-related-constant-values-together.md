---
title: "Comment : regrouper les valeurs de constante connexes (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be57b56047654d6eb3536bb0b8f63eca27decdb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="b03cc-102">Comment : regrouper les valeurs de constante connexes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b03cc-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="b03cc-103">Une énumération est le meilleur moyen de regrouper les constantes associées.</span><span class="sxs-lookup"><span data-stu-id="b03cc-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="b03cc-104">Vous créez une énumération avec la `Enum` instruction dans la section des déclarations d’une classe ou un module.</span><span class="sxs-lookup"><span data-stu-id="b03cc-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="b03cc-105">Pour plus d’informations, consultez [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="b03cc-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="b03cc-106">Groupe les valeurs de constantes connexes</span><span class="sxs-lookup"><span data-stu-id="b03cc-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="b03cc-107">Écrivez une déclaration qui inclut un niveau d’accès de code, le `Enum` (mot clé) et un nom valide.</span><span class="sxs-lookup"><span data-stu-id="b03cc-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="b03cc-108">Cet exemple crée la `Private` énumération, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="b03cc-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  <span data-ttu-id="b03cc-109">Définissez les constantes dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="b03cc-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="b03cc-110">Cet exemple crée la `Public` énumération `temperatureValues` et assigne ses valeurs.</span><span class="sxs-lookup"><span data-stu-id="b03cc-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b03cc-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b03cc-111">See Also</span></span>  
 [<span data-ttu-id="b03cc-112">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="b03cc-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="b03cc-113">Guide pratique : faire référence à un membre d’énumération</span><span class="sxs-lookup"><span data-stu-id="b03cc-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="b03cc-114">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="b03cc-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="b03cc-115">Vue d’ensemble des constantes</span><span class="sxs-lookup"><span data-stu-id="b03cc-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="b03cc-116">Constantes et types de données littérales</span><span class="sxs-lookup"><span data-stu-id="b03cc-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="b03cc-117">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="b03cc-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
