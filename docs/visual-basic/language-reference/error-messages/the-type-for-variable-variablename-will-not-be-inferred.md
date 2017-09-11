---
title: "Le type de variable &quot;&lt;variablename&gt;» ne sera pas déduit, car il est lié à un champ dans une portée englobante | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42110
- bc42110
dev_langs:
- VB
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 0f954fda84c9fd1a4af5315be2329de117e6d169
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="dcbd1-102">Le type de variable '&lt;variablename&gt;» ne sera pas déduit, car il est lié à un champ dans une portée englobante</span><span class="sxs-lookup"><span data-stu-id="dcbd1-102">The type for variable &#39;&lt;variablename&gt;&#39; will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="dcbd1-103">Le type de variable '\<variablename > » ne sera pas déduit, car il est lié à un champ dans une portée englobante.</span><span class="sxs-lookup"><span data-stu-id="dcbd1-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="dcbd1-104">Modifiez le nom de «\<variablename > », ou utilisez le nom qualifié complet (par exemple, 'Me.NomVariable' ou 'MyBase.NomVariable').</span><span class="sxs-lookup"><span data-stu-id="dcbd1-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="dcbd1-105">Une variable de contrôle de boucle dans votre code a le même nom qu’un champ de la classe ou une autre portée englobante.</span><span class="sxs-lookup"><span data-stu-id="dcbd1-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="dcbd1-106">Étant donné que la variable de contrôle est utilisée sans un `As` clause, elle est liée au champ dans la portée englobante, et le compilateur ne pas créer une variable pour lui ou déduire son type.</span><span class="sxs-lookup"><span data-stu-id="dcbd1-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="dcbd1-107">Dans l’exemple suivant, `Index`, la variable de contrôle dans les `For` instruction, est lié à la `Index` champ la `Customer` classe.</span><span class="sxs-lookup"><span data-stu-id="dcbd1-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="dcbd1-108">Le compilateur ne crée pas de variable pour la variable de contrôle `Index` ou déduire son type.</span><span class="sxs-lookup"><span data-stu-id="dcbd1-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
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
  
 <span data-ttu-id="dcbd1-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="dcbd1-109">By default, this message is a warning.</span></span> <span data-ttu-id="dcbd1-110">Pour plus d’informations sur le masquage des avertissements ou de considérer les avertissements comme des erreurs, consultez [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="dcbd1-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="dcbd1-111">**ID d’erreur :** BC42110</span><span class="sxs-lookup"><span data-stu-id="dcbd1-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="dcbd1-112">Pour traiter cet avertissement</span><span class="sxs-lookup"><span data-stu-id="dcbd1-112">To address this warning</span></span>  
  
-   <span data-ttu-id="dcbd1-113">Vérifiez la variable de contrôle de boucle local en modifiant son nom à un identificateur qui n’est pas le nom d’un champ de la classe.</span><span class="sxs-lookup"><span data-stu-id="dcbd1-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   <span data-ttu-id="dcbd1-114">Précisez que la variable de contrôle de boucle crée une liaison pour le champ de classe en ajoutant le préfixe `Me.` au nom de variable.</span><span class="sxs-lookup"><span data-stu-id="dcbd1-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   <span data-ttu-id="dcbd1-115">Au lieu de compter sur l’inférence de type local, utilisez un `As` clause pour spécifier un type pour la variable de contrôle de boucle.</span><span class="sxs-lookup"><span data-stu-id="dcbd1-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="dcbd1-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="dcbd1-116">Example</span></span>  
 <span data-ttu-id="dcbd1-117">Le code suivant montre l’exemple précédent avec la première correction en place.</span><span class="sxs-lookup"><span data-stu-id="dcbd1-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dcbd1-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcbd1-118">See Also</span></span>  
 <span data-ttu-id="dcbd1-119">[Instruction Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="dcbd1-119">[Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="dcbd1-120"> [For Each... Instruction suivante](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="dcbd1-120"> [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) </span></span>  
<span data-ttu-id="dcbd1-121"> [Pour... Instruction suivante](../../../visual-basic/language-reference/statements/for-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="dcbd1-121"> [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) </span></span>  
<span data-ttu-id="dcbd1-122"> [Comment : faire référence à l’Instance actuelle d’un objet](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="dcbd1-122"> [How to: Refer to the Current Instance of an Object](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md) </span></span>  
<span data-ttu-id="dcbd1-123"> [Inférence de Type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="dcbd1-123"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="dcbd1-124"> [Me, My, MyBase et MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span><span class="sxs-lookup"><span data-stu-id="dcbd1-124"> [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)</span></span>

