---
title: "#<a name=\"error-c-reference\"></a>error (informations de référence sur C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#error'
helpviewer_keywords: '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23528ae81e4ddca23c67c937ca2588ab4c982e98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="error-c-reference"></a>#error (référence C#)
`#error` vous permet de générer une erreur à partir d’un emplacement spécifique dans votre code. Exemple :  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>Remarques  
 `#error` est souvent utilisé dans une directive conditionnelle.  
  
 Il est possible aussi de générer un avertissement défini par l’utilisateur avec [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).  
  
## <a name="example"></a>Exemple  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Directives de préprocesseur C#](../../../csharp/language-reference/preprocessor-directives/index.md)
