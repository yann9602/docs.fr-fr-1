---
title: "Tâche 3 : créer les volets de PropertyGrid et boîte à outils"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90083692c2415ed6c1117185474d6bbaa9d1963b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Tâche 3 : créer les volets de PropertyGrid et boîte à outils
Dans cette tâche, vous allez créer le **boîte à outils** et **PropertyGrid** volets et les ajouter à réhébergé [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 Pour référence, le code qui doit être dans le fichier MainWindow.xaml.cs après avoir effectué les trois tâches dans le [réhébergement du Concepteur de flux de travail](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) série de rubriques est fourni à la fin de cette rubrique.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Pour créer la boîte à outils et l'ajouter à la grille  
  
1.  Ouvrez le projet HostingApplication que vous avez obtenu en suivant la procédure décrite dans [tâche 2 : héberger le Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).  
  
2.  Dans le **l’Explorateur de solutions** volet, cliquez sur le fichier MainWindow.xaml et sélectionnez **afficher le Code**.  
  
3.  Ajouter un `GetToolboxControl` méthode à la `MainWindow` classe crée un <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, ajoute un nouveau **boîte à outils** catégorie à la **boîte à outils**et assigne le <xref:System.Activities.Statements.Assign> et <xref:System.Activities.Statements.Sequence> types d’activités à cette catégorie.  
  
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
  
4.  Ajouter une privée `AddToolbox` méthode à la `MainWindow` classe place le **boîte à outils** dans la colonne de gauche dans la grille.  
  
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
  
6.  Appuyez sur F5 pour générer et exécuter votre solution. Le **boîte à outils** contenant le <xref:System.Activities.Statements.Assign> et <xref:System.Activities.Statements.Sequence> activités doivent être affichées.  
  
### <a name="to-create-the-propertygrid"></a>Pour créer PropertyGrid  
  
1.  Dans le **l’Explorateur de solutions** volet, cliquez sur le fichier MainWindow.xaml et sélectionnez **afficher le Code**.  
  
2.  Ajouter le `AddPropertyInspector` méthode à la `MainWindow` classe pour placer le **PropertyGrid** volet dans la colonne la plus à droite sur la grille.  
  
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
  
4.  Pour générer et exécuter la solution, appuyez sur F5. Le **boîte à outils**, zone de conception de workflow et **PropertyGrid** volets doivent tous être affichés, et lorsque vous faites glisser un <xref:System.Activities.Statements.Assign> activité ou un <xref:System.Activities.Statements.Sequence> activité sur la zone de conception, le grille des propriétés doit mettre à jour en fonction de l’activité en surbrillance.  
  
## <a name="example"></a>Exemple  
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
  
## <a name="see-also"></a>Voir aussi  
 [Réhébergement du concepteur de flux de travail](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Tâche 1 : Créer une nouvelle application Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [Tâche 2 : Héberger le concepteur de flux de travail](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
