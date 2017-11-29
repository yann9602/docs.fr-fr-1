---
title: "Quand utiliser une énumération (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3b2937cc71c0c31bd8dce3d77fb33f48e1b5750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="c7c7f-102">Quand utiliser une énumération (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7c7f-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="c7c7f-103">Les énumérations offrent un moyen simple de travailler avec des ensembles de constantes associées.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="c7c7f-104">Une énumération, ou `Enum`, est un nom symbolique pour un ensemble de valeurs.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="c7c7f-105">Les énumérations sont traitées comme des types de données, et vous pouvez les utiliser pour créer des jeux de constantes à utiliser avec des variables et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="c7c7f-106">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="c7c7f-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="c7c7f-107">Chaque fois qu’une procédure accepte un ensemble limité de variables, envisagez d’utiliser une énumération.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="c7c7f-108">Les énumérations rendent le code plus clair et plus lisible, particulièrement lorsque des noms explicites sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="c7c7f-109">Avantages de l’utilisation des énumérations :</span><span class="sxs-lookup"><span data-stu-id="c7c7f-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="c7c7f-110">Réduit les erreurs provoquées par transposer ou numéros d’erreur de frappe.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="c7c7f-111">Rend faciles à modifier les valeurs dans le futur.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="c7c7f-112">Rend le code plus facile à lire, ce qui signifie qu’il est peu probable que les erreurs lisibilité il.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="c7c7f-113">Garantit la compatibilité ascendante.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-113">Ensures forward compatibility.</span></span> <span data-ttu-id="c7c7f-114">Avec des énumérations, votre code est moins susceptible d’échouer si à l’avenir une personne modifie les valeurs correspondant aux noms de membre.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="c7c7f-115">Énumérations d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="c7c7f-115">Naming Enumerations</span></span>  
 <span data-ttu-id="c7c7f-116">Utilisez une convention d’affectation de noms pour les membres de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="c7c7f-117">Lorsque [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] rencontre un nom de membre d’énumération, une exception peut être levée si d’autres bibliothèques de types référencés contiennent le même nom.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-117">When [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="c7c7f-118">Utilisez un préfixe unique qui identifie les valeurs à partir de votre application ou composant.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="c7c7f-119">Lorsque vous faites référence à un membre d’une énumération, vous devez qualifier le nom du membre avec le nom de l’énumération ou bien utiliser la `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="c7c7f-120">Pour plus d’informations, consultez [énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="c7c7f-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="c7c7f-121">Énumérations prédéfinies</span><span class="sxs-lookup"><span data-stu-id="c7c7f-121">Predefined Enumerations</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="c7c7f-122">fournit plusieurs énumérations prédéfinies, telles que `FirstDayOfWeek` et `MsgBoxResult`, pour faciliter votre code.</span><span class="sxs-lookup"><span data-stu-id="c7c7f-122"> provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="c7c7f-123">Pour obtenir la liste de ces consultez [constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="c7c7f-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7c7f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7c7f-124">See Also</span></span>  
 [<span data-ttu-id="c7c7f-125">Comment : déclarer une énumération</span><span class="sxs-lookup"><span data-stu-id="c7c7f-125">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="c7c7f-126">Guide pratique : faire référence à un membre d’énumération</span><span class="sxs-lookup"><span data-stu-id="c7c7f-126">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="c7c7f-127">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="c7c7f-127">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="c7c7f-128">Comment : parcourir une énumération dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7c7f-128">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="c7c7f-129">Guide pratique : déterminer la chaîne associée à une valeur d’énumération</span><span class="sxs-lookup"><span data-stu-id="c7c7f-129">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="c7c7f-130">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="c7c7f-130">Enum Statement</span></span>](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [<span data-ttu-id="c7c7f-131">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="c7c7f-131">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
