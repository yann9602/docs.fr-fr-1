---
title: "string (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- string
- string_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.assetid: 3037e558-fb22-494d-bca1-a15ade11b11a
caps.latest.revision: 31
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a616808a8e6ff5e259c503c0143db4b8f73bdef2
ms.lasthandoff: 03/13/2017

---
# <a name="string-c-reference"></a>string (référence C#)
Le type `string` représente une séquence de zéro, un ou plusieurs caractères Unicode. `string` est un alias de <xref:System.String> dans le .NET Framework.  
  
 Bien que `string` soit un type référence, les opérateurs d’égalité (`==` et `!=`) sont définis pour comparer les valeurs d’objets `string`, pas les références. Cela permet de tester l’égalité de chaînes de façon plus intuitive. Exemple :  
  
```csharp  
  
      string a = "hello";  
string b = "h";  
// Append to contents of 'b'  
b += "ello";  
Console.WriteLine(a == b);  
Console.WriteLine((object)a == (object)b);  
```  
  
 Cette opération affiche « True », puis « False », car le contenu des chaînes est équivalent, mais `a` et `b` ne font pas référence à la même instance de chaîne.  
  
 L’opérateur + concatène les chaînes :  
  
```csharp  
  
string a = "good " + "morning";  
```  
  
 Cela crée un objet String qui contient « good morning ».  
  
 Les chaînes sont *immuables* : il est impossible de changer le contenu d’un objet String après avoir créé l’objet, bien que la syntaxe semble indiquer le contraire. Par exemple, lorsque vous écrivez ce code, le compilateur crée en fait un nouvel objet String pour stocker la nouvelle séquence de caractères, et ce nouvel objet est assigné à b. La chaîne « h » est alors disponible pour le garbage collection.  
  
```csharp  
  
      string b = "h";  
b += "ello";  
```  
  
 L’opérateur [] peut être utilisé pour un accès en lecture seule aux différents caractères d’un objet `string` :  
  
```csharp  
  
      string str = "test";  
char x = str[2];  // x = 's';  
```  
  
 Les littéraux de chaîne sont de type `string` et peuvent être écrits sous deux formes, entre guillemets et @-quoted. Les littéraux de chaîne entre guillemets sont placés entre guillemets doubles (") :  
  
```csharp  
"good morning"  // a string literal  
```  
  
 Les littéraux de chaîne peuvent contenir tout littéral de caractère. Les séquences d’échappement sont incluses. L’exemple suivant utilise la séquence d’échappement `\\` pour la barre oblique inverse, `\u0066` pour la lettre f et `\n` pour un saut de ligne.  
  
```  
  
      string a = "\\\u0066\n";  
Console.WriteLine(a);  
```  
  
> [!NOTE]
>  Le code d’échappement `\`u`dddd` (où `dddd` est un nombre à quatre chiffres) représente le caractère Unicode U+`dddd`. Les codes d’échappement Unicode à huit chiffres sont également reconnus : `\Udddddddd`.  
  
 Les littéraux de chaîne textuelle commencent par @ et sont placés entre guillemets doubles. Exemple :  
  
```csharp  
@"good morning"  // a string literal  
```  
  
 L’avantage des chaînes textuelles est que les séquences d’échappement *ne sont pas* traitées, ce qui facilite l’écriture, par exemple, d’un nom de fichier complet :  
  
```csharp  
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"  
```  
  
 Pour inclure un guillemet double dans une chaîne @-quoted, doublez-le :  
  
```csharp  
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.  
```  
  
 Une autre manière d’utiliser le symbole @ consiste à utiliser des identificateurs ([/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)) référencés qui sont des mots clés C#.  
  
 Pour plus d’informations sur les chaînes en C#, consultez la rubrique [Chaînes](../../../csharp/programming-guide/strings/index.md).  
  
## <a name="example"></a>Exemple  
 [!code-cs[csrefKeywordsTypes#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/string_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Bonnes pratiques pour l’utilisation de chaînes](http://msdn.microsoft.com/library/b9f0bf53-e2de-4116-8ce9-d4f91a1df4f7)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)   
 [Types valeur](../../../csharp/language-reference/keywords/value-types.md)   
 [Opérations de chaînes de base](http://msdn.microsoft.com/library/8133d357-90b5-4b62-9927-43323d99b6b6)   
 [Création de chaînes](http://msdn.microsoft.com/library/06fdf123-2fac-4459-8904-eb48ab908a30)   
 [Tableau des formats des résultats numériques](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)
