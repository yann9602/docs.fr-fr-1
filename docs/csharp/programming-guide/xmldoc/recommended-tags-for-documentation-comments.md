---
title: "Balises recommand&#233;es pour les commentaires de documentation (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "XML [C#], balises"
  - "documentation XML [C#], balises"
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Balises recommand&#233;es pour les commentaires de documentation (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le compilateur C\# traite des commentaires de documentation dans votre code et les met en forme dans un fichier XML dont vous spécifiez le nom dans l'option de ligne de commande **\/doc**.  Pour créer la documentation finale sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé, ou utilisez un outil [Pâté de sable \(sandbox\)](http://shfb.codeplex.com/)tel que.  
  
 Les balises sont traitées sur les constructions de code telles que les types et membres de types.  
  
> [!NOTE]
>  Les commentaires de documentation ne peuvent pas être appliqués à un espace de noms.  
  
 Le compilateur traite n'importe quelle balise représentant du XML correct.  Les balises suivantes fournissent des fonctionnalités fréquemment employées dans la documentation utilisateur.  
  
## Balises  
  
||||  
|-|-|-|  
|[\<c\>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para\>](../../../csharp/programming-guide/xmldoc/para.md)|[\<see\>](../../../csharp/programming-guide/xmldoc/see.md)\*|  
|[\<code\>](../../../csharp/programming-guide/xmldoc/code.md)|[\<param\>](../../../csharp/programming-guide/xmldoc/param.md)\*|[\<seealso\>](../../../csharp/programming-guide/xmldoc/seealso.md)\*|  
|[\<example\>](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref\>](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<summary\>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|[\<exception\>](../../../csharp/programming-guide/xmldoc/exception.md)\*|[\<permission\>](../../../csharp/programming-guide/xmldoc/permission.md)\*|[\<typeparam\>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*|  
|[\<include\>](../../../csharp/programming-guide/xmldoc/include.md)\*|[\<remarks\>](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref\>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[\<list\>](../../../csharp/programming-guide/xmldoc/list.md)|[\<returns\>](../../../csharp/programming-guide/xmldoc/returns.md)|[\<value\>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 \(\* indique que le compilateur vérifie la syntaxe.\)  
  
 Si vous souhaitez des crochets pointus pour apparaître dans le texte d'un commentaire de documentation, d'une utilisation `<` et `>`, comme indiqué dans l'exemple suivant.  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [\/doc \(Process Documentation Comments\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [Commentaires de documentation XML](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)