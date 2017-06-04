---
title: "Comment&#160;: ajouter des contr&#244;les &#224; des Windows Forms | Microsoft Docs"
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
  - "contrôles (Windows Forms), ajouter"
  - "contrôles Windows Forms, ajouter aux formulaires"
ms.assetid: 2af86001-9d62-4154-87fb-66db2c3cd9fd
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: ajouter des contr&#244;les &#224; des Windows Forms
La plupart des formulaires sont conçus en ajoutant à leur surface des contrôles pour définir une interface utilisateur.  Un *contrôle* est un composant d'un formulaire utilisé pour afficher des informations ou pour accepter les entrées d'utilisateur.  Pour plus d'informations sur les contrôles, consultez [contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour dessiner un contrôle sur un formulaire  
  
1.  Ouvrez le formulaire.  Pour plus d'informations, consultez [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/fr-fr/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  Dans la **Boîte à outils**, cliquez sur le contrôle à ajouter au formulaire.  
  
3.  Dans le formulaire, cliquez sur l'endroit où doit venir se positionner le coin supérieur gauche du contrôle, puis faites glisser la souris jusqu'à l'endroit où doit venir se positionner son coin supérieur droit.  
  
     Le contrôle est ajouté au formulaire avec la position et la taille indiquées.  
  
    > [!NOTE]
    >  Une taille par défaut est définie pour chaque contrôle.  Pour ajouter un contrôle de la taille par défaut, faites\-le glisser jusqu'au formulaire à partir de la **Boîte à outils**.  
  
### Pour faire glisser un contrôle jusqu'à un formulaire  
  
1.  Ouvrez le formulaire.  Pour plus d'informations, consultez [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/fr-fr/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5).  
  
2.  Dans la **Boîte à outils**, cliquez sur le contrôle souhaité et faites\-le glisser jusqu'à votre formulaire.  
  
     Le contrôle est ajouté au formulaire avec la taille par défaut et à la position indiquée.  
  
    > [!NOTE]
    >  Vous pouvez double\-cliquer sur un contrôle dans la **Boîte à outils** pour l'ajouter dans le coin supérieur gauche du formulaire avec sa taille par défaut.  
  
     En outre, il est possible d'ajouter dynamiquement des contrôles à un formulaire au moment de l'exécution.  Dans l'exemple de code suivant, un contrôle <xref:System.Windows.Forms.TextBox> est ajouté au formulaire lorsque vous cliquez sur le contrôle <xref:System.Windows.Forms.Button>.  
  
    > [!NOTE]
    >  La procédure suivante requiert l'existence d'un formulaire sur lequel est déjà placé un contrôle **Bouton** \(`Button1`\).  
  
### Pour ajouter par programme un contrôle à un formulaire  
  
1.  Dans la méthode qui gère l'événement `Click` du bouton au sein de la classe de votre formulaire, insérez du code semblable au code ci\-dessous afin d'ajouter une référence à la variable du contrôle, de définir `Location` du contrôle et d'ajouter le contrôle.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim MyText As New TextBox()  
       MyText.Location = New Point(25, 25)  
       Me.Controls.Add(MyText)  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       TextBox myText = new TextBox();  
       myText.Location = new Point(25,25);  
       this.Controls.Add (myText);  
    }  
  
    ```  
  
    ```cpp  
    private:  
      System::Void button1_Click(System::Object ^  sender,  
        System::EventArgs ^  e)  
      {  
        TextBox ^ myText = gcnew TextBox();  
        myText->Location = Point(25,25);  
        this->Controls->Add(myText);  
      }  
    ```  
  
    > [!NOTE]
    >  Vous pouvez également ajouter du code pour initialiser d'autres propriétés du contrôle.  
  
    > [!IMPORTANT]
    >  Vous risquez d'exposer votre ordinateur local à un problème de sécurité sur le réseau si vous référencez un `UserControl` nuisible.  Ce risque est présent dans le cas d'une personne malveillante qui crée un contrôle personnalisé préjudiciable, si vous ajoutez par erreur ce contrôle à votre projet.  
  
## Voir aussi  
 [contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)   
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [Comment : redimensionner des contrôles sur des Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md)   
 [Comment : définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)