---
title: "using, directive (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 02c50b1e7a54d776985b60570c898e7d0739c44c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="4e1a7-102">using, directive (référence C#)</span><span class="sxs-lookup"><span data-stu-id="4e1a7-102">using Directive (C# Reference)</span></span>
<span data-ttu-id="4e1a7-103">La directive `using` a trois utilisations :</span><span class="sxs-lookup"><span data-stu-id="4e1a7-103">The `using` directive has three uses:</span></span>  
  
-   <span data-ttu-id="4e1a7-104">Pour autoriser l'utilisation de types dans un espace de noms pour ne pas avoir à qualifier l'utilisation d'un type dans cet espace de noms :</span><span class="sxs-lookup"><span data-stu-id="4e1a7-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   <span data-ttu-id="4e1a7-105">Pour vous permettre d’accéder aux membres statiques d’un type sans devoir qualifier l’accès avec le nom du type.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-105">To allow you to access static members of a type without having to qualify the access with the type name.</span></span> 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    <span data-ttu-id="4e1a7-106">Pour plus d’informations, consultez la [directive using static](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="4e1a7-106">For more information, see the [using static directive](using-static.md).</span></span>

-   <span data-ttu-id="4e1a7-107">Pour créer un alias pour un espace de noms ou un type.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="4e1a7-108">Cela s’appelle une *directive using alias*.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-108">This is called a *using alias directive*.</span></span>  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 <span data-ttu-id="4e1a7-109">Le mot clé `using` est également utilisé pour créer des *instructions using<xref:System.IDisposable>, qui garantissent que les objets*  tels que les fichiers et les polices sont gérés correctement.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="4e1a7-110">Pour plus d’informations, consultez [Instruction using](../../../csharp/language-reference/keywords/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e1a7-110">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) for more information.</span></span>  
  
## <a name="using-static-type"></a><span data-ttu-id="4e1a7-111">Utilisation du type static</span><span class="sxs-lookup"><span data-stu-id="4e1a7-111">Using Static Type</span></span>  
 <span data-ttu-id="4e1a7-112">Vous pouvez accéder aux membres statiques d'un type sans devoir qualifier l'accès avec le nom du type :</span><span class="sxs-lookup"><span data-stu-id="4e1a7-112">You can access static members of a type without having to qualify the access with the type name:</span></span>  
  
```csharp  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="4e1a7-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="4e1a7-113">Remarks</span></span>  
 <span data-ttu-id="4e1a7-114">La portée d'une directive `using` se limite au fichier dans lequel elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>  
  
 <span data-ttu-id="4e1a7-115">Créez un alias `using` pour faciliter la qualification d'un identificateur pour un espace de noms ou un type.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-115">Create a `using` alias to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="4e1a7-116">Le côté droit d'une directive d'alias using doit toujours être un type complet quelles que soient les directives using placées avant.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-116">The right side of a using alias directive must always be a fully-qualified type regardless of the using directives that come before it.</span></span>  
  
 <span data-ttu-id="4e1a7-117">Créez une directive `using` pour utiliser les types dans un espace de noms sans avoir à spécifier l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-117">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="4e1a7-118">Une directive `using` ne vous donne pas accès à des espaces de noms imbriqués dans l'espace de noms que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-118">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>  
  
 <span data-ttu-id="4e1a7-119">Les espaces de noms sont organisés en deux catégories : définis par l'utilisateur et définis par le système.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-119">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="4e1a7-120">Les espaces de noms définis par l'utilisateur sont des espaces de noms définis dans votre code.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-120">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="4e1a7-121">Pour obtenir la liste des espaces de noms définis par le système, consultez [.NET Framework Class Library Overview](../../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4e1a7-121">For a list of the system-defined namespaces, see [.NET Framework Class Library Overview](../../../standard/class-library-overview.md).</span></span>  
  
 <span data-ttu-id="4e1a7-122">Pour obtenir des exemples de références de méthodes dans d’autres assemblys, consultez [créer et utiliser les assemblys à l’aide de la ligne de commande](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="4e1a7-122">For examples on referencing methods in other assemblies, see [Create and Use Assemblies Using the Command Line](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="4e1a7-123">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="4e1a7-123">Example 1</span></span>  
  
 <span data-ttu-id="4e1a7-124">L'exemple suivant montre comment définir et utiliser un alias `using` pour un espace de noms :</span><span class="sxs-lookup"><span data-stu-id="4e1a7-124">The following example shows how to define and use a `using` alias for a namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 <span data-ttu-id="4e1a7-125">Une directive d'alias using ne peut pas avoir un type générique ouvert sur le côté droit.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-125">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="4e1a7-126">Par exemple, vous ne pouvez pas créer un alias using pour un List\<T>, mais vous pouvez en créer un pour un List\<int>.</span><span class="sxs-lookup"><span data-stu-id="4e1a7-126">For example, you cannot create a using alias for a List\<T>, but you can create one for a List\<int>.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="4e1a7-127">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="4e1a7-127">Example 2</span></span>  
  
 <span data-ttu-id="4e1a7-128">L'exemple suivant montre comment définir une directive `using` et un alias `using` pour une classe :</span><span class="sxs-lookup"><span data-stu-id="4e1a7-128">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="4e1a7-129">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4e1a7-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e1a7-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e1a7-130">See Also</span></span>  
 [<span data-ttu-id="4e1a7-131">Référence C#</span><span class="sxs-lookup"><span data-stu-id="4e1a7-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4e1a7-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="4e1a7-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4e1a7-133">Utilisation d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="4e1a7-133">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [<span data-ttu-id="4e1a7-134">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="4e1a7-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4e1a7-135">Mots clés d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="4e1a7-135">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="4e1a7-136">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="4e1a7-136">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="4e1a7-137">using, instruction</span><span class="sxs-lookup"><span data-stu-id="4e1a7-137">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
