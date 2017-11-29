---
title: '&lt;exception&gt; (Guide de programmation C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bd859a09bfbe9f814bf57f0987fd49ded9ba7100
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltexceptiongt-c-programming-guide"></a>&lt;exception&gt; (Guide de programmation C#)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>Paramètres  
 cref = " `member`"  
 Référence à une exception qui est disponible à partir de l’environnement de compilation actuel. Le compilateur vérifie que l’exception donnée existe, et il traduit `member` en nom d’élément canonique dans le fichier XML de sortie. `member` doit apparaître entre guillemets doubles (" ").  
  
 Pour plus d’informations sur la façon de créer une référence cref à un type générique, consultez [\<see>](../../../csharp/programming-guide/xmldoc/see.md).  
  
 `description`  
 Description de l'exception.  
  
## <a name="remarks"></a>Remarques  
 La balise \<exception> vous permet de spécifier quelles exceptions peuvent être levées. Cette balise peut être appliquée à des définitions de méthodes, de propriétés, d’événements et d’indexeurs.  
  
 Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation dans un fichier.  
  
 Pour plus d’informations sur la gestion des exceptions, consultez [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/index.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
