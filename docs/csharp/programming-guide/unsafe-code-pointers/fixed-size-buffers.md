---
title: "Mémoires tampons de taille fixe (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3f99c2c6d477fca988fcca77de5ca5c2f8addd4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="02725-102">Mémoires tampons de taille fixe (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="02725-102">Fixed Size Buffers (C# Programming Guide)</span></span>
<span data-ttu-id="02725-103">En C#, vous pouvez utiliser l’instruction [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) pour créer une mémoire tampon avec un tableau de taille fixe dans une structure de données.</span><span class="sxs-lookup"><span data-stu-id="02725-103">In C#, you can use the [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="02725-104">Cela est utile lorsque vous utilisez du code existant, tel que du code écrit dans d’autres langages, des DLL préexistantes ou des projets COM.</span><span class="sxs-lookup"><span data-stu-id="02725-104">This is useful when you are working with existing code, such as code written in other languages, pre-existing DLLs or COM projects.</span></span> <span data-ttu-id="02725-105">Le tableau fixe peut accepter tous les attributs ou modificateurs qui sont autorisés pour les membres de structures régulières.</span><span class="sxs-lookup"><span data-stu-id="02725-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="02725-106">La seule restriction est que le tableau doit être de type `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="02725-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a><span data-ttu-id="02725-107">Notes</span><span class="sxs-lookup"><span data-stu-id="02725-107">Remarks</span></span>  
 <span data-ttu-id="02725-108">Dans les versions antérieures de C#, il était difficile de déclarer une structure de taille fixe de style C++, car un struct C# qui contient un tableau ne contient pas les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="02725-108">In early versions of C#, declaring a C++ style fixed-size structure was difficult because a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="02725-109">Le struct contient une référence aux éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="02725-109">Instead, the struct contains a reference to the elements.</span></span>  
  
 <span data-ttu-id="02725-110">Avec le langage C# 2.0, il est désormais possible d’incorporer un tableau de taille fixe dans un [struct](../../../csharp/language-reference/keywords/struct.md) lorsqu’il est utilisé dans un bloc de code [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="02725-110">C# 2.0 added the ability to embed an array of fixed size in a [struct](../../../csharp/language-reference/keywords/struct.md) when it is used in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) code block.</span></span>  
  
 <span data-ttu-id="02725-111">Par exemple, avant C# 2.0, le `struct` suivant avait une taille de 8 octets.</span><span class="sxs-lookup"><span data-stu-id="02725-111">For example, before C# 2.0, the following `struct` would be 8 bytes in size.</span></span> <span data-ttu-id="02725-112">Le tableau `pathName` est une référence au tableau alloué par tas :</span><span class="sxs-lookup"><span data-stu-id="02725-112">The `pathName` array is a reference to the heap-allocated array:</span></span>  
  
 [!code-csharp[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 <span data-ttu-id="02725-113">Avec C# 2.0, un `struct` peut maintenant contenir un tableau incorporé.</span><span class="sxs-lookup"><span data-stu-id="02725-113">Beginning with C# 2.0, a `struct` can contain an embedded array.</span></span> <span data-ttu-id="02725-114">Dans l’exemple suivant, le tableau `fixedBuffer` a une taille fixe.</span><span class="sxs-lookup"><span data-stu-id="02725-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="02725-115">Pour accéder aux éléments du tableau, vous devez utiliser une instruction `fixed` pour établir un pointeur vers le premier élément.</span><span class="sxs-lookup"><span data-stu-id="02725-115">To access the elements of the array, you use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="02725-116">L’instruction `fixed` épingle une instance de `fixedBuffer` à un emplacement spécifique de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="02725-116">The `fixed` statement pins an instance of `fixedBuffer` to a specific location in memory.</span></span>  
  
 [!code-csharp[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 <span data-ttu-id="02725-117">La taille du tableau `char` de 128 éléments est de 256 octets.</span><span class="sxs-lookup"><span data-stu-id="02725-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="02725-118">Les mémoires tampons [char](../../../csharp/language-reference/keywords/char.md) de taille fixe acceptent toujours deux octets par caractère, quel que soit l’encodage.</span><span class="sxs-lookup"><span data-stu-id="02725-118">Fixed size [char](../../../csharp/language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="02725-119">Ceci est vrai même lorsque les mémoires tampons char sont marshalées vers des méthodes ou des structs d’API avec `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="02725-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="02725-120">Pour plus d'informations, consultez <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="02725-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>  
  
 <span data-ttu-id="02725-121">Un autre tableau courant de taille fixe est le tableau [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="02725-121">Another common fixed-size array is the [bool](../../../csharp/language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="02725-122">La taille des éléments d’un tableau `bool` est toujours d’un octet.</span><span class="sxs-lookup"><span data-stu-id="02725-122">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="02725-123">Les tableaux `bool` ne conviennent pas à la création de tableaux d’octets ou de mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="02725-123">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02725-124">Le compilateur C# et le common language runtime (CLR) ne contrôlent pas le dépassement de la mémoire tampon de sécurité, sauf pour la mémoire créée à l’aide de [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="02725-124">Except for memory created by using [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="02725-125">Comme toujours pour le code unsafe, la prudence est recommandée.</span><span class="sxs-lookup"><span data-stu-id="02725-125">As with all unsafe code, use caution.</span></span>  
  
 <span data-ttu-id="02725-126">Les mémoires tampons unsafe diffèrent des tableaux normaux à différents niveaux :</span><span class="sxs-lookup"><span data-stu-id="02725-126">Unsafe buffers differ from regular arrays in the following ways:</span></span>  
  
-   <span data-ttu-id="02725-127">Les mémoires tampons unsafe peuvent uniquement être utilisées dans un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="02725-127">You can only use unsafe buffers in an unsafe context.</span></span>  
  
-   <span data-ttu-id="02725-128">Les mémoires tampons unsafe sont toujours des vecteurs ou des tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="02725-128">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="02725-129">La déclaration du tableau doit inclure un nombre, tel que `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="02725-129">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="02725-130">Vous ne pouvez pas utiliser `char id[]` à la place.</span><span class="sxs-lookup"><span data-stu-id="02725-130">You cannot use `char id[]` instead.</span></span>  
  
-   <span data-ttu-id="02725-131">Les mémoires tampons unsafe peuvent uniquement être des champs d’instance de structs dans un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="02725-131">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02725-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02725-132">See Also</span></span>  
 [<span data-ttu-id="02725-133">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="02725-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="02725-134">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="02725-134">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="02725-135">fixed, instruction</span><span class="sxs-lookup"><span data-stu-id="02725-135">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="02725-136">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="02725-136">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)
