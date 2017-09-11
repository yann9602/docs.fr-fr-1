---
title: "Conversion implicite de &quot;&lt;NomType1&gt;&quot;à&quot;&lt;NomType2&gt;« en copiant la valeur du paramètre &quot;ByRef&quot; &quot;&lt;parametername&gt;&quot; dans l’argument correspondant. | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
dev_langs:
- VB
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: 7
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
ms.openlocfilehash: 0d69bc5074ed5ef2f58010b3477752d3aa6a4b26
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a><span data-ttu-id="9f52d-103">Conversion implicite de '&lt;NomType1&gt;'à'&lt;NomType2&gt;« en copiant la valeur du paramètre 'ByRef' '&lt;parametername&gt;' dans l’argument correspondant.</span><span class="sxs-lookup"><span data-stu-id="9f52d-103">Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.</span></span>
<span data-ttu-id="9f52d-104">Une procédure est appelée avec un [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument d’un type différent de celui de son paramètre correspondant.</span><span class="sxs-lookup"><span data-stu-id="9f52d-104">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="9f52d-105">Si vous passez un argument `ByRef`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copie parfois sa valeur dans une variable locale de la procédure au lieu de passer une référence.</span><span class="sxs-lookup"><span data-stu-id="9f52d-105">If you pass an argument `ByRef`, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="9f52d-106">Dans ce cas, la procédure retourne [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit copier la valeur de variable locale dans l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="9f52d-106">In such a case, when the procedure returns, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="9f52d-107">Si une valeur d’argument `ByRef` est copiée dans la procédure, et si l’argument et le paramètre sont du même type, aucune conversion n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9f52d-107">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="9f52d-108">Mais si les types sont différents, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit convertir dans les deux sens.</span><span class="sxs-lookup"><span data-stu-id="9f52d-108">But if the types are different, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] must convert in both directions.</span></span> <span data-ttu-id="9f52d-109">Étant donné que vous ne pouvez pas utiliser `CType` ou un des autres mots clés de conversion sur un argument de procédure ou de paramètre, une telle conversion est toujours implicite.</span><span class="sxs-lookup"><span data-stu-id="9f52d-109">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="9f52d-110">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="9f52d-110">By default, this message is a warning.</span></span> <span data-ttu-id="9f52d-111">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9f52d-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="9f52d-112">**ID d’erreur :** BC41999</span><span class="sxs-lookup"><span data-stu-id="9f52d-112">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9f52d-113">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="9f52d-113">To correct this error</span></span>  
  
-   <span data-ttu-id="9f52d-114">Si possible, utilisez un argument d’appel du même type que le paramètre de procédure, par conséquent, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne doit pas effectuer de conversion.</span><span class="sxs-lookup"><span data-stu-id="9f52d-114">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="9f52d-115">Si vous avez besoin d’appeler la procédure avec un argument de type différent du type de paramètre, mais n’avez pas besoin de retourner une valeur dans l’argument d’appel, de définir le paramètre pour être [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) au lieu de `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="9f52d-115">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f52d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f52d-116">See Also</span></span>  
 <span data-ttu-id="9f52d-117">[Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span><span class="sxs-lookup"><span data-stu-id="9f52d-117">[Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span></span>  
<span data-ttu-id="9f52d-118"> [Arguments et paramètres de procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="9f52d-118"> [Procedure Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="9f52d-119"> [Passage des Arguments par valeur et par référence](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="9f52d-119"> [Passing Arguments by Value and by Reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="9f52d-120"> [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="9f52d-120"> [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)</span></span>
