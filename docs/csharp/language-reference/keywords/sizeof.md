---
title: "sizeof (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
dev_langs:
- CSharp
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 20
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7a1944caceaba3ffb8d83a8f67e5ef2975bf9644
ms.lasthandoff: 03/13/2017

---
# <a name="sizeof-c-reference"></a>sizeof (référence C#)
Permet d’obtenir la taille en octets d’un type non managé. Les types non managés incluent les types intégrés qui sont répertoriés dans le tableau ci-dessous, ainsi que les éléments suivants :  
  
-   Types d'enum  
  
-   Types de pointeur  
  
-   Les structs définis par l'utilisateur qui ne contiennent pas de champs ou de propriétés qui sont de type référence  
  
 L’exemple suivant montre comment extraire la taille d’un `int` :  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a>Remarques  
 Depuis la version 2.0 de C#, l’application de `sizeof` à des types intégrés ne nécessite plus l’utilisation du mode [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
 L’opérateur `sizeof` ne peut pas être surchargé. Les valeurs retournées par l’opérateur `sizeof` sont du type `int`. Le tableau suivant indique les valeurs constantes qui sont substituées aux expressions `sizeof` qui ont certains types intégrés comme opérandes.  
  
|Expression|Valeur constante|  
|----------------|--------------------|  
|`sizeof(sbyte)`|1|  
|`sizeof(byte)`|1|  
|`sizeof(short)`|2|  
|`sizeof(ushort)`|2|  
|`sizeof(int)`|4|  
|`sizeof(uint)`|4|  
|`sizeof(long)`|8|  
|`sizeof(ulong)`|8|  
|`sizeof(char)`|2 (Unicode)|  
|`sizeof(float)`|4|  
|`sizeof(double)`|8|  
|`sizeof(decimal)`|16|  
|`sizeof(bool)`|1|  
  
 Pour tous les autres types, y compris les structs, l’opérateur `sizeof` peut être utilisé uniquement dans les blocs de code unsafe. Bien que vous puissiez utiliser la méthode <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName>, la valeur retournée par cette méthode n’est pas toujours identique à celle retournée par `sizeof`. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> retourne la taille après que le type a été marshalé, alors que `sizeof` retourne la taille telle qu’elle a été allouée par le Common Language Runtime, y compris la marge intérieure.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [enum](../../../csharp/language-reference/keywords/enum.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md)   
 [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)
