---
title: "Comment&#160;: convertir un tableau de byte en int (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "tableaux d'octets (C#), convertir en type int"
  - "conversions (C#), tableau d'octets en type int"
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# Comment&#160;: convertir un tableau de byte en int (Guide de programmation C#)
Cet exemple indique comment utiliser la classe <xref:System.BitConverter> pour convertir un tableau d'octets en [int](../../../csharp/language-reference/keywords/int.md), et inversement.  Vous devrez peut\-être convertir des octets en un type de données intégré après avoir lu les octets sur le réseau, par exemple.  Outre la méthode [ToInt32\(Byte\<xref:System.BitConverter.ToInt32%28System.Byte%5B%5D%2CSystem.Int32%29> décrite dans cet exemple, le tableau suivant répertorie les méthodes dans la classe <xref:System.BitConverter> qui convertissent des octets \(d'un tableau d'octets\) en d'autres types intégrés.  
  
|Type retourné|Méthode|  
|-------------------|-------------|  
|`bool`|[ToBoolean\(Byte\<xref:System.BitConverter.ToBoolean%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`char`|[ToChar\(Byte\<xref:System.BitConverter.ToChar%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`double`|[ToDouble\(Byte\<xref:System.BitConverter.ToDouble%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`short`|[ToInt16\(Byte\<xref:System.BitConverter.ToInt16%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`int`|[ToInt32\(Byte\<xref:System.BitConverter.ToInt32%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`long`|[ToInt64\(Byte\<xref:System.BitConverter.ToInt64%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`float`|[ToSingle\(Byte\<xref:System.BitConverter.ToSingle%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`ushort`|[ToUInt16\(Byte\<xref:System.BitConverter.ToUInt16%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`uint`|[ToUInt32\(Byte\<xref:System.BitConverter.ToUInt32%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`ulong`|[ToUInt64\(Byte\<xref:System.BitConverter.ToUInt64%28System.Byte%5B%5D%2CSystem.Int32%29>|  
  
## Exemple  
 Dans cet exemple, un tableau d'octets est initialisé puis inversé en cas d'architecture avec primauté des octets de poids faible \(autrement dit, l'octet le moins significatif est stocké en premier\), puis la méthode [ToInt32\(Byte\<xref:System.BitConverter.ToInt32%28System.Byte%5B%5D%2CSystem.Int32%29> est appelée pour convertir quatre octets du tableau en `int` \(nombre entier\).  Le deuxième argument de [ToInt32\(Byte\<xref:System.BitConverter.ToInt32%28System.Byte%5B%5D%2CSystem.Int32%29> spécifie l'index de début du tableau d'octets.  
  
> [!NOTE]
>  La sortie peut différer selon l'ordre de primauté des octets utilisé dans l'architecture de votre ordinateur.  
  
 [!code-cs[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_1.cs)]  
  
## Exemple  
 Dans cet exemple, la méthode <xref:System.BitConverter.GetBytes%28System.Int32%29> de la classe <xref:System.BitConverter> est appelée pour convertir un `int` en un tableau d'octets.  
  
> [!NOTE]
>  La sortie peut différer selon l'ordre de primauté des octets utilisé dans l'architecture de votre ordinateur.  
  
 [!code-cs[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-byte-array-to-an-int_2.cs)]  
  
## Voir aussi  
 <xref:System.BitConverter>   
 <xref:System.BitConverter.IsLittleEndian>   
 [Types](../../../csharp/programming-guide/types/index.md)