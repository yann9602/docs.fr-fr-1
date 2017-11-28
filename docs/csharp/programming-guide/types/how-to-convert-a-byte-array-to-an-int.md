---
title: "Guide pratique pour convertir un tableau d’octets en valeur int (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#], byte array to int
- byte arrays [C#], converting to int
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee51cd94e961c7274286c812cb6900d26c6ce033
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a><span data-ttu-id="08a96-102">Guide pratique pour convertir un tableau d’octets en valeur int (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="08a96-102">How to: Convert a byte Array to an int (C# Programming Guide)</span></span>
<span data-ttu-id="08a96-103">Cet exemple montre comment utiliser la classe <xref:System.BitConverter> pour convertir un tableau d’octets en valeur [int](../../../csharp/language-reference/keywords/int.md), puis la reconvertir en tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="08a96-103">This example shows you how to use the <xref:System.BitConverter> class to convert an array of bytes to an [int](../../../csharp/language-reference/keywords/int.md) and back to an array of bytes.</span></span> <span data-ttu-id="08a96-104">Vous devrez peut-être convertir des octets en un type de données intégré après avoir lu les octets sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="08a96-104">You may have to convert from bytes to a built-in data type after you read bytes off the network, for example.</span></span> <span data-ttu-id="08a96-105">Outre la méthode [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) de l’exemple, le tableau suivant répertorie les méthodes dans la classe <xref:System.BitConverter> qui convertissent des octets (d’un tableau d’octets) en d’autres types intégrés.</span><span class="sxs-lookup"><span data-stu-id="08a96-105">In addition to the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method in the example, the following table lists methods in the <xref:System.BitConverter> class that convert bytes (from an array of bytes) to other built-in types.</span></span>  
  
|<span data-ttu-id="08a96-106">Type retourné</span><span class="sxs-lookup"><span data-stu-id="08a96-106">Type returned</span></span>|<span data-ttu-id="08a96-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="08a96-107">Method</span></span>|  
|-------------------|------------|  
|`bool`|<span data-ttu-id="08a96-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="08a96-108">[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))</span></span>|  
|`char`|<span data-ttu-id="08a96-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="08a96-109">[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))</span></span>|  
|`double`|<span data-ttu-id="08a96-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="08a96-110">[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))</span></span>|  
|`short`|<span data-ttu-id="08a96-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="08a96-111">[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))</span></span>|  
|`int`|<span data-ttu-id="08a96-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="08a96-112">[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))</span></span>|  
|`long`|<span data-ttu-id="08a96-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="08a96-113">[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))</span></span>|  
|`float`|<span data-ttu-id="08a96-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="08a96-114">[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))</span></span>|  
|`ushort`|<span data-ttu-id="08a96-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="08a96-115">[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))</span></span>|  
|`uint`|<span data-ttu-id="08a96-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="08a96-116">[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))</span></span>|  
|`ulong`|<span data-ttu-id="08a96-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span><span class="sxs-lookup"><span data-stu-id="08a96-117">[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))</span></span>|  
  
## <a name="example"></a><span data-ttu-id="08a96-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="08a96-118">Example</span></span>  
 <span data-ttu-id="08a96-119">Cet exemple initialise un tableau d’octets, inverse le tableau si l’architecture de l’ordinateur est little-endian (autrement dit, l’octet le moins significatif est stocké en premier), puis appelle la méthode [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) pour convertir quatre octets du tableau en valeur `int`.</span><span class="sxs-lookup"><span data-stu-id="08a96-119">This example initializes an array of bytes, reverses the array if the computer architecture is little-endian (that is, the least significant byte is stored first), and then calls the [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) method to convert four bytes in the array to an `int`.</span></span> <span data-ttu-id="08a96-120">Le deuxième argument de [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) spécifie l’index de départ du tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="08a96-120">The second argument to [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) specifies the start index of the array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08a96-121">La sortie peut varier en fonction du caractère endian de l’architecture de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="08a96-121">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="08a96-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="08a96-122">Example</span></span>  
 <span data-ttu-id="08a96-123">Dans cet exemple, la méthode <xref:System.BitConverter.GetBytes%28System.Int32%29> de la classe <xref:System.BitConverter> est appelée pour convertir une valeur `int` en tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="08a96-123">In this example, the <xref:System.BitConverter.GetBytes%28System.Int32%29> method of the <xref:System.BitConverter> class is called to convert an `int` to an array of bytes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08a96-124">La sortie peut varier en fonction du caractère endian de l’architecture de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="08a96-124">The output may differ depending on the endianess of your computer's architecture.</span></span>  
  
 [!code-csharp[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="08a96-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08a96-125">See Also</span></span>  
 <xref:System.BitConverter>  
 <xref:System.BitConverter.IsLittleEndian>  
 [<span data-ttu-id="08a96-126">Types</span><span class="sxs-lookup"><span data-stu-id="08a96-126">Types</span></span>](../../../csharp/programming-guide/types/index.md)
