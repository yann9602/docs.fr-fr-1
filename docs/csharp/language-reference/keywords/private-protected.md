---
title: "privés protégés (référence c#)"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: 5f7abd2569d5bad5af64161042e4e5d21e741c8c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="4d9fe-102">privés protégés (référence c#)</span><span class="sxs-lookup"><span data-stu-id="4d9fe-102">private protected (C# Reference)</span></span>
<span data-ttu-id="4d9fe-103">Le `private protected` combinaison de mots clés est un modificateur d’accès du membre.</span><span class="sxs-lookup"><span data-stu-id="4d9fe-103">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="4d9fe-104">Un membre protégé privé est accessible par les types dérivés de la classe conteneur, mais uniquement au sein de son assembly conteneur.</span><span class="sxs-lookup"><span data-stu-id="4d9fe-104">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="4d9fe-105">Pour obtenir une comparaison de `private protected` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4d9fe-105">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="4d9fe-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d9fe-106">Example</span></span>  
 <span data-ttu-id="4d9fe-107">Un membre privé protégé d’une classe de base est accessible à partir des types dérivés de l’assembly conteneur uniquement si le type statique de la variable est le type de classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="4d9fe-107">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="4d9fe-108">Prenons l’exemple de l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="4d9fe-108">For example, consider the following code segment:</span></span>  
  
 ```
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```  
 // Assembly2.cs  
 // Compile with: /reference:Assembly1.dll  
 class DerivedClass2 : BaseClass
 {
     void Access()
     {
         // Error CS0122, because myValue can only be
         // accessed by types in Assembly1
         // myValue = 10;
     }
 }
```  
 <span data-ttu-id="4d9fe-109">Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="4d9fe-109">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="4d9fe-110">Le premier fichier contient une classe de base publique, `BaseClass`et un type dérivé, `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="4d9fe-110">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="4d9fe-111">`BaseClass`possède un membre privé protégé, `myValue`, qui `DerivedClass1` tente d’accéder de deux manières.</span><span class="sxs-lookup"><span data-stu-id="4d9fe-111">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="4d9fe-112">La première tentative d’accès `myValue` via une instance de `BaseClass` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="4d9fe-112">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="4d9fe-113">Toutefois, la tentative de l’utiliser comme un membre hérité dans `DerivedClass1` réussira.</span><span class="sxs-lookup"><span data-stu-id="4d9fe-113">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>
<span data-ttu-id="4d9fe-114">Dans le deuxième fichier, une tentative d’accès `myValue` qu’un membre hérité de `DerivedClass2` génère une erreur, car il est accessible uniquement par les types dérivés dans Assembly1.</span><span class="sxs-lookup"><span data-stu-id="4d9fe-114">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span> 

 <span data-ttu-id="4d9fe-115">Les membres de struct ne peut pas être `private protected` car le struct ne peut pas être hérité.</span><span class="sxs-lookup"><span data-stu-id="4d9fe-115">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4d9fe-116">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="4d9fe-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4d9fe-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d9fe-117">See Also</span></span>  
 <span data-ttu-id="4d9fe-118">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4d9fe-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4d9fe-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4d9fe-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4d9fe-120">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="4d9fe-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="4d9fe-121">[Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="4d9fe-121">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="4d9fe-122">[Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="4d9fe-122">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="4d9fe-123">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="4d9fe-123">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="4d9fe-124">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="4d9fe-124">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="4d9fe-125">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="4d9fe-125">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="4d9fe-126">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="4d9fe-126">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="4d9fe-127">[Problèmes de sécurité pour les mots clés virtuels internes](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="4d9fe-127">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
