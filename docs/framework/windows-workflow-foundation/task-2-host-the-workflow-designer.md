---
title: "T&#226;che&#160;2&#160;: h&#233;berger le Workflow Designer | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# T&#226;che&#160;2&#160;: h&#233;berger le Workflow Designer
Cette rubrique décrit la procédure d'hébergement d'une instance du [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] dans une application [!INCLUDE[avalon1](../../../includes/avalon1-md.md)].  
  
 La procédure configure le contrôle **Grid** qui contient le concepteur, crée par programmation une instance du <xref:System.Activities.Presentation.WorkflowDesigner> qui contient une activité <xref:System.Activities.Statements.Sequence> par défaut, enregistre les métadonnées du concepteur pour fournir la prise en charge du concepteur pour toutes les activités intégrées, et héberge le [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] dans l'application [!INCLUDE[avalon2](../../../includes/avalon2-md.md)].  
  
### Pour héberger le concepteur de workflow  
  
1.  Ouvrez le projet HostingApplication que vous avez créé dans [Tâche 1 : créer une nouvelle application Windows Presentation Foundation.](../../../docs/framework/windows-workflow-foundation//task-1-create-a-new-wpf-app.md).  
  
2.  Pour faciliter l'utilisation du [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], ajustez la taille de la fenêtre.Pour ce faire, dans le concepteur, sélectionnez **MainWindow**, appuyez sur F4 pour afficher la fenêtre **Propriétés**, puis, dans la section **Disposition**, affectez la valeur 600 à la **Largeur** et la valeur 350 à la **Hauteur**.  
  
3.  Définissez le nom de la grille en sélectionnant le panneau **Grid** dans le concepteur \(cliquez sur la zone à l'intérieur de **MainWindow**\) et affectant la valeur « grid1 » à la propriété **Name** située en haut de la fenêtre **Propriétés**.  
  
4.  Pour ouvrir la boîte de dialogue **Éditeur de collection**, dans la fenêtre **Propriétés**, cliquez sur les points de suspension \(**…**\) situés en regard de la propriété `ColumnDefinitions`.  
  
5.  Pour insérer trois colonnes dans la disposition, dans la boîte de dialogue **Éditeur de collection**, cliquez sur le bouton **Ajouter**.La première colonne contiendra la **Boîte à outils**, la deuxième colonne hébergera le [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] et la troisième colonne sera utilisée pour l'inspecteur de propriétés.  
  
6.  Affectez la valeur 4\* à la propriété `Width` de la colonne centrale.  
  
7.  Pour enregistrer les modifications, cliquez sur **OK**.Le XAML suivant est ajouté à votre fichier MainWindow.xaml :  
  
    ```  
  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
  
    ```  
  
8.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur MainWindow.xaml et sélectionnez **Afficher le code**.Modifiez le code en procédant comme suit :  
  
    1.  Ajoutez les espaces de noms suivants :  
  
        ```csharp  
  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
  
        ```  
  
    2.  Pour déclarer un champ de membre privé devant contenir une instance de <xref:System.Activities.Presentation.WorkflowDesigner>, ajoutez le code suivant à la classe `MainWindow`.  
  
        ```csharp  
  
        public partial class MainWindow : Window  
        {  
            private WorkflowDesigner wd;  
  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
        }  
  
        ```  
  
    3.  Ajoutez la méthode `AddDesigner` suivante à la classe `MainWindow`.L'implémentation crée une instance de <xref:System.Activities.Presentation.WorkflowDesigner>, y ajoute une activité <xref:System.Activities.Statements.Sequence> et la place dans la colonne centrale de la **Grille** grid1.  
  
        ```csharp  
  
        private void AddDesigner()  
        {  
            //Create an instance of WorkflowDesigner class.  
            this.wd = new WorkflowDesigner();  
  
            //Place the designer canvas in the middle column of the grid.  
            Grid.SetColumn(this.wd.View, 1);  
  
            //Load a new Sequence as default.  
            this.wd.Load(new Sequence());  
  
            //Add the designer canvas to the grid.  
            grid1.Children.Add(this.wd.View);  
        }  
  
        ```  
  
    4.  Pour ajouter la prise en charge du concepteur pour toutes les activités intégrées, enregistrez les métadonnées du concepteur.Cela vous permet de déplacer des activités, de la boîte à outils vers l'activité <xref:System.Activities.Statements.Sequence> d'origine dans le [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].Pour ce faire, ajoutez la méthode `RegisterMetadata` à la classe `MainWindow`.  
  
        ```csharp  
  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        ```  
  
         [!INCLUDE[crabout](../../../includes/crabout-md.md)] l'enregistrement de concepteurs d'activités, consultez [Procédure : créer un concepteur d'activités personnalisées](../../../docs/framework/windows-workflow-foundation//how-to-create-a-custom-activity-designer.md).  
  
    5.  Dans le constructeur de classes `MainWindow`, ajoutez des appels aux méthodes précédemment déclarées pour enregistrer les métadonnées dans le but de la prise en charge du concepteur et pour créer l'objet <xref:System.Activities.Presentation.WorkflowDesigner>.  
  
        ```csharp  
        public MainWindow()  
        {  
            InitializeComponent();  
  
            // Register the metadata  
            RegisterMetadata();  
  
            // Add the WFF Designer  
            AddDesigner();  
        }  
  
        ```  
  
        > [!NOTE]
        >  La méthode `RegisterMetadata` enregistre les métadonnées du concepteur relatives aux activités intégrées, dont l'activité <xref:System.Activities.Statements.Sequence>.Étant donné que la méthode `AddDesigner` utilise l'activité <xref:System.Activities.Statements.Sequence>, la méthode `RegisterMetadata` doit être appelée en premier.  
  
9. Pour générer et exécuter la solution, appuyez sur F5.  
  
10. Pour savoir comment ajouter la prise en charge de la **boîte à outils** et de **PropertyGrid** à votre concepteur de workflow réhébergé, consultez [Tâche 3 : créer les volets de PropertyGrid et boîte à outils](../../../docs/framework/windows-workflow-foundation//task-3-create-the-toolbox-and-propertygrid-panes.md).  
  
## Voir aussi  
 [Réhébergement du Workflow Designer](../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md)   
 [Tâche 1 : créer une nouvelle application Windows Presentation Foundation.](../../../docs/framework/windows-workflow-foundation//task-1-create-a-new-wpf-app.md)   
 [Tâche 3 : créer les volets de PropertyGrid et boîte à outils](../../../docs/framework/windows-workflow-foundation//task-3-create-the-toolbox-and-propertygrid-panes.md)