---
title: "Référence d’assembly friend &lt;référence&gt; n’est pas valide"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords: BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39ae94e309ee8d18e6b5317445b7e4b7f6a42af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a>Référence d’assembly friend &lt;référence&gt; n’est pas valide
Référence d’assembly friend \<référence > n’est pas valide. Les assemblys signés avec un nom fort doivent spécifier une clé publique dans leurs déclarations InternalsVisibleTo.  
  
 Le nom d’assembly passé à la <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> constructeur d’attribut identifie un assembly avec nom fort, mais il n’inclut pas un `PublicKey` attribut.  
  
 **ID d’erreur :** BC31535  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Déterminez la clé publique de l’assembly friend avec un nom fort. Inclure la clé publique comme partie du nom de l’assembly passé à la <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> constructeur d’attribut à l’aide de la `PublicKey` attribut.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection.AssemblyName>  
 [Assemblys friend](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)  
 [Guide pratique : créer des assemblys Friend signés](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)
