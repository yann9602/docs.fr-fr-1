---
title: "Proc&#233;dure&#160;: cr&#233;er un concepteur d&#39;activit&#233;s personnalis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
caps.latest.revision: 25
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 25
---
# Proc&#233;dure&#160;: cr&#233;er un concepteur d&#39;activit&#233;s personnalis&#233;es
Les concepteurs d'activités personnalisées sont généralement implémentés de telle sorte que les activités qui leur sont associées soient composables avec d'autres activités dont les concepteurs peuvent être déposés dans l'aire de conception avec eux.Ces fonctionnalités requièrent qu'un concepteur d'activités personnalisées fournisse une « zone de dépôt » où une activité arbitraire peut être placée, ainsi que le moyen de gérer la collection d'éléments résultante sur l'aire de conception.Cette rubrique décrit comment créer un concepteur d'activités personnalisées qui contient une telle zone de dépôt et comment créer un concepteur d'activités personnalisées qui fournit cette fonctionnalité d'édition requise pour gérer la collection d'éléments de concepteur.  
  
 Les concepteurs d'activités personnalisées héritent généralement d'<xref:System.Activities.Presentation.ActivityDesigner>, qui est le type du concepteur d'activités de base par défaut pour toutes activités sans concepteur particulier.Ce type fournit l'expérience au moment du design tirée de l'interaction avec la grille des propriétés et de la configuration des aspects de base comme la gestion des couleurs et des icônes.  
  
 Pour faciliter le développement de concepteurs d'activités personnalisées, <xref:System.Activities.Presentation.ActivityDesigner> utilise deux contrôles d'assistance, <xref:System.Activities.Presentation.WorkflowItemPresenter> et <xref:System.Activities.Presentation.WorkflowItemsPresenter>.Ceux\-ci gèrent les fonctionnalités communes telles que le glisser\-déplacer, la suppression, la sélection et l'ajout d'éléments enfants.<xref:System.Activities.Presentation.WorkflowItemPresenter> autorise un seul  élément d'interface utilisateur enfant utilisateur en son sein, contenant la « zone de dépôt », tandis que <xref:System.Activities.Presentation.WorkflowItemsPresenter> peut assurer la prise en charge de plusieurs éléments d'interface utilisateur, notamment des fonctionnalités supplémentaires telles que le classement, le déplacement, la suppression et l'ajout d'éléments enfants.  
  
 L'autre aspect essentiel qu'il faut mettre en évidence dans l'implémentation d'un concepteur d'activités personnalisées concerne la façon dont les modifications sur place sont liées à l'aide de la liaison de données [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] à l'instance stockée en mémoire de ce que nous modifions dans le concepteur.Cette tâche est effectuée par l'arborescence des éléments de modèles, qui est également chargée de l'activation de la notification de modification et du suivi d'événements tels que les modifications d'états.  
  
 Cette rubrique présente deux procédures.  
  
1.  La première procédure décrit comment créer un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemPresenter> qui fournit la zone de dépôt qui reçoit d'autres activités.Cette procédure repose sur l'exemple [Concepteurs composites personnalisés \- Présentateur d'éléments de workflow](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md).  
  
2.  La deuxième procédure décrit comment créer un concepteur d'activités personnalisées avec un <xref:System.Activities.Presentation.WorkflowItemsPresenter> qui fournit les fonctionnalités requises pour modifier d'une collection d'éléments contenus.Cette procédure repose sur l'exemple [Concepteurs composites personnalisés \- Présentateur d'éléments de workflow](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md).  
  
### Pour créer un concepteur d'activités personnalisées avec une zone de dépôt à l'aide de WorkflowItemPresenter  
  
1.  Lancez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans le volet **Modèles installés**, sélectionnez **Fenêtres** dans votre catégorie de langage par défaut.  
  
4.  Dans le volet **Modèles**, sélectionnez **Application WPF**.  
  
5.  Dans la zone **Nom**, entrez `UsingWorkflowItemPresenter`.  
  
6.  Dans la zone **Emplacement**, entrez le répertoire dans lequel vous désirez enregistrer votre projet ou bien cliquez sur **Parcourir** pour naviguer jusqu'à celui\-ci.  
  
7.  Dans la zone **Solution**, acceptez la valeur par défaut.  
  
8.  Cliquez sur **OK**.  
  
9. Cliquez avec le bouton droit sur le fichier MainWindows.xaml dans l'**Explorateur de solutions**, sélectionnez **Supprimer**, puis confirmez en cliquant sur **OK** dans la boîte de dialogue **Microsoft Visual Studio**.  
  
10. Cliquez avec le bouton droit sur le projet UsingWorkflowItemPresenter dans l'**Explorateur de solutions**, sélectionnez **Ajouter**, puis **Nouvel élément...** pour afficher la boîte de dialogue **Ajouter un nouvel élément**, et sélectionnez la catégorie **WPF** dans la section **Modèles installés** située à gauche.  
  
11. Sélectionnez le modèle **Fenêtre \(WPF\)**, nommez\-le `RehostingWFDesigner`, puis cliquez sur **Ajouter**.  
  
12. Ouvrez le fichier RehostingWFDesigner.xaml et collez le code suivant dedans pour définir l'interface utilisateur de l'application.  
  
    ```  
  
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
            xmlns:sys="clr-namespace:System;assembly=mscorlib"  
            Title="Window1" Height="600" Width="900">  
        <Window.Resources>  
            <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
        </Window.Resources>  
        <Grid>  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="2*"/>  
                <ColumnDefinition Width="7*"/>  
                <ColumnDefinition Width="3*"/>  
            </Grid.ColumnDefinitions>  
            <Border Grid.Column="0">  
                <sapt:ToolboxControl Name="Toolbox">  
                    <sapt:ToolboxCategory CategoryName="Basic">  
                        <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.Sequence  
                            </sapt:ToolboxItemWrapper.ToolName>  
                           </sapt:ToolboxItemWrapper>  
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.WriteLine  
                            </sapt:ToolboxItemWrapper.ToolName>  
  
                        </sapt:ToolboxItemWrapper>  
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.If  
                            </sapt:ToolboxItemWrapper.ToolName>  
  
                        </sapt:ToolboxItemWrapper>  
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.While  
                            </sapt:ToolboxItemWrapper.ToolName>  
  
                        </sapt:ToolboxItemWrapper>  
                    </sapt:ToolboxCategory>  
                </sapt:ToolboxControl>  
            </Border>  
            <Border Grid.Column="1" Name="DesignerBorder"/>  
            <Border Grid.Column="2" Name="PropertyBorder"/>  
        </Grid>  
    </Window>  
  
    ```  
  
13. Pour associer un concepteur d'activités à un type d'activité, vous devez enregistrer ce concepteur auprès du magasin des métadonnées.Pour ce faire, ajoutez la méthode `RegisterMetadata` à la classe `RehostingWFDesigner`.Dans l'étendue de la méthode `RegisterMetadata`, créez un objet <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> et appelez la méthode <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> pour lui ajouter les attributs.Appelez la méthode <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> pour ajouter l'objet <xref:System.Activities.Presentation.Metadata.AttributeTable> au magasin des métadonnées.Le code suivant contient la logique de réhébergement pour le concepteur.Il enregistre les métadonnées, place `SimpleNativeActivity` dans la boîte à outils, puis crée le workflow.Mettez le code suivant dans le fichier RehostingWFDesigner.xaml.cs.  
  
    ```  
  
    using System;  
    using System.Activities.Core.Presentation;  
    using System.Activities.Presentation;  
    using System.Activities.Presentation.Metadata;  
    using System.Activities.Presentation.Toolbox;  
    using System.Activities.Statements;  
    using System.ComponentModel;  
    using System.Windows;  
  
    namespace UsingWorkflowItemPresenter  
    {  
        // Interaction logic for RehostingWFDesigner.xaml  
        public partial class RehostingWFDesigner  
        {  
            public RehostingWFDesigner()  
            {  
                InitializeComponent();  
            }  
  
            protected override void OnInitialized(EventArgs e)  
            {  
                base.OnInitialized(e);  
                // register metadata  
                (new DesignerMetadata()).Register();  
                RegisterCustomMetadata();  
                // add custom activity to toolbox  
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));  
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));  
  
                // create the workflow designer  
                WorkflowDesigner wd = new WorkflowDesigner();  
                wd.Load(new Sequence());  
                DesignerBorder.Child = wd.View;  
                PropertyBorder.Child = wd.PropertyInspectorView;  
  
            }  
  
            void RegisterCustomMetadata()  
            {  
                AttributeTableBuilder builder = new AttributeTableBuilder();  
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));  
                MetadataStore.AddAttributeTable(builder.CreateTable());  
            }  
        }  
    }  
  
    ```  
  
14. Cliquez avec le bouton droit sur le répertoire References dans l'Explorateur de solutions, puis sélectionnez **Ajouter une référence** pour afficher la boîte de dialogue **Ajouter une référence**.  
  
15. Cliquez sur l'onglet **.NET**, recherchez l'assembly nommé **System.Activities.Core.Presentation**, sélectionnez\-le, puis cliquez sur **OK**.  
  
16. En utilisant la même procédure, ajoutez des références aux assemblys suivants :  
  
    1.  System.Data.DataSetExtensions.dll  
  
    2.  System.Activities.Presentation.dll  
  
    3.  System.ServiceModel.Activities.dll  
  
17. Ouvrez le fichier App.xaml et remplacez la valeur de StartUpUri par "RehostingWFDesigner.xaml".  
  
18. Cliquez avec le bouton droit sur le projet UsingWorkflowItemPresenter dans l'**Explorateur de solutions**, sélectionnez **Ajouter**, puis **Nouvel élément...** pour afficher la boîte de dialogue **Ajouter un nouvel élément**, et sélectionnez la catégorie **Workflow** dans la section **Modèles installés** située à gauche.  
  
19. Sélectionnez le modèle **ActivityDesigner**, nommez\-le `SimpleNativeDesigner`, puis cliquez sur **Ajouter**.  
  
20. Ouvrez le fichier SimpleNativeDesigner.xaml et collez le code suivant dedans.Notez que ce code utilise <xref:System.Activities.Presentation.ActivityDesigner> comme élément racine et montre comment la liaison est utilisée pour intégrer <xref:System.Activities.Presentation.WorkflowItemPresenter> à votre concepteur afin qu'un type enfant puisse être affiché dans votre concepteur d'activités composites.  
  
    > [!NOTE]
    >  Le schéma de l'objet <xref:System.Activities.Presentation.ActivityDesigner> permet l'ajout d'un seul élément enfant à la définition de votre concepteur d'activités personnalisées. Toutefois, cet élément peut être un `StackPanel`, un `Grid` ou tout autre élément d'interface utilisateur composite.  
  
    ```  
  
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"  
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
  
21. Cliquez avec le bouton droit sur le projet UsingWorkflowItemPresenter dans l'**Explorateur de solutions**, sélectionnez **Ajouter**, puis **Nouvel élément...** pour afficher la boîte de dialogue **Ajouter un nouvel élément**, et sélectionnez la catégorie **Workflow** dans la section **Modèles installés** située à gauche.  
  
22. Sélectionnez le modèle **Activité de code**, nommez\-le `SimpleNativeActivity`, puis cliquez sur **Ajouter**.  
  
23. Implémentez la classe `SimpleNativeActivity` en entrant le code suivant dans le fichier SimpleNativeActivity.cs.  
  
    ```  
  
    using System.Activities;  
  
    namespace UsingWorkflowItemPresenter  
    {  
        public sealed class SimpleNativeActivity : NativeActivity  
        {  
            // this property contains an activity that will be scheduled in the execute method  
    // the WorkflowItemPresenter in the designer is bound to this to enable editing  
    // of the value  
            public Activity Body { get; set; }  
  
            protected override void CacheMetadata(NativeActivityMetadata metadata)  
            {  
               metadata.AddChild(Body);  
               base.CacheMetadata(metadata);  
  
            }  
  
            protected override void Execute(NativeActivityContext context)  
            {  
                context.ScheduleActivity(Body);  
            }  
        }  
    }  
  
    ```  
  
24. Dans le menu **Générer**, sélectionnez **Générer la solution**.  
  
25. Sélectionnez **Exécuter sans débogage** dans le menu **Déboguer** pour ouvrir la fenêtre de conception personnalisée réhébergée.  
  
### Pour créer un concepteur d'activités personnalisées à l'aide de WorkflowItemsPresenter  
  
1.  La procédure pour le deuxième concepteur d'activités personnalisées est parallèle à la première avec quelques changements, le premier étant de nommer la deuxième application `UsingWorkflowItemsPresenter`.De plus, cette application ne définit pas une nouvelle activité personnalisée.  
  
2.  Les fichiers CustomParallelDesigner.xaml et RehostingWFDesigner.xaml.cs comportent des différences fondamentales.Voici le code du fichier CustomParallelDesigne.xaml qui définit l'interface utilisateur.  
  
    ```  
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
        <sap:ActivityDesigner.Resources>  
            <DataTemplate x:Key="Collapsed">  
                <TextBlock>This is the Collapsed View</TextBlock>  
            </DataTemplate>  
            <DataTemplate x:Key="Expanded">  
                <StackPanel>  
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>  
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>  
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"  
                                        Items="{Binding Path=ModelItem.Branches}">  
                        <sap:WorkflowItemsPresenter.SpacerTemplate>  
                            <DataTemplate>  
                                <Ellipse Width="10" Height="10" Fill="Black"/>  
                            </DataTemplate>  
                        </sap:WorkflowItemsPresenter.SpacerTemplate>  
                        <sap:WorkflowItemsPresenter.ItemsPanel>  
                            <ItemsPanelTemplate>  
                                <StackPanel Orientation="Horizontal"/>  
                            </ItemsPanelTemplate>  
                        </sap:WorkflowItemsPresenter.ItemsPanel>  
                    </sap:WorkflowItemsPresenter>  
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
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>  
        </Grid>  
    </sap:ActivityDesigner>  
  
    ```  
  
3.  Voici le code du fichier RehostingWFDesigner.xaml.cs qui fournit la logique de réhébergement.  
  
    ```  
  
    using System;  
    using System.Activities.Core.Presentation;  
    using System.Activities.Presentation;  
    using System.Activities.Presentation.Metadata;  
    using System.Activities.Statements;  
    using System.ComponentModel;  
    using System.Windows;  
  
    namespaceUsingWorkflowItemsPresenter  
    {  
        public partial class RehostingWfDesigner : Window  
        {  
            public RehostingWfDesigner()  
            {  
                InitializeComponent();  
            }  
  
            protected override void OnInitialized(EventArgs e)  
            {  
                base.OnInitialized(e);  
                // register metadata  
                (new DesignerMetadata()).Register();  
                RegisterCustomMetadata();  
  
                // create the workflow designer  
                WorkflowDesigner wd = new WorkflowDesigner();  
                wd.Load(new Sequence());  
                DesignerBorder.Child = wd.View;  
                PropertyBorder.Child = wd.PropertyInspectorView;  
  
            }  
  
            void RegisterCustomMetadata()  
            {  
                AttributeTableBuilder builder = new AttributeTableBuilder();  
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));  
                MetadataStore.AddAttributeTable(builder.CreateTable());  
            }  
        }  
    }  
    ```  
  
## Voir aussi  
 <xref:System.Activities.Presentation.ActivityDesigner>   
 <xref:System.Activities.Presentation.WorkflowItemPresenter>   
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>   
 <xref:System.Activities.Presentation.WorkflowViewElement>   
 <xref:System.Activities.Presentation.Model.ModelItem>   
 [Personnalisation de l'expérience de conception de workflow](../../../docs/framework/windows-workflow-foundation//customizing-the-workflow-design-experience.md)