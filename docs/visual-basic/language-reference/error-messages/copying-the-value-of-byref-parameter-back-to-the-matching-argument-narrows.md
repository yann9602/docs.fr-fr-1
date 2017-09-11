---
title: "Copie de la valeur du paramètre &quot;ByRef&quot; &quot;&lt;parametername&gt;&quot;dans l’argument correspondant passe du type&quot;&lt;NomType1&gt;&quot; en type&quot;&lt;NomType2&gt;&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32053
- vbc32053
dev_langs:
- VB
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
caps.latest.revision: 8
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
ms.openlocfilehash: 10ad4af689c11f3e4defe43c4fed9ed579ba5305
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument-narrows-from-type-39lttypename1gt39-to-type-39lttypename2gt39"></a><span data-ttu-id="e2176-102">Copie de la valeur du paramètre 'ByRef' '&lt;parametername&gt;'dans l’argument correspondant passe du type'&lt;NomType1&gt;' en type'&lt;NomType2&gt;»</span><span class="sxs-lookup"><span data-stu-id="e2176-102">Copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument narrows from type &#39;&lt;typename1&gt;&#39; to type &#39;&lt;typename2&gt;&#39;</span></span>
<span data-ttu-id="e2176-103">Une procédure est appelée avec un argument qui s’étend au type de paramètre correspondant, et la conversion du paramètre à l’argument est restrictive.</span><span class="sxs-lookup"><span data-stu-id="e2176-103">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>  
  
 <span data-ttu-id="e2176-104">Quand vous définissez une classe ou une structure, vous pouvez définir un ou plusieurs opérateurs de conversion pour convertir le type de la classe ou de la structure en d’autres types.</span><span class="sxs-lookup"><span data-stu-id="e2176-104">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="e2176-105">Vous pouvez également définir des opérateurs de conversion inverse pour convertir ces autres types vers le type de votre classe ou de votre structure.</span><span class="sxs-lookup"><span data-stu-id="e2176-105">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="e2176-106">Lorsque vous utilisez votre type de classe ou de structure dans un appel de procédure, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] peut utiliser ces opérateurs de conversion pour convertir le type d’un argument pour le type de son paramètre correspondant.</span><span class="sxs-lookup"><span data-stu-id="e2176-106">When you use your class or structure type in a procedure call, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="e2176-107">Si vous passez l’argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copie parfois sa valeur dans une variable locale de la procédure au lieu de passer une référence.</span><span class="sxs-lookup"><span data-stu-id="e2176-107">If you pass the argument [ByRef](../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="e2176-108">Dans ce cas, la procédure retourne [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit copier la valeur de variable locale dans l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="e2176-108">In such a case, when the procedure returns, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="e2176-109">Si une valeur d’argument `ByRef` est copiée dans la procédure, et si l’argument et le paramètre sont du même type, aucune conversion n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e2176-109">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="e2176-110">Mais si les types sont différents, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit convertir dans les deux sens.</span><span class="sxs-lookup"><span data-stu-id="e2176-110">But if the types are different, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must convert in both directions.</span></span> <span data-ttu-id="e2176-111">Si un des types est votre type de classe ou structure, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit le convertir vers et à partir de l’autre type.</span><span class="sxs-lookup"><span data-stu-id="e2176-111">If one of the types is your class or structure type, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must convert it both to and from the other type.</span></span> <span data-ttu-id="e2176-112">Si une de ces conversions est étendue, la conversion inverse peut être restrictive.</span><span class="sxs-lookup"><span data-stu-id="e2176-112">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>  
  
 <span data-ttu-id="e2176-113">**ID d’erreur :** BC32053</span><span class="sxs-lookup"><span data-stu-id="e2176-113">**Error ID:** BC32053</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e2176-114">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e2176-114">To correct this error</span></span>  
  
-   <span data-ttu-id="e2176-115">Si possible, utilisez un argument d’appel du même type que le paramètre de procédure, par conséquent, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne doit pas effectuer de conversion.</span><span class="sxs-lookup"><span data-stu-id="e2176-115">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="e2176-116">Si vous avez besoin d’appeler la procédure avec un argument de type différent du type de paramètre, mais n’avez pas besoin de retourner une valeur dans l’argument d’appel, de définir le paramètre pour être [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) au lieu de `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="e2176-116">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
-   <span data-ttu-id="e2176-117">Si vous devez retourner une valeur dans l’argument d’appel, définir l’opérateur de conversion inverse [Widening](../../../visual-basic/language-reference/modifiers/widening.md), si possible.</span><span class="sxs-lookup"><span data-stu-id="e2176-117">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../../../visual-basic/language-reference/modifiers/widening.md), if possible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2176-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2176-118">See Also</span></span>  
 <span data-ttu-id="e2176-119">[Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span><span class="sxs-lookup"><span data-stu-id="e2176-119">[Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span></span>  
<span data-ttu-id="e2176-120"> [Arguments et paramètres de procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="e2176-120"> [Procedure Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="e2176-121"> [Passage des Arguments par valeur et par référence](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="e2176-121"> [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="e2176-122"> [Procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="e2176-122"> [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md) </span></span>  
<span data-ttu-id="e2176-123"> [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e2176-123"> [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="e2176-124"> [Comment : définir un opérateur](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="e2176-124"> [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="e2176-125"> [Comment : définir un opérateur de Conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="e2176-125"> [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="e2176-126"> [Conversions de type dans Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="e2176-126"> [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="e2176-127"> [Conversions étendues et restrictives](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="e2176-127"> [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span></span>
