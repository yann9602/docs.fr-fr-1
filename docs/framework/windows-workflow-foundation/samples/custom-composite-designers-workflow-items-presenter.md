---
title: "Concepteurs composites personnalis&#233;s&#160;- Pr&#233;sentateur d&#39;&#233;l&#233;ments de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Concepteurs composites personnalis&#233;s&#160;- Pr&#233;sentateur d&#39;&#233;l&#233;ments de workflow
<xref:System.Activities.Design.WorkflowItemsPresenter> est un type de clé dans le modèle de programmation de concepteur WF qui permet la modification d'une collection d'éléments contenus.Cet exemple montre comment générer un concepteur d'activités qui expose une telle collection modifiable.  
  
 Cet exemple illustre les opérations suivantes :  
  
-   Création d'un concepteur d'activités personnalisées avec un <xref:System.Activities.Design.WorkflowItemsPresenter>.  
  
-   Création d'un concepteur d'activités avec une vue « réduite » et « développée ».  
  
-   Substitution d'un concepteur par défaut dans une application réhébergée.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez l'exemple de solution **UsingWorkflowItemsPresenter.sln** pour C\# ou pour VB dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Générez et exécutez la solution.Une application de concepteur de workflow réhébergée doit s'ouvrir, et vous pouvez faire glisser des activités sur la zone de dessin.  
  
## Points clés de l'exemple  
 Le code de cet exemple illustre les points suivants :  
  
-   L'activité pour laquelle un concepteur est conçu : `Parallel`  
  
-   La création d'un concepteur d'activités personnalisées avec un <xref:System.Activities.Design.WorkflowItemsPresenter>.Quelques points à noter :  
  
    -   Notez l'utilisation de la liaison de données WPF pour lier à `ModelItem.Branches`.`ModelItem` est la propriété sur <xref:System.Activities.Design.WorkflowElementDesigner> qui fait référence à l'objet sous\-jacent pour lequel le concepteur est utilisé, dans ce cas, `Parallel`.  
  
    -   <xref:System.Activities.Design.WorkflowItemsPresenter.SpacerTemplate%2A> peut être utilisé pour placer un visuel à afficher entre les éléments individuels de la collection.  
  
    -   <xref:System.Activities.Design.WorkflowItemsPresenter.ItemsPanel%2A> est un modèle qui peut être fourni pour déterminer la disposition des éléments dans la collection.Dans le cas présent, un panneau d'empilement horizontal est utilisé.  
  
 L'exemple de code suivant illustre ce point.  
  
```xaml  
<sad:WorkflowItemsPresenter HintText="Drop Activities Here"  
                              Items="{Binding Path=ModelItem.Branches}">  
    <sad:WorkflowItemsPresenter.SpacerTemplate>  
      <DataTemplate>  
        <Ellipse Width="10" Height="10" Fill="Black"/>  
      </DataTemplate>  
    </sad:WorkflowItemsPresenter.SpacerTemplate>  
    <sad:WorkflowItemsPresenter.ItemsPanel>  
      <ItemsPanelTemplate>  
        <StackPanel Orientation="Horizontal"/>  
      </ItemsPanelTemplate>  
    </sad:WorkflowItemsPresenter.ItemsPanel>  
  </sad:WorkflowItemsPresenter>  
  
```  
  
-   Effectuez une association de `DesignerAttribute` au type `Parallel`, puis fournissez en sortie les attributs signalés.  
  
    -   En premier lieu, enregistrez tous les concepteurs par défaut.  
  
 Voici l'exemple de code.  
  
```csharp  
// register metadata  
(new DesignerMetadata()).Register();  
RegisterCustomMetadata();  
  
```  
  
```vb  
' register metadata  
Dim metadata = New DesignerMetadata()  
metadata.Register()  
' register custom metadata  
RegisterCustomMetadata()  
  
```  
  
-   -   Ensuite, substituez la parallèle dans la méthode `RegisterCustomMetadata`.  
  
 Le code suivant illustre ce point en C\# et en Visual Basic.  
  
 C\#  
  
```csharp  
void RegisterCustomMetadata()  
{  
      AttributeTableBuilder builder = new AttributeTableBuilder();  
      builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));  
      MetadataStore.AddAttributeTable(builder.CreateTable());  
}  
  
```  
  
```vb  
Sub RegisterCustomMetadata()  
   Dim builder As New AttributeTableBuilder()  
   builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))  
   MetadataStore.AddAttributeTable(builder.CreateTable())  
End Sub  
  
```  
  
-   Enfin, notez l'utilisation de modèles de données et de déclencheurs différents pour sélectionner le modèle approprié en fonction de la propriété `IsRootDesigner`.  
  
 Voici l'exemple de code.  
  
```xaml  
<sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"  
    xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">  
  <sad:ActivityDesigner.Resources>  
    <DataTemplate x:Key="Expanded">  
      <StackPanel>  
        <TextBlock>This is the Expanded View</TextBlock>  
        <sad:WorkflowItemsPresenter HintText="Drop Activities Here"  
                                    Items="{Binding Path=ModelItem.Branches}">  
          <sad:WorkflowItemsPresenter.SpacerTemplate>  
            <DataTemplate>  
              <Ellipse Width="10" Height="10" Fill="Black"/>  
            </DataTemplate>  
          </sad:WorkflowItemsPresenter.SpacerTemplate>  
          <sad:WorkflowItemsPresenter.ItemsPanel>  
            <ItemsPanelTemplate>  
              <StackPanel Orientation="Horizontal"/>  
            </ItemsPanelTemplate>  
          </sad:WorkflowItemsPresenter.ItemsPanel>  
        </sad:WorkflowItemsPresenter>  
      </StackPanel>  
    </DataTemplate>  
    <DataTemplate x:Key="Collapsed">  
      <TextBlock>This is the Collapsed View</TextBlock>  
    </DataTemplate>  
    <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
      <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
      <Style.Triggers>  
        <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">  
          <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
        </DataTrigger>  
      </Style.Triggers>  
    </Style>  
  </sad: ActivityDesigner.Resources>  
  <Grid>  
    <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>  
  </Grid>  
</sad: ActivityDesigner>  
  
```  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## Voir aussi  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>   
 [Développement d'applications avec Workflow Designer](../Topic/Developing%20Applications%20with%20the%20Workflow%20Designer.md)