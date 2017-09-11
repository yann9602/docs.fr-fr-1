---
title: "Mémoires tampons de taille fixe (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: 31
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
ms.openlocfilehash: e1a3dcf953cb56fc3436fdd5e7ecb60478a12922
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="c5744-102">Mémoires tampons de taille fixe (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c5744-102">Fixed Size Buffers (C# Programming Guide)</span></span>
<span data-ttu-id="c5744-103">En C#, vous pouvez utiliser l’instruction [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) pour créer une mémoire tampon avec un tableau de taille fixe dans une structure de données.</span><span class="sxs-lookup"><span data-stu-id="c5744-103">In C#, you can use the [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="c5744-104">Cela est utile lorsque vous utilisez du code existant, tel que du code écrit dans d’autres langages, des DLL préexistantes ou des projets COM.</span><span class="sxs-lookup"><span data-stu-id="c5744-104">This is useful when you are working with existing code, such as code written in other languages, pre-existing DLLs or COM projects.</span></span> <span data-ttu-id="c5744-105">Le tableau fixe peut accepter tous les attributs ou modificateurs qui sont autorisés pour les membres de structures régulières.</span><span class="sxs-lookup"><span data-stu-id="c5744-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="c5744-106">La seule restriction est que le tableau doit être de type `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="c5744-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a><span data-ttu-id="c5744-107">Notes</span><span class="sxs-lookup"><span data-stu-id="c5744-107">Remarks</span></span>  
 <span data-ttu-id="c5744-108">Dans les versions antérieures de C#, il était difficile de déclarer une structure de taille fixe de style C++, car un struct C# qui contient un tableau ne contient pas les éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="c5744-108">In early versions of C#, declaring a C++ style fixed-size structure was difficult because a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="c5744-109">Le struct contient une référence aux éléments du tableau.</span><span class="sxs-lookup"><span data-stu-id="c5744-109">Instead, the struct contains a reference to the elements.</span></span>  
  
 <span data-ttu-id="c5744-110">Avec le langage C# 2.0, il est désormais possible d’incorporer un tableau de taille fixe dans un [struct](../../../csharp/language-reference/keywords/struct.md) lorsqu’il est utilisé dans un bloc de code [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="c5744-110">C# 2.0 added the ability to embed an array of fixed size in a [struct](../../../csharp/language-reference/keywords/struct.md) when it is used in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) code block.</span></span>  
  
 <span data-ttu-id="c5744-111">Par exemple, avant C# 2.0, le `struct` suivant avait une taille de 8 octets.</span><span class="sxs-lookup"><span data-stu-id="c5744-111">For example, before C# 2.0, the following `struct` would be 8 bytes in size.</span></span> <span data-ttu-id="c5744-112">Le tableau `pathName` est une référence au tableau alloué par tas :</span><span class="sxs-lookup"><span data-stu-id="c5744-112">The `pathName` array is a reference to the heap-allocated array:</span></span>  
  
 <span data-ttu-id="c5744-113">[!code-cs[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c5744-113">[!code-cs[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]</span></span>  
  
 <span data-ttu-id="c5744-114">Avec C# 2.0, un `struct` peut maintenant contenir un tableau incorporé.</span><span class="sxs-lookup"><span data-stu-id="c5744-114">Beginning with C# 2.0, a `struct` can contain an embedded array.</span></span> <span data-ttu-id="c5744-115">Dans l’exemple suivant, le tableau `fixedBuffer` a une taille fixe.</span><span class="sxs-lookup"><span data-stu-id="c5744-115">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="c5744-116">Pour accéder aux éléments du tableau, vous devez utiliser une instruction `fixed` pour établir un pointeur vers le premier élément.</span><span class="sxs-lookup"><span data-stu-id="c5744-116">To access the elements of the array, you use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="c5744-117">L’instruction `fixed` épingle une instance de `fixedBuffer` à un emplacement spécifique de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="c5744-117">The `fixed` statement pins an instance of `fixedBuffer` to a specific location in memory.</span></span>  
  
 <span data-ttu-id="c5744-118">[!code-cs[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c5744-118">[!code-cs[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]</span></span>  
  
 <span data-ttu-id="c5744-119">La taille du tableau `char` de 128 éléments est de 256 octets.</span><span class="sxs-lookup"><span data-stu-id="c5744-119">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="c5744-120">Les mémoires tampons [char](../../../csharp/language-reference/keywords/char.md) de taille fixe acceptent toujours deux octets par caractère, quel que soit l’encodage.</span><span class="sxs-lookup"><span data-stu-id="c5744-120">Fixed size [char](../../../csharp/language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="c5744-121">Ceci est vrai même lorsque les mémoires tampons char sont marshalées vers des méthodes ou des structs d’API avec `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="c5744-121">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="c5744-122">Pour plus d'informations, consultez <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="c5744-122">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>  
  
 <span data-ttu-id="c5744-123">Un autre tableau courant de taille fixe est le tableau [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="c5744-123">Another common fixed-size array is the [bool](../../../csharp/language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="c5744-124">La taille des éléments d’un tableau `bool` est toujours d’un octet.</span><span class="sxs-lookup"><span data-stu-id="c5744-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="c5744-125">Les tableaux `bool` ne conviennent pas à la création de tableaux d’octets ou de mémoires tampons.</span><span class="sxs-lookup"><span data-stu-id="c5744-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5744-126">Le compilateur C# et le common language runtime (CLR) ne contrôlent pas le dépassement de la mémoire tampon de sécurité, sauf pour la mémoire créée à l’aide de [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md).</span><span class="sxs-lookup"><span data-stu-id="c5744-126">Except for memory created by using [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="c5744-127">Comme toujours pour le code unsafe, la prudence est recommandée.</span><span class="sxs-lookup"><span data-stu-id="c5744-127">As with all unsafe code, use caution.</span></span>  
  
 <span data-ttu-id="c5744-128">Les mémoires tampons unsafe diffèrent des tableaux normaux à différents niveaux :</span><span class="sxs-lookup"><span data-stu-id="c5744-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>  
  
-   <span data-ttu-id="c5744-129">Les mémoires tampons unsafe peuvent uniquement être utilisées dans un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="c5744-129">You can only use unsafe buffers in an unsafe context.</span></span>  
  
-   <span data-ttu-id="c5744-130">Les mémoires tampons unsafe sont toujours des vecteurs ou des tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="c5744-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="c5744-131">La déclaration du tableau doit inclure un nombre, tel que `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="c5744-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="c5744-132">Vous ne pouvez pas utiliser `char id[]` à la place.</span><span class="sxs-lookup"><span data-stu-id="c5744-132">You cannot use `char id[]` instead.</span></span>  
  
-   <span data-ttu-id="c5744-133">Les mémoires tampons unsafe peuvent uniquement être des champs d’instance de structs dans un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="c5744-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5744-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5744-134">See Also</span></span>  
 <span data-ttu-id="c5744-135">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c5744-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c5744-136">[Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="c5744-136">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="c5744-137">[fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c5744-137">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="c5744-138">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="c5744-138">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)

