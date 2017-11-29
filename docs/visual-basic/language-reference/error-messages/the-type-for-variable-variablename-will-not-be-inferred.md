---
title: "Le type de variable &#39; &lt;variablename&gt;&#39; ne sera pas déduit, car il est lié à un champ dans une portée englobante"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords: BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39968407f4de5436df324320c99dede4d72e2808
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="87e1e-102">Le type de variable &#39; &lt;variablename&gt;&#39; ne sera pas déduit, car il est lié à un champ dans une portée englobante</span><span class="sxs-lookup"><span data-stu-id="87e1e-102">The type for variable &#39;&lt;variablename&gt;&#39; will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="87e1e-103">Le type de variable '\<nom_variable >' ne sera pas déduit, car il est lié à un champ dans une portée englobante.</span><span class="sxs-lookup"><span data-stu-id="87e1e-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="87e1e-104">Modifiez le nom de «\<nom_variable >', ou utilisez le nom qualifié complet (par exemple, 'Me.NomVariable' ou 'MyBase.NomVariable').</span><span class="sxs-lookup"><span data-stu-id="87e1e-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="87e1e-105">Une variable de contrôle de boucle dans votre code a le même nom qu’un champ de la classe ou une autre portée englobante.</span><span class="sxs-lookup"><span data-stu-id="87e1e-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="87e1e-106">Étant donné que la variable de contrôle est utilisée sans un `As` clause, elle est liée au champ dans la portée englobante, et le compilateur ne pas créer une variable pour lui ou déduire son type.</span><span class="sxs-lookup"><span data-stu-id="87e1e-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="87e1e-107">Dans l’exemple suivant, `Index`, la variable de contrôle dans le `For` instruction, est lié à la `Index` champ la `Customer` classe.</span><span class="sxs-lookup"><span data-stu-id="87e1e-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="87e1e-108">Le compilateur ne crée pas une variable pour la variable de contrôle `Index` ou déduire son type.</span><span class="sxs-lookup"><span data-stu-id="87e1e-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="87e1e-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="87e1e-109">By default, this message is a warning.</span></span> <span data-ttu-id="87e1e-110">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [configuration des avertissements en Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="87e1e-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="87e1e-111">**ID d’erreur :** BC42110</span><span class="sxs-lookup"><span data-stu-id="87e1e-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="87e1e-112">Pour traiter cet avertissement</span><span class="sxs-lookup"><span data-stu-id="87e1e-112">To address this warning</span></span>  
  
-   <span data-ttu-id="87e1e-113">Vérifiez la variable de contrôle de boucle local en modifiant son nom à un identificateur qui n’est pas le nom d’un champ de la classe.</span><span class="sxs-lookup"><span data-stu-id="87e1e-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   <span data-ttu-id="87e1e-114">Préciser que la variable de contrôle de boucle est liée au champ de classe en ajoutant le préfixe `Me.` au nom de variable.</span><span class="sxs-lookup"><span data-stu-id="87e1e-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   <span data-ttu-id="87e1e-115">Au lieu d’utiliser l’inférence de type local, utilisez un `As` clause pour spécifier un type pour la variable de contrôle de boucle.</span><span class="sxs-lookup"><span data-stu-id="87e1e-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="87e1e-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="87e1e-116">Example</span></span>  
 <span data-ttu-id="87e1e-117">Le code suivant montre l’exemple précédent avec la première correction en place.</span><span class="sxs-lookup"><span data-stu-id="87e1e-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="87e1e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87e1e-118">See Also</span></span>  
 [<span data-ttu-id="87e1e-119">Option Infer (instruction)</span><span class="sxs-lookup"><span data-stu-id="87e1e-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="87e1e-120">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="87e1e-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="87e1e-121">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="87e1e-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="87e1e-122">Guide pratique : référencer l'instance actuelle d'un objet</span><span class="sxs-lookup"><span data-stu-id="87e1e-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [<span data-ttu-id="87e1e-123">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="87e1e-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="87e1e-124">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="87e1e-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
