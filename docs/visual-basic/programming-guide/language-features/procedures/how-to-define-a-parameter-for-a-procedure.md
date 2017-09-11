---
title: "Comment : définir un paramètre pour une procédure (Visual Basic) | Documents Microsoft"
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
- procedure parameters, defining data types for
- procedures, parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters, defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
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
ms.openlocfilehash: 5a29bab1c18920d293c51d83d4d8cffdcefe936c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a><span data-ttu-id="2c1c3-102">Comment : définir un paramètre pour une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c1c3-102">How to: Define a Parameter for a Procedure (Visual Basic)</span></span>
<span data-ttu-id="2c1c3-103">A *paramètre* permet au code appelant de passer une valeur à la procédure lorsqu’il l’appelle.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-103">A *parameter* allows the calling code to pass a value to the procedure when it calls it.</span></span> <span data-ttu-id="2c1c3-104">Vous déclarez chaque paramètre pour une procédure de la même manière que vous déclarez une variable, en spécifiant son nom et type de données.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-104">You declare each parameter for a procedure the same way you declare a variable, specifying its name and data type.</span></span> <span data-ttu-id="2c1c3-105">Vous spécifiez également le mécanisme de passage et si le paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-105">You also specify the passing mechanism, and whether the parameter is optional.</span></span>  
  
 <span data-ttu-id="2c1c3-106">Pour plus d’informations, consultez [paramètres de procédure et les Arguments](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="2c1c3-106">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-define-a-procedure-parameter"></a><span data-ttu-id="2c1c3-107">Pour définir un paramètre de procédure</span><span class="sxs-lookup"><span data-stu-id="2c1c3-107">To define a procedure parameter</span></span>  
  
1.  <span data-ttu-id="2c1c3-108">Dans la déclaration de procédure, ajoutez le nom du paramètre à la liste de paramètres de la procédure, en le séparant des autres paramètres par des virgules.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-108">In the procedure declaration, add the parameter name to the procedure's parameter list, separating it from other parameters by commas.</span></span>  
  
2.  <span data-ttu-id="2c1c3-109">Déterminez le type de données du paramètre.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-109">Decide the data type of the parameter.</span></span>  
  
3.  <span data-ttu-id="2c1c3-110">Suivre le nom du paramètre avec une `As` clause pour spécifier le type de données.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-110">Follow the parameter name with an `As` clause to specify the data type.</span></span>  
  
4.  <span data-ttu-id="2c1c3-111">Choisissez le mécanisme de passage souhaité pour le paramètre.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-111">Decide the passing mechanism you want for the parameter.</span></span> <span data-ttu-id="2c1c3-112">Normalement, vous passez un paramètre par valeur, sauf si vous souhaitez que la procédure puisse modifier sa valeur dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-112">Normally you pass a parameter by value, unless you want the procedure to be able to change its value in the calling code.</span></span>  
  
5.  <span data-ttu-id="2c1c3-113">Faites précéder le nom de paramètre avec [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) pour spécifier le mécanisme de passage.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-113">Precede the parameter name with [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) to specify the passing mechanism.</span></span> <span data-ttu-id="2c1c3-114">Pour plus d’informations, consultez [différences entre passage d’un Argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="2c1c3-114">For more information, see [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
6.  <span data-ttu-id="2c1c3-115">Si le paramètre est facultatif, faites précéder le mécanisme de passage de [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md) et suivez le type de données de paramètre d’un signe égal (`=`) et une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-115">If the parameter is optional, precede the passing mechanism with [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) and follow the parameter data type with an equal sign (`=`) and a default value.</span></span>  
  
     <span data-ttu-id="2c1c3-116">L’exemple suivant définit le contour d’un `Sub` procédure avec trois paramètres.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-116">The following example defines the outline of a `Sub` procedure with three parameters.</span></span> <span data-ttu-id="2c1c3-117">Les deux premiers sont requis et le troisième est facultatif.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-117">The first two are required and the third is optional.</span></span> <span data-ttu-id="2c1c3-118">Les déclarations de paramètre sont séparées dans la liste de paramètres par des virgules.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-118">The parameter declarations are separated in the parameter list by commas.</span></span>  
  
     <span data-ttu-id="2c1c3-119">[!code-vb[VbVbcnProcedures&#33;](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2c1c3-119">[!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="2c1c3-120">Le premier paramètre accepte un `customer` objet, et `updateCustomer` pouvez mettre directement à jour la variable passée à `c` , car l’argument est passé [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span><span class="sxs-lookup"><span data-stu-id="2c1c3-120">The first parameter accepts a `customer` object, and `updateCustomer` can directly update the variable passed to `c` because the argument is passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="2c1c3-121">La procédure ne peut pas modifier les valeurs des deux derniers arguments parce qu’ils sont passés [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="2c1c3-121">The procedure cannot change the values of the last two arguments because they are passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
     <span data-ttu-id="2c1c3-122">Si le code appelant ne fournit pas une valeur pour le `level` paramètre [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] lui affecte la valeur par défaut 0.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-122">If the calling code does not supply a value for the `level` parameter, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sets it to the default value of 0.</span></span>  
  
     <span data-ttu-id="2c1c3-123">Si le commutateur de la vérification de type ([Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est `Off`, le `As` clause est facultative lorsque vous définissez un paramètre.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-123">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off`, the `As` clause is optional when you define a parameter.</span></span> <span data-ttu-id="2c1c3-124">Toutefois, si un paramètre utilise une `As` clause, tous doivent l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-124">However, if any one parameter uses an `As` clause, all of them must use it.</span></span> <span data-ttu-id="2c1c3-125">Si le commutateur de vérification de type est `On`, le `As` clause est requise pour chaque définition de paramètre.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-125">If the type checking switch is `On`, the `As` clause is required for every parameter definition.</span></span>  
  
     <span data-ttu-id="2c1c3-126">Spécifier les types de données pour tous les éléments de programmation est appelé *typage fort*.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-126">Specifying data types for all your programming elements is known as *strong typing*.</span></span> <span data-ttu-id="2c1c3-127">Lorsque vous définissez `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] applique un typage fort.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-127">When you set `Option Strict On`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] enforces strong typing.</span></span> <span data-ttu-id="2c1c3-128">Il est fortement recommandé, pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="2c1c3-128">This is strongly recommended, for the following reasons:</span></span>  
  
    -   <span data-ttu-id="2c1c3-129">Il permet la prise en charge IntelliSense pour vos variables et des paramètres.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-129">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="2c1c3-130">Cela vous permet de voir leurs propriétés et autres membres que vous entrez dans votre code.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-130">This allows you to see their properties and other members as you type in your code.</span></span>  
  
    -   <span data-ttu-id="2c1c3-131">Il permet au compilateur d’effectuer la vérification du type.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-131">It allows the compiler to perform type checking.</span></span> <span data-ttu-id="2c1c3-132">Cela permet d’intercepter les instructions peuvent échouer au moment de l’exécution en raison d’erreurs de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-132">This helps catch statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="2c1c3-133">Il intercepte également les appels aux méthodes sur les objets qui ne les prennent pas en charge.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-133">It also catches calls to methods on objects that do not support them.</span></span>  
  
    -   <span data-ttu-id="2c1c3-134">Il en résulte une exécution plus rapide de votre code.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-134">It results in faster execution of your code.</span></span> <span data-ttu-id="2c1c3-135">L’une des raisons sont que si vous ne spécifiez pas un type de données pour un élément de programmation, le [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur lui assigne la `Object` type.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-135">One reason for this is that if you do not specify a data type for a programming element, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler assigns it the `Object` type.</span></span> <span data-ttu-id="2c1c3-136">Votre code compilé peut avoir à convertir entre `Object` et d’autres types de données, ce qui réduit les performances.</span><span class="sxs-lookup"><span data-stu-id="2c1c3-136">Your compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c1c3-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c1c3-137">See Also</span></span>  
 <span data-ttu-id="2c1c3-138">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="2c1c3-138">[Procedures](./index.md) </span></span>  
<span data-ttu-id="2c1c3-139"> [Procédures Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="2c1c3-139"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="2c1c3-140"> [Procédures Function](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="2c1c3-140"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="2c1c3-141"> [Comment : passer des Arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="2c1c3-141"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="2c1c3-142"> [Passage des Arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2c1c3-142"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="2c1c3-143"> [Procédures récursives](./recursive-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="2c1c3-143"> [Recursive Procedures](./recursive-procedures.md) </span></span>  
<span data-ttu-id="2c1c3-144"> [Surcharge de procédure](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="2c1c3-144"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="2c1c3-145"> [Objets et Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="2c1c3-145"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="2c1c3-146"> [Programmation orientée objet](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span><span class="sxs-lookup"><span data-stu-id="2c1c3-146"> [Object-Oriented Programming](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span></span>
