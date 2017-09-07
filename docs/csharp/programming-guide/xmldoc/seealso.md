---
title: "&lt;seealso&gt; (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cref
- <seealso>
- seealso
dev_langs:
- CSharp
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
caps.latest.revision: 11
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
ms.openlocfilehash: 7b4686ba83d2caedcc6c93ad8877d1da671d10d4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ltseealsogt-c-programming-guide"></a>&lt;seealso&gt; (Guide de programmation C#)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Paramètres  
 cref = " `member`"  
 Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel. Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie. `member` doit être placé entre guillemets doubles (" ").  
  
 Pour plus d’informations sur la façon de créer une référence cref à un type générique, consultez [\<see>](../../../csharp/programming-guide/xmldoc/see.md).  
  
## <a name="remarks"></a>Remarques  
 La balise \<seealso> vous permet de spécifier le texte que vous souhaitez voir apparaître dans une section Voir aussi. Utilisez [\<see>](../../../csharp/programming-guide/xmldoc/see.md) pour spécifier un lien à partir de l’intérieur du texte.  
  
 Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour traiter les commentaires de documentation dans un fichier.  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple d’utilisation de \<seealso>, consultez [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

