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
# <a name="how-to-convert-a-byte-array-to-an-int-c-programming-guide"></a>Guide pratique pour convertir un tableau d’octets en valeur int (Guide de programmation C#)
Cet exemple montre comment utiliser la classe <xref:System.BitConverter> pour convertir un tableau d’octets en valeur [int](../../../csharp/language-reference/keywords/int.md), puis la reconvertir en tableau d’octets. Vous devrez peut-être convertir des octets en un type de données intégré après avoir lu les octets sur le réseau. Outre la méthode [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) de l’exemple, le tableau suivant répertorie les méthodes dans la classe <xref:System.BitConverter> qui convertissent des octets (d’un tableau d’octets) en d’autres types intégrés.  
  
|Type retourné|Méthode|  
|-------------------|------------|  
|`bool`|[ToBoolean(Byte\[\], Int32)](xref:System.BitConverter.ToBoolean(System.Byte[],System.Int32))|  
|`char`|[ToChar(Byte\[\], Int32)](xref:System.BitConverter.ToChar(System.Byte[],System.Int32))|  
|`double`|[ToDouble(Byte\[\], Int32)](xref:System.BitConverter.ToDouble(System.Byte[],System.Int32))|  
|`short`|[ToInt16(Byte\[\], Int32)](xref:System.BitConverter.ToInt16(System.Byte[],System.Int32))|  
|`int`|[ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32))|  
|`long`|[ToInt64(Byte\[\], Int32)](xref:System.BitConverter.ToInt64(System.Byte[],System.Int32))|  
|`float`|[ToSingle(Byte\[\], Int32)](xref:System.BitConverter.ToSingle(System.Byte[],System.Int32))|  
|`ushort`|[ToUInt16(Byte\[\], Int32)](xref:System.BitConverter.ToUInt16(System.Byte[],System.Int32))|  
|`uint`|[ToUInt32(Byte\[\], Int32)](xref:System.BitConverter.ToUInt32(System.Byte[],System.Int32))|  
|`ulong`|[ToUInt64(Byte\[\], Int32)](xref:System.BitConverter.ToUInt64(System.Byte[],System.Int32))|  
  
## <a name="example"></a>Exemple  
 Cet exemple initialise un tableau d’octets, inverse le tableau si l’architecture de l’ordinateur est little-endian (autrement dit, l’octet le moins significatif est stocké en premier), puis appelle la méthode [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) pour convertir quatre octets du tableau en valeur `int`. Le deuxième argument de [ToInt32(Byte\[\], Int32)](xref:System.BitConverter.ToInt32(System.Byte[],System.Int32)) spécifie l’index de départ du tableau d’octets.  
  
> [!NOTE]
>  La sortie peut varier en fonction du caractère endian de l’architecture de votre ordinateur.  
  
 [!code-cs[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la méthode <xref:System.BitConverter.GetBytes%28System.Int32%29> de la classe <xref:System.BitConverter> est appelée pour convertir une valeur `int` en tableau d’octets.  
  
> [!NOTE]
>  La sortie peut varier en fonction du caractère endian de l’architecture de votre ordinateur.  
  
 [!code-cs[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.BitConverter>   
 <xref:System.BitConverter.IsLittleEndian>   
 [Types](../../../csharp/programming-guide/types/index.md)

