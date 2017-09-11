---
title: "Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 766b5cd0879edec1dc409e07c4f62ee693fd615d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="96703-102">Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="96703-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="96703-103">Il existe une autre méthode d’itération au sein d’un tableau qui consiste à utiliser l’instruction [foreach](../../../csharp/language-reference/keywords/foreach-in.md), comme indiqué dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="96703-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="96703-104">L’instruction `foreach` peut être utilisée pour effectuer une itération au sein d’un tableau, d’une classe de collection .NET Framework, ou d’une classe ou d’un struct qui implémente l’interface <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="96703-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96703-105">Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projet](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="96703-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="96703-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="96703-106">Example</span></span>  
 <span data-ttu-id="96703-107">Cet exemple montre comment imprimer les arguments de ligne de commande à l’aide de `foreach`.</span><span class="sxs-lookup"><span data-stu-id="96703-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 <span data-ttu-id="96703-108">[!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="96703-108">[!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]</span></span>  
  
 <span data-ttu-id="96703-109">[!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="96703-109">[!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96703-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96703-110">See Also</span></span>  
 <span data-ttu-id="96703-111"><xref:System.Array></span><span class="sxs-lookup"><span data-stu-id="96703-111"><xref:System.Array></span></span>   
 <span data-ttu-id="96703-112"><xref:System.Collections></span><span class="sxs-lookup"><span data-stu-id="96703-112"><xref:System.Collections></span></span>   
 <span data-ttu-id="96703-113">[Génération en ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span><span class="sxs-lookup"><span data-stu-id="96703-113">[Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span></span>  
 <span data-ttu-id="96703-114">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="96703-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="96703-115">[foreach, in](../../../csharp/language-reference/keywords/foreach-in.md) </span><span class="sxs-lookup"><span data-stu-id="96703-115">[foreach, in](../../../csharp/language-reference/keywords/foreach-in.md) </span></span>  
 <span data-ttu-id="96703-116">[Main() et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/index.md) </span><span class="sxs-lookup"><span data-stu-id="96703-116">[Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) </span></span>  
 <span data-ttu-id="96703-117">[Guide pratique pour afficher les arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="96703-117">[How to: Display Command Line Arguments](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md) </span></span>  
 [<span data-ttu-id="96703-118">Valeurs de retour Main()</span><span class="sxs-lookup"><span data-stu-id="96703-118">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

