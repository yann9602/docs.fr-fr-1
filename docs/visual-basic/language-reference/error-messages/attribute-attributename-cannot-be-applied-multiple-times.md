---
title: "Attribut & #39 ; &lt;attributename&gt;& #39 ; ne peut pas être appliqué plusieurs fois"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30663
- vbc30663
helpviewer_keywords: BC30663
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 216cf54fd164ca95b6378517a679b5b54183559f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="attribute-39ltattributenamegt39-cannot-be-applied-multiple-times"></a>Attribut & #39 ; &lt;attributename&gt;& #39 ; ne peut pas être appliqué plusieurs fois
L’attribut peut uniquement être appliqué qu’une seule fois. Le `AttributeUsage` attribut détermine si un attribut peut être appliqué plusieurs fois.  
  
 **ID d’erreur :** BC30663  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous que l’attribut n’est appliqué qu’une seule fois.  
  
2.  Si vous utilisez des attributs personnalisés que vous avez développés, envisagez de modifier leur `AttributeUsage` attribut pour permettre l’utilisation d’attributs multiples, comme dans l’exemple suivant.  
  
```vb  
<AttributeUsage(AllowMultiple := True)>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.AttributeUsageAttribute>  
 [Création d’attributs personnalisés](../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [AttributeUsage](../../../visual-basic/programming-guide/concepts/attributes/attributeusage.md)
