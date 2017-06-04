---
title: "Comment&#160;: ajouter des boutons Charger, Enregistrer et Annuler au contr&#244;le BindingNavigator Windows Forms | Microsoft Docs"
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
  - "contrôles (Windows Forms), manipulation"
  - "BindingNavigator (contrôle Windows Forms), ajout de boutons"
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: ajouter des boutons Charger, Enregistrer et Annuler au contr&#244;le BindingNavigator Windows Forms
Le contrôle <xref:System.Windows.Forms.BindingNavigator> est un contrôle <xref:System.Windows.Forms.ToolStrip> spécial destiné à la navigation et à la manipulation des contrôles de votre formulaire qui sont liés aux données.  
  
 Dans la mesure où il s'agit d'un contrôle <xref:System.Windows.Forms.ToolStrip>, le composant <xref:System.Windows.Forms.BindingNavigator> peut être modifié facilement pour inclure des commandes supplémentaires ou alternatives pour l'utilisateur.  
  
 Dans la procédure suivante, un contrôle <xref:System.Windows.Forms.TextBox> est lié aux données, et le contrôle <xref:System.Windows.Forms.ToolStrip> jouté au formulaire est modifié pour intégrer des boutons de chargement, d'enregistrement et d'annulation.  
  
### Pour ajouter des boutons de chargement, d'enregistrement et d'annulation au composant BindingNavigator  
  
1.  Ajoutez un contrôle <xref:System.Windows.Forms.TextBox> à votre formulaire.  
  
2.  Liez\-le à un <xref:System.Windows.Forms.BindingSource>, qui est lié à une source de données.  Pour cet exemple, le <xref:System.Windows.Forms.BindingSource> est lié à une base de données.  
  
3.  Après la génération du groupe de données et de l'adaptateur de table, faites glisser un contrôle <xref:System.Windows.Forms.BindingNavigator> jusqu'au formulaire.  
  
4.  Attribuez à la propriété <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> du contrôle <xref:System.Windows.Forms.BindingNavigator> la valeur <xref:System.Windows.Forms.BindingSource> sur le formulaire qui est lié aux contrôles.  
  
5.  Sélectionnez le contrôle <xref:System.Windows.Forms.BindingNavigator>.  
  
6.  Cliquez sur le glyphe de balise active \(![Glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) afin que la boîte de dialogue **Tâches BindingNavigator** apparaisse, puis sélectionnez **Modifier les éléments**.  
  
     Vous voyez s'afficher l'**éditeur de collections Items**.  
  
7.  Dans l'**éditeur de collections Items**, tapez le texte suivant :  
  
    1.  Ajoutez un <xref:System.Windows.Forms.ToolStripSeparator> et trois éléments <xref:System.Windows.Forms.ToolStripButton> en sélectionnant le type approprié de <xref:System.Windows.Forms.ToolStripItem> et cliquant sur le bouton **Ajouter**.  
  
    2.  Attribuez à la propriété <xref:System.Windows.Forms.ToolStripItem.Name%2A> des boutons les valeurs  `` LoadButton,  `` SaveButton et   `` CancelButton, respectivement.  
  
    3.  Attribuez à la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> des boutons les valeurs  `` Load \(charger\)`,` Save \(enregistrer\) et  `` Cancel \(annuler\).  
  
    4.  Attribuez à la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> de chacun des boutons la valeur  `` Text \(texte\).  Vous pouvez également attribuer à cette propriété la valeur  `` Image ``  ou  `` ImageAndText ``  et définir l'image à afficher dans la propriété <xref:System.Windows.Forms.ToolStripItem.Image%2A>.  
  
    5.  Cliquez sur **OK** pour fermer la boîte de dialogue. Les boutons sont ajoutés au <xref:System.Windows.Forms.ToolStrip>.  
  
8.  Cliquez avec le bouton droit sur le formulaire et choisissez **Afficher le code**.  
  
9. Dans l'éditeur de code, recherchez la ligne de code qui charge des données dans l'adaptateur de table.  Ce code a été généré lorsque vous installez la liaison de données à l'étape 2.  Le code doit se présenter comme suit : `TableAdapterName.Fill(DataSetName.TableName)`.  Il figurera très probablement dans l'événement <xref:System.Windows.Forms.Form.Load> du formulaire.  
  
10. Créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.ToolStripItem.Click>Load ``  `` <xref:System.Windows.Forms.ToolStripButton> que vous avez créé précédemment et déplacez\-y ce code de chargement de données.  
  
     Votre code doit ressembler au suivant :  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
     \[C\#\]  
  
    ```  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. Créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.ToolStripItem.Click>**Enregistrer** `` <xref:System.Windows.Forms.ToolStripButton> que vous avez créé précédemment et écrivez le code pour mettre à jour les données dans la table à laquelle le contrôle est lié.  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
     \[C\#\]  
  
    ```  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    >  Dans certains cas, le composant <xref:System.Windows.Forms.BindingNavigator> aura déjà un bouton  `` **Enregistrer**, mais aucun code n'aura été généré par le Concepteur Windows Forms.  Dans ce cas, vous pouvez placer le code précédent dans le gestionnaire d'événements <xref:System.Windows.Forms.ToolStripItem.Click> de ce bouton, au lieu de créer un bouton entièrement nouveau sur le <xref:System.Windows.Forms.ToolStrip>.  Toutefois, le bouton étant désactivé par défaut, vous devez attribuer à la propriété <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> du bouton la valeur `true` pour que le bouton fonctionne correctement.  
  
12. Créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.ToolStripItem.Click>Annuler ``  `` <xref:System.Windows.Forms.ToolStripButton> que vous avez créé précédemment et écrivez le code pour annuler toutes les modifications apportées à l'enregistrement des données qui est affiché.  
  
     \[Visual Basic\]  
  
    ```  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
     \[C\#\]  
  
    ```  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  La méthode <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> à une portée qui couvre la ligne de données.  Enregistrez toutes les modifications que vous apportez en consultant cet enregistrement individuel avant de naviguer jusqu'à l'enregistrement suivant.  
  
## Voir aussi  
 <xref:System.Windows.Forms.BindingNavigator>   
 <xref:System.Windows.Forms.BindingSource>   
 <xref:System.Windows.Forms.ToolStrip>   
 [BindingNavigator, contrôle](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)   
 [Vue d'ensemble du composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)