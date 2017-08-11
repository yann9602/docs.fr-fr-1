---
title: "when (référence C#)"
ms.date: 2017-03-07
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- when_CSharpKeyword
- when
dev_langs:
- CSharp
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
caps.latest.revision: 30
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ae869fa04d2dfb963694f258624c5cd594ff1184
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
 # <a name="when-c-reference"></a>when (référence C#)

Vous pouvez utiliser le mot clé contextuel `when` pour spécifier une condition de filtre dans deux contextes :

- dans l’instruction `catch` d’un bloc [try/catch](try-catch.md) ou [try/catch/finally](try-catch-finally.md) ;
- dans l’étiquette `case` d’une instruction [switch](switch.md).

## <a name="when-in-a-catch-statement"></a>`when` dans une instruction `catch`

Depuis C# 6, `When` peut être utilisé dans une instruction `catch` pour spécifier une condition qui doit avoir la valeur True pour que le gestionnaire d’une exception spécifique soit exécuté. Sa syntaxe est la suivante :

```csharp
catch ExceptionType [e] when (expr)
```
où *expr* est une expression qui prend une valeur booléenne. Si la valeur retournée est `true`, le gestionnaire de l’exception est exécuté ; si la valeur retournée est `false`, il n’est pas exécuté. 

L’exemple suivant utilise le mot clé `when` afin d’exécuter conditionnellement des gestionnaires pour une exception @System.Net.HttpRequestException selon le texte du message d’exception.

 [!code-cs[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a>`when` dans une instruction `switch`

Depuis la version 7, les étiquettes `case` n’ont plus besoin de s’exclure mutuellement et l’ordre dans lequel les étiquettes `case` s’affichent dans une instruction `switch` peut déterminer le bloc switch exécuté. Le mot clé `when` peut être utilisé pour spécifier une condition de filtre qui fait que son étiquette case associée a la valeur True uniquement si la condition de filtre a également la valeur True. Sa syntaxe est la suivante :

```csharp
case (expr) when (when-condition):
```
où *expr* est un modèle de constante ou de type qui est comparé à l’expression de correspondance, et *when-condition* représente toute expression booléenne. 

L’exemple suivant utilise le mot clé `when` pour tester les objets `Shape` ayant une superficie égale à zéro, ainsi que pour tester divers objets `Shape` ayant une superficie supérieure à zéro. 

 [!code-cs[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a>Voir aussi 
  [switch, instruction](switch.md)  
  [try/catch, instruction](try-catch.md)  
  [try/catch/finally, instruction](try-catch-finally.md) 


