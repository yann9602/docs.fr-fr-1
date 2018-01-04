---
title: "Extensibilité de la grille des propriétés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e3069e97a1696b37d56728eb86161cc2487dfdfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="property-grid-extensibliity"></a>Extensibilité de la grille des propriétés
Un développeur peut personnaliser la grille des propriétés qui s'affiche lorsqu'une activité donnée est sélectionnée dans le concepteur. Cela permet de créer une expérience d'édition enrichie. Cet exemple montre comment effectuer cette opération.  
  
## <a name="demonstrates"></a>Démonstrations  
 Extensibilité de la grille des propriétés du concepteur de workflow.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`  
  
## <a name="discussion"></a>Discussion  
 Pour étendre la grille des propriétés, un développeur dispose d'options permettant de personnaliser l'apparence incluse d'un éditeur de grilles des propriétés ou de fournir une boîte de dialogue qui s'affiche pour offrir une surface d'édition plus avancée. Deux éditeurs différents sont présentés dans cet exemple : un éditeur Inline et un éditeur de boîtes de dialogue.  
  
## <a name="inline-editor"></a>Éditeur inline  
 L'exemple d'éditeur inline montre les points suivants :  
  
-   Il crée un type qui dérive de <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.  
  
-   Dans le constructeur, la valeur <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> est définie avec un modèle de données [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)]. Il peut être lié à un modèle XAML, mais dans cet exemple, le code est utilisé pour initialiser la liaison de données.  
  
-   Le modèle de données a un contexte de données du <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> de l'élément restitué dans la grille des propriétés. Notez, dans le code suivant (provenant de CustomInlineEditor.cs), que ce contexte crée ensuite une liaison avec la propriété `Value`.  
  
    ```csharp  
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));  
    FrameworkElementFactory slider = new FrameworkElementFactory(typeof(Slider));  
    Binding sliderBinding = new Binding("Value");  
    sliderBinding.Mode = BindingMode.TwoWay;  
    slider.SetValue(Slider.MinimumProperty, 0.0);  
    slider.SetValue(Slider.MaximumProperty, 100.0);  
    slider.SetValue(Slider.ValueProperty, sliderBinding);  
    stack.AppendChild(slider);  
    ```  
  
-   Étant donné que l'activité et le concepteur se trouvent dans le même assembly, l'inscription des attributs du concepteur d'activités s'effectue dans le constructeur statique de l'activité elle-même, comme le montre l'exemple suivant issu de SimpleCodeActivity.cs.  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="dialog-editor"></a>Éditeur de boîtes de dialogue  
 L'exemple d'éditeur de boîtes de dialogue montre les points suivants :  
  
1.  Il crée un type qui dérive de <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.  
  
2.  Il définit la valeur <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> dans le constructeur avec un modèle de données [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]. Cet élément peut être créé en XAML, mais dans cet exemple, il est créé dans le code.  
  
3.  Le modèle de données a un contexte de données du <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> de l'élément restitué dans la grille des propriétés. Dans le code suivant, ce contexte crée ensuite une liaison avec la propriété `Value`. Il est essentiel d'inclure également un <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> pour fournir le bouton qui affiche la boîte de dialogue dans FilePickerEditor.cs.  
  
    ```  
    this.InlineEditorTemplate = new DataTemplate();  
  
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));  
    stack.SetValue(StackPanel.OrientationProperty, Orientation.Horizontal);  
    FrameworkElementFactory label = new FrameworkElementFactory(typeof(Label));  
    Binding labelBinding = new Binding("Value");  
    label.SetValue(Label.ContentProperty, labelBinding);  
    label.SetValue(Label.MaxWidthProperty, 90.0);  
  
    stack.AppendChild(label);  
  
    FrameworkElementFactory editModeSwitch = new FrameworkElementFactory(typeof(EditModeSwitchButton));  
  
    editModeSwitch.SetValue(EditModeSwitchButton.TargetEditModeProperty, PropertyContainerEditMode.Dialog);  
  
    stack.AppendChild(editModeSwitch);  
  
    this.InlineEditorTemplate.VisualTree = stack;  
    ```  
  
4.  Remplace le <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` méthode dans le type concepteur pour gérer l’affichage de la boîte de dialogue. Dans cet exemple, un <xref:System.Windows.Forms.FileDialog> de base est présenté.  
  
    ```  
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)  
    {  
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();  
        if (ofd.ShowDialog() == true)  
        {  
            propertyValue.Value = ofd.FileName;  
        }  
    }  
    ```  
  
5.  Étant donné que l'activité et le concepteur se trouvent dans le même assembly, l'inscription des attributs du concepteur d'activités s'effectue dans le constructeur statique de l'activité elle-même, comme le montre l'exemple suivant issu de SimpleCodeActivity.cs.  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Générez la solution, puis ouvrez Workflow1.xaml.  
  
2.  Faites glisser un **SimpleCodeActivity** à partir de la boîte à outils vers la zone de conception.  
  
3.  Cliquez sur le **SimpleCodeActivity** et ouvrez la grille des propriétés dans lequel il existe un contrôle slider et un fichier de contrôle de sélection.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
