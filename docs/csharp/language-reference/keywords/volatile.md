---
title: "volatile (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- volatile_CSharpKeyword
- volatile
dev_langs:
- CSharp
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 29
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
ms.openlocfilehash: c8f9fba15991197be885a973435089098a57db87
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="volatile-c-reference"></a><span data-ttu-id="ca7df-102">volatile (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ca7df-102">volatile (C# Reference)</span></span>
<span data-ttu-id="ca7df-103">Le mot clé `volatile` indique qu’un champ peut être modifié par plusieurs threads qui s’exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="ca7df-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="ca7df-104">Les champs qui sont déclarés `volatile` ne sont pas soumis aux optimisations du compilateur qui supposent l’accès par un seul thread.</span><span class="sxs-lookup"><span data-stu-id="ca7df-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="ca7df-105">Cela garantit que la valeur la plus à jour est présente dans le champ à tout moment.</span><span class="sxs-lookup"><span data-stu-id="ca7df-105">This ensures that the most up-to-date value is present in the field at all times.</span></span>  
  
 <span data-ttu-id="ca7df-106">Le modificateur `volatile` est généralement utilisé pour un champ auquel accèdent plusieurs threads sans utiliser l’instruction [lock](../../../csharp/language-reference/keywords/lock-statement.md) pour sérialiser l’accès.</span><span class="sxs-lookup"><span data-stu-id="ca7df-106">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="ca7df-107">Le mot clé `volatile` peut être appliqué aux champs des types suivants :</span><span class="sxs-lookup"><span data-stu-id="ca7df-107">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="ca7df-108">Types référence.</span><span class="sxs-lookup"><span data-stu-id="ca7df-108">Reference types.</span></span>  
  
-   <span data-ttu-id="ca7df-109">Types pointeur (dans un contexte unsafe).</span><span class="sxs-lookup"><span data-stu-id="ca7df-109">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="ca7df-110">Notez que, même si le pointeur lui-même peut être volatile, l’objet sur lequel il pointe ne le peut pas.</span><span class="sxs-lookup"><span data-stu-id="ca7df-110">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="ca7df-111">En d’autres termes, vous ne pouvez pas déclarer un pointeur vers un objet volatile.</span><span class="sxs-lookup"><span data-stu-id="ca7df-111">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="ca7df-112">Types tels que sbyte, byte, short, ushort, int, uint, char, float et bool.</span><span class="sxs-lookup"><span data-stu-id="ca7df-112">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="ca7df-113">Type enum avec l’un des types de base suivants : byte, sbyte, short, ushort, int ou uint.</span><span class="sxs-lookup"><span data-stu-id="ca7df-113">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="ca7df-114">Paramètres de type générique connus comme des types référence.</span><span class="sxs-lookup"><span data-stu-id="ca7df-114">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="ca7df-115">Voir <xref:System.IntPtr> et <xref:System.UIntPtr>.</span><span class="sxs-lookup"><span data-stu-id="ca7df-115"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="ca7df-116">Le mot clé volatile ne peut s’appliquer qu’aux champs d’une classe ou d’une structure.</span><span class="sxs-lookup"><span data-stu-id="ca7df-116">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="ca7df-117">Les variables locales ne peuvent pas être déclarées `volatile`.</span><span class="sxs-lookup"><span data-stu-id="ca7df-117">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca7df-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="ca7df-118">Example</span></span>  
 <span data-ttu-id="ca7df-119">L’exemple ci-dessous montre comment déclarer une variable de champ public comme `volatile`.</span><span class="sxs-lookup"><span data-stu-id="ca7df-119">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 <span data-ttu-id="ca7df-120">[!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ca7df-120">[!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca7df-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="ca7df-121">Example</span></span>  
 <span data-ttu-id="ca7df-122">L’exemple suivant montre comment il est possible de créer un thread auxiliaire ou de travail et de l’utiliser pour effectuer le traitement en parallèle avec le thread principal.</span><span class="sxs-lookup"><span data-stu-id="ca7df-122">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="ca7df-123">Pour obtenir des informations générales sur le multithreading, consultez [Threading](../../../standard/threading/index.md) et [Thread](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span><span class="sxs-lookup"><span data-stu-id="ca7df-123">For background information about multithreading, see [Threading](../../../standard/threading/index.md) and [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="ca7df-124">[!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ca7df-124">[!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ca7df-125">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ca7df-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ca7df-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca7df-126">See Also</span></span>  
 <span data-ttu-id="ca7df-127">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ca7df-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ca7df-128">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ca7df-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ca7df-129">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="ca7df-129">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="ca7df-130">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="ca7df-130">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

