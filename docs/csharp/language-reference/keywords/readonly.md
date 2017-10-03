---
title: "readonly (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- readonly_CSharpKeyword
- readonly
dev_langs:
- CSharp
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: 16
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
ms.openlocfilehash: 2660aa56721815cbbeb668328863956473cce8f1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="readonly-c-reference"></a>readonly (référence C#)
Le mot clé `readonly` est un modificateur que vous pouvez utiliser sur des champs. Lorsqu’une déclaration de champ inclut un modificateur `readonly`, les assignations aux champs introduites par la déclaration peuvent se produire uniquement dans le cadre de la déclaration ou dans un constructeur de la même classe.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, la valeur du champ `year` ne peut pas être modifiée dans la méthode `ChangeYear`, même si une valeur lui est affectée dans le constructeur de classe :  
  
 [!code-cs[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 Vous pouvez affecter une valeur à un champ `readonly` uniquement dans les contextes suivants :  
  
-   Lorsque la variable est initialisée dans la déclaration, par exemple :  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   Pour un champ d’instance, dans les constructeurs d’instance de la classe qui contient la déclaration de champ, ou pour un champ statique, dans le constructeur statique de la classe qui contient la déclaration de champ. Ce sont également les seuls contextes dans lesquels il est valide de passer un champ `readonly` comme paramètre [out](../../../csharp/language-reference/keywords/out.md) ou [ref](../../../csharp/language-reference/keywords/ref.md).  
  
> [!NOTE]
>  Le mot clé `readonly` est différent du mot clé [const](../../../csharp/language-reference/keywords/const.md). Un champ `const` ne peut être initialisé qu'au moment de la déclaration du champ. Un champ `readonly` peut être initialisé dans la déclaration ou dans un constructeur. C'est pourquoi, les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé. De même, alors qu’un champ `const` est une constante au moment de la compilation, le champ `readonly` peut être utilisé pour des constantes au moment de l’exécution, comme dans l’exemple suivant :  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="example"></a>Exemple  
 [!code-cs[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 Dans l’exemple précédent, si vous utilisez une instruction telle que :  
  
 `p2.y = 66;        // Error`  
  
 vous obtenez le message d’erreur du compilateur :  
  
 `The left-hand side of an assignment must be an l-value`  
  
 qui est la même erreur que vous obtenez lorsque vous tentez d’assigner une valeur à une constante.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [const](../../../csharp/language-reference/keywords/const.md)   
 [Champs](../../../csharp/programming-guide/classes-and-structs/fields.md)

