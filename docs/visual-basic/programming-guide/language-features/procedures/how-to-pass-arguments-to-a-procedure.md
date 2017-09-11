---
title: "Comment : passer des Arguments à une procédure (Visual Basic) | Documents Microsoft"
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
- arguments [Visual Basic], passing to procedures
- procedures, arguments
- procedures, parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures, calling
- argument passing, procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
caps.latest.revision: 14
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
ms.openlocfilehash: 1e0a8d5e798f25f22f53f56a7c01bd69e3e14463
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="99893-102">Comment : passer des arguments à une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99893-102">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>
<span data-ttu-id="99893-103">Lorsque vous appelez une procédure, vous suivez le nom de la procédure avec une liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="99893-103">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="99893-104">Vous fournissez un argument correspondant à chaque paramètre requis que la procédure définit et vous pouvez éventuellement fournir des arguments à le `Optional` paramètres.</span><span class="sxs-lookup"><span data-stu-id="99893-104">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="99893-105">Si vous ne fournissez pas une `Optional` paramètre dans l’appel, vous devez inclure une virgule pour marquer sa place dans la liste d’arguments si vous fournissez des arguments suivants.</span><span class="sxs-lookup"><span data-stu-id="99893-105">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="99893-106">Si vous souhaitez passer un argument d’un type de données différent de celui de son paramètre correspondant, tel que `Byte` à `String`, vous pouvez définir le commutateur de vérification de type ([Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) à `Off`.</span><span class="sxs-lookup"><span data-stu-id="99893-106">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="99893-107">Si `Option Strict` est `On`, vous devez utiliser l’élargissement des conversions ou des mots clés de conversion explicite.</span><span class="sxs-lookup"><span data-stu-id="99893-107">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="99893-108">Pour plus d’informations, consultez [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) et [les fonctions de Conversion de Type](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="99893-108">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="99893-109">Pour plus d’informations, consultez [paramètres de procédure et les Arguments](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="99893-109">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="99893-110">Pour passer un ou plusieurs arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="99893-110">To pass one or more arguments to a procedure</span></span>  
  
1.  <span data-ttu-id="99893-111">Dans l’instruction appelante, suivre le nom de la procédure entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="99893-111">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2.  <span data-ttu-id="99893-112">À l’intérieur des parenthèses, placez une liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="99893-112">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="99893-113">Inclure un argument pour chaque paramètre requis que la procédure définit et séparez les arguments par des virgules.</span><span class="sxs-lookup"><span data-stu-id="99893-113">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3.  <span data-ttu-id="99893-114">Assurez-vous que chaque argument est une expression valide qui correspond à un type de données convertible au type de la procédure définit pour le paramètre correspondant.</span><span class="sxs-lookup"><span data-stu-id="99893-114">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4.  <span data-ttu-id="99893-115">Si un paramètre est défini en tant que [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md), vous pouvez inclure dans la liste d’arguments ou l’omettre.</span><span class="sxs-lookup"><span data-stu-id="99893-115">If a parameter is defined as [Optional](../../../../visual-basic/language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="99893-116">Si vous l’omettez, la procédure utilise la valeur par défaut définie pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="99893-116">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5.  <span data-ttu-id="99893-117">Si vous omettez un argument pour un `Optional` paramètre et qu’un autre paramètre après lui dans la liste de paramètres, vous pouvez marquer la place de l’argument omis par une virgule supplémentaire dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="99893-117">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="99893-118">L’exemple suivant appelle la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>fonction.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A></span><span class="sxs-lookup"><span data-stu-id="99893-118">The following example calls the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     <span data-ttu-id="99893-119">[!code-vb[VbVbcnProcedures&#34;](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="99893-119">[!code-vb[VbVbcnProcedures#34](./codesnippet/VisualBasic/how-to-pass-arguments-to-a-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="99893-120">L’exemple précédent fournit le premier argument requis, qui est la chaîne de message à afficher.</span><span class="sxs-lookup"><span data-stu-id="99893-120">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="99893-121">Omet un argument pour le second paramètre facultatif qui spécifie les boutons à afficher dans la boîte de message.</span><span class="sxs-lookup"><span data-stu-id="99893-121">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="99893-122">Étant donné que l’appel ne fournit pas de valeur, `MsgBox` utilise la valeur par défaut, `MsgBoxStyle.OKOnly`, qui affiche uniquement une **OK** bouton.</span><span class="sxs-lookup"><span data-stu-id="99893-122">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="99893-123">La deuxième virgule dans la liste d’arguments marque la place du deuxième argument omis et la dernière chaîne est passée au troisième paramètre facultatif de `MsgBox`, qui représente le texte à afficher dans la barre de titre.</span><span class="sxs-lookup"><span data-stu-id="99893-123">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99893-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99893-124">See Also</span></span>  
 <span data-ttu-id="99893-125">[Procédures Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="99893-125">[Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="99893-126"> [Procédures Function](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="99893-126"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="99893-127"> [Procédures de propriété](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="99893-127"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="99893-128"> [Procédures d’opérateur](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="99893-128"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="99893-129"> [Comment : définir un paramètre pour une procédure](./how-to-define-a-parameter-for-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="99893-129"> [How to: Define a Parameter for a Procedure](./how-to-define-a-parameter-for-a-procedure.md) </span></span>  
<span data-ttu-id="99893-130"> [Passage des Arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="99893-130"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="99893-131"> [Procédures récursives](./recursive-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="99893-131"> [Recursive Procedures](./recursive-procedures.md) </span></span>  
<span data-ttu-id="99893-132"> [Surcharge de procédure](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="99893-132"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="99893-133"> [Objets et Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="99893-133"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="99893-134"> [Programmation orientée objet](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span><span class="sxs-lookup"><span data-stu-id="99893-134"> [Object-Oriented Programming](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)</span></span>
