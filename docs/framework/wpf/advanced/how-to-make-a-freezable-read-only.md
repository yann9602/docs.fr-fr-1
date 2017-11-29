---
title: "Comment : mettre un Freezable en lecture seule"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c407a2fcccfbda29ba23f63ba6ae71302c734d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-a-freezable-read-only"></a>Comment : mettre un Freezable en lecture seule
Cet exemple montre comment rendre un <xref:System.Windows.Freezable> en lecture seule en appelant sa <xref:System.Windows.Freezable.Freeze%2A> (méthode).  
  
 Vous ne pouvez pas figer un <xref:System.Windows.Freezable> si l’une des conditions suivantes est de l’objet `true` sur l’objet :  
  
-   Il a animé ou propriétés lié aux données.  
  
-   Il possède des propriétés qui sont définies par une ressource dynamique. Pour plus d’informations sur les ressources dynamiques, consultez le [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Il contient <xref:System.Windows.Freezable> sous-objets qui ne peut pas être figés.  
  
 Si ces conditions sont `false` pour votre <xref:System.Windows.Freezable> objet et que vous ne souhaitez pas modifier, envisagez de geler pour gagner des avantages de performances.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant gèle un <xref:System.Windows.Media.SolidColorBrush>, qui est un type de <xref:System.Windows.Freezable> objet.  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 Pour plus d’informations sur <xref:System.Windows.Freezable> , consultez la [vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CanFreeze%2A>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [Vue d’ensemble des objets Freezable](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
