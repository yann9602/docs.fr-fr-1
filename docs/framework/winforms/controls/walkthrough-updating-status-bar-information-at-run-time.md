---
title: "Proc&#233;dure pas &#224; pas&#160;: mise &#224; jour des informations de barre d&#39;&#233;tat au moment de l&#39;ex&#233;cution | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "panneaux, actualiser la barre d'état"
  - "barres d'état, actualiser les panneaux"
  - "barres d'état, mettre à jour au moment de l'exécution"
  - "StatusBar (contrôle Windows Forms), actualiser les panneaux"
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Proc&#233;dure pas &#224; pas&#160;: mise &#224; jour des informations de barre d&#39;&#233;tat au moment de l&#39;ex&#233;cution
> [!IMPORTANT]
>  Les contrôles <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> remplacent les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> et y ajoutent des fonctionnalités ; toutefois, les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> sont conservés pour la compatibilité descendante et une utilisation future, si tel est votre choix.  
  
 Souvent, un programme vous demandera de mettre à jour le contenu des volets de barre d'état de façon dynamique au moment de l'exécution, en fonction des changements de l'état de l'application ou de toute autre interaction utilisateur.  Il s'agit là d'un moyen très répandu de signaler aux utilisateurs que des touches telles que VERR.MAJ, VERR.NUM ou DÉFIL sont activées, ou de fournir des références de date ou d'heure.  
  
 Dans l'exemple suivant, vous utiliserez une instance de la classe <xref:System.Windows.Forms.StatusBarPanel> pour héberger une horloge.  
  
### Pour préparer la barre d'état pour la mise à jour  
  
1.  Créez un formulaire Windows.  
  
2.  Ajoutez un contrôle <xref:System.Windows.Forms.StatusBar> à votre formulaire.  Pour plus d'informations, consultez [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
3.  Ajoutez un panneau de barre d'état à votre contrôle <xref:System.Windows.Forms.StatusBar>.  Pour plus d'informations, consultez [Comment : ajouter des panneaux à un contrôle StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md).  
  
4.  Pour le contrôle <xref:System.Windows.Forms.StatusBar> que vous avez ajouté à votre formulaire, affectez à la propriété <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> la valeur `true`.  
  
5.  Ajoutez un composant <xref:System.Windows.Forms.Timer> Windows Forms au formulaire.  
  
    > [!NOTE]
    >  Le composant <xref:System.Windows.Forms.Timer?displayProperty=fullName> Windows Forms est conçu pour un environnement Windows Forms.  Si vous avez besoin d'une minuterie \(Timer\) adaptée à un environnement serveur, consultez [Introduction to Server\-Based Timers](http://msdn.microsoft.com/fr-fr/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
6.  Affectez à la propriété <xref:System.Windows.Forms.Timer.Enabled%2A> la valeur `true`.  
  
7.  Affectez à la propriété <xref:System.Windows.Forms.Timer.Interval%2A> de <xref:System.Windows.Forms.Timer> la valeur 30000.  
  
    > [!NOTE]
    >  La propriété <xref:System.Windows.Forms.Timer.Interval%2A> du composant <xref:System.Windows.Forms.Timer> a la valeur 30 secondes \(30 000 millisecondes\) pour garantir la précision de l'heure affichée.  
  
### Pour implémenter la minuterie et mettre à jour la barre d'état  
  
1.  Insérez le code suivant dans le gestionnaire d'événements du composant <xref:System.Windows.Forms.Timer> de manière à mettre à jour le panneau du contrôle <xref:System.Windows.Forms.StatusBar>.  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     À ce stade, vous êtes prêt à exécuter l'application et à observer le fonctionnement de l'horloge dans le panneau de la barre d'état.  
  
### Pour tester l'application  
  
1.  Déboguez l'application et appuyez sur F5 pour l'exécuter.  Pour plus d'informations sur le débogage, consultez [Débogage dans Visual Studio](../Topic/Debugging%20in%20Visual%20Studio.md).  
  
    > [!NOTE]
    >  L'horloge s'affichera dans la barre d'état au bout d'environ 30 secondes.  Ce délai est nécessaire pour obtenir l'heure la plus précise possible.  En revanche, pour que l'horloge s'affiche plus vite, vous pouvez réduire la valeur de la propriété <xref:System.Windows.Forms.Timer.Interval%2A> définie à l'étape 7 de la procédure précédente.  
  
## Voir aussi  
 <xref:System.Windows.Forms.StatusBar>   
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 [Comment : ajouter des panneaux à un contrôle StatusBar](../../../../docs/framework/winforms/controls/how-to-add-panels-to-a-statusbar-control.md)   
 [Comment : déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l'utilisateur a cliqué](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)   
 [Vue d'ensemble du contrôle StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)