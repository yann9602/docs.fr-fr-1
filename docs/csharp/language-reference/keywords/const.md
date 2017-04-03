---
title: "const (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- const_CSharpKeyword
- const
dev_langs:
- CSharp
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
caps.latest.revision: 28
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
ms.openlocfilehash: 700e80272384a946609d538c5516f0480b7fed27
ms.lasthandoff: 03/13/2017

---
# <a name="const-c-reference"></a>const (référence C#)
Vous utilisez le mot clé `const` pour déclarer un champ constant ou un élément local constant. Les champs et les éléments locaux constants ne sont pas des variables et ne peuvent pas être modifiés. Les constantes peuvent être des chiffres, des valeurs booléennes, des chaînes ou une référence null. Ne créez pas une constante pour représenter des informations qui doivent être modifiées. Par exemple, n'utilisez pas un champ constant pour stocker le prix d'un service, le numéro de version du produit ou le nom de la marque d'une société. Ces valeurs peuvent changer dans le temps, et dans la mesure où les compilateurs propagent les constantes, le code compilé avec vos bibliothèques devra être recompilé pour refléter ces modifications. Consultez également le mot clé [readonly](../../../csharp/language-reference/keywords/readonly.md). Exemple :  
  
```  
  
      const int x = 0;  
public const double gravitationalConstant = 6.673e-11;  
private const string productName = "Visual C#";  
```  
  
## <a name="remarks"></a>Remarques  
 Le type d'une déclaration constante indique le type des membres introduit par la déclaration. L'initialiseur d'un élément local constant ou d'un champ constant doit être une expression constante qui peut être implicitement convertie en type cible.  
  
 Une expression constante est une expression qui peut être complètement évaluée au moment de la compilation. C'est pourquoi, les seules valeurs possibles pour les constantes des types référence sont `string` et une référence null.  
  
 La déclaration constante peut déclarer plusieurs constantes, notamment :  
  
```  
public const double x = 1.0, y = 2.0, z = 3.0;  
```  
  
 Le modificateur `static` n'est pas autorisé dans une déclaration constante.  
  
 Une constante peut être utilisée dans une expression constante, comme suit :  
  
```  
public const int c1 = 5;  
public const int c2 = c1 + 100;  
```  
  
> [!NOTE]
>  Le mot clé [readonly](../../../csharp/language-reference/keywords/readonly.md) est différent du mot clé `const`. Un champ `const` ne peut être initialisé qu'au moment de la déclaration du champ. Un champ `readonly` peut être initialisé dans la déclaration ou dans un constructeur. C'est pourquoi, les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé. De même, bien qu'un champ `const` soit une constante au moment de la compilation, le champ `readonly` peut être utilisé pour des constantes au moment de l'exécution, comme ci-après : `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`  
  
## <a name="example"></a>Exemple  
 [!code-cs[csrefKeywordsModifiers#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_1.cs)]  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment utiliser des constantes en tant que variables locales.  
  
 [!code-cs[csrefKeywordsModifiers#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [readonly](../../../csharp/language-reference/keywords/readonly.md)
