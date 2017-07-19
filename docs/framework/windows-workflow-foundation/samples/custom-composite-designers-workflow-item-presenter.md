---
title: "Concepteurs composites personnalis&#233;s&#160;- Pr&#233;sentateur d&#39;&#233;l&#233;ments de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Concepteurs composites personnalis&#233;s&#160;- Pr&#233;sentateur d&#39;&#233;l&#233;ments de workflow
Le <xref:System.Activities.Presentation.WorkflowItemPresenter> est un type de clé dans le modèle de programmation de concepteur WF qui permet la création d'une « zone de dépôt » où une activité arbitraire peut être placée.Cet exemple montre comment générer un concepteur d'activités qui fait apparaître une telle « zone de dépôt ».  
  
 Cet exemple illustre les opérations suivantes :  
  
## Démonstrations  
  
-   Création d'un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemPresenter>.  
  
-   Inscription du concepteur personnalisé à l'aide du magasin des métadonnées.  
  
-   Programmation de la boîte à outils réhébergée de façon déclarative et impérative.  
  
## Détails de l'exemple  
 Le code de cet exemple illustre les points suivants :  
  
-   Le concepteur d'activités personnalisées est généré pour la classe `SimpleNativeActivity`.  
  
-   La création d'un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemPresenter>.  
  
```xaml  
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
    <sap:ActivityDesigner.Resources>  
        <DataTemplate x:Key="Collapsed">  
            <StackPanel>  
                <TextBlock>This is the collapsed view</TextBlock>  
            </StackPanel>  
        </DataTemplate>  
        <DataTemplate x:Key="Expanded">  
            <StackPanel>  
                <TextBlock>Custom Text</TextBlock>  
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"  
                                        HintText="Please drop an activity here" />  
            </StackPanel>  
        </DataTemplate>  
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">  
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>  
            <Style.Triggers>  
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">  
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>  
                </DataTrigger>  
            </Style.Triggers>  
        </Style>  
    </sap:ActivityDesigner.Resources>  
    <Grid>  
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />  
    </Grid>  
</sap:ActivityDesigner>  
```  
  
 Notez l'utilisation de la liaison de données WPF pour lier à `ModelItem.Body`.`ModelItem` est la propriété sur <xref:System.Activities.Presentation.WorkflowElementDesigner> qui fait référence à l'objet sous\-jacent pour lequel le concepteur est utilisé, dans ce cas, **SimpleNativeActivity**.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Ouvrez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Appuyez sur F5 pour compiler et exécuter l'application.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## Voir aussi  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>   
 [Développement d'applications avec Workflow Designer](../Topic/Developing%20Applications%20with%20the%20Workflow%20Designer.md)