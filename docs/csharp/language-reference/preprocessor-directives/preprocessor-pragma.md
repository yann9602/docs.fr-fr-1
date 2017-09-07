---
title: "#<a name=\"pragma-c-reference\"></a>pragma (informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: 18
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
ms.openlocfilehash: e03fc387b105c1dee3b7fed93263ad8ef22d5934
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="pragma-c-reference"></a>#pragma (informations de référence sur C#)
La directive `#pragma` fournit au compilateur des instructions spéciales pour la compilation du fichier dans lequel elle apparaît. Les instructions doivent être prises en charge par le compilateur. En d’autres termes, vous ne pouvez pas utiliser `#pragma` pour créer des instructions de prétraitement personnalisées. Le compilateur Microsoft C# prend en charge les deux instructions `#pragma` suivantes :  
  
 [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
  
 [#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma pragma-name pragma-arguments  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pragma-name`  
 Nom d’une directive pragma reconnue.  
  
 `pragma-arguments`  
 Arguments propres à la directive pragma.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md)   
 [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)   
 [#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

