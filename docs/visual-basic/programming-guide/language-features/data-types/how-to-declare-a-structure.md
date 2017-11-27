---
title: "Comment : déclarer une structure (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8203327e189d095c9f7ceeb3b68ea24efe9ba882
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-structure-visual-basic"></a><span data-ttu-id="612fb-102">Comment : déclarer une structure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="612fb-102">How to: Declare a Structure (Visual Basic)</span></span>
<span data-ttu-id="612fb-103">Vous commencez une déclaration de structure par le [instruction Structure](../../../../visual-basic/language-reference/statements/structure-statement.md), et vous la terminez avec la `End` `Structure` instruction.</span><span class="sxs-lookup"><span data-stu-id="612fb-103">You begin a structure declaration with the [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md), and you end it with the `End` `Structure` statement.</span></span> <span data-ttu-id="612fb-104">Entre ces deux instructions, vous devez déclarer au moins un *élément*.</span><span class="sxs-lookup"><span data-stu-id="612fb-104">Between these two statements you must declare at least one *element*.</span></span> <span data-ttu-id="612fb-105">Les éléments peuvent être de n’importe quel type de données, mais au moins doit être une variable non partagée ou un événement non partagé.</span><span class="sxs-lookup"><span data-stu-id="612fb-105">The elements can be of any data type, but at least one must be either a nonshared variable or a nonshared, noncustom event.</span></span>  
  
 <span data-ttu-id="612fb-106">Vous ne peut pas initialiser un des éléments de structure dans la déclaration de structure.</span><span class="sxs-lookup"><span data-stu-id="612fb-106">You cannot initialize any of the structure elements in the structure declaration.</span></span> <span data-ttu-id="612fb-107">Lorsque vous déclarez une variable qui doit être d’un type structure, vous affectez des valeurs aux éléments en y accédant via la variable.</span><span class="sxs-lookup"><span data-stu-id="612fb-107">When you declare a variable to be of a structure type, you assign values to the elements by accessing them through the variable.</span></span>  
  
 <span data-ttu-id="612fb-108">Pour en savoir plus sur les différences entre les classes et structures, consultez [Structures et Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span><span class="sxs-lookup"><span data-stu-id="612fb-108">For a discussion of the differences between structures and classes, see [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).</span></span>  
  
 <span data-ttu-id="612fb-109">À des fins de démonstration, considérez une situation dans laquelle vous souhaitez effectuer le suivi de nom d’un employé, numéro de poste et salaire.</span><span class="sxs-lookup"><span data-stu-id="612fb-109">For demonstration purposes, consider a situation where you want to keep track of an employee's name, telephone extension, and salary.</span></span> <span data-ttu-id="612fb-110">Une structure vous permet de procéder à une variable.</span><span class="sxs-lookup"><span data-stu-id="612fb-110">A structure allows you to do this in a single variable.</span></span>  
  
### <a name="to-declare-a-structure"></a><span data-ttu-id="612fb-111">Pour déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="612fb-111">To declare a structure</span></span>  
  
1.  <span data-ttu-id="612fb-112">Créer de début et fin des instructions pour la structure.</span><span class="sxs-lookup"><span data-stu-id="612fb-112">Create the beginning and ending statements for the structure.</span></span>  
  
     <span data-ttu-id="612fb-113">Vous pouvez spécifier le niveau d’accès d’une structure à l’aide de la [Public](../../../../visual-basic/language-reference/modifiers/public.md), [protégé](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), ou [privé](../../../../visual-basic/language-reference/modifiers/private.md) (mot clé), ou vous pouvez la laisser par défaut `Public`.</span><span class="sxs-lookup"><span data-stu-id="612fb-113">You can specify the access level of a structure using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, or you can let it default to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  <span data-ttu-id="612fb-114">Ajouter des éléments dans le corps de la structure.</span><span class="sxs-lookup"><span data-stu-id="612fb-114">Add elements to the body of the structure.</span></span>  
  
     <span data-ttu-id="612fb-115">Une structure doit avoir au moins un élément.</span><span class="sxs-lookup"><span data-stu-id="612fb-115">A structure must have at least one element.</span></span> <span data-ttu-id="612fb-116">Vous devez déclarer chaque élément et lui attribuer un niveau d’accès.</span><span class="sxs-lookup"><span data-stu-id="612fb-116">You must declare every element and specify an access level for it.</span></span> <span data-ttu-id="612fb-117">Si vous utilisez la [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) sans les mots clés, l’accessibilité par défaut est `Public`.</span><span class="sxs-lookup"><span data-stu-id="612fb-117">If you use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) without any keywords, the accessibility defaults to `Public`.</span></span>  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     <span data-ttu-id="612fb-118">Le `salary` champ dans l’exemple précédent est `Private`, ce qui signifie qu’il n’est pas accessible en dehors de la structure, même à partir de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="612fb-118">The `salary` field in the preceding example is `Private`, which means it is inaccessible outside the structure, even from the containing class.</span></span> <span data-ttu-id="612fb-119">Toutefois, le `giveRaise` procédure est `Public`, donc il peut être appelée à l’extérieur de la structure.</span><span class="sxs-lookup"><span data-stu-id="612fb-119">However, the `giveRaise` procedure is `Public`, so it can be called from outside the structure.</span></span> <span data-ttu-id="612fb-120">De même, vous pouvez déclencher la `salaryReviewTime` événement à partir de l’extérieur de la structure.</span><span class="sxs-lookup"><span data-stu-id="612fb-120">Similarly, you can raise the `salaryReviewTime` event from outside the structure.</span></span>  
  
     <span data-ttu-id="612fb-121">En plus des variables, `Sub` des procédures et des événements, vous pouvez également définir des constantes, `Function` des procédures et des propriétés dans une structure.</span><span class="sxs-lookup"><span data-stu-id="612fb-121">In addition to variables, `Sub` procedures, and events, you can also define constants, `Function` procedures, and properties in a structure.</span></span> <span data-ttu-id="612fb-122">Vous pouvez désigner au plus une propriété comme le *propriété par défaut*, à condition qu’elle accepte au moins un argument.</span><span class="sxs-lookup"><span data-stu-id="612fb-122">You can designate at most one property as the *default property*, provided it takes at least one argument.</span></span> <span data-ttu-id="612fb-123">Vous pouvez gérer un événement avec un [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="612fb-123">You can handle an event with a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure.</span></span> <span data-ttu-id="612fb-124">Pour plus d’informations, consultez [Comment : déclarer et appeler une propriété par défaut en Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span><span class="sxs-lookup"><span data-stu-id="612fb-124">For more information, see [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="612fb-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="612fb-125">See Also</span></span>  
 [<span data-ttu-id="612fb-126">Types de données</span><span class="sxs-lookup"><span data-stu-id="612fb-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="612fb-127">Types de données élémentaires</span><span class="sxs-lookup"><span data-stu-id="612fb-127">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="612fb-128">Types de données composites</span><span class="sxs-lookup"><span data-stu-id="612fb-128">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="612fb-129">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="612fb-129">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="612fb-130">Structures</span><span class="sxs-lookup"><span data-stu-id="612fb-130">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="612fb-131">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="612fb-131">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="612fb-132">Variables de structure</span><span class="sxs-lookup"><span data-stu-id="612fb-132">Structure Variables</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [<span data-ttu-id="612fb-133">Structures et autres éléments de programmation</span><span class="sxs-lookup"><span data-stu-id="612fb-133">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [<span data-ttu-id="612fb-134">Structures et classes</span><span class="sxs-lookup"><span data-stu-id="612fb-134">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [<span data-ttu-id="612fb-135">Type de données défini par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="612fb-135">User-Defined Data Type</span></span>](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
