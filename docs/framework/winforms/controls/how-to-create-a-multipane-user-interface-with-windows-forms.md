---
title: "Comment : créer une interface utilisateur à plusieurs volets à l'aide des Windows Forms"
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
- SplitContainer control [Windows Forms], examples
- ListView control [Windows Forms], examples
- RichTextBox control [Windows Forms], examples
- Panel control [Windows Forms], examples
- TreeView control [Windows Forms], examples
- Splitter control [Windows Forms], examples
ms.assetid: e79f6bcc-3740-4d1e-b46a-c5594d9b7327
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f29fb5fc4f873431471cd1c037446a5157d5f07c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms"></a><span data-ttu-id="eff5d-102">Comment : créer une interface utilisateur à plusieurs volets à l'aide des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eff5d-102">How to: Create a Multipane User Interface with Windows Forms</span></span>
<span data-ttu-id="eff5d-103">Dans la procédure suivante, vous allez créer une interface utilisateur à plusieurs volets semblable à celle utilisée dans Microsoft Outlook, avec une **dossier** liste, un **Messages** volet et un **aperçu** volet.</span><span class="sxs-lookup"><span data-stu-id="eff5d-103">In the following procedure, you will create a multipane user interface that is similar to the one used in Microsoft Outlook, with a **Folder** list, a **Messages** pane, and a **Preview** pane.</span></span> <span data-ttu-id="eff5d-104">Cette disposition est obtenue principalement par le biais d’ancrage de contrôles dans le formulaire.</span><span class="sxs-lookup"><span data-stu-id="eff5d-104">This arrangement is achieved chiefly through docking controls with the form.</span></span>  
  
 <span data-ttu-id="eff5d-105">Lorsque vous ancrez un contrôle, vous déterminez le bord du conteneur parent auquel un contrôle est attaché.</span><span class="sxs-lookup"><span data-stu-id="eff5d-105">When you dock a control, you determine which edge of the parent container a control is fastened to.</span></span> <span data-ttu-id="eff5d-106">Par conséquent, si vous définissez la <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Right>, le bord droit du contrôle sera ancré sur le bord droit de son contrôle parent.</span><span class="sxs-lookup"><span data-stu-id="eff5d-106">Thus, if you set the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Right>, the right edge of the control will be docked to the right edge of its parent control.</span></span> <span data-ttu-id="eff5d-107">En outre, le bord ancré du contrôle est redimensionné pour correspondre à celui de son contrôle conteneur.</span><span class="sxs-lookup"><span data-stu-id="eff5d-107">Additionally, the docked edge of the control is resized to match that of its container control.</span></span> <span data-ttu-id="eff5d-108">Pour plus d’informations sur la façon dont <xref:System.Windows.Forms.SplitContainer.Dock%2A> fonctionne de la propriété, consultez [Comment : ancrer des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="eff5d-108">For more information about how the <xref:System.Windows.Forms.SplitContainer.Dock%2A> property works, see [How to: Dock Controls on Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).</span></span>  
  
 <span data-ttu-id="eff5d-109">Cette procédure se concentre sur la disposition du <xref:System.Windows.Forms.SplitContainer> et d’autres contrôles sur le formulaire, et non sur l’ajout de fonctionnalités pour que l’application ressemble à Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="eff5d-109">This procedure focuses on arranging the <xref:System.Windows.Forms.SplitContainer> and the other controls on the form, not on adding functionality to make the application mimic Microsoft Outlook.</span></span>  
  
 <span data-ttu-id="eff5d-110">Pour créer cette interface utilisateur, vous placez tous les contrôles dans un <xref:System.Windows.Forms.SplitContainer> contrôle, qui contient un <xref:System.Windows.Forms.TreeView> contrôle dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="eff5d-110">To create this user interface, you place all the controls within a <xref:System.Windows.Forms.SplitContainer> control, which contains a <xref:System.Windows.Forms.TreeView> control in the left-hand panel.</span></span> <span data-ttu-id="eff5d-111">Le volet droit de la <xref:System.Windows.Forms.SplitContainer> contrôle contient un deuxième <xref:System.Windows.Forms.SplitContainer> contrôler avec un <xref:System.Windows.Forms.ListView> contrôle ci-dessus un <xref:System.Windows.Forms.RichTextBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="eff5d-111">The right-hand panel of the <xref:System.Windows.Forms.SplitContainer> control contains a second <xref:System.Windows.Forms.SplitContainer> control with a <xref:System.Windows.Forms.ListView> control above a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="eff5d-112">Ces <xref:System.Windows.Forms.SplitContainer> contrôles permettent un redimensionnement indépendant des autres contrôles sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="eff5d-112">These <xref:System.Windows.Forms.SplitContainer> controls enable independent resizing of the other controls on the form.</span></span> <span data-ttu-id="eff5d-113">Vous pouvez adapter les techniques présentées dans cette procédure pour élaborer les interfaces utilisateur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="eff5d-113">You can adapt the techniques in this procedure to craft custom user interfaces of your own.</span></span>  
  
### <a name="to-create-an-outlook-style-user-interface-programmatically"></a><span data-ttu-id="eff5d-114">Pour créer une interface utilisateur de style Outlook par programmation</span><span class="sxs-lookup"><span data-stu-id="eff5d-114">To create an Outlook-style user interface programmatically</span></span>  
  
1.  <span data-ttu-id="eff5d-115">Dans un formulaire, déclarez chaque contrôle constituant votre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="eff5d-115">Within a form, declare each control that comprises your user interface.</span></span> <span data-ttu-id="eff5d-116">Pour cet exemple, utilisez le <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, et <xref:System.Windows.Forms.RichTextBox> permettant de reproduire l’interface utilisateur de Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="eff5d-116">For this example, use the <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer>, and <xref:System.Windows.Forms.RichTextBox> controls to mimic the Microsoft Outlook user interface.</span></span>  
  
    ```vb  
    Private WithEvents treeView1 As System.Windows.Forms.TreeView  
    Private WithEvents listView1 As System.Windows.Forms.ListView  
    Private WithEvents richTextBox1 As System.Windows.Forms.RichTextBox  
    Private WithEvents splitContainer1 As _  
        System.Windows.Forms.SplitContainer  
    Private WithEvents splitContainer2 As _  
        System.Windows.Forms.SplitContainer  
    ```  
  
    ```csharp  
    private System.Windows.Forms.TreeView treeView1;  
    private System.Windows.Forms.ListView listView1;  
    private System.Windows.Forms.RichTextBox richTextBox1;  
    private System.Windows.Forms. SplitContainer splitContainer2;  
    private System.Windows.Forms. SplitContainer splitContainer1;  
    ```  
  
2.  <span data-ttu-id="eff5d-117">Créer une procédure qui définit votre interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="eff5d-117">Create a procedure that defines your user interface.</span></span> <span data-ttu-id="eff5d-118">Le code suivant définit les propriétés afin que le formulaire ressemble à l’interface utilisateur dans Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="eff5d-118">The following code sets the properties so that the form will resemble the user interface in Microsoft Outlook.</span></span> <span data-ttu-id="eff5d-119">Toutefois, à l’aide d’autres contrôles ou station d’accueil différemment, il est tout aussi facile de créer d’autres interfaces utilisateur qui sont tout aussi flexibles.</span><span class="sxs-lookup"><span data-stu-id="eff5d-119">However, by using other controls or docking them differently, it is just as easy to create other user interfaces that are equally flexible.</span></span>  
  
    ```vb  
    Public Sub CreateOutlookUI()  
        ' Create an instance of each control being used.  
        Me.components = New System.ComponentModel.Container()  
        Me.treeView1 = New System.Windows.Forms.TreeView()  
        Me.listView1 = New System.Windows.Forms.ListView()  
        Me.richTextBox1 = New System.Windows.Forms.RichTextBox()  
        Me.splitContainer1 = New System.Windows.Forms.SplitContainer()  
        Me.splitContainer2= New System.Windows.Forms. SplitContainer()  
  
        ' Should you develop this into a working application,  
        ' use the AddHandler method to hook up event procedures here.  
  
        ' Set properties of TreeView control.  
        ' Use the With statement to avoid repetitive code.  
        With Me.treeView1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 0  
            .Nodes.Add("treeView")  
        End With  
  
    ' Set properties of ListView control.  
       With Me.listView1  
          .Dock = System.Windows.Forms.DockStyle.Top  
          .TabIndex = 2  
          .Items.Add("listView")  
       End With  
  
    ' Set properties of RichTextBox control.  
       With Me.richTextBox1  
          .Dock = System.Windows.Forms.DockStyle.Fill  
          .TabIndex = 3  
          .Text = "richTextBox1"  
       End With  
  
        ' Set properties of the first SplitContainer control.  
        With Me.splitContainer1  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 1  
            .SplitterWidth = 4  
            .SplitterDistance = 150  
            .Orientation = Orientation.Horizontal  
            .Panel1.Controls.Add(Me.listView1)  
            .Panel2.Controls.Add(Me.richTextBox1)  
    End With  
  
        ' Set properties of the second SplitContainer control.  
        With Me.splitContainer2  
            .Dock = System.Windows.Forms.DockStyle.Fill  
            .TabIndex = 4  
            .SplitterWidth = 4  
            .SplitterDistance = 100  
            .Panel1.Controls.Add(Me.treeView1)  
            .Panel2.Controls.Add(Me.SplitContainer1)  
    End With  
  
    ' Add the main SplitContainer control to the form.  
        Me.Controls.Add(Me.splitContainer2)  
        Me.Text = "Intricate UI Example"  
    End Sub  
    ```  
  
    ```csharp  
    public void createOutlookUI()  
    {  
        // Create an instance of each control being used.  
        treeView1 = new System.Windows.Forms.TreeView();  
        listView1 = new System.Windows.Forms.ListView();  
        richTextBox1 = new System.Windows.Forms.RichTextBox();  
        splitContainer2 = new System.Windows.Forms.SplitContainer();  
        splitContainer1 = new System.Windows.Forms.SplitContainer();  
  
        // Insert code here to hook up event methods.  
  
        // Set properties of TreeView control.  
        treeView1.Dock = System.Windows.Forms.DockStyle.Fill;  
        treeView1.TabIndex = 0;  
        treeView1.Nodes.Add("treeView");  
  
        // Set properties of ListView control.  
        listView1.Dock = System.Windows.Forms.DockStyle.Top;  
        listView1.TabIndex = 2;  
        listView1.Items.Add("listView");  
  
        // Set properties of RichTextBox control.  
        richTextBox1.Dock = System.Windows.Forms.DockStyle.Fill;  
        richTextBox1.TabIndex = 3;  
        richTextBox1.Text = "richTextBox1";  
  
        // Set properties of first SplitContainer control.  
        splitContainer1.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 1;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 150;  
        splitContainer2.Orientation = Orientation.Horizontal;  
        splitContainer2.Panel1.Controls.Add(this.listView1);  
        splitContainer2.Panel1.Controls.Add(this.richTextBox1);  
  
        // Set properties of second SplitContainer control.  
        splitContainer2.Dock = System.Windows.Forms.DockStyle.Fill;  
        splitContainer2.TabIndex = 4;  
        splitContainer2.SplitterWidth = 4;  
        splitContainer2.SplitterDistance = 100;  
        splitContainer2.Panel1.Controls.Add(this.treeView1);  
        splitContainer2.Panel1.Controls.Add(this.splitContainer1);  
  
        // Add the main SplitContainer control to the form.  
        this.Controls.Add(this.splitContainer2);  
        this.Text = "Intricate UI Example";  
    }  
    ```  
  
3.  <span data-ttu-id="eff5d-120">Dans [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], ajoutez un appel à la procédure que vous venez de créer dans le `New()` procédure.</span><span class="sxs-lookup"><span data-stu-id="eff5d-120">In [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], add a call to the procedure you just created in the `New()` procedure.</span></span> <span data-ttu-id="eff5d-121">Dans [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], ajoutez la ligne de code au constructeur de la classe de formulaire.</span><span class="sxs-lookup"><span data-stu-id="eff5d-121">In [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], add this line of code to the constructor for the form class.</span></span>  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="eff5d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eff5d-122">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="eff5d-123">SplitContainer, contrôle</span><span class="sxs-lookup"><span data-stu-id="eff5d-123">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [<span data-ttu-id="eff5d-124">Guide pratique pour créer une interface utilisateur à plusieurs volets avec des Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="eff5d-124">How to: Create a Multipane User Interface with Windows Forms Using the Designer</span></span>](../../../../docs/framework/winforms/controls/create-a-multipane-user-interface-with-wf-using-the-designer.md)
