---
title: "Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 557e72342901fab8bbe66e9cc3405cb4b2d9c1e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="60ed2-102">Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="60ed2-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="60ed2-103">Il existe une autre méthode d’itération au sein d’un tableau qui consiste à utiliser l’instruction [foreach](../../../csharp/language-reference/keywords/foreach-in.md), comme indiqué dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="60ed2-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="60ed2-104">L’instruction `foreach` peut être utilisée pour effectuer une itération au sein d’un tableau, d’une classe de collection .NET Framework, ou d’une classe ou d’un struct qui implémente l’interface <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="60ed2-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60ed2-105">Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projet](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="60ed2-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60ed2-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="60ed2-106">Example</span></span>  
 <span data-ttu-id="60ed2-107">Cet exemple montre comment imprimer les arguments de ligne de commande à l’aide de `foreach`.</span><span class="sxs-lookup"><span data-stu-id="60ed2-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="60ed2-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60ed2-108">See Also</span></span>  
 <xref:System.Array>  
 <xref:System.Collections>  
 [<span data-ttu-id="60ed2-109">Génération à partir de la ligne de commande avec csc.exe</span><span class="sxs-lookup"><span data-stu-id="60ed2-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="60ed2-110">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="60ed2-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="60ed2-111">foreach, in</span><span class="sxs-lookup"><span data-stu-id="60ed2-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="60ed2-112">Main() et arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="60ed2-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="60ed2-113">Comment : afficher les arguments de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="60ed2-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="60ed2-114">Valeurs de retour Main()</span><span class="sxs-lookup"><span data-stu-id="60ed2-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
