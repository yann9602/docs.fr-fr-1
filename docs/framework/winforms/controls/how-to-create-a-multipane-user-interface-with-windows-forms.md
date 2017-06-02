---
title: "Comment&#160;: cr&#233;er une interface utilisateur &#224; plusieurs volets &#224; l&#39;aide des Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ListView (contrôle Windows Forms), exemples"
  - "Panel (contrôle Windows Forms), exemples"
  - "RichTextBox (contrôle Windows Forms), exemples"
  - "SplitContainer (contrôle Windows Forms), exemples"
  - "Splitter (contrôle Windows Forms), exemples"
  - "TreeView (contrôle Windows Forms), exemples"
ms.assetid: e79f6bcc-3740-4d1e-b46a-c5594d9b7327
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Comment&#160;: cr&#233;er une interface utilisateur &#224; plusieurs volets &#224; l&#39;aide des Windows Forms
Dans la procédure suivante, vous créerez une interface utilisateur à plusieurs volets qui est semblable à celle qui est utilisée dans Microsoft Outlook, avec une liste **Dossier**, un volet **Messages** et un volet **Aperçu**.  Cette disposition est obtenue principalement en ancrant des contrôles sur le formulaire.  
  
 Lorsque vous ancrez un contrôle, vous déterminez le bord du conteneur parent auquel un contrôle est attaché.  Par conséquent, si vous affectez à la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle>, le bord droit du contrôle sera ancré au bord droit de son contrôle parent.  En outre, le bord ancré du contrôle est redimensionné pour correspondre à celui de son contrôle conteneur.  Pour plus d'informations sur le fonctionnement de la propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A>, consultez [Comment : ancrer des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md).  
  
 Cette procédure se concentre sur la disposition du contrôle <xref:System.Windows.Forms.SplitContainer> et des autres contrôles sur le formulaire, et non sur l'ajout de fonctionnalités pour que l'application ressemble à Microsoft Outlook.  
  
 Pour créer cette interface utilisateur, vous placez tous les contrôles dans un contrôle <xref:System.Windows.Forms.SplitContainer> qui contient un contrôle <xref:System.Windows.Forms.TreeView> dans le panneau gauche.  Le panneau droit du contrôle <xref:System.Windows.Forms.SplitContainer> contient un deuxième contrôle <xref:System.Windows.Forms.SplitContainer> avec un contrôle <xref:System.Windows.Forms.ListView> au\-dessus d'un contrôle <xref:System.Windows.Forms.RichTextBox>.  Ces contrôles <xref:System.Windows.Forms.SplitContainer> permettent un redimensionnement indépendant des autres contrôles sur le formulaire.  Les techniques présentées dans cette procédure vous aideront à créer vos propres interfaces utilisateur personnalisées.  
  
### Pour créer par programme une interface utilisateur du style Outlook  
  
1.  Dans un formulaire, déclarez chaque contrôle constituant votre interface utilisateur.  Pour cet exemple, utilisez les contrôles <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.SplitContainer> et <xref:System.Windows.Forms.RichTextBox> pour reproduire l'interface utilisateur Microsoft Outlook.  
  
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
  
2.  Créez une procédure définissant votre interface utilisateur.  Le code suivant définit les propriétés de telle sorte que le formulaire ressemble à l'interface utilisateur de Microsoft Outlook.  Toutefois, en utilisant d'autres contrôles ou en les ancrant différemment, il est tout aussi facile de créer d'autres interfaces utilisateur présentant une souplesse équivalente.  
  
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
  
3.  Dans [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], ajoutez un appel à la procédure que vous venez de créer dans la procédure `New()`.  Dans [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], ajoutez cette ligne de code au constructeur de la classe Form.  
  
    ```vb  
    ' Add this to the New procedure.  
    CreateOutlookUI()  
  
    ```  
  
    ```csharp  
    // Add this to the form class's constructor.  
    createOutlookUI();  
  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.SplitContainer>   
 [SplitContainer, contrôle](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)   
 [Comment : créer une interface utilisateur à plusieurs volets avec des Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/create-a-multipane-user-interface-with-wf-using-the-designer.md)