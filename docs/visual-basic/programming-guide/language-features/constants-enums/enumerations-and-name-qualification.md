---
title: "Énumérations et qualification de noms (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cb97d6a8f4b7e81f2b759010214e200ec63ff21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="3e8fd-102">Énumérations et qualification de noms (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e8fd-102">Enumerations and Name Qualification (Visual Basic)</span></span>
<span data-ttu-id="3e8fd-103">Normalement, lorsque vous faites référence à un membre d’une énumération, vous devez qualifier le nom du membre avec le nom de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="3e8fd-103">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="3e8fd-104">Par exemple, pour faire référence à la `Sunday` membre de votre `Days` énumération, vous utilisez la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="3e8fd-104">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="3e8fd-105">À l’aide de l’instruction Imports</span><span class="sxs-lookup"><span data-stu-id="3e8fd-105">Using the Imports Statement</span></span>  
 <span data-ttu-id="3e8fd-106">Vous pouvez éviter d’utiliser des noms qualifiés complets en ajoutant un `Imports` instruction dans la section de déclarations d’espace de noms de votre code, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3e8fd-106">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 <span data-ttu-id="3e8fd-107">Un `Imports` instruction importe des noms d’espace de noms de projets référencés et d’assemblys et depuis le même projet que le module dans lequel apparaît l’instruction.</span><span class="sxs-lookup"><span data-stu-id="3e8fd-107">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="3e8fd-108">Une fois que cette instruction est ajoutée, vous pouvez faire référence aux membres de l’énumération sans qualification, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3e8fd-108">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 <span data-ttu-id="3e8fd-109">En organisant les ensembles de constantes connexes dans les énumérations, vous pouvez utiliser les mêmes noms de constantes dans des contextes différents.</span><span class="sxs-lookup"><span data-stu-id="3e8fd-109">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="3e8fd-110">Par exemple, vous pouvez utiliser les mêmes noms pour les constantes de jour de la semaine dans la `Days` et `WorkDays` énumérations.</span><span class="sxs-lookup"><span data-stu-id="3e8fd-110">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="3e8fd-111">Si vous utilisez la `Imports` instruction avec vos énumérations, vous devez veiller à éviter les références ambiguës.</span><span class="sxs-lookup"><span data-stu-id="3e8fd-111">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="3e8fd-112">Prenons l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="3e8fd-112">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 <span data-ttu-id="3e8fd-113">En supposant que `Monday` est membre des deux le `Days` énumération et la `Workdays` énumération, ce code génère une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="3e8fd-113">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="3e8fd-114">Pour éviter les références ambiguës lorsque vous faites référence à une constante individuelle, qualifiez le nom de constant par son énumération.</span><span class="sxs-lookup"><span data-stu-id="3e8fd-114">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="3e8fd-115">Le code suivant fait référence à la `Saturday` constantes dans les `Days` et `WorkDays` énumérations.</span><span class="sxs-lookup"><span data-stu-id="3e8fd-115">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3e8fd-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e8fd-116">See Also</span></span>  
 [<span data-ttu-id="3e8fd-117">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="3e8fd-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="3e8fd-118">Comment : déclarer une énumération</span><span class="sxs-lookup"><span data-stu-id="3e8fd-118">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="3e8fd-119">Guide pratique : faire référence à un membre d’énumération</span><span class="sxs-lookup"><span data-stu-id="3e8fd-119">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="3e8fd-120">Comment : parcourir une énumération dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e8fd-120">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="3e8fd-121">Guide pratique : déterminer la chaîne associée à une valeur d’énumération</span><span class="sxs-lookup"><span data-stu-id="3e8fd-121">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="3e8fd-122">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="3e8fd-122">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="3e8fd-123">Constantes et types de données littérales</span><span class="sxs-lookup"><span data-stu-id="3e8fd-123">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="3e8fd-124">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="3e8fd-124">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="3e8fd-125">Imports (instruction) (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="3e8fd-125">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="3e8fd-126">Types de données</span><span class="sxs-lookup"><span data-stu-id="3e8fd-126">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
