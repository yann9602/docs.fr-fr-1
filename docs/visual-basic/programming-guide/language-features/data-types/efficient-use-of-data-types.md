---
title: "Utilisation efficace des Types de données (Visual Basic) | Documents Microsoft"
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
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function, preferred to Asc
- data types [Visual Basic], using efficiently
- optimization, data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function, preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: 16
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
ms.openlocfilehash: ca8d5885aea12a3f1f9cb35f08bf63c1a89e7ebc
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="fffc0-102">Utilisation efficace des types de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fffc0-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="fffc0-103">Les variables non déclarées et les variables déclarées sans type de données sont affectés les `Object` type de données.</span><span class="sxs-lookup"><span data-stu-id="fffc0-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="fffc0-104">Cela rend plus facile d’écrire rapidement des programmes, mais il peut les rendre à s’exécuter plus lentement.</span><span class="sxs-lookup"><span data-stu-id="fffc0-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>  
  
## <a name="strong-typing"></a><span data-ttu-id="fffc0-105">Le typage fort</span><span class="sxs-lookup"><span data-stu-id="fffc0-105">Strong Typing</span></span>  
 <span data-ttu-id="fffc0-106">Spécifier les types de données pour toutes les variables est appelé *typage fort*.</span><span class="sxs-lookup"><span data-stu-id="fffc0-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="fffc0-107">Le typage fort présente plusieurs avantages :</span><span class="sxs-lookup"><span data-stu-id="fffc0-107">Using strong typing has several advantages:</span></span>  
  
-   <span data-ttu-id="fffc0-108">Il permet la prise en charge IntelliSense pour vos variables.</span><span class="sxs-lookup"><span data-stu-id="fffc0-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="fffc0-109">Cela vous permet de voir leurs propriétés et autres membres que vous entrez dans le code.</span><span class="sxs-lookup"><span data-stu-id="fffc0-109">This allows you to see their properties and other members as you type in the code.</span></span>  
  
-   <span data-ttu-id="fffc0-110">Il tire parti de la vérification du type du compilateur.</span><span class="sxs-lookup"><span data-stu-id="fffc0-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="fffc0-111">Il intercepte les instructions qui peuvent échouer au moment de l’exécution en raison d’erreurs de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="fffc0-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="fffc0-112">Il intercepte également les appels aux méthodes sur les objets qui ne les prennent pas en charge.</span><span class="sxs-lookup"><span data-stu-id="fffc0-112">It also catches calls to methods on objects that do not support them.</span></span>  
  
-   <span data-ttu-id="fffc0-113">Il en résulte une exécution plus rapide de votre code.</span><span class="sxs-lookup"><span data-stu-id="fffc0-113">It results in faster execution of your code.</span></span>  
  
## <a name="most-efficient-data-types"></a><span data-ttu-id="fffc0-114">Types de données plus efficaces</span><span class="sxs-lookup"><span data-stu-id="fffc0-114">Most Efficient Data Types</span></span>  
 <span data-ttu-id="fffc0-115">Pour les variables qui ne contiennent jamais de fractions, les types de données intégraux sont plus efficaces que les types intégraux.</span><span class="sxs-lookup"><span data-stu-id="fffc0-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="fffc0-116">Dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], `Integer` et `UInteger` sont les types numériques plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="fffc0-116">In [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], `Integer` and `UInteger` are the most efficient numeric types.</span></span>  
  
 <span data-ttu-id="fffc0-117">Pour les nombres fractionnaires, `Double` est le type de données plus efficace, car les processeurs des plateformes actuelles exécutent des opérations en virgule flottante en double précision.</span><span class="sxs-lookup"><span data-stu-id="fffc0-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="fffc0-118">Toutefois, les opérations avec `Double` ne sont pas aussi rapides qu’avec les types intégraux, tels que `Integer`.</span><span class="sxs-lookup"><span data-stu-id="fffc0-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
## <a name="specifying-data-type"></a><span data-ttu-id="fffc0-119">Spécification du Type de données</span><span class="sxs-lookup"><span data-stu-id="fffc0-119">Specifying Data Type</span></span>  
 <span data-ttu-id="fffc0-120">Utilisez le [une instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pour déclarer une variable d’un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="fffc0-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="fffc0-121">Vous pouvez spécifier simultanément son niveau d’accès à l’aide de la [Public](../../../../visual-basic/language-reference/modifiers/public.md), [protégé](../../../../visual-basic/language-reference/modifiers/protected.md), [ami](../../../../visual-basic/language-reference/modifiers/friend.md), ou [privé](../../../../visual-basic/language-reference/modifiers/private.md) (mot clé), comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="fffc0-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a><span data-ttu-id="fffc0-122">Conversion de caractères</span><span class="sxs-lookup"><span data-stu-id="fffc0-122">Character Conversion</span></span>  
 <span data-ttu-id="fffc0-123">Le `AscW` et `ChrW` fonctions opèrent en Unicode.</span><span class="sxs-lookup"><span data-stu-id="fffc0-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="fffc0-124">Vous devez les utiliser de préférence à `Asc` et `Chr`, qui doivent traduire dans et hors d’Unicode.</span><span class="sxs-lookup"><span data-stu-id="fffc0-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fffc0-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fffc0-125">See Also</span></span>  
 <span data-ttu-id="fffc0-126"><xref:Microsoft.VisualBasic.Strings.Asc%2A></xref:Microsoft.VisualBasic.Strings.Asc%2A></span><span class="sxs-lookup"><span data-stu-id="fffc0-126"><xref:Microsoft.VisualBasic.Strings.Asc%2A></span></span>   
 <span data-ttu-id="fffc0-127"><xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A></span><span class="sxs-lookup"><span data-stu-id="fffc0-127"><xref:Microsoft.VisualBasic.Strings.AscW%2A></span></span>   
 <span data-ttu-id="fffc0-128"><xref:Microsoft.VisualBasic.Strings.Chr%2A></xref:Microsoft.VisualBasic.Strings.Chr%2A></span><span class="sxs-lookup"><span data-stu-id="fffc0-128"><xref:Microsoft.VisualBasic.Strings.Chr%2A></span></span>   
 <span data-ttu-id="fffc0-129"><xref:Microsoft.VisualBasic.Strings.ChrW%2A></xref:Microsoft.VisualBasic.Strings.ChrW%2A></span><span class="sxs-lookup"><span data-stu-id="fffc0-129"><xref:Microsoft.VisualBasic.Strings.ChrW%2A></span></span>   
<span data-ttu-id="fffc0-130"> [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="fffc0-130"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="fffc0-131"> [Types de données numériques](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="fffc0-131"> [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md) </span></span>  
<span data-ttu-id="fffc0-132"> [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="fffc0-132"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="fffc0-133"> [Utilisation de la fonctionnalité IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense)</span><span class="sxs-lookup"><span data-stu-id="fffc0-133"> [Using IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense)</span></span>
