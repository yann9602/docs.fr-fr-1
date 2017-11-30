---
title: "protégée interne (référence c#)"
ms.date: 11/15/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
author: sputier
ms.author: wiwagn
ms.openlocfilehash: f9004a5e8d65179c9ff2e30688e63c14c95ab431
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="9389e-102">protégée interne (référence c#)</span><span class="sxs-lookup"><span data-stu-id="9389e-102">protected internal (C# Reference)</span></span>
<span data-ttu-id="9389e-103">Le `protected internal` combinaison de mots clés est un modificateur d’accès du membre.</span><span class="sxs-lookup"><span data-stu-id="9389e-103">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="9389e-104">Un membre interne protégé est accessible à partir de l’assembly actuel ou des types qui sont dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="9389e-104">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="9389e-105">Pour obtenir une comparaison de `protected internal` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9389e-105">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
   
## <a name="example"></a><span data-ttu-id="9389e-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="9389e-106">Example</span></span>  
 <span data-ttu-id="9389e-107">Un membre interne d’une classe de base est accessible à partir de n’importe quel type au sein de son assembly conteneur.</span><span class="sxs-lookup"><span data-stu-id="9389e-107">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="9389e-108">Il est également accessible dans une classe dérivée, située dans un autre assembly que si l’accès s’effectue via une variable du type de classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9389e-108">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="9389e-109">Prenons l’exemple de l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="9389e-109">For example, consider the following code segment:</span></span>  

```
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   protected internal int myValue = 0;  
}

class TestAccess 
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}  
```  
  
```  
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass : BaseClass   
{  
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10; 

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
} 
```  
 <span data-ttu-id="9389e-110">Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="9389e-110">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span> <span data-ttu-id="9389e-111">Le premier fichier contient une classe de base publique, `BaseClass`et une autre classe, `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="9389e-111">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="9389e-112">`BaseClass`possède un membre interne protégé, `myValue`, qui est accessible par le `TestAccess` type.</span><span class="sxs-lookup"><span data-stu-id="9389e-112">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span> <span data-ttu-id="9389e-113">Dans le deuxième fichier, une tentative d’accès `myValue` via une instance de `BaseClass` génère une erreur, lors d’un accès à ce membre via une instance d’une classe dérivée, `DerivedClass` réussira.</span><span class="sxs-lookup"><span data-stu-id="9389e-113">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span> 

 <span data-ttu-id="9389e-114">Les membres de struct ne peut pas être `protected internal` car le struct ne peut pas être hérité.</span><span class="sxs-lookup"><span data-stu-id="9389e-114">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9389e-115">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9389e-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9389e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9389e-116">See Also</span></span>  
 <span data-ttu-id="9389e-117">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9389e-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9389e-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9389e-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9389e-119">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="9389e-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="9389e-120">[Modificateurs d’accès](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="9389e-120">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="9389e-121">[Niveaux d’accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="9389e-121">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="9389e-122">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="9389e-122">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="9389e-123">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="9389e-123">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="9389e-124">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="9389e-124">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 <span data-ttu-id="9389e-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span><span class="sxs-lookup"><span data-stu-id="9389e-125">[internal](../../../csharp/language-reference/keywords/internal.md) </span></span>  
 <span data-ttu-id="9389e-126">[Problèmes de sécurité pour les mots clés virtuels internes](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="9389e-126">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>
