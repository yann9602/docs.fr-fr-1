---
title: "Comment : ouvrir un fichier qui est déplacé dans un contrôle RichTextBox"
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
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dfb5f0f442b18159c18a6e5345f6757674fbb90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>Comment : ouvrir un fichier qui est déplacé dans un contrôle RichTextBox
Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], le <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, et <xref:System.Windows.Documents.FlowDocument> tous les contrôles ont des fonctionnalités intégrées de glisser-déplacer. La fonctionnalité intégrée permet de glisser-déplacer du texte au sein et entre les contrôles. Toutefois, elle ne permet pas l’ouverture d’un fichier en supprimant le fichier sur le contrôle. Ces contrôles marquent également les événements de glisser-déplacer comme géré. Par conséquent, par défaut, vous ne pouvez pas ajouter vos propres gestionnaires d’événements pour fournir une fonctionnalité pour ouvrir des fichiers déposés.  
  
 Pour ajouter une gestion supplémentaire pour les événements de glisser-déplacer dans ces contrôles, utilisez le <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> pour ajouter vos gestionnaires d’événements pour les événements de glisser-déplacer. Définir le `handledEventsToo` paramètre `true` pour que le gestionnaire spécifié soit appelé pour un événement routé qui a déjà été marqué comme géré par un autre élément le long de l’itinéraire d’événement.  
  
> [!TIP]
>  Vous pouvez remplacer la fonctionnalité de glisser-déplacer intégrée de <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, et <xref:System.Windows.Documents.FlowDocument> en gérant les versions préliminaires des événements de glisser-déplacer et de marquer les événements d’aperçu comme géré. Toutefois, cela désactive la fonctionnalité de glisser-déposer intégrée et n’est pas recommandée.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment ajouter des gestionnaires pour les <xref:System.Windows.DragDrop.DragOver> et <xref:System.Windows.DragDrop.Drop> événements sur un <xref:System.Windows.Controls.RichTextBox>. Cet exemple utilise le <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> méthode et définit le `handledEventsToo` paramètre `true` afin que les gestionnaires d’événements seront appelés même si le <xref:System.Windows.Controls.RichTextBox> marque ces événements comme étant géré. Le code dans les gestionnaires d’événements ajoute des fonctionnalités pour ouvrir un fichier texte qui est déplacé dans le <xref:System.Windows.Controls.RichTextBox>.  
  
 Pour tester cet exemple, faites glisser un fichier texte ou un fichier de format RTF du texte enrichi à partir de l’Explorateur Windows pour le <xref:System.Windows.Controls.RichTextBox>. Le fichier va être ouvert dans le <xref:System.Windows.Controls.RichTextBox>. Si vous appuyez sur la touche MAJ avant de supprimer le fichier, le fichier s’ouvre sous forme de texte brut.  
  
 [!code-xaml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
