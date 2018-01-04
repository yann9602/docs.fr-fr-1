---
title: "Comment : ajouter des boutons Charger, Enregistrer et Annuler au contrôle BindingNavigator Windows Forms"
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
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dd45b33fb1f99c280e126b9e601692a85da5dba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>Comment : ajouter des boutons Charger, Enregistrer et Annuler au contrôle BindingNavigator Windows Forms
Le <xref:System.Windows.Forms.BindingNavigator> contrôle est à usage spécial <xref:System.Windows.Forms.ToolStrip> contrôle qui est destiné à la navigation et la manipulation de contrôles liés aux données sur votre formulaire.  
  
 Car il s’agit d’un <xref:System.Windows.Forms.ToolStrip> (contrôle), le <xref:System.Windows.Forms.BindingNavigator> composant peut facilement être modifié pour inclure des commandes supplémentaires ou alternatives pour l’utilisateur.  
  
 Dans la procédure suivante, un <xref:System.Windows.Forms.TextBox> contrôle est lié aux données et le <xref:System.Windows.Forms.ToolStrip> contrôle qui est ajouté au formulaire est modifiée pour inclure charger, enregistrer et annuler des boutons.  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>Pour ajouter une charge, enregistrer et annuler des boutons pour le composant de BindingNavigator  
  
1.  Ajoutez un contrôle <xref:System.Windows.Forms.TextBox> à votre formulaire.  
  
2.  Lier à un <xref:System.Windows.Forms.BindingSource>, qui est lié à une source de données. Pour cet exemple, le <xref:System.Windows.Forms.BindingSource> est lié à une base de données.  
  
3.  Une fois que l’adaptateur de jeu de données et de table sont générées, faites glisser un <xref:System.Windows.Forms.BindingNavigator> contrôle au formulaire.  
  
4.  Définir le <xref:System.Windows.Forms.BindingNavigator> du contrôle <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> propriété le <xref:System.Windows.Forms.BindingSource> sur le formulaire qui est lié aux contrôles.  
  
5.  Sélectionnez le contrôle <xref:System.Windows.Forms.BindingNavigator>.  
  
6.  Cliquez sur le glyphe de balise active (![glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) afin que la **tâches BindingNavigator** boîte de dialogue s’affiche et sélectionnez **modifier les éléments**.  
  
     Le **éditeur de collections Items** s’affiche.  
  
7.  Dans le **éditeur de collections Items**, procédez comme suit :  
  
    1.  Ajouter un <xref:System.Windows.Forms.ToolStripSeparator> et trois <xref:System.Windows.Forms.ToolStripButton> éléments en sélectionnant le type approprié de <xref:System.Windows.Forms.ToolStripItem> et en cliquant sur le **ajouter** bouton.  
  
    2.  Définir le <xref:System.Windows.Forms.ToolStripItem.Name%2A> propriété des boutons pour**LoadButton**,**SaveButton**, et**CancelButton**, respectivement.  
  
    3.  Définir le <xref:System.Windows.Forms.ToolStripItem.Text%2A> propriété des boutons pour**charge** `,` **enregistrer**, et**Annuler**.  
  
    4.  Définir le <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriété pour chacun des boutons pour**texte**. Vous pouvez également définir cette propriété**Image**ou**ImageAndText**et définir l’image à afficher dans le <xref:System.Windows.Forms.ToolStripItem.Image%2A> propriété.  
  
    5.  Cliquez sur **OK** pour fermer la boîte de dialogue. Les boutons sont ajoutés à la <xref:System.Windows.Forms.ToolStrip>.  
  
8.  Avec le bouton droit de la forme et choisissez **afficher le Code**.  
  
9. Dans l’éditeur de Code, recherchez la ligne de code qui charge des données dans l’adaptateur de table. Ce code a été généré lorsque vous configurez la liaison de données à l’étape 2. Le code doit être semblable au suivant : `TableAdapterName.Fill(DataSetName.TableName)`. Il figurera très probablement être sous la forme <xref:System.Windows.Forms.Form.Load> événements.  
  
10. Créer un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> l’événement de la**charge** <xref:System.Windows.Forms.ToolStripButton> créé précédemment et de placer ce code de chargement de données.  
  
     Votre code doit à présent ressembler à ce qui suit :  
  
    ```vb  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. Créer un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> l’événement de la **enregistrer** <xref:System.Windows.Forms.ToolStripButton> vous avez créé précédemment et d’écrire du code pour mettre à jour les données dans la table, le contrôle est lié à.  
  
    ```vb  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    >  Dans certains cas, le <xref:System.Windows.Forms.BindingNavigator> composant a déjà un**enregistrer** bouton, mais aucun code n’aura été généré par le Concepteur Windows Forms. Dans ce cas, vous pouvez placer le code précédent dans le <xref:System.Windows.Forms.ToolStripItem.Click> Gestionnaire d’événements pour ce bouton, au lieu de créer un nouveau bouton sur le <xref:System.Windows.Forms.ToolStrip>. Toutefois, le bouton est désactivé par défaut, vous devez donc définir la <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> propriété du bouton `true` pour que le bouton fonctionne correctement.  
  
12. Créer un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> l’événement de la**Annuler** <xref:System.Windows.Forms.ToolStripButton> créé précédemment et d’écrire du code pour annuler toute modification apportée à l’enregistrement de données qui s’affiche.  
  
    ```vb  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
    ```csharp  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  Le <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> (méthode) est limitée à la ligne de données. Enregistrez les modifications apportées lors de l’affichage de cet enregistrement individuel avant de naviguer jusqu'à l’enregistrement suivant.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.ToolStrip>  
 [BindingNavigator, contrôle](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Vue d'ensemble du composant BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
