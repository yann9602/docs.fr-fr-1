---
title: "Comment : appeler une boîte de dialogue Imprimer"
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
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ba541b367e56a809fa444528dccd69860c4de46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-invoke-a-print-dialog"></a>Comment : appeler une boîte de dialogue Imprimer
Pour fournir la possibilité d’imprimer depuis votre application, vous pouvez simplement créer et ouvrir un <xref:System.Windows.Controls.PrintDialog> objet.  
  
## <a name="example"></a>Exemple  
 Le contrôle <xref:System.Windows.Controls.PrintDialog> offre un point d'entrée unique pour l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], la configuration et la soumission de travaux [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]. Le contrôle est facile à utiliser et peut être instancié à l’aide de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] balisage ou code. L’exemple suivant montre comment instancier et ouvrir le contrôle dans le code et l’impression à partir de celui-ci. Il montre également comment s’assurer que la boîte de dialogue donner à l’utilisateur la possibilité de définir une plage de pages spécifique. L’exemple de code suppose qu’il existe un fichier FixedDocumentSequence.xps à la racine du lecteur C:.  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 Une fois que la boîte de dialogue est ouverte, les utilisateurs pourront sélectionner dans les imprimantes installées sur leur ordinateur. Ils aura également la possibilité de sélectionner le [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319) pour créer un [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] fichier au lieu de l’impression.  
  
> [!NOTE]
>  Le <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> contrôle de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], qui est décrite dans cette rubrique, ne doit pas être confondu avec le <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> composant de [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].  
  
 En principe, vous pouvez utiliser la <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> méthode sans jamais ouvrir la boîte de dialogue. Dans ce sens, le contrôle peut être utilisé comme un composant d’impression inaperçu. Mais pour des raisons de performances, il serait préférable d’utiliser le <xref:System.Printing.PrintQueue.AddJob%2A> méthode ou l’une des nombreuses <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> et <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> méthodes de la <xref:System.Windows.Xps.XpsDocumentWriter>. Pour plus d’informations, consultez [par programme les fichiers impression XPS](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) et.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.PrintDialog>  
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Vue d’ensemble de l’impression](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319)
