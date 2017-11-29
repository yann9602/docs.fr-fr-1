---
title: "Utilisation d'un éditeur d'expressions personnalisé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0901b58b-e037-44a8-8281-f6f54361cfca
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dcf9970b2b4986c3948704d848c67d8a3c6f7d9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-a-custom-expression-editor"></a><span data-ttu-id="c00f0-102">Utilisation d'un éditeur d'expressions personnalisé</span><span class="sxs-lookup"><span data-stu-id="c00f0-102">Using a Custom Expression Editor</span></span>
<span data-ttu-id="c00f0-103">Un éditeur d'expressions personnalisé peut être implémenté pour fournir une expérience d'édition d'expressions plus riche ou plus simple.</span><span class="sxs-lookup"><span data-stu-id="c00f0-103">A custom expression editor can be implemented to provide a richer or simpler expression editing experience.</span></span> <span data-ttu-id="c00f0-104">Il existe plusieurs scénarios dans lesquels vous souhaiterez peut-être utiliser un éditeur d'expressions personnalisé :</span><span class="sxs-lookup"><span data-stu-id="c00f0-104">There are several scenarios in which you might want to use a custom expression editor:</span></span>  
  
-   <span data-ttu-id="c00f0-105">Pour assurer la prise en charge d'IntelliSense et d'autres fonctionnalités d'édition riches dans un concepteur de workflow réhébergé.</span><span class="sxs-lookup"><span data-stu-id="c00f0-105">To provide support for IntelliSense and other rich editing features in a rehosted workflow designer.</span></span> <span data-ttu-id="c00f0-106">Ces fonctionnalités doivent être fournies car l'éditeur d'expressions [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] par défaut ne peut pas être utilisé dans les applications réhébergées.</span><span class="sxs-lookup"><span data-stu-id="c00f0-106">This functionality must be provided because the default [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] expression editor cannot be used in rehosted applications.</span></span>  
  
-   <span data-ttu-id="c00f0-107">Pour simplifier l'édition d'expressions pour les utilisateurs analystes d'entreprise, afin qu'ils ne soient pas, par exemple, obligés de se familiariser avec [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] ou de traiter des expressions [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c00f0-107">To simplify the expression editing experience for the business analyst users, so that they are not, for example, required to learn [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or deal with [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] expressions.</span></span>  
  
 <span data-ttu-id="c00f0-108">Trois étapes de base sont nécessaires pour implémenter un éditeur d'expressions personnalisé :</span><span class="sxs-lookup"><span data-stu-id="c00f0-108">Three basic steps are needed to implement a custom expression editor:</span></span>  
  
1.  <span data-ttu-id="c00f0-109">Implémentez l'interface <xref:System.Activities.Presentation.View.IExpressionEditorService>.</span><span class="sxs-lookup"><span data-stu-id="c00f0-109">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="c00f0-110">Cette interface gère la création et la destruction des éditeurs d'expression.</span><span class="sxs-lookup"><span data-stu-id="c00f0-110">This interface manages the creation and destruction of expression editors.</span></span>  
  
2.  <span data-ttu-id="c00f0-111">Implémentez l'interface <xref:System.Activities.Presentation.View.IExpressionEditorInstance>.</span><span class="sxs-lookup"><span data-stu-id="c00f0-111">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface.</span></span> <span data-ttu-id="c00f0-112">Cette interface implémente l'interface utilisateur d'édition d'expressions.</span><span class="sxs-lookup"><span data-stu-id="c00f0-112">This interface implements the UI for expression editing UI.</span></span>  
  
3.  <span data-ttu-id="c00f0-113">Publiez <xref:System.Activities.Presentation.View.IExpressionEditorService> dans votre application de workflow réhébergée.</span><span class="sxs-lookup"><span data-stu-id="c00f0-113">Publish the <xref:System.Activities.Presentation.View.IExpressionEditorService> in your rehosted workflow application.</span></span>  
  
## <a name="implementing-a-custom-expression-editor-in-a-class-library"></a><span data-ttu-id="c00f0-114">Implémentation d'un éditeur d'expressions personnalisé dans une bibliothèque de classes</span><span class="sxs-lookup"><span data-stu-id="c00f0-114">Implementing a Custom Expression Editor in a Class Library</span></span>  
 <span data-ttu-id="c00f0-115">Voici un exemple de code pour une classe `MyEditorService` (preuve de concept) qui implémente l'interface <xref:System.Activities.Presentation.View.IExpressionEditorService> contenue dans un projet de bibliothèque MyExpressionEditorService.</span><span class="sxs-lookup"><span data-stu-id="c00f0-115">Here is a sample of code for a (proof of concept) `MyEditorService` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface is contained in a MyExpressionEditorService library project.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Activities.Presentation.View;  
using System.Activities.Presentation.Hosting;  
using System.Activities.Presentation.Model;  
  
namespace MyExpressionEditorService  
{  
    public class MyEditorService : IExpressionEditorService  
    {  
        public void CloseExpressionEditors()  
        {  
  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, System.Windows.Size initialSize)  
                {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType)  
            {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType, System.Windows.Size initialSize)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public void UpdateContext(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces)  
        {  
  
        }  
  
    }  
}  
```  
  
 <span data-ttu-id="c00f0-116">Voici le code d'une classe `MyExpressionEditorInstance` qu'implémente l'interface <xref:System.Activities.Presentation.View.IExpressionEditorInstance> dans un projet de bibliothèque MyExpressionEditorService.</span><span class="sxs-lookup"><span data-stu-id="c00f0-116">Here is the code for a `MyExpressionEditorInstance` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface in a MyExpressionEditorService library project.</span></span>  
  
```  
using System;  
using System.Activities.Presentation.View;  
using System.Windows;  
using System.Reflection;  
using System.Windows.Controls;  
  
namespace MyExpressionEditorService  
{  
    public class MyExpressionEditorInstance : IExpressionEditorInstance  
    {  
        private TextBox textBox = new TextBox();  
  
        public bool AcceptsReturn { get; set; }  
        public bool AcceptsTab { get; set; }  
        public bool HasAggregateFocus {  
            get  
            {  
                return true;  
            }  
        }  
  
        public System.Windows.Controls.ScrollBarVisibility HorizontalScrollBarVisibility { get; set; }  
        public System.Windows.Controls.Control HostControl {  
            get  
            {  
                return textBox;  
            }  
        }  
        public int MaxLines { get; set; }  
        public int MinLines { get; set; }  
        public string Text { get; set; }  
        public System.Windows.Controls.ScrollBarVisibility VerticalScrollBarVisibility { get; set; }  
  
        public event EventHandler Closing;  
        public event EventHandler GotAggregateFocus;  
        public event EventHandler LostAggregateFocus;  
        public event EventHandler TextChanged;  
  
        public bool CanCompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCopy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanDecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanGlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanIncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanPaste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanQuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanRedo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanUndo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
  
        public void ClearSelection()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public void Close()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public bool CompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Copy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Cut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool DecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public void Focus()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public string GetCommittedText()  
        {  
            return "CommittedText";  
        }  
        public bool GlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool IncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool ParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Paste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool QuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Redo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Undo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
    }  
}  
```  
  
### <a name="publishing-a-custom-expression-editor-in-a-wpf-project"></a><span data-ttu-id="c00f0-117">Publication d'un éditeur d'expressions personnalisé dans un projet WPF</span><span class="sxs-lookup"><span data-stu-id="c00f0-117">Publishing a Custom Expression Editor in a WPF Project</span></span>  
 <span data-ttu-id="c00f0-118">Voici le code qui montre comment héberger à nouveau le concepteur dans une application [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] et comment créer et publier le service `MyEditorService`.</span><span class="sxs-lookup"><span data-stu-id="c00f0-118">Here is the code that shows how to rehost the designer in a [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application and how to create and publish the `MyEditorService` service.</span></span> <span data-ttu-id="c00f0-119">Avant d'utiliser ce code, ajoutez une référence au projet de bibliothèque MyExpressionEditorService du projet qui contient l'application avalon2.</span><span class="sxs-lookup"><span data-stu-id="c00f0-119">Before using this code, add a reference to the MyExpressionEditorService library project from the project that contains the avalon2 application.</span></span>  
  
```  
using System.Windows;  
using System.Windows.Controls;  
using System.Activities.Presentation;  
using System.Activities.Statements;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation.View;  
using MyExpressionEditorService;  
  
namespace WpfApplication1  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
  
        private MyEditorService expressionEditorService;  
        public MainWindow()  
        {  
            InitializeComponent();  
            new DesignerMetadata().Register();  
            createDesigner();  
        }  
  
        public void createDesigner()  
        {  
            WorkflowDesigner designer = new WorkflowDesigner();  
            Sequence root = new Sequence()  
            {  
                Activities = {  
                new Assign(),  
                new WriteLine()}  
            };  
  
            designer.Load(root);  
  
            Grid.SetColumn(designer.View, 0);  
  
            // Create ExpressionEditorService   
            this.expressionEditorService = new MyEditorService();  
  
            // Publish the instance of MyEditorService.  
            designer.Context.Services.Publish<IExpressionEditorService>(this.expressionEditorService);  
  
            MyGrid.Children.Add(designer.View);  
        }  
    }  
}  
```  
  
### <a name="notes"></a><span data-ttu-id="c00f0-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="c00f0-120">Notes</span></span>  
 <span data-ttu-id="c00f0-121">Si vous utilisez un **ExpressionTextBox** contrôle dans un concepteur d’activités personnalisées, il n’est pas nécessaire créer et détruire les éditeurs d’expressions à l’aide de la <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> et <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> méthodes de la <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span><span class="sxs-lookup"><span data-stu-id="c00f0-121">If you are using an **ExpressionTextBox** control in a custom activity designer, it is not necessary to create and destroy expression editors using the <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> and <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> methods of the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="c00f0-122">La classe <xref:System.Activities.Presentation.View.ExpressionTextBox> gère cet aspect pour vous.</span><span class="sxs-lookup"><span data-stu-id="c00f0-122">The <xref:System.Activities.Presentation.View.ExpressionTextBox> class manages this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c00f0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c00f0-123">See Also</span></span>  
 <xref:System.Activities.Presentation.View.IExpressionEditorService>  
 <xref:System.Activities.Presentation.View.IExpressionEditorInstance>  
 [<span data-ttu-id="c00f0-124">Utilisation d’ExpressionTextBox dans un concepteur d’activités personnalisées</span><span class="sxs-lookup"><span data-stu-id="c00f0-124">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
