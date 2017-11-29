---
title: "unsafe (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords: unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fffbe36e39d279b2364b178188381a403c8ff86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="unsafe-c-reference"></a>unsafe (référence C#)
Le mot clé `unsafe` désigne un contexte non sécurisé, qui est requis pour toute opération impliquant des pointeurs. Pour plus d’informations, consultez l’article [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 Vous pouvez utiliser le modificateur `unsafe` dans la déclaration d’un type ou d’un membre. Toute l’étendue de texte du type ou du membre est ainsi considérée comme un contexte unsafe. Par exemple, ce qui suit est une méthode déclarée avec le modificateur `unsafe` :  
  
```  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 La portée du contexte unsafe s’étend de la liste de paramètres à la fin de la méthode, de sorte que les pointeurs peuvent également être utilisés dans la liste de paramètres :  
  
```  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 Vous pouvez également avoir recours à un bloc unsafe pour utiliser un code unsafe dans ce bloc. Exemple :  
  
```  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 Pour compiler du code unsafe, vous devez spécifier l’option de compilateur [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md). Le code unsafe n’est pas vérifiable par le service CLR (Common Language Runtime).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
