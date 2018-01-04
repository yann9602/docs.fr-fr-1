---
title: "Comment : déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l'utilisateur a cliqué"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a91ad8c28bae7d517a9e13937d5de340b1b6a605
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="9d8bd-102">Comment : déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l'utilisateur a cliqué</span><span class="sxs-lookup"><span data-stu-id="9d8bd-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="9d8bd-103">Le <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> contrôles remplacer et ajouter des fonctionnalités à la <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> contrôle ; Toutefois, le <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> contrôles sont conservés pour la compatibilité descendante et l’utilisation future si vous Choisissez.</span><span class="sxs-lookup"><span data-stu-id="9d8bd-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="9d8bd-104">Programme le [contrôle StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) contrôle pour répondre aux clics de l’utilisateur, utilisez une instruction case dans la <xref:System.Windows.Forms.StatusBar.PanelClick> événement.</span><span class="sxs-lookup"><span data-stu-id="9d8bd-104">To program the [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="9d8bd-105">L’événement contient un argument (l’argument panel), qui contient une référence à le clic sur <xref:System.Windows.Forms.StatusBarPanel>.</span><span class="sxs-lookup"><span data-stu-id="9d8bd-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="9d8bd-106">À l’aide de cette référence, vous pouvez déterminer l’index du panneau et programmer en conséquence.</span><span class="sxs-lookup"><span data-stu-id="9d8bd-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d8bd-107">Vérifiez que le <xref:System.Windows.Forms.StatusBar> du contrôle <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> est définie sur `true`.</span><span class="sxs-lookup"><span data-stu-id="9d8bd-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="9d8bd-108">Pour déterminer l’utilisateur a cliqué sur le panneau de configuration</span><span class="sxs-lookup"><span data-stu-id="9d8bd-108">To determine which panel was clicked</span></span>  
  
1.  <span data-ttu-id="9d8bd-109">Dans le <xref:System.Windows.Forms.StatusBar.PanelClick> Gestionnaire d’événements, utilisez un `Select Case` (dans [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) ou `switch case` ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ou [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) pour déterminer le panneau a été utilisé en examinant l’index du panneau dans les arguments d’événement.</span><span class="sxs-lookup"><span data-stu-id="9d8bd-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) or `switch case` ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] or [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="9d8bd-110">L’exemple de code suivant nécessite la présence, dans le formulaire, d’un <xref:System.Windows.Forms.StatusBar> (contrôle), `StatusBar1`et deux <xref:System.Windows.Forms.StatusBarPanel> objets, `StatusBarPanel1` et `StatusBarPanel2`.</span><span class="sxs-lookup"><span data-stu-id="9d8bd-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,   
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     <span data-ttu-id="9d8bd-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="9d8bd-111">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.statusBar1.PanelClick += new   
       System.Windows.Forms.StatusBarPanelClickEventHandler   
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9d8bd-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d8bd-112">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="9d8bd-113">Guide pratique pour définir la taille des panneaux de la barre d'état</span><span class="sxs-lookup"><span data-stu-id="9d8bd-113">How to: Set the Size of Status-Bar Panels</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-size-of-status-bar-panels.md)  
 [<span data-ttu-id="9d8bd-114">Procédure pas à pas : mise à jour des informations de barre d'état au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="9d8bd-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [<span data-ttu-id="9d8bd-115">Vue d’ensemble du contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="9d8bd-115">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)
