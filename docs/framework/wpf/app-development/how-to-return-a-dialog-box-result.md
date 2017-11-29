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
ms.openlocfilehash: d5a1b8cdc0544bfba3f708db40e8b9c593b45b35
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="038bd-102">Comment : retourner un résultat de boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="038bd-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="038bd-103">Cet exemple montre comment récupérer le résultat de la boîte de dialogue pour une fenêtre ouverte en appelant <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="038bd-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="038bd-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="038bd-104">Example</span></span>  
 <span data-ttu-id="038bd-105">Avant qu’une boîte de dialogue se ferme, son <xref:System.Windows.Window.DialogResult%2A> propriété doit être définie avec un <xref:System.Nullable%601> <xref:System.Boolean> qui indique comment l’utilisateur a fermé la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="038bd-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="038bd-106">Cette valeur est retournée par <xref:System.Windows.Window.ShowDialog%2A> pour autoriser le code client déterminer comment la boîte de dialogue a été fermée et, par conséquent, comment traiter le résultat.</span><span class="sxs-lookup"><span data-stu-id="038bd-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="038bd-107"><xref:System.Windows.Window.DialogResult%2A>ne peut être définie que si une fenêtre a été ouverte en appelant <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="038bd-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="038bd-108">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="038bd-108">.NET Framework Security</span></span>  
 <span data-ttu-id="038bd-109">Appel de <xref:System.Windows.Window.ShowDialog%2A> requiert l’autorisation d’utiliser toutes les fenêtres et événements d’entrée d’utilisateur sans restriction.</span><span class="sxs-lookup"><span data-stu-id="038bd-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
