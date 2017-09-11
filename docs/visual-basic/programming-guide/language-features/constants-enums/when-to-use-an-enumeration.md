---
title: "Quand utiliser une énumération (Visual Basic) | Documents Microsoft"
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
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
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
ms.openlocfilehash: 3853950382fd4336c569f9d772aea3c1312f2ebc
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="d5a14-102">Quand utiliser une énumération (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a14-102">When to Use an Enumeration (Visual Basic)</span></span>
<span data-ttu-id="d5a14-103">Les énumérations offrent un moyen simple de travailler avec des ensembles de constantes associées.</span><span class="sxs-lookup"><span data-stu-id="d5a14-103">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="d5a14-104">Une énumération, ou `Enum`, est un nom symbolique pour un ensemble de valeurs.</span><span class="sxs-lookup"><span data-stu-id="d5a14-104">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="d5a14-105">Les énumérations sont traitées comme des types de données, et vous pouvez les utiliser pour créer des jeux de constantes utilisables avec des variables et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="d5a14-105">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="d5a14-106">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="d5a14-106">When to Use an Enumeration</span></span>  
 <span data-ttu-id="d5a14-107">Chaque fois qu’une procédure accepte un jeu limité de variables, envisagez d’utiliser une énumération.</span><span class="sxs-lookup"><span data-stu-id="d5a14-107">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="d5a14-108">Énumérations rendent le code plus clair et plus lisible, en particulier lorsque des noms explicites sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="d5a14-108">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="d5a14-109">Les avantages de l’utilisation des énumérations :</span><span class="sxs-lookup"><span data-stu-id="d5a14-109">The benefits of using enumerations include:</span></span>  
  
-   <span data-ttu-id="d5a14-110">Réduit les erreurs dues à la transposition ou entrée incorrecte de nombres.</span><span class="sxs-lookup"><span data-stu-id="d5a14-110">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="d5a14-111">Rend plus facile à modifier les valeurs dans le futur.</span><span class="sxs-lookup"><span data-stu-id="d5a14-111">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="d5a14-112">Rend le code plus facile à lire, ce qui signifie qu’il est peu probable que les erreurs lisibilité il.</span><span class="sxs-lookup"><span data-stu-id="d5a14-112">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
-   <span data-ttu-id="d5a14-113">Garantit la compatibilité ascendante.</span><span class="sxs-lookup"><span data-stu-id="d5a14-113">Ensures forward compatibility.</span></span> <span data-ttu-id="d5a14-114">Avec des énumérations, votre code est moins susceptible d’échouer si l’avenir quelqu'un modifie les valeurs correspondant aux noms de membres.</span><span class="sxs-lookup"><span data-stu-id="d5a14-114">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="d5a14-115">Énumérations d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="d5a14-115">Naming Enumerations</span></span>  
 <span data-ttu-id="d5a14-116">Utilisez une convention d’affectation de noms pour les membres de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="d5a14-116">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="d5a14-117">Lorsque [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] rencontre un nom de membre d’énumération, une exception peut être levée si d’autres bibliothèques de types référencées contiennent le même nom.</span><span class="sxs-lookup"><span data-stu-id="d5a14-117">When [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="d5a14-118">Utilisez un préfixe unique qui identifie les valeurs à partir de votre application ou composant.</span><span class="sxs-lookup"><span data-stu-id="d5a14-118">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="d5a14-119">Lorsque vous faites référence à un membre d’une énumération, vous devez qualifier le nom du membre avec le nom d’énumération ou bien utiliser la `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="d5a14-119">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="d5a14-120">Pour plus d’informations, consultez [énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="d5a14-120">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="d5a14-121">Énumérations prédéfinies</span><span class="sxs-lookup"><span data-stu-id="d5a14-121">Predefined Enumerations</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="d5a14-122">fournit plusieurs énumérations prédéfinies, telles que `FirstDayOfWeek` et `MsgBoxResul`t, pour faciliter votre code.</span><span class="sxs-lookup"><span data-stu-id="d5a14-122"> provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResul`t, to facilitate your code.</span></span> <span data-ttu-id="d5a14-123">Pour obtenir la liste, consultez [constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="d5a14-123">For a list of these see [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a14-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5a14-124">See Also</span></span>  
 <span data-ttu-id="d5a14-125">[Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="d5a14-125">[How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="d5a14-126"> [Comment : faire référence à un membre d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span><span class="sxs-lookup"><span data-stu-id="d5a14-126"> [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span></span>  
<span data-ttu-id="d5a14-127"> [Énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="d5a14-127"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="d5a14-128"> [Comment : parcourir une énumération dans Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="d5a14-128"> [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span></span>  
<span data-ttu-id="d5a14-129"> [Comment : déterminer la chaîne associée à une valeur d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span><span class="sxs-lookup"><span data-stu-id="d5a14-129"> [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span></span>  
<span data-ttu-id="d5a14-130"> [Enum, instruction](../../../../visual-basic/language-reference/statements/enum-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d5a14-130"> [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md) </span></span>  
<span data-ttu-id="d5a14-131"> [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="d5a14-131"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
