---
title: "Comment&#160;: ajouter des contr&#244;les dans une collection au moment de l&#39;ex&#233;cution, ou comment les supprimer | Microsoft Docs"
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
  - "collections, ajouter des éléments"
  - "contrôles (Windows Forms), ajouter avec des collections"
  - "contrôles (Windows Forms), supprimer avec des collections"
  - "Controls (collections)"
  - "au moment de l'exécution, ajouter des contrôles"
  - "au moment de l'exécution, supprimer des contrôles"
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: ajouter des contr&#244;les dans une collection au moment de l&#39;ex&#233;cution, ou comment les supprimer
Les tâches courantes du développement d'applications incluent l'ajout et la suppression de contrôles dans un contrôle conteneur de vos formulaires \(par exemple, le contrôle <xref:System.Windows.Forms.Panel> ou <xref:System.Windows.Forms.GroupBox>, voire le formulaire lui\-même\).  Au moment du design, vous pouvez faire glisser des contrôles directement vers un panneau ou une zone de groupe.  Au moment de l'exécution, ces contrôles gèrent une collection `Controls`, qui effectue le suivi des contrôles qui y sont placés.  
  
> [!NOTE]
>  L'exemple de code suivant s'applique à n'importe quel contrôle qui gère une collection de contrôles qui y sont contenus.  
  
### Pour ajouter par programme un contrôle à une collection  
  
1.  Créez une instance du contrôle à ajouter.  
  
2.  Définissez les propriétés du nouveau contrôle.  
  
3.  Ajoutez le contrôle à la collection `Controls` du contrôle parent.  
  
     L'exemple de code suivant montre comment créer une instance du contrôle <xref:System.Windows.Forms.Button>.  Il nécessite l'utilisation d'un formulaire avec un contrôle <xref:System.Windows.Forms.Panel> ; par ailleurs, la méthode de gestion d'événements pour le bouton en cours de création \(`NewPanelButton_Click`\) doit déjà exister.  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code   
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {   
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code   
       // below is used as an example. Substite the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### Pour supprimer par programme des contrôles d'une collection  
  
1.  Supprimez le gestionnaire d'événements de l'événement.  En [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], utilisez le mot clé [RemoveHandler Statement](../../../../ocs/visual-basic/language-reference/statements/removehandler-statement.md) ; en [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], utilisez [\-\=, opérateur](../Topic/-=%20Operator%20\(C%23%20Reference\)2.md).  
  
2.  Utilisez la méthode `Remove` pour supprimer le contrôle souhaité de la collection `Controls` du panneau.  
  
3.  Appelez la méthode <xref:System.Windows.Forms.Control.Dispose%2A> pour libérer toutes les ressources utilisées par le contrôle.  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of   
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _   
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of   
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.   
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.Panel>   
 [Panel, contrôle](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)