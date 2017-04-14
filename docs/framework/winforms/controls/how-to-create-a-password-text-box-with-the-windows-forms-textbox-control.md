---
title: "Comment&#160;: cr&#233;er une zone de texte pour mot de passe avec le contr&#244;le TextBox Windows Forms | Microsoft Docs"
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
  - "zones de mot de passe, créer"
  - "PasswordChar (propriété dans les zones de texte)"
  - "mots de passe, masque de saisie"
  - "mots de passe, zone de texte pour mot de passe"
  - "TextBox (contrôle Windows Forms), saisir des mots de passe"
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: cr&#233;er une zone de texte pour mot de passe avec le contr&#244;le TextBox Windows Forms
Une zone de mot de passe est une zone de texte Windows Forms qui affiche des caractères d'espace réservé lorsqu'un utilisateur tape une chaîne.  
  
### Pour créer une zone de texte pour mot de passe  
  
1.  Définissez la propriété <xref:System.Windows.Forms.TextBox.PasswordChar%2A> du contrôle <xref:System.Windows.Forms.TextBox> à un caractère spécifique.  
  
     La propriété <xref:System.Windows.Forms.TextBox.PasswordChar%2A> spécifie le caractère affiché dans la zone de texte.  Par exemple, si vous souhaitez que des astérisques s'affichent dans la zone de mot de passe, spécifiez \* pour la propriété <xref:System.Windows.Forms.TextBox.PasswordChar%2A> dans la fenêtre Propriétés.  Puis, indépendamment du caractère qu'un utilisateur tape au clavier, un astérisque apparaît dans la zone de texte.  
  
2.  \(Facultatif\) Définissez la propriété <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>.  La propriété détermine le nombre de caractères qui peuvent être tapés dans la zone de texte.  Si la longueur maximale est dépassée, le système émet un signal sonore et la zone de texte n'accepte plus de caractères.  Peut\-être ne souhaiterez\-vous pas effectuer cette opération, étant donné que la longueur maximale du mot de passe peut être utile au pirate tentant de deviner un mot de passe.  
  
     'exemple de code suivant montre comment initialiser une zone de texte qui acceptera une chaîne de 14 caractères au maximum et affichera des astérisques à la place de la chaîne.  La procédure `InitializeMyControl`  ne s'exécutera pas automatiquement ; elle doit être appelée.  
  
    > [!IMPORTANT]
    >  L'utilisation de la propriété <xref:System.Windows.Forms.TextBox.PasswordChar%2A> dans une zone de texte permet de garantir que personne d'autre ne pourra lire le mot de passe d'un utilisateur en observant la saisie de celui\-ci.  Cette mesure de sécurité ne concerne aucunement le stockage ou la transmission du mot de passe par votre application.  Dans la mesure où le texte saisi n'est pas chiffré, vous devez le considérer comme n'importe quelle donnée confidentielle.  Mais s'il n'apparaît pas comme tel, le mot de passe est traité comme une chaîne de texte brut \(sauf si vous avez implémenté d'autres mesures de sécurité\).  
  
    ```vb  
    Private Sub InitializeMyControl()  
       ' Set to no text.  
       TextBox1.Text = ""  
       ' The password character is an asterisk.  
       TextBox1.PasswordChar = "*"  
       ' The control will allow no more than 14 characters.  
       TextBox1.MaxLength = 14  
    End Sub  
  
    ```  
  
    ```csharp  
    private void InitializeMyControl()  
    {  
       // Set to no text.  
       textBox1.Text = "";  
       // The password character is an asterisk.  
       textBox1.PasswordChar = '*';  
       // The control will allow no more than 14 characters.  
       textBox1.MaxLength = 14;  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void InitializeMyControl()  
       {  
          // Set to no text.  
          textBox1->Text = "";  
          // The password character is an asterisk.  
          textBox1->PasswordChar = '*';  
          // The control will allow no more than 14 characters.  
          textBox1->MaxLength = 14;  
       }  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.TextBox>   
 [Vue d'ensemble du contrôle TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)   
 [Comment : contrôler le point d'insertion dans un contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)   
 [Comment : créer une zone de texte en lecture seule](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)   
 [Comment : insérer des guillemets dans une chaîne](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)   
 [Comment : sélectionner du texte dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)   
 [Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)   
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)