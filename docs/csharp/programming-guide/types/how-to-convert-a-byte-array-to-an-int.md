---
title: "Guide pratique pour convertir un tableau d’octets en valeur int (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 86ecfe95ab6fb5ce60e7568050cdf974d0dc3d88
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="b6ae6-102">Guide pratique pour convertir un tableau d’octets en valeur int (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b6ae6-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="b6ae6-103">Cet exemple montre comment utiliser la classe <xref:System.BitConverter> pour convertir un tableau d’octets en valeur [int](../../../csharp/language-reference/keywords/int.md), puis la reconvertir en tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="b6ae6-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../../csharp/language-reference/keywords/int.md) and back to an array of bytes.</span></span> <span data-ttu-id="b6ae6-104">Vous devrez peut-être convertir des octets en un type de données intégré après avoir lu les octets sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="b6ae6-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="b6ae6-105">Outre la méthode [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) de l’exemple, le tableau suivant répertorie les méthodes dans la classe <xref:System.BitConverter> qui convertissent des octets (d’un tableau d’octets) en d’autres types intégrés.</span><span class="sxs-lookup"><span data-stu-id="b6ae6-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="b6ae6-106">Type retourné</span><span class="sxs-lookup"><span data-stu-id="b6ae6-106">Type returned</span></span>|<span data-ttu-id="b6ae6-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="b6ae6-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="b6ae6-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b6ae6-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="b6ae6-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b6ae6-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="b6ae6-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b6ae6-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="b6ae6-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b6ae6-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="b6ae6-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b6ae6-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="b6ae6-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b6ae6-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="b6ae6-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b6ae6-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="b6ae6-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b6ae6-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="b6ae6-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b6ae6-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="b6ae6-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="b6ae6-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b6ae6-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6ae6-118">Example</span></span>  
 <span data-ttu-id="b6ae6-119">Cet exemple initialise un tableau d’octets, inverse le tableau si l’architecture de l’ordinateur est little-endian (autrement dit, l’octet le moins significatif est stocké en premier), puis appelle la méthode [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) pour convertir quatre octets du tableau en valeur `int`.</span><span class="sxs-lookup"><span data-stu-id="b6ae6-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="b6ae6-120">Le deuxième argument de [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) spécifie l’index de départ du tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="b6ae6-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6ae6-121">La sortie peut varier en fonction du caractère endian de l’architecture de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b6ae6-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 <span data-ttu-id="b6ae6-122">[!code-cs[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b6ae6-122">[!code-cs[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6ae6-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6ae6-123">Example</span></span>  
 <span data-ttu-id="b6ae6-124">Dans cet exemple, la méthode <xref:System.BitConverter.GetBytes%28System.Int32%29> de la classe <xref:System.BitConverter> est appelée pour convertir une valeur `int` en tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="b6ae6-124">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6ae6-125">La sortie peut varier en fonction du caractère endian de l’architecture de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b6ae6-125">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 <span data-ttu-id="b6ae6-126">[!code-cs[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="b6ae6-126">[!code-cs[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6ae6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6ae6-127">See Also</span></span>  
 <span data-ttu-id="b6ae6-128"><xref:System.BitConverter></span><span class="sxs-lookup"><span data-stu-id="b6ae6-128"><xref:System.BitConverter></span></span>   
 <span data-ttu-id="b6ae6-129"><xref:System.BitConverter.IsLittleEndian></span><span class="sxs-lookup"><span data-stu-id="b6ae6-129"><xref:System.BitConverter.IsLittleEndian></span></span>   
 [<span data-ttu-id="b6ae6-130">Types</span><span class="sxs-lookup"><span data-stu-id="b6ae6-130">Types</span></span>](../../../csharp/programming-guide/types/index.md)

