---
title: "Comment&#160;: r&#233;organiser des formulaires MDI enfants | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "formulaires enfants, réorganiser"
  - "MDI, réorganiser les formulaires enfants"
ms.assetid: a0786378-3206-4ccc-898e-7d3b38cc5089
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: r&#233;organiser des formulaires MDI enfants
Les applications comportent souvent des commandes de menu qui permettent de disposer en mosaïque ou en cascade les formulaires MDI enfants ouverts, ou encore de les réorganiser.  Vous pouvez utiliser la méthode <xref:System.Windows.Forms.Form.LayoutMdi%2A> avec l'une des valeurs de l'énumération <xref:System.Windows.Forms.MdiLayout> pour réorganiser les formulaires enfants dans un formulaire MDI parent.  
  
 Les valeurs de l'énumération <xref:System.Windows.Forms.MdiLayout> permettent d'afficher des formulaires enfants en cascade, en mosaïque horizontale ou verticale, ou sous forme d'icônes de formulaires enfants disposées dans la partie inférieure du formulaire MDI.  Ces valeurs ont le même effet que les commandes Windows **Cascade**, **Afficher les fenêtres côte à côte**, **Afficher les fenêtres empilées** et **Afficher le Bureau**, respectivement.  
  
 Ces méthodes sont souvent utilisées en tant que gestionnaires d'événements appelés par l'événement <xref:System.Windows.Forms.Control.Click> d'un élément de menu.  Ainsi, un élément de menu présentant le texte « Cascade » peut produire l'effet souhaité dans les fenêtres MDI enfants.  
  
### Pour réorganiser les formulaires enfants  
  
1.  Dans une méthode, utilisez la méthode <xref:System.Windows.Forms.Form.LayoutMdi%2A> pour définir l'énumération <xref:System.Windows.Forms.MdiLayout> pour le formulaire MDI parent.  L'exemple ci\-dessous utilise la valeur d'énumération <xref:System.Windows.Forms.MdiLayout?displayProperty=fullName> pour les fenêtres enfants du formulaire MDI parent \(`Form1`\).  L'énumération est utilisée dans le code pendant l'exécution du Gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Control.Click> de l'élément de menu **Cascade**.  
  
    ```vb  
    Protected Sub CascadeWindows_Click(ByVal sender As System.Object, ByVal e As System.EventArgs)  
       Me.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade)  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void CascadeWindows_Click(object sender, System.EventArgs e){  
       this.LayoutMdi(System.Windows.Forms.MdiLayout.Cascade);  
    }  
    ```  
  
    > [!NOTE]
    >  De la même façon, vous pouvez disposer les fenêtres en mosaïque et les afficher sous forme d'icônes en modifiant la valeur d'énumération <xref:System.Windows.Forms.MdiLayout> utilisée.  
  
2.  Si vous utilisez Visual C\#, placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d'événements.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
## Voir aussi  
 [Applications d'interface multidocument \(MDI, Multiple Document Interface\)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)   
 [Comment : créer des formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [Comment : créer des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)   
 [Comment : déterminer l'enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)   
 [Comment : envoyer des données à l'enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)