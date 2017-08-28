---
title: "Checked et Unchecked (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: 17
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
ms.openlocfilehash: 744f59dbf7ee8370010ff76d4e9dde20490de403
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="checked-and-unchecked-c-reference"></a>Checked et Unchecked (référence C#)
Les instructions C# peuvent s'exécuter dans un contexte vérifié (checked) ou non vérifié (unchecked). Dans un contexte vérifié, un dépassement de capacité arithmétique lève une exception. Dans un contexte non vérifié, un dépassement de capacité arithmétique et le résultat sont tronqués.  
  
-   [checked](../../../csharp/language-reference/keywords/checked.md) Indique un contexte vérifié.  
  
-   [unchecked](../../../csharp/language-reference/keywords/unchecked.md) Indique un contexte non vérifié.  
  
 Si ni `checked`, ni `unchecked` n'est spécifié, le contexte par défaut dépend de facteurs externes, notamment les options du compilateur.  
  
 Les opérations suivantes sont concernées par la vérification du dépassement de capacité :  
  
-   Expressions utilisant les opérateurs prédéfinis suivants dans des types intégraux :  
  
     `++` `--` - (unaire)   `+` -   `*` `/`  
  
-   Conversions numériques explicites entre types intégraux.  
  
 L’option de compilateur[/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) vous permet d’indiquer le contexte vérifié ou non vérifié pour toutes les instructions arithmétiques entières qui ne figurent pas explicitement dans l’étendue d’un mot clé`checked` ou `unchecked`.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés d’instructions](../../../csharp/language-reference/keywords/statement-keywords.md)

