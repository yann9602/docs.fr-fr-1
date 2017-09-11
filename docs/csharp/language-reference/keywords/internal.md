---
title: "internal (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- internal_CSharpKeyword
- internal
dev_langs:
- CSharp
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
caps.latest.revision: 23
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
ms.openlocfilehash: 5674a78e2c317357c31d9e2661a25ce86cbf4f6a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="internal-c-reference"></a><span data-ttu-id="58740-102">internal (référence C#)</span><span class="sxs-lookup"><span data-stu-id="58740-102">internal (C# Reference)</span></span>
<span data-ttu-id="58740-103">Le mot clé `internal` est un [modificateur d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) pour les types et les membres de type.</span><span class="sxs-lookup"><span data-stu-id="58740-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> <span data-ttu-id="58740-104">Les types et les membres internes (internal) sont accessibles uniquement dans les fichiers d’un même assembly, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="58740-104">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  
  
 <span data-ttu-id="58740-105">Les types et les membres ayant le modificateur d’accès `protected internal` sont accessibles à partir de l’assembly actuel ou des types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="58740-105">Types or members that have access modifier `protected internal` can be accessed from the current assembly or from types that are derived from the containing class.</span></span>  
  
 <span data-ttu-id="58740-106">Pour obtenir une comparaison de `internal` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) et [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="58740-106">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="58740-107">Pour plus d’informations, consultez [Assemblys et le Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span><span class="sxs-lookup"><span data-stu-id="58740-107">For more information about assemblies, see [Assemblies and the Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
 <span data-ttu-id="58740-108">L’accès interne est fréquemment utilisé lors du développement basé sur les composants, car il permet à un groupe de composants de collaborer de façon privée sans être exposés au reste du code de l’application.</span><span class="sxs-lookup"><span data-stu-id="58740-108">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="58740-109">Par exemple, un framework de création d’interfaces graphiques utilisateur peut fournir les classes `Control` et `Form` qui coopèrent en utilisant des membres ayant un accès interne.</span><span class="sxs-lookup"><span data-stu-id="58740-109">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="58740-110">Étant donné que ces membres sont internes, ils ne sont pas exposés au code qui utilise le framework.</span><span class="sxs-lookup"><span data-stu-id="58740-110">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="58740-111">Le fait de référencer un type ou un membre avec accès interne en dehors de l’assembly dans lequel il a été défini constitue une erreur.</span><span class="sxs-lookup"><span data-stu-id="58740-111">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58740-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="58740-112">Example</span></span>  
 <span data-ttu-id="58740-113">Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="58740-113">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="58740-114">Le premier fichier contient la classe de base interne `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="58740-114">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="58740-115">Dans le deuxième fichier, une tentative d’instanciation de `BaseClass` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="58740-115">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
```  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="58740-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="58740-116">Example</span></span>  
 <span data-ttu-id="58740-117">Dans cet exemple, utilisez les mêmes fichiers que vous avez utilisés dans l’exemple 1, et remplacez le niveau d’accessibilité `BaseClass` par `public`.</span><span class="sxs-lookup"><span data-stu-id="58740-117">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="58740-118">Remplacez également le niveau d’accessibilité du membre `IntM` par `internal`.</span><span class="sxs-lookup"><span data-stu-id="58740-118">Also change the accessibility level of the member `IntM` to `internal`.</span></span> <span data-ttu-id="58740-119">Dans ce cas, vous pouvez instancier la classe, mais vous ne pouvez pas accéder au membre interne.</span><span class="sxs-lookup"><span data-stu-id="58740-119">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
```  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="58740-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="58740-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="58740-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58740-121">See Also</span></span>  
 <span data-ttu-id="58740-122">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="58740-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="58740-123">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="58740-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="58740-124">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="58740-124">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="58740-125">[Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="58740-125">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="58740-126">[Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="58740-126">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="58740-127">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="58740-127">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="58740-128">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="58740-128">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="58740-129">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="58740-129">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 [<span data-ttu-id="58740-130">protected</span><span class="sxs-lookup"><span data-stu-id="58740-130">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)

