---
title: "Comment&#160;: d&#233;finir le texte affich&#233; par un contr&#244;le Windows Forms | Microsoft Docs"
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
  - "bouton (contrôle Windows Forms), texte du bouton"
  - "bouton (contrôle Windows Forms), affichage de texte"
  - "boutons, texte"
  - "légendes, définir"
  - "légendes, contrôles Windows Forms"
  - "contrôles (Windows Forms), légendes"
  - "exemples (Windows Forms), contrôles"
  - "formulaires, légendes"
  - "étiquettes, ajouter au contrôle CommandButton"
  - "StdFont (objet) et CommandButton (légende)"
  - "texte"
  - "Text (propriété), contrôle Windows Forms"
  - "texte, contrôles Windows Forms"
  - "Windows Forms, légendes"
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: d&#233;finir le texte affich&#233; par un contr&#244;le Windows Forms
Généralement, les contrôles Windows Forms affichent du texte en rapport avec la fonction principale du contrôle.  Par exemple, un contrôle <xref:System.Windows.Forms.Button> affiche habituellement une légende indiquant l'action à exécuter quand le bouton est activé.  Pour tous les contrôles, vous pouvez définir ou retourner le texte à l'aide de la propriété <xref:System.Windows.Forms.Control.Text%2A>.  Vous pouvez modifier la police en utilisant la propriété <xref:System.Windows.Forms.Control.Font%2A>.  Vous pouvez également définir le texte à l'aide du concepteur.  Consultez également [Comment : créer des touches d'accès rapide pour les contrôles Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/ms233673%20\(v=vs.110\)), [Comment : définir le texte affiché par un contrôle Windows Forms à l'aide du concepteur](http://msdn.microsoft.com/library/ms233665%20\(v=vs.110\)), [Comment : définir l'image affichée par un contrôle Windows Forms](http://msdn.microsoft.com/library/ms233656%20\(v=vs.110\)).  
  
### Pour définir le texte affiché par un contrôle par programmation  
  
1.  Affectez une chaîne comme valeur de la propriété <xref:System.Windows.Forms.Control.Text%2A>.  
  
     Pour créer une touche d'accès soulignée, incluez une esperluette \(&\) avant la lettre qui sera la touche d'accès.  
  
2.  Affectez un objet de type <xref:System.Drawing.Font> comme valeur de la propriété <xref:System.Windows.Forms.Control.Font%2A>.  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp#  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  Vous pouvez utiliser un caractère d'échappement pour afficher un caractère spécial dans des éléments d'interface utilisateur qui l'interpréteraient normalement différemment, tels que des éléments de menu.  Par exemple, la ligne de code suivante définit le texte de l'élément de menu pour qu'il indique « & Now For Something Completely Different » :  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp#  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.Text%2A?displayProperty=fullName>   
 [Comment : créer des touches d'accès rapide pour des contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)   
 [Comment : répondre à un clic du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)