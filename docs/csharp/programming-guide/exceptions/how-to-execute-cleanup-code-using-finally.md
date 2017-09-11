---
title: "Guide pratique pour exécuter le code de nettoyage à l'aide de finally (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
caps.latest.revision: 21
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
ms.openlocfilehash: b1f7bccacf20a9322f4de75740cdc34b4a97fa4c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a><span data-ttu-id="c0915-102">Guide pratique pour exécuter le code de nettoyage à l'aide de finally (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c0915-102">How to: Execute Cleanup Code Using finally (C# Programming Guide)</span></span>
<span data-ttu-id="c0915-103">L’objectif d’une instruction `finally` est de vérifier que le nettoyage nécessaire des objets, généralement ceux contenant des ressources externes, se produit immédiatement, même si une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="c0915-103">The purpose of a `finally` statement is to ensure that the necessary cleanup of objects, usually objects that are holding external resources, occurs immediately, even if an exception is thrown.</span></span> <span data-ttu-id="c0915-104">Un exemple de nettoyage de ce type est l’appel à <xref:System.IO.Stream.Close%2A> sur un <xref:System.IO.FileStream> immédiatement après son utilisation au lieu d’attendre que l’objet soit récupéré par garbage collection par le Common Language Runtime, comme suit :</span><span class="sxs-lookup"><span data-stu-id="c0915-104">One example of such cleanup is calling <xref:System.IO.Stream.Close%2A> on a <xref:System.IO.FileStream> immediately after use instead of waiting for the object to be garbage collected by the common language runtime, as follows:</span></span>  
  
 <span data-ttu-id="c0915-105">[!code-cs[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c0915-105">[!code-cs[csProgGuideExceptions#16](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0915-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="c0915-106">Example</span></span>  
 <span data-ttu-id="c0915-107">Pour transformer le code précédent en instruction `try-catch-finally`, le code de nettoyage est séparé du code actif comme suit.</span><span class="sxs-lookup"><span data-stu-id="c0915-107">To turn the previous code into a `try-catch-finally` statement, the cleanup code is separated from the working code, as follows.</span></span>  
  
 <span data-ttu-id="c0915-108">[!code-cs[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c0915-108">[!code-cs[csProgGuideExceptions#17](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-execute-cleanup-code-using-finally_2.cs)]</span></span>  
  
 <span data-ttu-id="c0915-109">Comme une exception peut se produire à tout moment dans le bloc `try` avant l’appel à `OpenWrite()`, ou comme l’appel `OpenWrite()` lui-même peut échouer, nous n’avons aucune garantie que le fichier est ouvert quand nous essayons de le fermer.</span><span class="sxs-lookup"><span data-stu-id="c0915-109">Because an exception can occur at any time within the `try` block before the `OpenWrite()` call, or the `OpenWrite()` call itself could fail, we are not guaranteed that the file is open when we try to close it.</span></span> <span data-ttu-id="c0915-110">Le bloc `finally` ajoute un contrôle pour garantir que l’objet <xref:System.IO.FileStream> n’est pas `null` avant d’appeler la méthode <xref:System.IO.Stream.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0915-110">The `finally` block adds a check to make sure that the <xref:System.IO.FileStream> object is not `null` before you call the <xref:System.IO.Stream.Close%2A> method.</span></span> <span data-ttu-id="c0915-111">Sans le contrôle `null`, le bloc `finally` pourrait lever sa propre <xref:System.NullReferenceException>, mais la levée d’exceptions dans des blocs `finally` doit être évitée, dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="c0915-111">Without the `null` check, the `finally` block could throw its own <xref:System.NullReferenceException>, but throwing exceptions in `finally` blocks should be avoided if it is possible.</span></span>  
  
 <span data-ttu-id="c0915-112">Une connexion de base de données est également susceptible d’être fermée dans un bloc `finally`.</span><span class="sxs-lookup"><span data-stu-id="c0915-112">A database connection is another good candidate for being closed in a `finally` block.</span></span> <span data-ttu-id="c0915-113">Le nombre de connexions à un serveur de base de données étant parfois limité, vous devez fermer les connexions de base de données le plus rapidement possible.</span><span class="sxs-lookup"><span data-stu-id="c0915-113">Because the number of connections allowed to a database server is sometimes limited, you should close database connections as quickly as possible.</span></span> <span data-ttu-id="c0915-114">Si une exception est levée avant que vous puissiez fermer votre connexion, c’est un autre cas où il vaut mieux utiliser le bloc `finally` qu’attendre le nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="c0915-114">If an exception is thrown before you can close your connection, this is another case where using the `finally` block is better than waiting for garbage collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0915-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0915-115">See Also</span></span>  
 <span data-ttu-id="c0915-116">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c0915-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c0915-117">[Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/index.md) </span><span class="sxs-lookup"><span data-stu-id="c0915-117">[Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md) </span></span>  
 <span data-ttu-id="c0915-118">[Gestion des exceptions](../../../csharp/programming-guide/exceptions/exception-handling.md) </span><span class="sxs-lookup"><span data-stu-id="c0915-118">[Exception Handling](../../../csharp/programming-guide/exceptions/exception-handling.md) </span></span>  
 <span data-ttu-id="c0915-119">[using, instruction](../../../csharp/language-reference/keywords/using-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c0915-119">[using Statement](../../../csharp/language-reference/keywords/using-statement.md) </span></span>  
 <span data-ttu-id="c0915-120">[try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span><span class="sxs-lookup"><span data-stu-id="c0915-120">[try-catch](../../../csharp/language-reference/keywords/try-catch.md) </span></span>  
 <span data-ttu-id="c0915-121">[try-finally](../../../csharp/language-reference/keywords/try-finally.md) </span><span class="sxs-lookup"><span data-stu-id="c0915-121">[try-finally](../../../csharp/language-reference/keywords/try-finally.md) </span></span>  
 [<span data-ttu-id="c0915-122">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="c0915-122">try-catch-finally</span></span>](../../../csharp/language-reference/keywords/try-catch-finally.md)

