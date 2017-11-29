---
title: "Type de &#39; &lt;variablename&gt;&#39; ne peut pas être déduit, car les limites de la boucle et du s’étend pas vers le même type"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords: BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 022e29e38a93d2880bbfa250e65a8b95b39ff140
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="3a36a-102">Type de &#39; &lt;variablename&gt;&#39; ne peut pas être déduit, car les limites de la boucle et du s’étend pas vers le même type</span><span class="sxs-lookup"><span data-stu-id="3a36a-102">Type of &#39;&lt;variablename&gt;&#39; cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>
<span data-ttu-id="3a36a-103">Vous avez écrit une `For...Next` boucle dans laquelle le compilateur ne peut pas déduire un type de données pour la variable de contrôle de boucle, car les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="3a36a-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>  
  
-   <span data-ttu-id="3a36a-104">Le type de données de la variable de contrôle de boucle n’est pas spécifié avec une clause `As` .</span><span class="sxs-lookup"><span data-stu-id="3a36a-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>  
  
-   <span data-ttu-id="3a36a-105">Les limites de la boucle et l’incrémentation contiennent au moins deux types de données.</span><span class="sxs-lookup"><span data-stu-id="3a36a-105">The loop bounds and step variable contain at least two data types.</span></span>  
  
-   <span data-ttu-id="3a36a-106">Il n’existe aucune conversion standard entre les types de données.</span><span class="sxs-lookup"><span data-stu-id="3a36a-106">No standard conversions exist between the data types.</span></span>  
  
 <span data-ttu-id="3a36a-107">Par conséquent, le compilateur ne peut pas déduire le type de données de variable de contrôle d’une boucle.</span><span class="sxs-lookup"><span data-stu-id="3a36a-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>  
  
 <span data-ttu-id="3a36a-108">Dans l’exemple suivant, la variable de l’étape est un caractère et les limites de la boucle sont des entiers.</span><span class="sxs-lookup"><span data-stu-id="3a36a-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="3a36a-109">Étant donné qu’aucune conversion standard entre les caractères et les entiers, cette erreur est signalée.</span><span class="sxs-lookup"><span data-stu-id="3a36a-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 <span data-ttu-id="3a36a-110">**ID d’erreur :** BC30982</span><span class="sxs-lookup"><span data-stu-id="3a36a-110">**Error ID:** BC30982</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3a36a-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="3a36a-111">To correct this error</span></span>  
  
-   <span data-ttu-id="3a36a-112">Modifier les types des limites de la boucle et selon vos besoins afin qu’au moins un d’eux est un type de la clause d’incrémentation.</span><span class="sxs-lookup"><span data-stu-id="3a36a-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="3a36a-113">Dans l’exemple précédent, remplacez le type de `stepVar` à `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3a36a-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     <span data-ttu-id="3a36a-114">- ou -</span><span class="sxs-lookup"><span data-stu-id="3a36a-114">—or—</span></span>  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   <span data-ttu-id="3a36a-115">Utilisez les fonctions de conversion explicite pour convertir les limites de la boucle et la variable de l’étape pour les types appropriés.</span><span class="sxs-lookup"><span data-stu-id="3a36a-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="3a36a-116">Dans l’exemple précédent, appliquez le `Val` à fonction `stepVar`.</span><span class="sxs-lookup"><span data-stu-id="3a36a-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3a36a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a36a-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [<span data-ttu-id="3a36a-118">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="3a36a-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="3a36a-119">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="3a36a-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="3a36a-120">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="3a36a-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="3a36a-121">Option Infer (instruction)</span><span class="sxs-lookup"><span data-stu-id="3a36a-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="3a36a-122">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="3a36a-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="3a36a-123">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="3a36a-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
