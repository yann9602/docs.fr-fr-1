---
title: "&lt;value&gt; (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <value>
dev_langs:
- CSharp
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
caps.latest.revision: 12
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
ms.openlocfilehash: 71c8d5ab2e99291f05ef362960b0eeac969e9de1
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ltvaluegt-c-programming-guide"></a>&lt;value&gt; (Guide de programmation C#)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `property-description`  
 Description de la propriété.  
  
## <a name="remarks"></a>Remarques  
 La balise \<value> vous permet de décrire la valeur représentée par une propriété. Notez que lorsque vous ajoutez une propriété via l’Assistant Code de l’environnement de développement Visual Studio .NET, il ajoute une balise [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) pour la nouvelle propriété. Vous devez ensuite ajouter manuellement une balise \<value> pour décrire la valeur représentée par la propriété.  
  
 Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

