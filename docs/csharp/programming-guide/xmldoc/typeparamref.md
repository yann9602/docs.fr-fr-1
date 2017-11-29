---
title: "&lt;typeparamref&gt; (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 296761f72d3d306c4f37632d7110e31b62c44734
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lttypeparamrefgt-c-programming-guide"></a>&lt;typeparamref&gt; (Guide de programmation C#)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a>Paramètres  
 `name`  
 Nom du paramètre de type. Mettez le nom entre guillemets doubles (" ").  
  
## <a name="remarks"></a>Remarques  
 Pour plus d’informations sur les paramètres de type dans les types et méthodes génériques, consultez [Génériques](../../../csharp/programming-guide/generics/index.md).  
  
 Utilisez cette balise pour permettre aux consommateurs du fichier de documentation d’appliquer une mise en forme particulière au mot, par exemple l’italique.  
  
 Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Balises recommandées pour les commentaires de documentation](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
