---
title: "La résolution de surcharge à liaison tardive ne peut pas être appliquée à &#39; &lt;nom_procédure&gt;&#39; car l’instance d’accès est un type interface"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb7f8a9f6eadfc9fd856ea57d362b43d25ff81a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-39ltprocedurenamegt39-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="e1d66-102">La résolution de surcharge à liaison tardive ne peut pas être appliquée à &#39; &lt;nom_procédure&gt;&#39; car l’instance d’accès est un type interface</span><span class="sxs-lookup"><span data-stu-id="e1d66-102">Latebound overload resolution cannot be applied to &#39;&lt;procedurename&gt;&#39; because the accessing instance is an interface type</span></span>
<span data-ttu-id="e1d66-103">Le compilateur tente de résoudre une référence à une propriété surchargée ou une procédure, mais la référence échoue parce qu’un argument est de type `Object` et l’objet de référence a le type de données d’une interface.</span><span class="sxs-lookup"><span data-stu-id="e1d66-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="e1d66-104">Le `Object` argument force le compilateur à résoudre la référence en tant qu’à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="e1d66-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>  
  
 <span data-ttu-id="e1d66-105">Dans ces circonstances, le compilateur résout la surcharge via la classe d’implémentation à la place de l’interface sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="e1d66-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="e1d66-106">Si la classe renomme l’une des versions surchargées, le compilateur ne tient pas compte de cette version comme une surcharge car son nom est différent.</span><span class="sxs-lookup"><span data-stu-id="e1d66-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="e1d66-107">Le compilateur ignore la version renommée lorsque le bon choix pour résoudre la référence peut avoir été alors à son tour.</span><span class="sxs-lookup"><span data-stu-id="e1d66-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>  
  
 <span data-ttu-id="e1d66-108">**ID d’erreur :** BC30933</span><span class="sxs-lookup"><span data-stu-id="e1d66-108">**Error ID:** BC30933</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e1d66-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e1d66-109">To correct this error</span></span>  
  
-   <span data-ttu-id="e1d66-110">Utilisez `CType` pour effectuer un cast de l’argument de `Object` au type spécifié par la signature de la surcharge que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="e1d66-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>  
  
     <span data-ttu-id="e1d66-111">Notez qu’il ne permet pas d’effectuer un cast de l’objet de référence à l’interface sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="e1d66-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="e1d66-112">Vous devez effectuer un cast de l’argument pour éviter cette erreur.</span><span class="sxs-lookup"><span data-stu-id="e1d66-112">You must cast the argument to avoid this error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1d66-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1d66-113">Example</span></span>  
 <span data-ttu-id="e1d66-114">L’exemple suivant montre un appel à une procédure surchargée `Sub` procédure qui provoque cette erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="e1d66-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 <span data-ttu-id="e1d66-115">Dans l’exemple précédent, si le compilateur a autorisé l’appel à `s1` lors de l’écriture, la résolution a lieu via la classe `c1` au lieu de l’interface `i1`.</span><span class="sxs-lookup"><span data-stu-id="e1d66-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="e1d66-116">Cela signifie que le compilateur ne tient pas compte `s2` , car son nom est différent dans `c1`, même s’il est le bon choix, comme défini par `i1`.</span><span class="sxs-lookup"><span data-stu-id="e1d66-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>  
  
 <span data-ttu-id="e1d66-117">Vous pouvez corriger l’erreur en modifiant l’appel à une des lignes de code suivantes :</span><span class="sxs-lookup"><span data-stu-id="e1d66-117">You can correct the error by changing the call to either of the following lines of code:</span></span>  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 <span data-ttu-id="e1d66-118">Chacune des lignes précédentes du code effectue un cast explicite le `Object` variable `o1` à un des types de paramètres définis pour les surcharges.</span><span class="sxs-lookup"><span data-stu-id="e1d66-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d66-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1d66-119">See Also</span></span>  
 [<span data-ttu-id="e1d66-120">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="e1d66-120">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="e1d66-121">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="e1d66-121">Overload Resolution</span></span>](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)  
 [<span data-ttu-id="e1d66-122">CType (fonction)</span><span class="sxs-lookup"><span data-stu-id="e1d66-122">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
