---
title: Covariance et contravariance (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 066d9a3c-aab7-4ea6-826d-0b1a85399c74
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e1282f84171fa75db9656634a83f7cd5d4b9ac82
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="covariance-and-contravariance-c"></a><span data-ttu-id="f15b8-102">Covariance et contravariance (C#)</span><span class="sxs-lookup"><span data-stu-id="f15b8-102">Covariance and Contravariance (C#)</span></span>
<span data-ttu-id="f15b8-103">En C#, la covariance et la contravariance permettent la conversion de références implicite pour les types tableau, les types délégués et les arguments de type générique.</span><span class="sxs-lookup"><span data-stu-id="f15b8-103">In C#, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="f15b8-104">La covariance conserve la compatibilité d’assignation et la contravariance l’inverse.</span><span class="sxs-lookup"><span data-stu-id="f15b8-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>  
  
 <span data-ttu-id="f15b8-105">Le code suivant illustre la différence entre la compatibilité d’assignation, la covariance et la contravariance.</span><span class="sxs-lookup"><span data-stu-id="f15b8-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>  
  
```csharp  
// Assignment compatibility.   
string str = "test";  
// An object of a more derived type is assigned to an object of a less derived type.   
object obj = str;  
  
// Covariance.   
IEnumerable<string> strings = new List<string>();  
// An object that is instantiated with a more derived type argument   
// is assigned to an object instantiated with a less derived type argument.   
// Assignment compatibility is preserved.   
IEnumerable<object> objects = strings;  
  
// Contravariance.             
// Assume that the following method is in the class:   
// static void SetObject(object o) { }   
Action<object> actObject = SetObject;  
// An object that is instantiated with a less derived type argument   
// is assigned to an object instantiated with a more derived type argument.   
// Assignment compatibility is reversed.   
Action<string> actString = actObject;  
```  
  
 <span data-ttu-id="f15b8-106">La covariance pour les tableaux permet la conversion implicite d’un tableau d’un type plus dérivé en un tableau d’un type moins dérivé.</span><span class="sxs-lookup"><span data-stu-id="f15b8-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="f15b8-107">Cette opération n’est cependant pas sécurisée au niveau des types, comme le montre l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="f15b8-107">But this operation is not type safe, as shown in the following code example.</span></span>  
  
```csharp  
object[] array = new String[10];  
// The following statement produces a run-time exception.  
// array[0] = 10;  
```  
  
 <span data-ttu-id="f15b8-108">La prise en charge de la covariance et la contravariance pour les groupes de méthodes permet la correspondance des signatures de méthode avec des types délégués.</span><span class="sxs-lookup"><span data-stu-id="f15b8-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="f15b8-109">Ceci vous permet d’affecter aux délégués non seulement les méthodes ayant des signatures correspondantes, mais aussi des méthodes qui retournent des types plus dérivés (covariance) ou qui acceptent des paramètres ayant des types moins dérivés (contravariance) que ceux spécifiés par le type délégué.</span><span class="sxs-lookup"><span data-stu-id="f15b8-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="f15b8-110">Pour plus d’informations, consultez [Variance dans les délégués (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) et [Utilisation de la variance dans les délégués (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="f15b8-110">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="f15b8-111">L’exemple de code suivant montre la prise en charge de la covariance et de la contravariance pour les groupes de méthode.</span><span class="sxs-lookup"><span data-stu-id="f15b8-111">The following code example shows covariance and contravariance support for method groups.</span></span>  
  
```csharp  
static object GetObject() { return null; }  
static void SetObject(object obj) { }  
  
static string GetString() { return ""; }  
static void SetString(string str) { }  
  
static void Test()  
{  
    // Covariance. A delegate specifies a return type as object,  
    // but you can assign a method that returns a string.  
    Func<object> del = GetString;  
  
    // Contravariance. A delegate specifies a parameter type as string,  
    // but you can assign a method that takes an object.  
    Action<string> del2 = SetObject;  
}  
```  
  
 <span data-ttu-id="f15b8-112">Dans le NET Framework 4 ou ultérieur, C# prend en charge la covariance et la contravariance dans les interfaces et les délégués génériques, et permet la conversion implicite de paramètres de type générique.</span><span class="sxs-lookup"><span data-stu-id="f15b8-112">In .NET Framework 4 or newer C# supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="f15b8-113">Pour plus d’informations, consultez [Variance dans les interfaces génériques (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) et [Variance dans les délégués (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="f15b8-113">For more information, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md) and [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
 <span data-ttu-id="f15b8-114">L’exemple de code suivant illustre la conversion de références implicite pour les interfaces génériques.</span><span class="sxs-lookup"><span data-stu-id="f15b8-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 <span data-ttu-id="f15b8-115">Une interface ou un délégué générique est dit de type *variant* si ses paramètres génériques sont déclarés covariants ou contravariants.</span><span class="sxs-lookup"><span data-stu-id="f15b8-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="f15b8-116">C# vous permet de créer vos propres interfaces et délégués de type variant.</span><span class="sxs-lookup"><span data-stu-id="f15b8-116">C# enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="f15b8-117">Pour plus d’informations, consultez [Création d’interfaces génériques de type variant (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) et [Variance dans les délégués (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="f15b8-117">For more information, see [Creating Variant Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md) and [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="f15b8-118">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="f15b8-118">Related Topics</span></span>  
  
|<span data-ttu-id="f15b8-119">Titre</span><span class="sxs-lookup"><span data-stu-id="f15b8-119">Title</span></span>|<span data-ttu-id="f15b8-120">Description</span><span class="sxs-lookup"><span data-stu-id="f15b8-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f15b8-121">Variance dans les interfaces génériques (C#)</span><span class="sxs-lookup"><span data-stu-id="f15b8-121">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="f15b8-122">Décrit la covariance et la contravariance dans les interfaces génériques et fournit la liste des interfaces génériques de type variant dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f15b8-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|  
|[<span data-ttu-id="f15b8-123">Création d’interfaces génériques de type variant (C#)</span><span class="sxs-lookup"><span data-stu-id="f15b8-123">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)|<span data-ttu-id="f15b8-124">Montre comment créer des interfaces de type variant personnalisées.</span><span class="sxs-lookup"><span data-stu-id="f15b8-124">Shows how to create custom variant interfaces.</span></span>|  
|[<span data-ttu-id="f15b8-125">Utilisation de la variance dans les interfaces pour les collections génériques (C#)</span><span class="sxs-lookup"><span data-stu-id="f15b8-125">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="f15b8-126">Montre comment la prise en charge de la covariance et de la contravariance dans les interfaces <xref:System.Collections.Generic.IEnumerable%601> et <xref:System.IComparable%601> peut vous aider à réutiliser du code.</span><span class="sxs-lookup"><span data-stu-id="f15b8-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|  
|[<span data-ttu-id="f15b8-127">Variance dans les délégués (C#)</span><span class="sxs-lookup"><span data-stu-id="f15b8-127">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)|<span data-ttu-id="f15b8-128">Présente la covariance et la contravariance dans les délégués génériques et non génériques, et fournit une liste des délégués génériques de type variant dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f15b8-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|  
|[<span data-ttu-id="f15b8-129">Utilisation de la variance dans les délégués (C#)</span><span class="sxs-lookup"><span data-stu-id="f15b8-129">Using Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)|<span data-ttu-id="f15b8-130">Montre comment utiliser la prise en charge de la covariance et de la contravariance dans les délégués non génériques pour faire correspondre des signatures de méthode avec des types délégués.</span><span class="sxs-lookup"><span data-stu-id="f15b8-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|  
|[<span data-ttu-id="f15b8-131">Utilisation de la variance pour les délégués génériques Func et Action (C#)</span><span class="sxs-lookup"><span data-stu-id="f15b8-131">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="f15b8-132">Montre comment la prise en charge de la covariance et de la contravariance dans les délégués `Func` et `Action` peut vous aider à réutiliser du code.</span><span class="sxs-lookup"><span data-stu-id="f15b8-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|

