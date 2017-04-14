---
title: "Proc&#233;dure pas &#224; pas&#160;: utilisation du contr&#244;le MaskedTextBox | Microsoft Docs"
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
  - "entrée, contrôler pour garantir la validité"
  - "MaskedTextBox (contrôle Windows Forms), validation"
  - "MaskedTextBox (contrôle Windows Forms), procédures pas à pas"
  - "texte, contrôles pour l'entrée"
  - "entrée d'utilisateur, contrôler"
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Proc&#233;dure pas &#224; pas&#160;: utilisation du contr&#244;le MaskedTextBox
Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Initialisation du contrôle <xref:System.Windows.Forms.MaskedTextBox>  
  
-   Utilisation du gestionnaire d'événements <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> pour avertir l'utilisateur lorsqu'un caractère n'est pas conforme au masque  
  
-   Assignation d'un type à la propriété <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> et utilisation du gestionnaire d'événements <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> pour avertir l'utilisateur lorsque la valeur qu'il essaie de valider n'est pas valide pour le type  
  
## Création du projet et ajout d'un contrôle  
  
#### Pour ajouter un contrôle MaskedTextBox à votre formulaire  
  
1.  Ouvrez le formulaire sur lequel vous souhaitez placer le contrôle <xref:System.Windows.Forms.MaskedTextBox>.  
  
2.  Faites glisser un contrôle <xref:System.Windows.Forms.MaskedTextBox> de la **Boîte à outils** vers votre formulaire.  
  
3.  Cliquez avec le bouton droit sur le contrôle et choisissez **Propriétés**.  Dans la fenêtre **Propriétés**, sélectionnez la propriété **Masque** et cliquez sur le bouton de sélection **...** en regard du nom de la propriété.  
  
4.  Dans la boîte de dialogue **Masque de saisie**, sélectionnez le masque **Date courte**, puis cliquez sur **OK**.  
  
5.  Dans la fenêtre **Propriétés**, affectez à la propriété <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> la valeur `true`.  Avec cette propriété, un court signal sonore est déclenché chaque fois que l'utilisateur essaie d'entrer un caractère qui n'est pas conforme à la définition du masque.  
  
 Pour obtenir un résumé des caractères que la propriété Masque prend en charge, consultez la section Notes de la propriété <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>.  
  
## Alerter l'utilisateur des erreurs d'entrée  
  
#### Ajoutez une info\-bulle pour les refus d'entrée dans le masque  
  
1.  Retournez à la **Boîte à outils** et ajoutez une <xref:System.Windows.Forms.ToolTip> à votre formulaire.  
  
2.  Créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> qui déclenche le <xref:System.Windows.Forms.ToolTip> en cas d'erreur d'entrée.  L'info\-bulle demeure visible pendant cinq secondes, ou jusqu'à ce que l'utilisateur clique dessus.  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
  
    ```  
  
## Alerter l'utilisateur des types non valides  
  
#### Ajoutez une info\-bulle pour les types de données non valides  
  
1.  Dans le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load> de votre formulaire, assignez un objet <xref:System.Type> représentant le type <xref:System.DateTime> à la propriété <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> du contrôle <xref:System.Windows.Forms.MaskedTextBox> :  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2.  Ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> :  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.MaskedTextBox>   
 [MaskedTextBox, contrôle](../../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)