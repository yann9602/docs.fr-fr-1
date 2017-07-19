---
title: '&lt;exception&gt; (Guide de programmation C#) | Microsoft Docs'
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- exception
- <exception>
dev_langs:
- CSharp
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2ab14da86cd85eabda58aa2e1177f9f8136e3ee2
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

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
 [!code-cs[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/exception_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
