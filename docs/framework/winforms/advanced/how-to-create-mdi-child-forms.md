---
title: "Comment&#160;: cr&#233;er des formulaires MDI enfants | Microsoft Docs"
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
  - "formulaires enfants"
  - "MDI, créer des formulaires"
ms.assetid: 164b69bb-2eca-4339-ada3-0679eb2c6dda
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Comment&#160;: cr&#233;er des formulaires MDI enfants
Les formulaires MDI enfants constituent un élément essentiel des [Applications d'interface multidocument \(MDI, Multiple Document Interface\)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), car ils représentent le centre de l'interaction utilisateur.  
  
 Dans la procédure suivante, vous allez créer un formulaire MDI enfant qui affiche un contrôle <xref:System.Windows.Forms.RichTextBox>, semblable à la plupart des applications de traitement de texte.  La remplacement du contrôle <xref:System.Windows.Forms> par d'autres contrôles, tels que le contrôle <xref:System.Windows.Forms.DataGridView> ou une combinaison de contrôles, vous permet de créer des fenêtres MDI enfants \(et, par extension, des applications MDI\) avec diverses possibilités.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer des formulaires MDI enfants  
  
1.  Créez un projet Windows Forms.  Dans la fenêtre **Propriétés** du formulaire, affectez la valeur `true` à sa propriété <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, et la valeur `Maximized` à sa propriété `WindowsState`.  
  
     Ainsi, vous désignez le formulaire comme le conteneur MDI des fenêtres enfants.  
  
2.  Faites glisser un contrôle <xref:System.Windows.Forms.MenuStrip> de la `Toolbox` vers le formulaire.  Affectez la valeur **Fichier** à sa propriété `Text`.  
  
3.  Cliquez sur le bouton de sélection \(...\) à côté de la propriété{b\> \<b}**Éléments**, puis cliquez sur **Ajouter** pour ajouter deux éléments de menu ToolStrip enfants.  Affectez les valeurs **Nouveau** et **Fenêtre** à la propriété `Text` de ces éléments.  
  
4.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, pointez sur **Ajouter**, puis sélectionnez **Ajouter un nouvel élément**.  
  
5.  Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Windows Form** \(dans [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]\) ou **Application Windows Forms \(.NET\)** \(dans [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) dans le volet **Modèles**.  Dans la zone **Nom**, nommez le formulaire Form2.  Cliquez sur le bouton **Ouvrir** pour ajouter le formulaire au projet.  
  
    > [!NOTE]
    >  Le formulaire MDI enfant que vous avez créé lors de cette étape est un Windows Form standard.  Il a donc une propriété <xref:System.Windows.Forms.Form.Opacity%2A>, ce qui vous permet de contrôler la transparence du formulaire.  Cependant, la propriété <xref:System.Windows.Forms.Form.Opacity%2A> a été conçue pour les fenêtres de niveau supérieur.  Ne l'utilisez pas avec des formulaires MDI enfants, car des problèmes de peinture peuvent survenir.  
  
     Ce formulaire sera le modèle pour vos formulaires MDI enfants.  
  
     Le **Concepteur Windows Forms** s'ouvre et affiche le formulaire Form2.  
  
6.  Faites glisser un contrôle **RichTextBox** de la **Boîte à outils** vers le formulaire.  
  
7.  Dans la fenêtre **Propriétés**, affectez la valeur **Haut, Gauche** à la propriété `Anchor` et la valeur **Remplissage** à la propriété `Dock`.  
  
     Ainsi, le contrôle <xref:System.Windows.Forms.RichTextBox> remplit complètement la zone de formulaire MDI enfant, même quand le formulaire est redimensionné.  
  
8.  Double\-cliquez sur l'élément de menu **Nouveau** pour créer un gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> pour lui.  
  
9. Insérez du code semblable au suivant pour créer un formulaire MDI enfant quand l'utilisateur clique sur l'élément de menu **Nouveau**.  
  
    > [!NOTE]
    >  Dans l'exemple suivant, le gestionnaire d'événements gère l'événement <xref:System.Windows.Forms.Control.Click> pour `MenuItem2`.  Sachez que, selon les spécificités de votre architecture d'application, votre élément de menu **Nouveau** peut ne pas être `MenuItem2`.  
  
    ```vb  
    Protected Sub MDIChildNew_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MenuItem2.Click  
       Dim NewMDIChild As New Form2()  
       'Set the Parent Form of the Child window.  
       NewMDIChild.MdiParent = Me  
       'Display the new form.  
       NewMDIChild.Show()  
    End Sub  
  
    ```  
  
    ```csharp  
    protected void MDIChildNew_Click(object sender, System.EventArgs e){  
       Form2 newMDIChild = new Form2();  
       // Set the Parent Form of the Child window.  
       newMDIChild.MdiParent = this;  
       // Display the new form.  
       newMDIChild.Show();  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void menuItem2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          Form2^ newMDIChild = gcnew Form2();  
          // Set the Parent Form of the Child window.  
          newMDIChild->MdiParent = this;  
          // Display the new form.  
          newMDIChild->Show();  
       }  
    ```  
  
     Dans [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)], ajoutez la directive `#include` suivante en haut de Form1.h :  
  
    ```cpp  
    #include "Form2.h"  
    ```  
  
10. Dans la liste déroulante en haut de la fenêtre **Propriétés**, sélectionnez la barre de menus qui correspond au MenuStrip **Fichier** et affectez le <xref:System.Windows.Forms.ToolStripMenuItem> de Fenêtre comme valeur de la propriété <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>.  
  
     Cela permettra au menu **Fenêtre** de tenir à jour une liste des fenêtres MDI enfants ouvertes avec une coche à côté de la fenêtre enfant active.  
  
11. Appuyez sur F5 pour exécuter l'application.  En sélectionnant **Nouveau** dans le menu **Fichier**, vous pouvez créer des formulaires MDI enfants dont la liste est tenue à jour dans l'élément de menu **Fenêtre**.  
  
    > [!NOTE]
    >  Quand un formulaire MDI enfant a un composant <xref:System.Windows.Forms.MainMenu> \(avec, généralement, une structure d'éléments de menu\) et qu'il est ouvert dans un formulaire MDI parent qui a un composant <xref:System.Windows.Forms.MainMenu> \(avec, généralement, une structure d'éléments de menu\), les éléments de menu fusionnent automatiquement si vous avez défini la propriété <xref:System.Windows.Forms.MenuItem.MergeType%2A> \(et, éventuellement, la propriété <xref:System.Windows.Forms.MenuItem.MergeOrder%2A>\).  Affectez la valeur <xref:System.Windows.Forms.MenuMerge> à la propriété <xref:System.Windows.Forms.MenuItem.MergeType%2A> des deux composants <xref:System.Windows.Forms.MainMenu> et à tous les éléments de menu du formulaire enfant.  Définissez aussi la propriété <xref:System.Windows.Forms.MenuItem.MergeOrder%2A> pour que les éléments de menu des deux menus apparaissent dans l'ordre souhaité.  De plus, sachez que quand vous fermez un formulaire MDI parent, chaque formulaire MDI enfant déclenche un événement <xref:System.Windows.Forms.Form.Closing> avant que l'événement <xref:System.Windows.Forms.Form.Closing> pour le parent MDI soit déclenché.  L'annulation de l'événement <xref:System.Windows.Forms.Form.Closing> d'un enfant MDI n'empêchera pas le déclenchement de l'événement <xref:System.Windows.Forms.Form.Closing> du MDI parent. Toutefois, l'argument <xref:System.ComponentModel.CancelEventArgs> pour l'événement <xref:System.Windows.Forms.Form.Closing> du MDI parent prendra la valeur `true`.  Vous pouvez forcer la fermeture du MDI parent et de tous les formulaires MDI enfants en affectant la valeur `false` à l'argument <xref:System.ComponentModel.CancelEventArgs>.  
  
## Voir aussi  
 [Applications d'interface multidocument \(MDI, Multiple Document Interface\)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)   
 [Comment : créer des formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)   
 [Comment : déterminer l'enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)   
 [Comment : envoyer des données à l'enfant MDI actif](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)   
 [Comment : réorganiser des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)