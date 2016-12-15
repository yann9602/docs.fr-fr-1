---
title: "string (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "string"
  - "string_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "chaînes [C#], référence"
  - "@, littéral de chaîne"
  - "littéraux de chaîne [C#]"
  - "string, mot clé [C#]"
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# string (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le type `string` représente une séquence de zéros ou plusieurs caractères Unicode.  `string` est un alias pour <xref:System.String> dans .NET Framework.  
  
 Bien que `string` soit un type référence, les opérateurs d'égalité \(`==` et `!=`\) sont définis pour comparer les valeurs d'objets `string`, pas de références.  Le test d'égalité des chaînes est ainsi plus intuitif.  Par exemple :  
  
```c#  
  
      string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 Cela affiche "True", puis "False" parce que le contenu des chaînes est équivalent, mais `a` et `b` ne font pas référence à la même instance de chaîne.  
  
 L'opérateur \+ concatène les chaînes :  
  
```c#  
  
string a = "good " + "morning";  
```  
  
 Cela crée un objet de chaîne qui contient "good morning".  
  
 Les chaînes sont *immuables* – le contenu d'un objet chaîne ne peut pas être modifié une fois que l'objet a été créé, même si la syntaxe peut laisser croire que la modification est possible.  Par exemple, lorsque vous écrivez ce code, le compilateur crée en fait un objet String pour stocker la nouvelle séquence de caractères et ce nouvel objet est assigné à b.  La chaîne « h » est ensuite prête pour le garbage collection.  
  
```c#  
  
      string b = "h";  
b += "ello";  
```  
  
 L'opérateur \[\] permet d'accéder en lecture seule aux différents caractères d'une `string` :  
  
```c#  
  
      string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 Les littéraux de chaîne sont de type `string` et sont indiqués entre des guillemets, avec ou sans le symbole @.  Les littéraux de chaîne entre guillemets, mais sans symbole @ sont entourés de guillemets doubles \("\) :  
  
```c#  
"good morning"  // a string literal  
```  
  
 Les littéraux de chaîne peuvent contenir n'importe quel littéral de caractère.  Les séquences d'échappement sont incluses.  L'exemple suivant utilise la séquence d'échappement `\\` pour la barre oblique inverse, `\u0066` pour la lettre f, et `\n` pour le saut de ligne.  
  
```  
  
      string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  Le code d'échappement `\u``dddd` \(où `dddd` est un nombre à 4 chiffres\) représente le caractère Unicode U\+`dddd`.  Les codes d'effacement Unicode à huit chiffres sont également reconnus : `\Udddddddd`.  
  
 Les littéraux de chaîne textuels commencent par le symbole @ et sont également entourés de guillemets anglais doubles \("\).  Par exemple :  
  
```c#  
@"good morning"  // a string literal  
```  
  
 Les chaînes textuelles permettent de spécifier que les séquences d'échappement *ne doivent pas* être traitées, ce qui facilite l'écriture d'un nom de fichier qualifié complet, par exemple :  
  
```c#  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 Pour ajouter des guillemets doubles au sein d'une chaîne entre guillemets avec le symbole @, doublez\-les :  
  
```c#  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 Le symbole @ peut également être employé avec des identificateurs référencés \([\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)\) qui sont des mots clés C\#.  
  
 Pour plus d'informations sur les chaînes en C\#, consultez [Chaînes](../../../csharp/programming-guide/strings/index.md).  
  
## Exemple  
 [!code-cs[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Meilleures pratiques pour l'utilisation de chaînes](../Topic/Best%20Practices%20for%20Using%20Strings%20in%20the%20.NET%20Framework.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)   
 [Types valeur](../../../csharp/language-reference/keywords/value-types.md)   
 [Opérations de chaînes de base](../Topic/Basic%20String%20Operations%20in%20the%20.NET%20Framework.md)   
 [Création de nouvelles chaînes](../Topic/Creating%20New%20Strings%20in%20the%20.NET%20Framework.md)   
 [Tableau des formats des résultats numériques](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)