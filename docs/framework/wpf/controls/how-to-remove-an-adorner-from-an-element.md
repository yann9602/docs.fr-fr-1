---
title: "Comment : supprimer un ornement d'un élément"
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
helpviewer_keywords: adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20d17ef43f99f6815334c0acbf7eb2040959751e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remove-an-adorner-from-an-element"></a>Comment : supprimer un ornement d'un élément
Cet exemple montre comment supprimer par programme un ornement spécifique d’un <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Exemple  
 Cet exemple de code en clair supprime le premier ornement du tableau des ornements retourné par <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  Cet exemple se trouve récupère les ornements d’un <xref:System.Windows.UIElement> nommé *myTextBox*.  Si l’élément spécifié dans l’appel à <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> n’a pas d’ornements, `null` est retourné.  Ce code vérifie un tableau null explicitement et est idéale pour les applications où un tableau null est censé être relativement courante.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a>Exemple  
 Cet exemple de code condensé est fonctionnellement équivalent à l’exemple détaillé ci-dessus. Ce code ne vérifie pas explicitement un tableau null, il est donc possible qu’un <xref:System.NullReferenceException> exception peut être déclenchée.  Ce code est mieux adapté aux applications où un tableau null est supposé être rares.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des ornements](../../../../docs/framework/wpf/controls/adorners-overview.md)
