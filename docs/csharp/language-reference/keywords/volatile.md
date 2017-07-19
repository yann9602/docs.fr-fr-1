---
title: "volatile (référence C#) | Microsoft Docs"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 801187b1fcc25a1eea1f40ec8ac4c67af42e5880
ms.contentlocale: fr-fr
ms.lasthandoff: 05/10/2017

---
# <a name="volatile-c-reference"></a>volatile (référence C#)
Le mot clé `volatile` indique qu’un champ peut être modifié par plusieurs threads qui s’exécutent simultanément. Les champs qui sont déclarés `volatile` ne sont pas soumis aux optimisations du compilateur qui supposent l’accès par un seul thread. Cela garantit que la valeur la plus à jour est présente dans le champ à tout moment.  
  
 Le modificateur `volatile` est généralement utilisé pour un champ auquel accèdent plusieurs threads sans utiliser l’instruction [lock](../../../csharp/language-reference/keywords/lock-statement.md) pour sérialiser l’accès.  
  
 Le mot clé `volatile` peut être appliqué aux champs des types suivants :  
  
-   Types référence.  
  
-   Types pointeur (dans un contexte unsafe). Notez que, même si le pointeur lui-même peut être volatile, l’objet sur lequel il pointe ne le peut pas. En d’autres termes, vous ne pouvez pas déclarer un pointeur vers un objet volatile.  
  
-   Types tels que sbyte, byte, short, ushort, int, uint, char, float et bool.  
  
-   Type enum avec l’un des types de base suivants : byte, sbyte, short, ushort, int ou uint.  
  
-   Paramètres de type générique connus comme des types référence.  
  
-   Voir <xref:System.IntPtr> et <xref:System.UIntPtr>.  
  
 Le mot clé volatile ne peut s’appliquer qu’aux champs d’une classe ou d’une structure. Les variables locales ne peuvent pas être déclarées `volatile`.  
  
## <a name="example"></a>Exemple  
 L’exemple ci-dessous montre comment déclarer une variable de champ public comme `volatile`.  
  
 [!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment il est possible de créer un thread auxiliaire ou de travail et de l’utiliser pour effectuer le traitement en parallèle avec le thread principal. Pour obtenir des informations générales sur le multithreading, consultez [Threading](../../../standard/threading/index.md) et [Thread](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).  
  
 [!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)
