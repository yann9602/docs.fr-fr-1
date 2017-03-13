---
title: "unsafe (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "unsafe_CSharpKeyword"
  - "unsafe"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "unsafe (mot clé C#)"
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# unsafe (r&#233;f&#233;rence C#)
Le mot clé `unsafe` indique un contexte non sécurisé, qui est requis pour toute opération impliquant des pointeurs.  Pour plus d'informations, consultez [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
 Vous pouvez utiliser le modificateur `unsafe` dans une déclaration de type ou de membre.  L'étendue textuelle complète du type ou du membre est ainsi considérée comme un contexte non sécurisé.  Par exemple, la méthode suivante est déclarée avec le modificateur `unsafe` :  
  
```  
  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 La portée du contexte non sécurisé s'étend de la liste de paramètres à la fin de la méthode, de sorte que les pointeurs puissent aussi être utilisés dans la liste de paramètres :  
  
```  
  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 Vous pouvez également utiliser un bloc non sécurisé pour activer l'utilisation d'un code unsafe au sein de ce bloc.  Par exemple :  
  
```  
  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 Pour compiler du code unsafe, vous devez spécifier l'option du compilateur [\/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  Le code unsafe n'est pas vérifiable par le Common Language Runtime.  
  
## Exemple  
 [!code-cs[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [fixed, instruction](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)