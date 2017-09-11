---
title: "Main() et arguments de ligne de commande (Guide de programmation C#)"
ms.date: 2017-08-02
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
dev_langs:
- CSharp
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
caps.latest.revision: 30
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
ms.sourcegitcommit: d019d1c5757a961c03439d756e808ae13fd8a67b
ms.openlocfilehash: 51408654abd0dcd2f7159438b507c44bd579bfd9
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="main-and-command-line-arguments-c-programming-guide"></a><span data-ttu-id="9a079-102">Main() et arguments de ligne de commande (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="9a079-102">Main() and command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="9a079-103">La méthode `Main` est le point d’entrée d’une application C#.</span><span class="sxs-lookup"><span data-stu-id="9a079-103">The `Main` method is the entry point of a C# application.</span></span> <span data-ttu-id="9a079-104">(Les bibliothèques et les services ne requièrent pas de méthode `Main` comme point d’entrée.) Lorsque l’application est démarrée, la méthode `Main` est la première méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="9a079-104">(Libraries and services do not require a `Main` method as an entry point.) When the application is started, the `Main` method is the first method that is invoked.</span></span>

 <span data-ttu-id="9a079-105">Il ne peut y avoir qu’un seul point d’entrée dans un programme C#.</span><span class="sxs-lookup"><span data-stu-id="9a079-105">There can only be one entry point in a C# program.</span></span> <span data-ttu-id="9a079-106">Si plusieurs classes ont une méthode `Main`, vous devez compiler votre programme avec l’option de compilateur **/main** pour spécifier quelle méthode `Main` utiliser comme point d’entrée.</span><span class="sxs-lookup"><span data-stu-id="9a079-106">If you have more than one class that has a `Main` method, you must compile your program with the **/main** compiler option to specify which `Main` method to use as the entry point.</span></span> <span data-ttu-id="9a079-107">Pour plus d’informations, consultez l’article [/main (C# Compiler Options) (/main [Options du compilateur C#])](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="9a079-107">For more information, see [/main (C# Compiler Options)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).</span></span>

 <span data-ttu-id="9a079-108">[!code-cs[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9a079-108">[!code-cs[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]</span></span>

## <a name="overview"></a><span data-ttu-id="9a079-109">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="9a079-109">Overview</span></span>

- <span data-ttu-id="9a079-110">La méthode `Main` est le point d’entrée d’un programme exécutable ; c’est l’endroit où le contrôle du programme commence et se termine.</span><span class="sxs-lookup"><span data-stu-id="9a079-110">The `Main` method is the entry point of an executable program; it is where the program control starts and ends.</span></span>
- <span data-ttu-id="9a079-111">`Main` est déclaré à l’intérieur d’une classe ou d’un struct.</span><span class="sxs-lookup"><span data-stu-id="9a079-111">`Main` is declared inside a class or struct.</span></span> <span data-ttu-id="9a079-112">`Main` doit être [statique](../../../csharp/language-reference/keywords/static.md) et ne doit pas être [public](../../../csharp/language-reference/keywords/public.md).</span><span class="sxs-lookup"><span data-stu-id="9a079-112">`Main` must be [static](../../../csharp/language-reference/keywords/static.md) and it need not be [public](../../../csharp/language-reference/keywords/public.md).</span></span> <span data-ttu-id="9a079-113">(Dans l’exemple précédent, il reçoit l’accès [privé](../../../csharp/language-reference/keywords/private.md) par défaut.) Il n’est pas nécessaire que la classe ou le struct englobant soit statique.</span><span class="sxs-lookup"><span data-stu-id="9a079-113">(In the earlier example, it receives the default access of [private](../../../csharp/language-reference/keywords/private.md).) The enclosing class or struct is not required to be static.</span></span>
- <span data-ttu-id="9a079-114">`Main` peut avoir un type de retour `void`, `int` ou, à partir de C# 7.1, `Task` ou `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="9a079-114">`Main` can either have a `void`, `int`, or, starting with C# 7.1, `Task`, or `Task<int>` return type.</span></span>
- <span data-ttu-id="9a079-115">Si et seulement si `Main` retourne un `Task` ou `Task<int>`, la déclaration de `Main` peut inclure le modificateur [`async`](../../language-reference/keywords/async.md).</span><span class="sxs-lookup"><span data-stu-id="9a079-115">If and only if `Main` returns a `Task` or `Task<int>`, the declaration of `Main` may include the [`async`](../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="9a079-116">Notez que cela exclut spécifiquement une méthode `async void Main`.</span><span class="sxs-lookup"><span data-stu-id="9a079-116">Note that this specifically excludes an `async void Main` method.</span></span>
- <span data-ttu-id="9a079-117">La méthode `Main` peut être déclarée avec ou sans paramètre `string[]`, qui contient des arguments de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="9a079-117">The `Main` method can be declared with or without a `string[]` parameter that contains command-line arguments.</span></span> <span data-ttu-id="9a079-118">Lorsque vous utilisez [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] pour créer des applications Windows, vous pouvez ajouter le paramètre manuellement ou bien utiliser la classe <xref:System.Environment> pour obtenir les arguments de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="9a079-118">When using [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] to create Windows applications, you can add the parameter manually or else use the <xref:System.Environment> class to obtain the command-line arguments.</span></span> <span data-ttu-id="9a079-119">Les paramètres sont lus comme des arguments de ligne de commande avec index de base zéro.</span><span class="sxs-lookup"><span data-stu-id="9a079-119">Parameters are read as zero-indexed command-line arguments.</span></span> <span data-ttu-id="9a079-120">Contrairement à C et C++, le nom du programme n’est pas traité comme le premier argument de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="9a079-120">Unlike C and C++, the name of the program is not treated as the first command-line argument.</span></span>

<span data-ttu-id="9a079-121">L’ajout des types de retour `async` et `Task`, `Task<int>` simplifie le code de programme lorsque les applications de console doivent démarrer et `await` des opérations asynchrones dans `Main`.</span><span class="sxs-lookup"><span data-stu-id="9a079-121">The addition of `async` and `Task`, `Task<int>` return types simplifies program code when console applications need to start and `await` asynchronous operations in `Main`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9a079-122">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9a079-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9a079-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a079-123">See also</span></span>
<span data-ttu-id="9a079-124">[Génération à partir de la ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
[Guide de programmation C#](../../../csharp/programming-guide/index.md)
[Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)
[À l’intérieur d’un programme C#](../../../csharp/programming-guide/inside-a-program/index.md)</span><span class="sxs-lookup"><span data-stu-id="9a079-124">[Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
[C# Programming Guide](../../../csharp/programming-guide/index.md)
[Methods](../../../csharp/programming-guide/classes-and-structs/methods.md)
[Inside a C# Program](../../../csharp/programming-guide/inside-a-program/index.md)</span></span>

