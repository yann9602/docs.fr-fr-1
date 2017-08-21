---
title: "Comment : créer un domaine d'application"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 39d8db32f82827e76d9517d387e2fc001fc209aa
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-an-application-domain"></a>Comment : créer un domaine d'application
Un hôte Common Language Runtime crée automatiquement des domaines d’application quand ils sont nécessaires. Toutefois, vous pouvez créer vos propres domaines d’application et y charger les assemblys que vous souhaitez gérer personnellement. Vous pouvez également créer des domaines d’application à partir desquels vous exécutez du code.  
  
 Vous pouvez créer un domaine d’application à l’aide de l’une des méthodes **CreateDomain** surchargées dans la classe <xref:System.AppDomain?displayProperty=fullName>. Vous pouvez nommer le domaine d’application et le référencer par ce nom.  
  
 L’exemple suivant crée un domaine d’application et lui attribue le nom `MyDomain`, puis imprime le nom du domaine hôte et du domaine d’application enfant créé dans la console.  
  
## <a name="example"></a>Exemple  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)] [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)] [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation avec des domaines d’application](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [Utilisation des domaines d’application](../../../docs/framework/app-domains/use.md)

