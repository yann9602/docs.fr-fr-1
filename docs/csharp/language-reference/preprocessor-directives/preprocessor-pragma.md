---
title: "#<a name=\"pragma-c-reference\"></a>pragma (informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#pragma'
helpviewer_keywords: '#pragma directive [C#]'
ms.assetid: 5b7944cd-d402-46a1-ad8f-feffb2d83673
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6f53bd0ed3f35f049b0a1cbb21c5b9a563f9fce9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-c-reference"></a>#pragma (référence C#)
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
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)  
 [#pragma checksum](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)
