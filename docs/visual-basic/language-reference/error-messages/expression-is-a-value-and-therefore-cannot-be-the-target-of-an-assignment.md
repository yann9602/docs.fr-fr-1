---
title: "Cette expression est une valeur et ne peut donc pas être la cible d'une assignation"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords: BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bec3e2d298160bd0b459dc3b7ef93b94648e439a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a><span data-ttu-id="65738-102">Cette expression est une valeur et ne peut donc pas être la cible d'une assignation</span><span class="sxs-lookup"><span data-stu-id="65738-102">Expression is a value and therefore cannot be the target of an assignment</span></span>
<span data-ttu-id="65738-103">Une instruction tente d’assigner une valeur à une expression.</span><span class="sxs-lookup"><span data-stu-id="65738-103">A statement attempts to assign a value to an expression.</span></span> <span data-ttu-id="65738-104">Vous pouvez affecter une valeur uniquement à une variable accessible en écriture, une propriété ou un élément de tableau en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="65738-104">You can assign a value only to a writable variable, property, or array element at run time.</span></span> <span data-ttu-id="65738-105">L’exemple suivant illustre la manière dont cette erreur peut se produire.</span><span class="sxs-lookup"><span data-stu-id="65738-105">The following example illustrates how this error can occur.</span></span>  
  
```  
Dim yesterday As Integer  
ReadOnly maximum As Integer = 45  
yesterday + 1 = DatePart(DateInterval.Day, Now)  
' The preceding line is an ERROR because of an expression on the left.  
maximum = 50  
' The preceding line is an ERROR because maximum is declared ReadOnly.  
```  
  
 <span data-ttu-id="65738-106">Des exemples similaires pourraient s’appliquent aux propriétés et aux éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="65738-106">Similar examples could apply to properties and array elements.</span></span>  
  
 <span data-ttu-id="65738-107">**Accès indirect.**</span><span class="sxs-lookup"><span data-stu-id="65738-107">**Indirect Access.**</span></span> <span data-ttu-id="65738-108">Un accès indirect via un type valeur peut également générer cette erreur.</span><span class="sxs-lookup"><span data-stu-id="65738-108">Indirect access through a value type can also generate this error.</span></span> <span data-ttu-id="65738-109">Prenons l’exemple de code suivant, qui tente de définir la valeur de <xref:System.Drawing.Point> en accédant à indirectement via <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="65738-109">Consider the following code example, which attempts to set the value of <xref:System.Drawing.Point> by accessing it indirectly through <xref:System.Windows.Forms.Control.Location%2A>.</span></span>  
  
```  
' Assume this code runs inside Form1.  
Dim exitButton As New System.Windows.Forms.Button()  
exitButton.Text = "Exit this form"  
exitButton.Location.X = 140  
' The preceding line is an ERROR because of no storage for Location.  
```  
  
 <span data-ttu-id="65738-110">La dernière instruction de l’exemple précédent échoue, car elle crée uniquement une allocation temporaire pour la <xref:System.Drawing.Point> structure retournée par le <xref:System.Windows.Forms.Control.Location%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="65738-110">The last statement of the preceding example fails because it creates only a temporary allocation for the <xref:System.Drawing.Point> structure returned by the <xref:System.Windows.Forms.Control.Location%2A> property.</span></span> <span data-ttu-id="65738-111">Une structure est un type valeur, et la structure temporaire n’est pas conservée après l’exécution de l’instruction.</span><span class="sxs-lookup"><span data-stu-id="65738-111">A structure is a value type, and the temporary structure is not retained after the statement runs.</span></span> <span data-ttu-id="65738-112">Le problème est résolu en déclarant et en utilisant une variable pour <xref:System.Windows.Forms.Control.Location%2A>, ce qui crée une allocation plus permanente pour le <xref:System.Drawing.Point> structure.</span><span class="sxs-lookup"><span data-stu-id="65738-112">The problem is resolved by declaring and using a variable for <xref:System.Windows.Forms.Control.Location%2A>, which creates a more permanent allocation for the <xref:System.Drawing.Point> structure.</span></span> <span data-ttu-id="65738-113">L’exemple suivant montre le code de remplace la dernière instruction de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="65738-113">The following example shows code that can replace the last statement of the preceding example.</span></span>  
  
```  
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)  
exitButton.Location = exitLocation  
```  
  
 <span data-ttu-id="65738-114">**ID d’erreur :** BC30068</span><span class="sxs-lookup"><span data-stu-id="65738-114">**Error ID:** BC30068</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="65738-115">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="65738-115">To correct this error</span></span>  
  
-   <span data-ttu-id="65738-116">Si l’instruction assigne une valeur à une expression, remplacez l’expression par une variable accessible en écriture seule, une propriété ou un élément de tableau.</span><span class="sxs-lookup"><span data-stu-id="65738-116">If the statement assigns a value to an expression, replace the expression with a single writable variable, property, or array element.</span></span>  
  
-   <span data-ttu-id="65738-117">Si l’instruction effectue un accès indirect via un type valeur (généralement une structure), créez une variable pour stocker le type de valeur.</span><span class="sxs-lookup"><span data-stu-id="65738-117">If the statement makes indirect access through a value type (usually a structure), create a variable to hold the value type.</span></span>  
  
-   <span data-ttu-id="65738-118">Affecter la structure appropriée (ou autre type de valeur) à la variable.</span><span class="sxs-lookup"><span data-stu-id="65738-118">Assign the appropriate structure (or other value type) to the variable.</span></span>  
  
-   <span data-ttu-id="65738-119">Utilisez la variable pour accéder à la propriété pour lui attribuer une valeur.</span><span class="sxs-lookup"><span data-stu-id="65738-119">Use the variable to access the property to assign it a value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65738-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65738-120">See Also</span></span>  
 [<span data-ttu-id="65738-121">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="65738-121">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="65738-122">Instructions</span><span class="sxs-lookup"><span data-stu-id="65738-122">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="65738-123">Procédures de dépannage</span><span class="sxs-lookup"><span data-stu-id="65738-123">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
