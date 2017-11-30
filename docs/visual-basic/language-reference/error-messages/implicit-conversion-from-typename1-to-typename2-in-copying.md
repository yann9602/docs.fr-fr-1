---
title: "Conversion implicite de &#39; &lt;nom_type1&gt;&#39; à &#39;&lt; nom_type2&gt;&#39; lors de la copie de la valeur des &#39; ByRef &#39; paramètre &#39; &lt;nom_paramètre&gt;&#39; retour à l’argument correspondant."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords: BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e858b475a816a35d18822643de5a273abe28562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a><span data-ttu-id="98fd6-102">Conversion implicite de &#39; &lt;nom_type1&gt;&#39; à &#39;&lt; nom_type2&gt;&#39; lors de la copie de la valeur des &#39; ByRef &#39; paramètre &#39; &lt;nom_paramètre&gt;&#39; retour à l’argument correspondant.</span><span class="sxs-lookup"><span data-stu-id="98fd6-102">Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.</span></span>
<span data-ttu-id="98fd6-103">Une procédure est appelée avec un [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument d’un type différent de celui de son paramètre correspondant.</span><span class="sxs-lookup"><span data-stu-id="98fd6-103">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="98fd6-104">Si vous passez un argument `ByRef`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] copie parfois la valeur d’argument dans une variable locale de la procédure au lieu de passer une référence.</span><span class="sxs-lookup"><span data-stu-id="98fd6-104">If you pass an argument `ByRef`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="98fd6-105">Dans ce cas, quand la procédure est retournée, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doit recopier la valeur de la variable locale dans l’argument du code appelant.</span><span class="sxs-lookup"><span data-stu-id="98fd6-105">In such a case, when the procedure returns, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="98fd6-106">Si une valeur d’argument `ByRef` est copiée dans la procédure, et si l’argument et le paramètre sont du même type, aucune conversion n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="98fd6-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="98fd6-107">Toutefois, si les types sont différents, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doit effectuer une conversion dans les deux sens.</span><span class="sxs-lookup"><span data-stu-id="98fd6-107">But if the types are different, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must convert in both directions.</span></span> <span data-ttu-id="98fd6-108">Étant donné que vous ne pouvez pas utiliser `CType` ou une des autres mots clés de conversion sur un argument de procédure ou de paramètre, une telle conversion est toujours implicite.</span><span class="sxs-lookup"><span data-stu-id="98fd6-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="98fd6-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="98fd6-109">By default, this message is a warning.</span></span> <span data-ttu-id="98fd6-110">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="98fd6-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="98fd6-111">**ID d’erreur :** BC41999</span><span class="sxs-lookup"><span data-stu-id="98fd6-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="98fd6-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="98fd6-112">To correct this error</span></span>  
  
-   <span data-ttu-id="98fd6-113">Si possible, utilisez un argument d’appel du même type que celui du paramètre de procédure, pour que [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] n’ait pas besoin d’effectuer de conversion.</span><span class="sxs-lookup"><span data-stu-id="98fd6-113">If possible, use a calling argument of the same type as the procedure parameter, so [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="98fd6-114">Si vous avez besoin d’appeler la procédure avec un argument de type différent du type de paramètre, mais n’avez pas besoin de retourner une valeur dans l’argument d’appel, définissez le paramètre [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) au lieu de `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="98fd6-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98fd6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98fd6-115">See Also</span></span>  
 [<span data-ttu-id="98fd6-116">Procédures</span><span class="sxs-lookup"><span data-stu-id="98fd6-116">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="98fd6-117">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="98fd6-117">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="98fd6-118">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="98fd6-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="98fd6-119">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="98fd6-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
