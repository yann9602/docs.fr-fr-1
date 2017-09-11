---
title: "Comment : créer une Variable (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Dim statement
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: 29
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 3b5aa4e5e0b84f41ac3df73bc70d8402d10b21a2
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="302db-102">Comment : créer une variable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="302db-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="302db-103">Vous créez une variable avec un [une instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="302db-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="302db-104">Pour créer une variable</span><span class="sxs-lookup"><span data-stu-id="302db-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="302db-105">Déclarez la variable dans une `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="302db-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="302db-106">Incluent des spécifications pour les caractéristiques de la variable, comme [privé](../../../../visual-basic/language-reference/modifiers/private.md), [statique](../../../../visual-basic/language-reference/modifiers/static.md), [ombres](../../../../visual-basic/language-reference/modifiers/shadows.md), ou [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="302db-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="302db-107">Pour plus d’informations, consultez [caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="302db-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="302db-108">Vous n’avez pas besoin du `Dim` (mot clé) si vous utilisez d’autres mots clés dans la déclaration.</span><span class="sxs-lookup"><span data-stu-id="302db-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="302db-109">Suivez les spécifications de nom de la variable, qui doit respecter [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] règles et conventions.</span><span class="sxs-lookup"><span data-stu-id="302db-109">Follow the specifications with the variable's name, which must follow [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] rules and conventions.</span></span> <span data-ttu-id="302db-110">Pour plus d’informations, consultez [noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="302db-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="302db-111">Suivre le nom de la [comme](../../../../visual-basic/language-reference/statements/as-clause.md) clause pour spécifier le type de données de la variable.</span><span class="sxs-lookup"><span data-stu-id="302db-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="302db-112">Si vous ne spécifiez pas le type de données, il utilise la valeur par défaut : `Object`.</span><span class="sxs-lookup"><span data-stu-id="302db-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="302db-113">Suivez les `As` clause par un signe égal (`=`) et suivez le signe égal de la valeur initiale de la variable.</span><span class="sxs-lookup"><span data-stu-id="302db-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="302db-114">assigne la valeur spécifiée à la variable chaque fois qu’il exécute la `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="302db-114"> assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="302db-115">Si vous ne spécifiez pas de valeur initiale, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] assigne la valeur initiale par défaut pour le type de données de la variable lorsqu’il pénètre dans le code qui contient la `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="302db-115">If you do not specify an initial value, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="302db-116">Si la variable est un type référence, vous pouvez créer une instance de sa classe en incluant le [nouveau opérateur](../../../../visual-basic/language-reference/operators/new-operator.md) mot clé dans le `As` clause.</span><span class="sxs-lookup"><span data-stu-id="302db-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="302db-117">Si vous n’utilisez pas `New`, la valeur initiale de la variable est [rien](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="302db-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="302db-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="302db-118">See Also</span></span>  
 <span data-ttu-id="302db-119">[Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span><span class="sxs-lookup"><span data-stu-id="302db-119">[Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md) </span></span>  
<span data-ttu-id="302db-120"> [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="302db-120"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="302db-121"> [Noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="302db-121"> [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="302db-122"> [Caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="302db-122"> [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span></span>  
<span data-ttu-id="302db-123"> [Types valeur et Types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="302db-123"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="302db-124"> [Instructions](../../../../visual-basic/language-reference/statements/index.md) </span><span class="sxs-lookup"><span data-stu-id="302db-124"> [Statements](../../../../visual-basic/language-reference/statements/index.md) </span></span>  
<span data-ttu-id="302db-125"> [Inférence de Type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="302db-125"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="302db-126"> [Option Infer (instruction)](../../../../visual-basic/language-reference/statements/option-infer-statement.md)</span><span class="sxs-lookup"><span data-stu-id="302db-126"> [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)</span></span>

