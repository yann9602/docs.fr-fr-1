---
title: Guide pratique pour intercepter une exception non-CLS
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 473cace033983915c66647d14cae16dc7f5d5b9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="d51da-102">Guide pratique pour intercepter une exception non-CLS</span><span class="sxs-lookup"><span data-stu-id="d51da-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="d51da-103">Certains langages .NET, dont C++/CLI, permettent aux objets de lever des exceptions qui ne dérivent pas d’<xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="d51da-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="d51da-104">De telles exceptions sont appelées *exceptions non-CLS* ou *non exceptions*.</span><span class="sxs-lookup"><span data-stu-id="d51da-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="d51da-105">Dans [!INCLUDE[csprcs](~/includes/csprcs-md.md)], vous ne pouvez pas lever d’exceptions non-CLS, mais vous pouvez les intercepter de deux façons :</span><span class="sxs-lookup"><span data-stu-id="d51da-105">In [!INCLUDE[csprcs](~/includes/csprcs-md.md)] you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
-   <span data-ttu-id="d51da-106">Dans un bloc `catch (Exception e)`, en tant que <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span><span class="sxs-lookup"><span data-stu-id="d51da-106">Within a `catch (Exception e)` block as a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
     <span data-ttu-id="d51da-107">Par défaut, un assembly [!INCLUDE[csprcs](~/includes/csprcs-md.md)] intercepte les exceptions non-CLS comme des exceptions encapsulées.</span><span class="sxs-lookup"><span data-stu-id="d51da-107">By default, a [!INCLUDE[csprcs](~/includes/csprcs-md.md)] assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="d51da-108">Utilisez cette méthode si vous devez accéder à l’exception d’origine, qui est accessible via la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A>.</span><span class="sxs-lookup"><span data-stu-id="d51da-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span> <span data-ttu-id="d51da-109">La procédure située plus loin dans cette rubrique explique comment intercepter les exceptions de cette manière.</span><span class="sxs-lookup"><span data-stu-id="d51da-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
-   <span data-ttu-id="d51da-110">Dans un bloc catch général (un bloc catch sans type d’exception spécifié) qui est placé après un bloc `catch (Exception)` ou `catch (Exception e)`.</span><span class="sxs-lookup"><span data-stu-id="d51da-110">Within a general catch block (a catch block without an exception type specified) that is put after a `catch (Exception)` or `catch (Exception e)` block.</span></span>  
  
     <span data-ttu-id="d51da-111">Utilisez cette méthode lorsque vous souhaitez effectuer une action (comme écrire dans un fichier journal) en réponse à des exceptions non-CLS, et que vous n’avez pas besoin d’accéder aux informations de l’exception.</span><span class="sxs-lookup"><span data-stu-id="d51da-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="d51da-112">Par défaut, le common language runtime inclut dans un wrapper toutes les exceptions.</span><span class="sxs-lookup"><span data-stu-id="d51da-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="d51da-113">Pour désactiver ce comportement, ajoutez cet attribut d’assembly à votre code, généralement dans le fichier AssemblyInfo.cs : `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="d51da-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="d51da-114">Comment intercepter une exception non-CLS</span><span class="sxs-lookup"><span data-stu-id="d51da-114">To catch a non-CLS exception</span></span>  
  
1.  <span data-ttu-id="d51da-115">Dans un `catch(Exception e) block`, utilisez le mot clé `as` pour tester si `e` peut être casté en <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span><span class="sxs-lookup"><span data-stu-id="d51da-115">Within a `catch(Exception e) block`, use the `as` keyword to test whether `e` can be cast to a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
2.  <span data-ttu-id="d51da-116">Accédez à l’exception d’origine via la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A>.</span><span class="sxs-lookup"><span data-stu-id="d51da-116">Access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d51da-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="d51da-117">Example</span></span>  
 <span data-ttu-id="d51da-118">L’exemple suivant montre comment intercepter une exception non-CLS levée à partir d’une bibliothèque de classes écrite en C++ /CLR.</span><span class="sxs-lookup"><span data-stu-id="d51da-118">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLR.</span></span> <span data-ttu-id="d51da-119">Notez que dans cet exemple, le code client [!INCLUDE[csprcs](~/includes/csprcs-md.md)] sait par avance que le type d’exception levé est un <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d51da-119">Note that in this example, the [!INCLUDE[csprcs](~/includes/csprcs-md.md)] client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d51da-120">Vous pouvez caster la propriété <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> en son type d’origine, tant que celui-ci est accessible à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="d51da-120">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property back its original type as long as that type is accessible from your code.</span></span>  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## <a name="see-also"></a><span data-ttu-id="d51da-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d51da-121">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>  
 [<span data-ttu-id="d51da-122">Exceptions et gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="d51da-122">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
