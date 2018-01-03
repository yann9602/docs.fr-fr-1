---
title: "Méthodes partielles (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33e34c63988e74be2c22cb7b1358f5e8b04048c6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="partial-methods-visual-basic"></a><span data-ttu-id="a4818-102">Méthodes partielles (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4818-102">Partial Methods (Visual Basic)</span></span>
<span data-ttu-id="a4818-103">Les méthodes partielles permettent aux développeurs d’insérer une logique personnalisée dans du code.</span><span class="sxs-lookup"><span data-stu-id="a4818-103">Partial methods enable developers to insert custom logic into code.</span></span> <span data-ttu-id="a4818-104">En règle générale, le code fait partie d’une classe généré par le concepteur.</span><span class="sxs-lookup"><span data-stu-id="a4818-104">Typically, the code is part of a designer-generated class.</span></span> <span data-ttu-id="a4818-105">Les méthodes partielles sont définies dans une classe partielle qui est créée par un générateur de code, et ils sont couramment utilisés pour fournir une notification que quelque chose a été modifiée.</span><span class="sxs-lookup"><span data-stu-id="a4818-105">Partial methods are defined in a partial class that is created by a code generator, and they are commonly used to provide notification that something has been changed.</span></span> <span data-ttu-id="a4818-106">Elles permettent au développeur de spécifier un comportement personnalisé en réponse à la modification.</span><span class="sxs-lookup"><span data-stu-id="a4818-106">They enable the developer to specify custom behavior in response to the change.</span></span>  
  
 <span data-ttu-id="a4818-107">Le concepteur du Générateur de code définit uniquement la signature de méthode et un ou plusieurs appels à la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4818-107">The designer of the code generator defines only the method signature and one or more calls to the method.</span></span> <span data-ttu-id="a4818-108">Les développeurs peuvent ensuite fournir des implémentations de la méthode s’ils souhaitent personnaliser le comportement du code généré.</span><span class="sxs-lookup"><span data-stu-id="a4818-108">Developers can then provide implementations for the method if they want to customize the behavior of the generated code.</span></span> <span data-ttu-id="a4818-109">Lorsqu’aucune implémentation n’est fournie, les appels à la méthode sont supprimés par le compilateur, ce qui entraîne aucune surcharge supplémentaire des performances.</span><span class="sxs-lookup"><span data-stu-id="a4818-109">When no implementation is provided, calls to the method are removed by the compiler, resulting in no additional performance overhead.</span></span>  
  
## <a name="declaration"></a><span data-ttu-id="a4818-110">Déclaration</span><span class="sxs-lookup"><span data-stu-id="a4818-110">Declaration</span></span>  
 <span data-ttu-id="a4818-111">Le code généré marque la définition d’une méthode partielle en plaçant le mot clé `Partial` au début de la ligne de signature.</span><span class="sxs-lookup"><span data-stu-id="a4818-111">The generated code marks the definition of a partial method by placing the keyword `Partial` at the start of the signature line.</span></span>  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 <span data-ttu-id="a4818-112">La définition doit remplir les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="a4818-112">The definition must meet the following conditions:</span></span>  
  
-   <span data-ttu-id="a4818-113">La méthode doit être un `Sub`, et non un `Function`.</span><span class="sxs-lookup"><span data-stu-id="a4818-113">The method must be a `Sub`, not a `Function`.</span></span>  
  
-   <span data-ttu-id="a4818-114">Le corps de la méthode doit être vide.</span><span class="sxs-lookup"><span data-stu-id="a4818-114">The body of the method must be left empty.</span></span>  
  
-   <span data-ttu-id="a4818-115">Le modificateur d’accès doit être `Private`.</span><span class="sxs-lookup"><span data-stu-id="a4818-115">The access modifier must be `Private`.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="a4818-116">Implémentation</span><span class="sxs-lookup"><span data-stu-id="a4818-116">Implementation</span></span>  
 <span data-ttu-id="a4818-117">L’implémentation consiste principalement à remplir le corps de la méthode partielle.</span><span class="sxs-lookup"><span data-stu-id="a4818-117">The implementation consists primarily of filling in the body of the partial method.</span></span> <span data-ttu-id="a4818-118">L’implémentation est en général dans une classe partielle distincte de la définition et est écrite par un développeur qui souhaite étendre le code généré.</span><span class="sxs-lookup"><span data-stu-id="a4818-118">The implementation is typically in a separate partial class from the definition, and is written by a developer who wants to extend the generated code.</span></span>  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 <span data-ttu-id="a4818-119">L’exemple précédent duplique la signature dans la déclaration exactement, mais les variations sont possibles.</span><span class="sxs-lookup"><span data-stu-id="a4818-119">The previous example duplicates the signature in the declaration exactly, but variations are possible.</span></span> <span data-ttu-id="a4818-120">En particulier, les autres modificateurs peuvent être ajoutés, tels que `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="a4818-120">In particular, other modifiers can be added, such as `Overloads` or `Overrides`.</span></span> <span data-ttu-id="a4818-121">Seul `Overrides` modificateur est autorisé.</span><span class="sxs-lookup"><span data-stu-id="a4818-121">Only one `Overrides` modifier is permitted.</span></span> <span data-ttu-id="a4818-122">Pour plus d’informations sur les modificateurs de méthode, consultez [Sub, instruction](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a4818-122">For more information about method modifiers, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="use"></a><span data-ttu-id="a4818-123">Utilisez</span><span class="sxs-lookup"><span data-stu-id="a4818-123">Use</span></span>  
 <span data-ttu-id="a4818-124">Vous appelez une méthode partielle comme vous appelleriez n’importe quel autre `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="a4818-124">You call a partial method as you would call any other `Sub` procedure.</span></span> <span data-ttu-id="a4818-125">Si la méthode a été implémentée, les arguments sont évalués et le corps de la méthode est exécuté.</span><span class="sxs-lookup"><span data-stu-id="a4818-125">If the method has been implemented, the arguments are evaluated and the body of the method is executed.</span></span> <span data-ttu-id="a4818-126">Toutefois, n’oubliez pas que l’implémentation d’une méthode partielle est facultative.</span><span class="sxs-lookup"><span data-stu-id="a4818-126">However, remember that implementing a partial method is optional.</span></span> <span data-ttu-id="a4818-127">Si la méthode n’est pas implémentée, un appel n’a aucun effet et les expressions passées comme arguments à la méthode ne sont pas évaluées.</span><span class="sxs-lookup"><span data-stu-id="a4818-127">If the method is not implemented, a call to it has no effect, and expressions passed as arguments to the method are not evaluated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4818-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4818-128">Example</span></span>  
 <span data-ttu-id="a4818-129">Dans un fichier nommé Product.Designer.vb, définissez une `Product` classe qui a un `Quantity` propriété.</span><span class="sxs-lookup"><span data-stu-id="a4818-129">In a file named Product.Designer.vb, define a `Product` class that has a `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 <span data-ttu-id="a4818-130">Dans un fichier nommé Product.vb, fournissez une implémentation pour `QuantityChanged`.</span><span class="sxs-lookup"><span data-stu-id="a4818-130">In a file named Product.vb, provide an implementation for `QuantityChanged`.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 <span data-ttu-id="a4818-131">Enfin, dans la méthode Main d’un projet, déclarez un `Product` de l’instance et fournir une valeur initiale pour son `Quantity` propriété.</span><span class="sxs-lookup"><span data-stu-id="a4818-131">Finally, in the Main method of a project, declare a `Product` instance and provide an initial value for its `Quantity` property.</span></span>  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 <span data-ttu-id="a4818-132">Une boîte de message doit s’afficher qui affiche ce message :</span><span class="sxs-lookup"><span data-stu-id="a4818-132">A message box should appear that displays this message:</span></span>  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a><span data-ttu-id="a4818-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4818-133">See Also</span></span>  
 [<span data-ttu-id="a4818-134">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="a4818-134">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="a4818-135">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="a4818-135">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="a4818-136">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="a4818-136">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="a4818-137">Partial</span><span class="sxs-lookup"><span data-stu-id="a4818-137">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [<span data-ttu-id="a4818-138">Génération de code dans LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a4818-138">Code Generation in LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="a4818-139">Ajout d’une logique métier à l’aide de méthodes partielles</span><span class="sxs-lookup"><span data-stu-id="a4818-139">Adding Business Logic By Using Partial Methods</span></span>](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
