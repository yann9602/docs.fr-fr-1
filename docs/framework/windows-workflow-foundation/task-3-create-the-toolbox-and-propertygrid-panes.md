---
title: "T&#226;che 3&#160;: cr&#233;er les volets de PropertyGrid et bo&#238;te &#224; outils | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# T&#226;che 3&#160;: cr&#233;er les volets de PropertyGrid et bo&#238;te &#224; outils
Dans cette tâche, vous allez créer les volets **Boîte à outils** et **PropertyGrid** et les ajouter au [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] réhébergé.  
  
 Pour référence, le code qui doit se trouver dans le fichier MainWindow.xaml.cs une fois terminée l'exécution des trois tâches de la série de rubriques [Réhébergement du Workflow Designer](../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md) est fourni à la fin de cette rubrique.  
  
### Pour créer la boîte à outils et l'ajouter à la grille  
  
1.  Ouvrez le projet HostingApplication que vous avez obtenu en suivant la procédure décrite dans [Tâche 2 : héberger le Workflow Designer](../../../docs/framework/windows-workflow-foundation//task-2-host-the-workflow-designer.md).  
  
2.  Dans le volet **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier MainWindow.xam et sélectionnez **Afficher le code**.  
  
3.  Ajoutez à la classe `MainWindow` une méthode `GetToolboxControl` qui crée un <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, ajoute une nouvelle catégorie **Boîte à outils** à la **Boîte à outils**, et affecte les types d'activité <xref:System.Activities.Statements.Assign> et <xref:System.Activities.Statements.Sequence> à cette catégorie.  
  
    ```csharp  
  
    private ToolboxControl GetToolboxControl()  
    {  
        // Create the ToolBoxControl.  
        ToolboxControl ctrl = new ToolboxControl();  
  
        // Create a category.  
        ToolboxCategory category = new ToolboxCategory("category1");  
  
        // Create Toolbox items.  
        ToolboxItemWrapper tool1 =   
            new ToolboxItemWrapper("System.Activities.Statements.Assign",   
            typeof(Assign).Assembly.FullName, null, "Assign");  
  
        ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",   
            typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
        // Add the Toolbox items to the category.  
        category.Add(tool1);  
        category.Add(tool2);  
  
        // Add the category to the ToolBox control.  
        ctrl.Categories.Add(category);  
        return ctrl;  
    }  
  
    ```  
  
4.  Ajoutez à la classe `MainWindow` une méthode `AddToolbox` privée qui place la **Boîte à outils** dans la colonne de gauche de la grille.  
  
    ```csharp  
  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
  
    ```  
  
5.  Ajoutez un appel à la méthode `AddToolBox` dans le constructeur de classe `MainWindow()`, comme illustré dans le code suivant.  
  
    ```csharp  
  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
  
    ```  
  
6.  Appuyez sur F5 pour générer et exécuter votre solution.La **Boîte à outils** qui contient les activités <xref:System.Activities.Statements.Assign> et <xref:System.Activities.Statements.Sequence> doit être affichée.  
  
### Pour créer PropertyGrid  
  
1.  Dans le volet **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier MainWindow.xam et sélectionnez **Afficher le code**.  
  
2.  Ajoutez la méthode `AddPropertyInspector` à la classe `MainWindow` pour placer le volet **PropertyGrid** dans la colonne la plus à droite de la grille.  
  
    ```csharp  
  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
  
    ```  
  
3.  Ajoutez un appel à la méthode `AddPropertyInspector` dans le constructeur de classe `MainWindow()`, comme illustré dans le code suivant.  
  
    ```csharp  
  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
        this.AddToolBox();  
  
        this.AddPropertyInspector();   
    }  
  
    ```  
  
4.  Pour générer et exécuter la solution, appuyez sur F5.La **Boîte à outils**, la zone de conception de workflow et les volets **PropertyGrid** doivent tous être affichés, et lorsque vous faites glisser une activité <xref:System.Activities.Statements.Assign> ou une activité <xref:System.Activities.Statements.Sequence> sur la zone de conception, la grille des propriétés doit être mise à jour en fonction de l'activité en surbrillance.  
  
## Exemple  
 Le fichier MainWindow.xaml.cs doit maintenant contenir le code suivant.  
  
```  
  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
//dlls added  
using System.Activities;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation;  
using System.Activities.Presentation.Metadata;  
using System.Activities.Presentation.Toolbox;  
using System.Activities.Statements;  
using System.ComponentModel;  
  
namespace HostingApplication  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
        private WorkflowDesigner wd;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
            RegisterMetadata();  
            AddDesigner();  
            this.AddToolBox();  
            this.AddPropertyInspector();  
        }  
  
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
  
        private void RegisterMetadata()  
        {  
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        private ToolboxControl GetToolboxControl()  
        {  
            // Create the ToolBoxControl.  
            ToolboxControl ctrl = new ToolboxControl();  
  
            // Create a category.  
            ToolboxCategory category = new ToolboxCategory("category1");  
  
            // Create Toolbox items.  
            ToolboxItemWrapper tool1 =  
                new ToolboxItemWrapper("System.Activities.Statements.Assign",  
                typeof(Assign).Assembly.FullName, null, "Assign");  
  
            ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",  
                typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
            // Add the Toolbox items to the category.  
            category.Add(tool1);  
            category.Add(tool2);  
  
            // Add the category to the ToolBox control.  
            ctrl.Categories.Add(category);  
            return ctrl;  
        }  
  
        private void AddToolBox()  
        {  
            ToolboxControl tc = GetToolboxControl();  
            Grid.SetColumn(tc, 0);  
            grid1.Children.Add(tc);  
        }  
  
        private void AddPropertyInspector()  
        {  
            Grid.SetColumn(wd.PropertyInspectorView, 2);  
            grid1.Children.Add(wd.PropertyInspectorView);  
        }  
  
    }  
}  
  
```  
  
## Voir aussi  
 [Réhébergement du Workflow Designer](../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md)   
 [Tâche 1 : créer une nouvelle application Windows Presentation Foundation.](../../../docs/framework/windows-workflow-foundation//task-1-create-a-new-wpf-app.md)   
 [Tâche 2 : héberger le Workflow Designer](../../../docs/framework/windows-workflow-foundation//task-2-host-the-workflow-designer.md)