---
title: Impossible de combiner VbStrConv.Wide et VbStrConv.Narrow | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArgument_IllegalWideNarrow
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8d184fab3a63bc69caa67f315a9cb0f32514e2c1
ms.lasthandoff: 03/13/2017

---
# <a name="vbstrconvwide-and-vbstrconvnarrow-cannot-be-combined"></a>Impossible de combiner VbStrConv.Wide et VbStrConv.Narrow
Votre application essaie de combiner les membres de l’énumération `VbStrConv` `Wide` et `Narrow`, qui s’excluent mutuellement.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Supprimez `VbStrConv.Wide` ou `VbStrConv.Narrow`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Globalization>   
 [Énumération de VbStrConv NOTINBUILD](http://msdn.microsoft.com/en-us/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Introduction aux applications internationales basées sur le .NET Framework](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
