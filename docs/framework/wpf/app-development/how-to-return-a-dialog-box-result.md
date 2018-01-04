---
title: "Comment : retourner un résultat de boîte de dialogue"
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
helpviewer_keywords: dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f8133ffa7be9cb4e0600fc2681402d5e0f7471c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-return-a-dialog-box-result"></a>Comment : retourner un résultat de boîte de dialogue
Cet exemple montre comment récupérer le résultat de la boîte de dialogue pour une fenêtre ouverte en appelant <xref:System.Windows.Window.ShowDialog%2A>.  
  
## <a name="example"></a>Exemple  
 Avant qu’une boîte de dialogue se ferme, son <xref:System.Windows.Window.DialogResult%2A> propriété doit être définie avec un <xref:System.Nullable%601> <xref:System.Boolean> qui indique comment l’utilisateur a fermé la boîte de dialogue. Cette valeur est retournée par <xref:System.Windows.Window.ShowDialog%2A> pour autoriser le code client déterminer comment la boîte de dialogue a été fermée et, par conséquent, comment traiter le résultat.  
  
> [!NOTE]
>  <xref:System.Windows.Window.DialogResult%2A>ne peut être définie que si une fenêtre a été ouverte en appelant <xref:System.Windows.Window.ShowDialog%2A>.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Appel de <xref:System.Windows.Window.ShowDialog%2A> requiert l’autorisation d’utiliser toutes les fenêtres et événements d’entrée d’utilisateur sans restriction.
