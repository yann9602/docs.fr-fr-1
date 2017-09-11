---
title: "extern (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- extern_CSharpKeyword
- extern
dev_langs:
- CSharp
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
caps.latest.revision: 26
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
ms.openlocfilehash: e499ade5ec8a9339b0d425c59809cf7c177466fb
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="extern-c-reference"></a><span data-ttu-id="323b4-102">extern (référence C#)</span><span class="sxs-lookup"><span data-stu-id="323b4-102">extern (C# Reference)</span></span>
<span data-ttu-id="323b4-103">Le modificateur `extern` permet de déclarer une méthode qui est implémentée en externe.</span><span class="sxs-lookup"><span data-stu-id="323b4-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="323b4-104">Le modificateur `extern` est souvent utilisé avec l'attribut `DllImport` lors de l'utilisation de services Interop à appeler dans du code non managé.</span><span class="sxs-lookup"><span data-stu-id="323b4-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="323b4-105">Dans ce cas, la méthode doit également être déclarée comme `static`, comme indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="323b4-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>  
  
```  
[DllImport("avifil32.dll")]  
private static extern void AVIFileInit();  
```  
  
 <span data-ttu-id="323b4-106">Le mot clé `extern` peut également définir un alias d'assembly externe, permettant ainsi de référencer différentes versions du même composant à partir d'un seul assembly.</span><span class="sxs-lookup"><span data-stu-id="323b4-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="323b4-107">Pour plus d’informations, consultez [extern alias](../../../csharp/language-reference/keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="323b4-107">For more information, see [extern alias](../../../csharp/language-reference/keywords/extern-alias.md).</span></span>  
  
 <span data-ttu-id="323b4-108">C’est une erreur d’utiliser conjointement les modificateurs [abstract](../../../csharp/language-reference/keywords/abstract.md) et `extern` pour modifier le même membre.</span><span class="sxs-lookup"><span data-stu-id="323b4-108">It is an error to use the [abstract](../../../csharp/language-reference/keywords/abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="323b4-109">L'utilisation du modificateur `extern` signifie que la méthode est implémentée en dehors du code C#, tandis que l'utilisation du modificateur `abstract` signifie que l'implémentation de la méthode n'est pas effectuée dans la classe.</span><span class="sxs-lookup"><span data-stu-id="323b4-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>  
  
 <span data-ttu-id="323b4-110">L'utilisation du mot clé extern est plus restreinte dans C# que dans C++.</span><span class="sxs-lookup"><span data-stu-id="323b4-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="323b4-111">Pour comparer son utilisation dans C# et C++, consultez : Utilisation d'extern pour spécifier la liaison dans le Guide de référence du langage C++.</span><span class="sxs-lookup"><span data-stu-id="323b4-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>  
  
## <a name="example"></a><span data-ttu-id="323b4-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="323b4-112">Example</span></span>  
 <span data-ttu-id="323b4-113">**Example 1.**</span><span class="sxs-lookup"><span data-stu-id="323b4-113">**Example 1.**</span></span> <span data-ttu-id="323b4-114">Dans cet exemple, le programme reçoit une chaîne provenant de l’utilisateur et l’affiche dans une boîte de message.</span><span class="sxs-lookup"><span data-stu-id="323b4-114">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="323b4-115">Le programme utilise la méthode `MessageBox` importée de la bibliothèque User32.dll.</span><span class="sxs-lookup"><span data-stu-id="323b4-115">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>  
  
 <span data-ttu-id="323b4-116">[!code-cs[csrefKeywordsModifiers#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/extern_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="323b4-116">[!code-cs[csrefKeywordsModifiers#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/extern_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="323b4-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="323b4-117">Example</span></span>  
 <span data-ttu-id="323b4-118">**Example 2.**</span><span class="sxs-lookup"><span data-stu-id="323b4-118">**Example 2.**</span></span> <span data-ttu-id="323b4-119">Cet exemple illustre un programme C# qui fait appel à une bibliothèque C (une DLL native).</span><span class="sxs-lookup"><span data-stu-id="323b4-119">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>  
  
 1. <span data-ttu-id="323b4-120">Créez le fichier C suivant et nommez-le `cmdll.c` :</span><span class="sxs-lookup"><span data-stu-id="323b4-120">Create the following C file and name it `cmdll.c`:</span></span>  
  
```  
// cmdll.c  
// Compile with: /LD  
int __declspec(dllexport) SampleMethod(int i)  
{  
   return i*10;  
}  
```  
  
## <a name="example"></a><span data-ttu-id="323b4-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="323b4-121">Example</span></span>  
 2. <span data-ttu-id="323b4-122">Ouvrez une fenêtre d’invite de commandes d’outils natifs Visual Studio x64 (ou x32) à partir du répertoire d’installation de Visual Studio et compilez le fichier `cmdll.c` en tapant **cl /LD cmdll.c** à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="323b4-122">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl /LD cmdll.c** at the command prompt.</span></span>  
  
 3. <span data-ttu-id="323b4-123">Dans le même répertoire, créez le fichier C# suivant et nommez-le `cm.cs` :</span><span class="sxs-lookup"><span data-stu-id="323b4-123">In the same directory, create the following C# file and name it `cm.cs`:</span></span>  
  
```  
// cm.cs  
using System;  
using System.Runtime.InteropServices;  
public class MainClass   
{  
   [DllImport("Cmdll.dll")]  
   public static extern int SampleMethod(int x);  
  
   static void Main()   
   {  
      Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="323b4-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="323b4-124">Example</span></span>  
 3. <span data-ttu-id="323b4-125">Ouvrez une fenêtre d'invite de commandes d'outils natifs Visual Studio x64 (ou x32) à partir du répertoire d'installation de Visual Studio et compilez le fichier `cm.cs` en tapant :</span><span class="sxs-lookup"><span data-stu-id="323b4-125">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>  
  
> <span data-ttu-id="323b4-126">**csc cm.cs** (pour l’invite de commandes x64)</span><span class="sxs-lookup"><span data-stu-id="323b4-126">**csc cm.cs** (for the x64 command prompt)</span></span>   
>  <span data-ttu-id="323b4-127">-ou-</span><span class="sxs-lookup"><span data-stu-id="323b4-127">—or—</span></span>  
> <span data-ttu-id="323b4-128">**csc /platform:x 86 cm.cs** (pour l’invite de commandes x32)</span><span class="sxs-lookup"><span data-stu-id="323b4-128">**csc /platform:x86 cm.cs** (for the x32 command prompt)</span></span>  
  
 <span data-ttu-id="323b4-129">Cette opération crée le fichier exécutable `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="323b4-129">This will create the executable file `cm.exe`.</span></span>  
  
 4. <span data-ttu-id="323b4-130">Exécutez `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="323b4-130">Run `cm.exe`.</span></span> <span data-ttu-id="323b4-131">La méthode `SampleMethod` passe la valeur 5 au fichier DLL, qui retourne la valeur multipliée par 10.</span><span class="sxs-lookup"><span data-stu-id="323b4-131">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="323b4-132">Le programme génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="323b4-132">The program produces the following output:</span></span>  
  
```  
SampleMethod() returns 50.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="323b4-133">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="323b4-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="323b4-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="323b4-134">See Also</span></span>  
 <span data-ttu-id="323b4-135"><xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="323b4-135"><xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName></span></span>   
 <span data-ttu-id="323b4-136">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="323b4-136">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="323b4-137">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="323b4-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="323b4-138">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="323b4-138">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="323b4-139">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="323b4-139">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

