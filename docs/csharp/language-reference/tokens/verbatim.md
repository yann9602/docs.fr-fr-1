---
title: "@ (référence C#)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30f937951557ba65971a752b414cce6b485149be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-c-reference"></a>@ (référence C#)

Le caractère spécial `@` sert d’identificateur de chaîne textuelle. Il peut être utilisé des façons suivantes :

1. Pour activer les mots clés C# à utiliser comme identificateurs. Le caractère `@` est le préfixe d’un élément de code que le compilateur doit interpréter comme un identificateur plutôt qu’un mot clé C#. L’exemple suivant utilise le caractère `@` pour définir un identificateur nommé `for` qu’il utilise dans une boucle `for`.

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. Pour indiquer qu’un littéral de chaîne doit être interprété textuellement. Le caractère `@` dans cette instance définit un *littéral de chaîne textuelle*. Les séquences d’échappement simples (comme `"\\"` pour une barre oblique inverse), hexadécimales (comme `"\x0041"` pour un A majuscule) et Unicode (comme `"\u0041"` pour un A majuscule), sont interprétées littéralement. Seule une séquence d’échappement de guillemet (`""`) n’est pas interprétée littéralement ; elle génère un guillemet simple. L’exemple suivant définit deux chemins de fichier identiques, un à l’aide d’un littéral de chaîne standard et l’autre à l’aide d’un littéral de chaîne textuelle. Il s’agit là de l’une des utilisations les plus courantes de littéraux de chaîne textuelle.

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   L’exemple suivant illustre l’effet de la définition d’un littéral de chaîne standard et d’un littéral de chaîne textuelle qui contiennent des séquences de caractères identiques.

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. Pour permettre au compilateur de faire la distinction entre les attributs en cas de conflit de noms. Un attribut est un type qui dérive de <xref:System.Attribute>. Son nom de type comprend généralement le suffixe **Attribute**, bien que le compilateur n’applique pas cette convention. L’attribut peut ensuite être référencé dans le code par son nom de type complet (par exemple, `[InfoAttribute]`) ou son nom abrégé (par exemple, `[Info]`). Toutefois, un conflit survient si deux noms de type d’attribut abrégés sont identiques et que l’un d’eux inclut le suffixe **Attribute**, mais pas l’autre. Par exemple, la compilation du code suivant échoue, car le compilateur ne peut pas déterminer si l’attribut `Info` ou `InfoAttribute` est appliqué à la méthode `Main`.

   ```csharp
   using System;

   [AttributeUsage(AttributeTargets.Class)]
   public class Info : Attribute
   {
      private string information;
      
      public Info(string info)
      {
          information = info;
      }
   }

   [AttributeUsage(AttributeTargets.Method)]
   public class InfoAttribute : Attribute
   {
      private string information;
      
      public InfoAttribute(string info)
      {
          information = info;
      }
   }

   [Info("A simple executable.")]
   public class Example
   {
      [InfoAttribute("The entry point.")]
      public static void Main()
      {
      }
   }
   ```  

   Si l’identificateur de chaîne textuelle est utilisé pour identifier l’attribut `Info`, l’exemple est correctement compilé.

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]

## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Caractères spéciaux C#](../../../csharp/language-reference/tokens/index.md)
